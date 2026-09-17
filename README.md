# Enterprise Network Topology

> [🎥 XEM VIDEO DEMO & MINH CHỨNG KẾT QUẢ TRIỂN KHAI TRÊN YOUTUBE](https://youtu.be/zQlxyENyXIo)
>
> ▶️ **YOUTUBE**  |  **DEMO & MINH CHỨNG KẾT QUẢ**

---

## Tổng quan dự án

Repo này lưu trữ cấu hình và tài liệu cho một lab mạng doanh nghiệp mô phỏng môi trường triển khai thực tế, gồm:

- Tường lửa và định tuyến: pfSense
- Mạng nội bộ và DMZ: chia theo VLAN/segment riêng biệt
- Quản trị Active Directory và Group Policy Objects (GPO)
- Dịch vụ mail: Mailcow
- Reverse proxy và cân bằng tải: NGINX
- Sơ đồ kiến trúc mạng tổng thể của hệ thống

Mục tiêu chính là xây dựng một môi trường mạng doanh nghiệp có khả năng mô phỏng hoạt động sản xuất, bảo mật ranh giới mạng, quản lý người dùng và triển khai dịch vụ nội bộ.

---

## Kiến trúc hệ thống

Dự án này bao gồm các thành phần chính sau:

1. pfSense Firewall
   - Là thiết bị bảo vệ ranh giới mạng cho hệ thống
   - Cấu hình địa chỉ IP và định tuyến cho các segment mạng
   - Quản lý NAT, DHCP, DNS và kiểm soát truy cập mạng

2. Active Directory / GPO
   - Thiết lập miền Windows, quản trị người dùng và máy tính
   - Áp dụng chính sách theo nhóm qua GPO
   - Tích hợp các cấu hình bảo mật và thiết lập hệ thống máy trạm

3. Mail Server (Mailcow)
   - Triển khai môi trường email doanh nghiệp
   - Có thể dùng cho SMTP, IMAP, quản trị mail và dịch vụ liên quan

4. NGINX
   - Được cấu hình làm reverse proxy và cân bằng tải cho các dịch vụ web
   - Có thể định tuyến lưu lượng đến các backend khác nhau

5. Topology Diagram
   - Sơ đồ mạng tổng quan được lưu trong thư mục Topology
   - Giúp trực quan hóa cách các subnet và dịch vụ kết nối với nhau

---

## Cấu hình mạng chính

Các segment cơ bản trong lab:

- LAN quản trị / Domain: 172.16.16.0/24
- DMZ: 192.168.102.0/24
- LAN nội bộ / user: 192.168.103.0/24

Các gateway và điểm kết nối quan trọng:

- pfSense LAN: 172.16.16.254
- pfSense DMZ: 192.168.102.254
- pfSense LAN user: 192.168.103.254
- DNS nội bộ: 172.16.16.100

Dữ liệu cấu hình mạng được lưu trong:

- config/pfsense.xml
- config/nginx.conf
- config/GPO_AD/

---

## Cấu trúc thư mục

```text
Project 2/
├── README.md
├── config/
│   ├── nginx.conf
│   ├── pfsense.xml
│   ├── GPO_AD/
│   │   └── ... các chính sách AD / GPO export
│   └── Mailcow/
│       └── docker-compose.yml
├── Topology/
│   └── sơ đồ mạng.png
└── ...
```

---

## Thành phần lưu trữ

### 1. config/
Chứa các file cấu hình hệ thống quan trọng:

- pfSense export XML
- Cấu hình reverse proxy NGINX
- Export GPO Active Directory
- Cấu hình dịch vụ Mailcow

### 2. Topology/
Lưu sơ đồ mạng và hình ảnh mô tả kiến trúc hệ thống.

### 3. README.md
Tài liệu tổng hợp mục tiêu, mô tả kiến trúc và hướng dẫn sử dụng nhanh.

---

## Mục tiêu học tập / triển khai

Repo này phù hợp cho các mục đích:

- Mô phỏng môi trường doanh nghiệp thực tế
- Tìm hiểu cách xây dựng hệ thống bảo mật mạng bằng pfSense
- Thiết lập và quản trị Windows domain với Active Directory
- Triển khai dịch vụ mail bằng Mailcow
- Cấu hình NGINX làm reverse proxy / load balancer
- Tạo sơ đồ và triển khai phòng lab mạng có tính thực tế cao

---

## Ghi chú

- Đây là một dự án mô phỏng/lab, không phải môi trường Production sẵn sàng chạy ngay trên internet.
- Cần kiểm tra và điều chỉnh IP, DNS, dịch vụ và máy chủ phù hợp với môi trường triển khai thực tế.
- Nhiều phần cấu hình đã được export sẵn để dễ dàng nghiên cứu và tái triển khai.

---

## Liên kết nhanh

- Demo: https://youtu.be/zQlxyENyXIo
- pfSense: firewall và định tuyến
- Active Directory: quản trị miền và GPO
- Mailcow: dịch vụ email doanh nghiệp
- NGINX: proxy và cân bằng tải

---

## Kết luận

Dự án này thể hiện một kiến trúc mạng doanh nghiệp hoàn chỉnh, kết hợp giữa bảo mật, quản trị tài nguyên, mail server và dịch vụ web. Repo này phù hợp để làm tài liệu tham khảo, học tập hoặc làm nền tảng cho các dự án lab mạng chuyên sâu hơn.
