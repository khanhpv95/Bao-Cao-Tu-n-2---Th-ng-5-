#Tìm hiểu Ubuntu: Đặt password cho root, logout, login, kiểm tra về network.
##Mục Lục
##[1. Đặt password cho root](#passwd)
##[2. Login, logout](#login)
##[3. Kiểm tra về network](#network)
##[4. Tìm hiểu về địa chỉ 127.0.0.1](#loopback)

##Nội Dung

<a name="passwd"></a>

##1. Đặt password cho root.
-Bước 1: Sử dụng câu lệnh `sudo passwd root` để đặt password chi root.
-Bước 2: logout và đăng nhập bằng tài khoản root để kiểm tra.

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

