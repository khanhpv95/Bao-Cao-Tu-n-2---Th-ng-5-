#Tìm hiểu giao thức và dịch vụ DNS
##Mục lục
##[1. Định nghĩa](#dinhnghia)
##[2. Công Dụng](#congdung)
##[3. Triển khai](#trienkhai)
##[4. Cài đặt](#caidat)
##[5. Tìm hiểu thuộc tính của zone thuận, nghịch](#zone)


##Nội Dung

<a name="dinhngia"></a>

##1. Định nghĩa

DNS có thể được hiểu theo 2 cách, tùy vào số lượng dịch vụ được cài đặt trên server.

- DNS: (Domain name system) DNS đc hiểu là hệ thống phân dải tên miền khi và chỉ khi có nhiều dịch vụ được cài đặt trên 1 server , khi đó DNS đc coi là 1 hệ thống phân dải tên miền cho nhiều dịch vụ như WEB, MAIL, File ....

- DNS: (Domain name service) DNS đc hiểu là dịch vụ phân dải tên miền khi chỉ có 1 đơn lẻ dịch vụ được cài đặt trên 1 server.


<a name="congdung"></a>

##2. Công dụng

DNS dùng để giúp phân dải tên miền. Cụ thể, DNS giúp phân dải từ địa chỉ ip ra tên miền, giúp người dùng không cần phài nhớ địa chỉ ip của dịch vụ. ví dụ: DNS của google là 8.8.8.8


<a name="trienkhai"></a>

##3. Triển khai

- Công dụng quan trọng nhất của DNS là phân giải tên miền, vì vậy, DNS có thể được triển khai gắn liền với các dịch vụ như: WEB, mail, file ... 
- Ngoài ra, khi thiết lập DNS trên network, DNS còn giúp tăng tốc trình duyệt web. Ví dụ, ta trỏ địa chỉ DNS trong IPv4 configure  sang DNS của google: 8.8.8.8

<a name="caidat"></a>

##4.Cài đặt

Hướng dẫn cài đặt DNS theo sơ đồ sau: [DNS](https://drive.google.com/drive/folders/0B48XCZnnqa_ieEpwTkRGRFc2TFk)

<a name="zone"></a>

##5. Tìm hiểu thuộc tính của zone thuận, nghịch

Sau đây là ví dụ về 1 zone thuận và 1 zone nghịch:

**zone thuận**

<img src="http://i.imgur.com/B4Pn1qR.png">

**zone nghịch**

<img src="http://i.imgur.com/AboeLWA.png">


###5.1 SOA 

SOA: (Start of authority) chỉ ra rằng máy chủ Name Server là nơi cung cấp thông tin tin cậy từ dữ liệu có trong zone. Cú pháp của record SOA:
 ```sh
[tên-miền] IN SOA [tên-server-dns] [địa-chỉ-email] (
Rerial number;
Refresh number;
Retry number;
Expire number;
Minimum TTL;
 ```
- Serial : Áp dụng cho mọi dữ liệu trong zone và là 1 số nguyên. Ở đây họ sử dụng đinh dạng YYYYMMDDNN, trong đó YYYY là năm, MM là tháng, DD là ngày, NN số lần sửa đổi dữ liệu zone trong ngày. Vd: 2011071001

- Refresh: Chỉ ra khoảng thời gian máy chủ Secondary kiểm tra dữ liệu zone trên máy Primary để cập nhật nếu cần.

-  Retry: nếu máy chủ Secondary không kết nối được với máy chủ Primary theo thời hạn mô tả trong refresh.

-  Expire : Nếu sau khoảng thời gian này mà máy chủ Secondary không kết nối được với máy chủ Primary thì dữ liệu zone trên máy Secondary sẽ bị quá hạn.

- Minimum TTL: TTL viết tắt của time to live. Giá trị này áp dụng cho mọi record trong zone và được đính kèm trong thông tin trả lời một truy vấn. Mục đích của nó là chỉ ra thời gian mà các máy chủ name server khác cache lại thông tin trả lời.

###5.2 NS

NS (Name Server): Mỗi name server cho zone sẽ có một NS record. Cú pháp khai báo:

[tên-domain] IN NS [DNS-Server_name]

ví dụ: `@  IN NS khanh-dns.hanu.vn.`

###5.3  A (Address) 

- Record A (Address) ánh xạ tên máy(hostname) vào địa chỉ IP. 

Ví dụ: `@ IN A 200.0.0.24`

###5.4 PTR (Pointer)

- Record PTR (pointer) dùng để ánh xạ địa chỉ IP thành hostname. 
- Ví dụ: `24 IN PTR khanh-dns.hanu.vn.`

##Tổng kết

Bài  viết đưa ra những thông tin về DNS. 
Cảm ơn đã theo dõi bài viết. Mọi ý kiến đóng góp xin gửi về địa chỉ email: khanhhh95@gmail.com.





  
































