#Tìm hiểu giao thức HTTP và dịch vụ Web
##Mục Lục
##[1. Giao thức HTTP.](#http)

- [1.1 Khái niệm](#khainiem)
- [1.2 khái quát về HTTP](#khaiquat)
- [1.3 Định dạng HTTP request và HTTP resonse](#dinhdang)

##[2. Dịch vụ web.](#web)

- [2.1 Định nghĩa](#dinhnghia)
- [2.2 Công dụng](#congdung)
- [2.3 Triển khai](#trienkhai)
- [2.4 Cài đặt](#caidat)

<a name="http"></a>
##Nội dung
##1. Giao thức HTTP

<a name="khainiem"></a>
##1.1 Khái niệm
Hypertext Transfer Protocol (HTTP) là một giao thức không trạng thái (stateless) nằm ở tầng ứng dụng, đảm nhiệm việc giao tiếp giữa các hệ thống phân tán với nhau, và nó là nền tảng của web. 

<a name="khaiquat"></a>
##1.2 Khái quát về HTTP
<ul>
<li>HTTP cho phép giao tiếp giữa rất nhiều loại server/client với nhau, chủ yếu thông qua TCP/IP. Cổng giao tiếp chuẩn là 80. Giao tiếp giữa client và server dựa vào một cặp request/response. Client khởi tạo HTTP request và nhận HTTP response từ server gửi về.</li>

<li>HTTP request bao gồm hai thành phần quan trọng là URL và Verb (phương thức), được gửi từ client. Ở phía ngược lại, server trả về HTTP response trong đó chứa Status code và Message body.</li>
</ul>

<a name="dinhdang"></a>
##1.3 Định dạng HTTP request và HTTP resonse
Một HTTP request hoặc response có dạng như sau:

<img src="http://i.imgur.com/yJVjQro.png">

Trong đó:

**a. start-line**

<ul>
<li>đối với request start-line là Request-Line

<img src="http://i.imgur.com/L8NM0wg.png">

  <ul>
    <li>Verb là GET, POST, PUT, DELETE, OPTIONS, HEAD hoặc TRACE</li>
    <li>URL là đường dẫn tới địa chỉ yêu cầu</li>
    <li>HTTP-Version là "HTTP/1.1"</li>
    </ul>
</li>

<li>đối với response là Status-Line

<ul>
    <li>HTTP-Version là "HTTP/1.1"</li>
    <li>Status-Code là mã kết quả trả về</li>
    <li>Reason-Phrase là mô tả của Status-Code</li>
</ul>

<img src="http://i.imgur.com/B6HO4ng.png">
</li>

</ul>

**b. message-header**

<img src="http://i.imgur.com/PC5YCLu.png">

Tham khảo danh sách các trường của meassage header tại: [wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

###c. Tìm hiểu về thuộc tính: `verb` `url` `Status code`
**c1. verb**

Client gửi request tới server bằng một số các phương thức thường dùng như:

<ul>
     <li>GET: được thiết kế để truy vấn dữ liệu, tài nguyên trên server, với các tham số và giá trị nằm ngay trên URL.</li>
      <li>POST: được dùng trong các trường hợp tạo ra sự thay đổi về dữ liệu, tài nguyên trên server như upload một file hoặc submit một web form.</li>
      <li>PUT: được thiết kế để cập nhật dữ liệu, tài nguyên trên server.</li>
      <li>DELETE: được thiết kế để xóa dữ liệu, tài nguyên trên server.</li>
</ul>
  
**c2. URL**

URL là một cấu trúc đơn giản thường bao gồm:

<ul>
     <li>protocol: http hoặc https</li>
      <li>host: tên miền server</li>
      <li>port: mặc định là 80</li>
      <li>resource path: đường dẫn tới resource trên server.</li>
      <li>query: truy vấn</li>
</ul>
  
  
**c3. Status code**

Status code là thông tin quan trọng server trả về cho client, cho biết kết quả xử lý request của server. Các loại status code thường gặp:
<ul>
    <li>1xx: Informational Message: Loại status code này được mô tả ở HTTP/1.1 và hoàn toàn mang tính chất tạm thời, client có thể bỏ qua chúng.</li>
      
    <li>2xx: Successful: Server trả về status dạng này khi đã xử lý thành công request của client. Đối với GET request, dữ liệu trả về nằm trong message body. Phổ biến nhất là mã 200 OK. Ngoài ra còn có:
    <ul>
      <li>202 Accepted: request từ client đã được chấp nhận nhưng có thể server không trả về kết quả cho client. Điều này hữu dụng trong trường hợp xử lý bất đồng bộ phía server: server thông báo cho client không phải tiếp tục chờ đợi cho tới khi quá trình xử lý trên server hoàn tất.</li>
      <li>204 No content: không có phần message body trong response.</li>
      <li>205 Reset content: tương tự như 204, nhưng mã trả về này yêu cầu client reset document view.</li>
      <li>206 Partial content: server chỉ gửi về một phần dữ liệu phụ thuộc và giá trị range header client gửi lên. Giá trị này được sử dụng bởi các tool hỗ trợ download như wget, IDM để phân mảnh dữ liệu thành nhiều phần nhằm tải về đồng thời hoặc hỗ trợ tiếp tục download khi bị ngắt giữa chừng.</li>
    </ul>
    </li>
  
      
    <li>3xx: Redirection: Server thông báo cho client phải thực hiện thêm action để hoàn thành request.
    <ul>
      <li>301 Moved Permanently: resource đã được chuyển hoàn toàn tới địa chỉ trong trường Location của response.</li>
      <li>303 See Other: resource được chuyển tạm thời tới địa chỉ trong trường Location của response.</li>
      <li>304 Not Modified: resource không thay đổi từ lần cuối cùng client gửi request, và client nên sử dụng dữ liệu đã lưu trong bộ nhớ cache. Điều này được thực hiện bằng cách khi gửi request, client gửi đi trường ETag là định danh của phần dữ liệu đã request lần trước, server so sánh với trường ETag ứng với dữ liệu của nó để kiểu tra sự thay đổi.</li>
    </ul>
    </li>
      
    <li>4xx: Client Error: Lỗi phát hiện ở client.
    <ul>
      <li>400 Bad Request: request không đúng định dạng, cú pháp.</li>
      <li>401 Unauthorized: client chưa xác thực.</li>
      <li>403 Forbidden: client không có quyền truy cập.</li>
      <li>404 Not Found: không tìm thấy resource.</li>
      <li>405 Method Not Allowed: phương thức (HTTP verb) không được server hỗ trợ.</li>
    <ul>
    </li>
    
   <li>5xx: Server Error: Có lỗi xảy ra trong quá trình xử lý của server. Mã 500 Internal Server Error là phổ biến nhất.
    <ul>
      <li>501 Not Implemented: server không hỗ trợ chức năng client yêu cầu.</li>
      <li>503 Service Unavailable: một thành phần xử lý trên server bị lỗi hoặc server bị quá tải.</li>
    </ul>
   
   </li>
</ul>    

<a name="web"></a>

##2. Dịch vụ web 

<a name="dinhnghia"></a>

###2.1 Định nghĩa
a, Khái niệm:

Là một hệ thống phần mềm được thiết kế để hỗ trợ khả năng tương tác giữa các ứng dụng trên các máy tính khác nhau thông qua mạng Internet, giao diện chung và sự gắn kết của nó được mô tả bằng XML.Tìm hiểu thêm về XML theo link: [XML](http://freetuts.net/xml-la-gi-cu-phap-can-ban-cua-xml-513.html). Web service là tài nguyên phần mềm có thể xác định bằng địa chỉ URL, thực hiện các chức năng và đưa ra các thông tin người dùng yêu cầu. 

b, Giao thức sử dụng: HTTP hoặc HTTPs

c, Port sử dụng: 80 (Dùng cho giao thức http), 443 (dùng cho giao thức https)

d, Đặc điểm: 

<ul>
<li>Cho phép client và server tương tác ngay cả trong môi trường khác nhau. (Ví dụ server chạy linux, client chạy windows).</li>
<li>Phần lớn được xây dựng dựa trên mã nguồn mở </li>
<li>Nó có thể triển khai bởi 1 phần mềm ứng dụng phía server (Ví dụ : PHP, Oracle Application server, Microsoft .NET)</li>
<li> Một Web service bao gồm có nhiều mô-đun và có thể công bố lên mạng Internet.</li>
</ul>

e, Cấu tạo:

<ul>
<li>Web server: lưu cơ sở dữ liệu, phần mềm ứng dụng web </li>
<li>Web Client: là các máy người dùng, người dùng truy cập vào web server thông qua việc nhập url vào trình duyện web như chrome, filefox ... </li>
</ul>


<a name="congdung"></a>

###2.2 Công dụng

Công dụng chính của website là cung cấp thông tin cho người dùng. website có thể đáp ứng hầu như toàn bộ nhu cầu của con người  như: giải trí, tìm kiếm thông tin, mua hàng ....

<a name="trienkhai> </a>


###2.3 Triển khai

Có thể triển khai đồng thời với dịch vụ DNS. DNS giúp người dùng không cần nhớ địa chỉ IP của website mà vẫn có thể truy cập được đến website 

<a name="caidat"></a>

###2.4 Cài đặt

Có 2 cách cài đặt dịch vụ web là cài đặt web bằng APACHE hoặc NGNIX. 

Hướng dẫn cài đặt tại: [Cài đặt](https://drive.google.com/drive/folders/0B48XCZnnqa_iSmlyRm41ZkhRcFk)


##3. Tổng kết

Bài viết cung cấp thông tin về giao thức HTTP và Dịch vụ web. Cảm ơn đã theo dõi.










