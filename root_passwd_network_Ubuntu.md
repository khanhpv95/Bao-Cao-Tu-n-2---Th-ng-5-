#Tìm hiểu Ubuntu: Đặt password cho root, logout, login, kiểm tra về network.
##Mục Lục
##[1. Đặt password cho root](#passwd)
##[2. Login, logout](#login)
##[3. Kiểm tra về network](#network)
##[4. Tìm hiểu về địa chỉ 127.0.1.1](#loopback)

##Nội Dung

<a name="passwd"></a>

##1. Đặt password cho root.
<ul>
<li>Bước 1: Sử dụng câu lệnh  `sudo passwd root`  để đặt password cho root.</li>
Tại đây, ta nhập lần lượt password cho user, nhập password cho tài khoản root và xác nhận lại mật khẩu.

<img src="http://i.imgur.com/4M6eNep.png">


Tại đây, ta nhập lần lượt password cho user, nhập password cho tài khoản root và xác nhận lại mật khẩu.

<li>Bước 2: logout và đăng nhập bằng tài khoản root để kiểm tra.</li>

<img src="http://i.imgur.com/86gkW39.png">
</ul>

<a name="login"></a>
##2. Login và logout trong Ubuntu.
###2.1 Login 
Để login vào Ubuntu, ta có thể sử dụng tài khoản user hoặc tài khoản root để đăng nhập.
Chú ý: Có thể sử dụng tài khoản user để quản trị server nhằm tránh việc mất tài khoản root. 
Khi sử dụng tài khoản user để quản trị ta phải sử dụng cú pháp như sau:
`sudo + command`
###2.2 Logout
Cũng giống như những dòng server khác như centos việc logout vô cùng đơn giản. 
Sử dụng cú pháp: `logout`

##3. kiểm tra về network 
Để kiểm tra network, ta sử dụng câu lệnh `ip a` để kiểm tra xem card mạng đã được đặt ip chưa.
Nếu chưa được đặt thì ta có thể đặt ip tạm thời hoặc đặt ip cho cho card.
Tham khảo bài viết: https://github.com/khanhpv95/baocao1/blob/master/IPtinhdong.md


