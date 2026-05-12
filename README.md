# SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ TẠO docker ccompose chứa:
Mariadb: sử dụng image: mariadb:latest để làm hệ quản trị csdl cho wordpress
Phpmyadmin: sư dụng image: phpmyadmin:latest để đăng nhập vào mariadb rồi tạo csdl trống (chỉ để xem, ko cần tạo bảng từ đây, wordpress sẽ làm hết)
WordPress: Sử dụng image: wordpress:latest, truyền các tham số môi trường cho wordpress là các thông tin truy cập csdl mariadb, tạo bởi Phpmyadmin
Yêu cầu: sau khi có 3 service này trong file docker-compose.yml :
Cấu hình để hệ thống chạy
Sử dụng cloudflare tunnel để public web này lên 1 sub-domain
Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...
Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ...
Nhận xét việc sử dụng mã nguồn mở wordpress để tạo website (tốn công sức thế nào, dễ/khó dùng ra sao, tốn kém tài nguyên(ssh/ram) của máy chủ ra sao,....)
# Bài làm
### Bước 1: Tạo file docker-compose.yml
Tạo file: nano docker-compose.yml
<img width="1153" height="929" alt="image" src="https://github.com/user-attachments/assets/acd36090-962d-4a51-a07f-55ccdfec4f4b" />
### Bước 2 : Chạy docker compose
Chạy:
docker compose up -d
<img width="807" height="911" alt="image" src="https://github.com/user-attachments/assets/067ae6c4-f17b-41a4-ab5a-2207c1cde514" />

Kiểm tra container:
docker ps
<img width="952" height="916" alt="image" src="https://github.com/user-attachments/assets/5f0aab9b-634d-4e20-8e68-2cf1ccd2b142" />
### Bước 3: Truy cập website
WordPress
http://IP_UBUNTU:8001
phpMyAdmin
http://IP_UBUNTU:8082
Nếu chưa biết IP Ubuntu
Chạy:
ip a
<img width="727" height="613" alt="image" src="https://github.com/user-attachments/assets/ffff6c8c-3cdb-449a-9f15-27c6bc37479c" />
kết quả IP Ubuntu của bạn là:
192.168.1.13
Bây giờ mở WordPress
Trên trình duyệt Windows hoặc Ubuntu mở:
http://192.168.1.13:8001
<img width="1591" height="882" alt="image" src="https://github.com/user-attachments/assets/12b95e60-170b-410f-9434-729e96a6edf1" />
<img width="1723" height="998" alt="image" src="https://github.com/user-attachments/assets/16cc775b-5f81-4b28-aff0-840e7ea3ef77" />

phpMyAdmin
Mở:
http://192.168.1.13:8082
### Tạo bài viết 1
Giới thiệu bản thân
Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, .
<img width="1721" height="998" alt="image" src="https://github.com/user-attachments/assets/1c292364-8fb4-4524-9ba9-69530f231996" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/061e9304-f087-424b-8ef3-a4e6cabe925e" />

 ### Tạo bài viết 2
   Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ...
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0146e6e6-5a1a-440d-ae77-87e214b53b62" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41ff5d13-159d-4a00-b936-31fa4654503b" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6bd82164-f404-41bd-bf86-b0c6db7ce414" />
Sử dụng cloudflare tunnel để public web này lên 1 sub-domain
cloudflared --version
LOGIN CLOUDFLARE: cloudflared tunnel login
TẠO TUNNEL
chạy: cloudflared tunnel create wordpress-tunnel
Tạo file config: nano ~/.cloudflared/config.yml
<img width="1172" height="677" alt="image" src="https://github.com/user-attachments/assets/d01c6003-f2fa-4f8b-8919-45ca3072b09b" />
Vào Wordpess -> cài đặt -> tổng quan và sửa URL
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/63be88a8-b98a-442a-a7e6-9dddd83c2b7c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7b224076-3ab0-49f3-a9a5-a0959f4e4016" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f4a472d7-61ef-4bf3-94b6-a763e8fbcc7a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a4382317-d97f-4b40-90af-724e19a91605" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f6aa31ea-1232-4c60-b3f5-f42b8a52846c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1e442a00-0428-4e48-adc3-935b70ead9f3" />
### Nhận xét việc sử dụng mã nguồn mở wordpress để tạo website (tốn công sức thế nào, dễ/khó dùng ra sao, tốn kém tài nguyên(ssh/ram) của máy chủ ra sao,....)
WordPress là một mã nguồn mở mạnh và phổ biến giúp tạo website nhanh chóng mà không cần lập trình quá nhiều. Khi kết hợp với Docker Compose, việc triển khai WordPress trở nên thuận tiện hơn vì có thể quản lý MariaDB, PhpMyAdmin và WordPress bằng container.

Ưu điểm:

Cài đặt nhanh
Dễ sử dụng
Có nhiều plugin và theme
Hỗ trợ đăng bài viết, ảnh, video dễ dàng
Nhược điểm:
Tốn RAM và tài nguyên hơn website tĩnh
Nếu dùng nhiều plugin website có thể chậm
Cần cấu hình bảo mật khi public lên Internet
Qua bài thực hành em học được cách sử dụng Docker Compose, quản lý container, cấu hình WordPress với MariaDB và public website bằng Cloudflare Tunnel.




