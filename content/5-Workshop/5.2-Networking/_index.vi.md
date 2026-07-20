---
title: "Xây dựng Hạ tầng Mạng"
date: 2026-07-10
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

# 5.2. Xây dựng Hạ tầng Mạng (Networking)

## 5.2.1. Tạo VPC và Internet Gateway

Hạ tầng mạng cô lập (VPC) là nền tảng bảo mật vững chắc cho toàn bộ ứng dụng, giúp kiểm soát hoàn toàn luồng giao thông mạng.

1. Truy cập vào giao diện VPC Console, chọn **Create VPC**.
2. Khởi tạo một VPC với tên `ResumeMatching-VPC` và thiết lập dải IP `IPv4 CIDR` là `10.0.0.0/16`.
3. Đừng quên bật tính năng `Enable DNS Hostnames` để VPC có thể phân giải tên miền.
4. Tạo một Internet Gateway có tên `ResumeMatching-IGW` để cung cấp đường truyền kết nối ra internet cho các tài nguyên công khai.
5. Thực hiện Attach Internet Gateway vừa tạo vào `ResumeMatching-VPC`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/tao_VPC.jpg" alt="Tạo VPC" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Enable_DNS_Hostnames.jpg" alt="Bật DNS Hostnames" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Internet_Gateway.jpg" alt="Tạo Internet Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Attach_vao_VPC.jpg" alt="Attach IGW vào VPC" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.2.2. Cấu hình Subnet và Route Table

Chia nhỏ dải mạng VPC thành các mạng con để phân tách các tầng ứng dụng (Public cho Load Balancer, Private App cho EC2, Private DB cho RDS).

1. Truy cập mục **Subnets** và tạo lần lượt các subnet với các dải CIDR phù hợp:
   * Public Subnets: `Public-Subnet-A` (`10.0.1.0/24`), `Public-Subnet-B` (`10.0.2.0/24`).
   * Private App Subnets: `Private-App-A` (`10.0.11.0/24`), `Private-App-B` (`10.0.12.0/24`).
   * Private DB Subnets: `Private-DB-A` (`10.0.21.0/24`), `Private-DB-B` (`10.0.22.0/24`).
2. Tạo một Route Table công khai với tên `Public-RT` và gán vào VPC.
3. Trong phần **Edit routes** của `Public-RT`, thêm route có `Destination` là `0.0.0.0/0` và trỏ `Target` đến Internet Gateway (`igw-...`).
4. Gán (Associate) `Public-RT` vào 2 subnets: `Public-Subnet-A` và `Public-Subnet-B`.
5. Tạo thêm các Route Table riêng tư là `Private-App-RT`, `ResumeMatching-Private-App-RT-B` và `Private-DB-RT`, sau đó lần lượt gán chúng cho các App Subnet và DB Subnet tương ứng để đảm bảo các tầng này không lộ ra internet.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Tao_cac_Public_va_Private_subnet.jpg" alt="Tạo các Subnets" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Public_Route_Table.jpg" alt="Tạo Public Route Table" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Add_Routes.jpg" alt="Thêm Route ra IGW" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Gan_Public_Route_Table.jpg" alt="Gán Public Route Table vào Subnets" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_va_gan_Private_App_Route_Table.jpg" alt="Tạo và gán Private App RT" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_va_gan_Database_Route_Table.jpg" alt="Tạo và gán Database RT" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Route_Table_B.jpg" alt="Chi tiết Route Table B" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.2.3. Thiết lập NAT Gateway cho Private Subnets

Giúp các instance ở Private Subnet kết nối ra internet một chiều (để tải package, cập nhật phần mềm) nhưng từ chối các kết nối khởi tạo từ internet đi vào.

1. Khởi tạo hai **Elastic IP** tĩnh là `ResumeMatching-EIP` và `ResumeMatching-EIP-B`.
2. Tạo **NAT Gateway** tên `ResumeMatching-NAT` đặt tại `Public-Subnet-A` và gắn Elastic IP thứ nhất.
3. Tạo thêm **NAT Gateway** tên `ResumeMatching-NAT-B` đặt tại Availability Zone còn lại và gắn Elastic IP thứ hai nhằm đảm bảo tính sẵn sàng cao (High Availability).
4. Mở cấu hình của các Route Table Private App, thêm route `0.0.0.0/0` và trỏ `Target` về các NAT Gateway tương ứng vừa khởi tạo.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Elastic_IP.jpg" alt="Tạo Elastic IP" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Elastic_IP_B (phía sau bước tạo Elastic IP).jpg" alt="Phân bổ Elastic IP B" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_NAT.jpg" alt="Tạo NAT Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_NAT_B (bước này phía sau bước tạo NAT).jpg" alt="Tạo NAT Gateway B" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Add_Route_Tables_cho_Private-App-RT.jpg" alt="Định tuyến qua NAT Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
