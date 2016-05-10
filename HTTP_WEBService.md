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






