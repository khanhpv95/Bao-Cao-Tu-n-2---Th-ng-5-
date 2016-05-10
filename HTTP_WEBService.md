#Tìm hiểu giao thức HTTP và dịch vụ Web
##Mục Lục
##[1. Giao thức HTTP.](#http)
##[2. Dịch vụ web.](#web)


<a name="http"></a>
##Nội dung
##1. Giao thức HTTP
##1.1 Khái niệm
Hypertext Transfer Protocol (HTTP) là một giao thức không trạng thái (stateless) nằm ở tầng ứng dụng, đảm nhiệm việc giao tiếp giữa các hệ thống phân tán với nhau, và nó là nền tảng của web. 

##1.2 Khái quát về HTTP
<ul>
<li>HTTP cho phép giao tiếp giữa rất nhiều loại server/client với nhau, chủ yếu thông qua TCP/IP. Cổng giao tiếp chuẩn là 80. Giao tiếp giữa client và server dựa vào một cặp request/response. Client khởi tạo HTTP request và nhận HTTP response từ server gửi về.</li>

<li>HTTP request bao gồm hai thành phần quan trọng là URL và Verb (phương thức), được gửi từ client. Ở phía ngược lại, server trả về HTTP response trong đó chứa Status code và Message body.</li>
</ul>
##1.3 Định dạng HTTP request và HTTP resonse
Một HTTP request hoặc response có dạng như sau:

<img src="">

Trong đó:

**a. start-line**

<ul>
<li>đối với request start-line là Request-Line

<img src="">
  <ul>
    <li>Verb là GET, POST, PUT, DELETE, OPTIONS, HEAD hoặc TRACE</li>
    <li>URL là đường dẫn tới địa chỉ yêu cầu</li>
    <li>HTTP-Version là "HTTP/1.1"</li>
    </ul>
</li>

<li>đối với response là Status-Line

<img src="">
    <ul>
     <li>HTTP-Version là "HTTP/1.1"</li>
      <li>Status-Code là mã kết quả trả về</li>
      <li>Reason-Phrase là mô tả của Status-Code</li>
    </ul>
</li>

</ul>

**b. message-header**

<img src="">

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
    </ul>
    
    
    
    </li>
  
      
    <li>3xx: Redirection: Server thông báo cho client phải thực hiện thêm action để hoàn thành request.
    <ul>
      <li>301 Moved Permanently: resource đã được chuyển hoàn toàn tới địa chỉ trong trường Location của response.</li>
    </ul>
    
    
    </li>
      
    <li>4xx: Client Error: Lỗi phát hiện ở client.</li>
      
    <li>5xx: Server Error: Có lỗi xảy ra trong quá trình xử lý của server. Mã 500 Internal Server Error là phổ biến nhất.</li>
            
</ul>      







