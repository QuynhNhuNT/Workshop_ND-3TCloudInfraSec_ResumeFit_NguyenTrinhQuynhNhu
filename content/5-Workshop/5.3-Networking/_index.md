---
title: "5.3 - Network Infrastructure"
date: 2026-07-10
weight: 2
chapter: false
pre: " <b> 5.3. </b> "
---

# 5.3. Network Infrastructure (Networking)

## 5.3.1. Create VPC and Internet Gateway

An isolated network environment (VPC) is a solid security foundation for the entire application, allowing full control over network traffic.

1. Navigate to the VPC Console and select **Create VPC**.
2. Initialize a VPC named `ResumeMatching-VPC` and configure the `IPv4 CIDR` range as `10.0.0.0/16`.
3. Enable the `Enable DNS Hostnames` feature so that the VPC can resolve domain names.
4. Create an Internet Gateway named `ResumeMatching-IGW` to provide outbound internet connectivity for public resources.
5. Attach the newly created Internet Gateway to `ResumeMatching-VPC`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/tao_VPC.jpg" alt="Create VPC" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Enable_DNS_Hostnames.jpg" alt="Enable DNS Hostnames" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Internet_Gateway.jpg" alt="Create Internet Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Attach_vao_VPC.jpg" alt="Attach IGW to VPC" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.3.2. Configure Subnets and Route Tables

Divide the VPC IP range into subnets to isolate the application layers (Public for Load Balancers, Private App for EC2s, and Private DB for RDS).

1. Go to the **Subnets** section and create subnets with appropriate CIDR blocks:
   * Public Subnets: `Public-Subnet-A` (`10.0.1.0/24`), `Public-Subnet-B` (`10.0.2.0/24`).
   * Private App Subnets: `Private-App-A` (`10.0.11.0/24`), `Private-App-B` (`10.0.12.0/24`).
   * Private DB Subnets: `Private-DB-A` (`10.0.21.0/24`), `Private-DB-B` (`10.0.22.0/24`).
2. Create a public Route Table named `Public-RT` and associate it with the VPC.
3. Under the **Edit routes** section of `Public-RT`, add a route with `Destination` `0.0.0.0/0` pointing `Target` to the Internet Gateway (`igw-...`).
4. Associate `Public-RT` with two subnets: `Public-Subnet-A` and `Public-Subnet-B`.
5. Create additional private Route Tables named `Private-App-RT`, `ResumeMatching-Private-App-RT-B`, and `Private-DB-RT`. Associate them with the App Subnets and DB Subnets respectively to ensure these layers are not exposed to the internet.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Tao_cac_Public_va_Private_subnet.jpg" alt="Create Subnets" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Public_Route_Table.jpg" alt="Create Public Route Table" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Add_Routes.jpg" alt="Add Route to IGW" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Gan_Public_Route_Table.jpg" alt="Associate Public Route Table to Subnets" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_va_gan_Private_App_Route_Table.jpg" alt="Create and Associate Private App RT" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_va_gan_Database_Route_Table.jpg" alt="Create and Associate Database RT" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Route_Table_B.jpg" alt="Route Table B details" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.3.3. Configure NAT Gateway for Private Subnets

Allows instances in the Private Subnets to make one-way outbound connections to the internet (to download packages and update software) while blocking any inbound connections initiated from the internet.

1. Allocate two static **Elastic IPs** named `ResumeMatching-EIP` and `ResumeMatching-EIP-B`.
2. Create a **NAT Gateway** named `ResumeMatching-NAT` in `Public-Subnet-A` and associate it with the first Elastic IP.
3. Create another **NAT Gateway** named `ResumeMatching-NAT-B` in the other Availability Zone and associate it with the second Elastic IP to ensure High Availability.
4. Open the configurations of the Private App Route Tables, add a route for `0.0.0.0/0` and point the `Target` to the respective NAT Gateways.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Elastic_IP.jpg" alt="Allocate Elastic IP" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Elastic_IP_B (phía sau bước tạo Elastic IP).jpg" alt="Allocate Elastic IP B" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_NAT.jpg" alt="Create NAT Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_NAT_B (bước này phía sau bước tạo NAT).jpg" alt="Create NAT Gateway B" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Add_Route_Tables_cho_Private-App-RT.jpg" alt="Route through NAT Gateway" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
