<div align="center">

# 🏍️ AutoWash Pro

**Motorbike Wash Management System — Hệ Thống Quản Lý Tiệm Rửa Xe Máy Thông Minh**

[![.NET](https://img.shields.io/badge/.NET-9.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![EF Core](https://img.shields.io/badge/EF%20Core-9.0-512BD4?logo=dotnet)](https://learn.microsoft.com/en-us/ef/core/)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-2019+-CC2927?logo=microsoftsqlserver)](https://www.microsoft.com/en-us/sql-server)
[![JWT](https://img.shields.io/badge/Auth-JWT%20Bearer-000000?logo=jsonwebtokens)](https://jwt.io/)
[![Swagger](https://img.shields.io/badge/Docs-Swagger%20UI-85EA2D?logo=swagger)](https://swagger.io/)

</div>

---

<div align="center">

[🇬🇧 English](#-english) &nbsp;|&nbsp; [🇻🇳 Tiếng Việt](#-tiếng-việt)

</div>

---

## 🇬🇧 English

### Overview

**AutoWash Pro** is a robust backend REST API built with **ASP.NET Core 9.0** for small-to-medium motorbike wash businesses in Vietnam. It handles advance online bookings with real-time slot capacity enforcement, walk-in counter operations, a 4-tier customer loyalty program with automated point expiration and monthly tier evaluation, alongside an executive admin dashboard for operations and financial analytics.

### 🚀 Key Features

| Domain | Capabilities |
| :--- | :--- |
| **Authentication** | Customer registration & login • Staff & Admin login • JWT Bearer tokens with strict role-based authorization |
| **Service Catalogue** | Public service & pricing listings • Per-vehicle-type pricing (Xe số, Xe tay ga, Xe phân khối lớn) • Admin CRUD |
| **Booking Engine** | Advance bookings (Member: 7d, Silver: 10d, Gold: 12d, Platinum: 14d window) • Walk-in counter flow • Real-time slot availability • Serializable-transaction capacity check (max 4 per 30-min slot) • Customer cancellation |
| **Checkout & Loyalty** | Booking completion with automated promotional discounts • Append-only points ledger • Automatic earn/redeem (1 loyalty point = 100 VND) |
| **Loyalty Tiers** | Member ➔ Silver ➔ Gold ➔ Platinum • Monthly 30-day rolling review of visits & spend • Automatic upgrade/downgrade with customer notifications |
| **Points Expiry** | Points expire 12 months after earning • Monthly background job expires overdue points • 30-day advance near-expiry alerts |
| **Admin Panel** | Tier threshold configuration • Promotion CRUD • Customer lookup & manual tier override • Executive dashboard reports |
| **Background Jobs** | Hosted services running on the 1st of each month • Restart-safe persistence to database |

### 🛠 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Runtime** | ASP.NET Core 9.0 Web API |
| **ORM** | Entity Framework Core 9.0 (Code-First) |
| **Database** | Microsoft SQL Server 2019+ |
| **Authentication** | JWT Bearer (`Microsoft.AspNetCore.Authentication.JwtBearer`) |
| **Security** | BCrypt.Net-Next password hashing |
| **API Docs** | Swashbuckle / Swagger UI with Bearer token authentication |
| **Background Jobs**| `IHostedService` / `BackgroundService` |

---

## 🇻🇳 Tiếng Việt

### 1. Tổng quan Dự án

**AutoWash Pro** là hệ thống Backend Web API hoàn chỉnh xây dựng trên nền tảng **ASP.NET Core 9.0** phục vụ quản trị và điều phối dịch vụ tiệm rửa xe máy chuyên nghiệp. Hệ thống giải quyết trọn vẹn bài toán vận hành thực tế: loại bỏ tình trạng ùn tắc khách hàng thông qua cơ chế đặt lịch hẹn thông minh (Capacity Check), phân luồng khách vãng lai (Walk-in), tự động hóa chương trình chăm sóc khách hàng thân thiết 4 hạng bậc và cung cấp báo cáo doanh thu minh bạch cho chủ tiệm.

### 2. Các Tính năng Trọng tâm

- 📅 **Hệ thống Đặt lịch Hẹn Trực tuyến:** Đặt lịch trước theo khung giờ 30 phút, kiểm tra sức chứa tối đa theo thời gian thực (tối đa 4 xe/khung giờ).
- 🛵 **Khách Vãng lai (Walk-in Counter):** Lễ tân tạo đơn nhanh tại quầy, tự động xếp vào hàng đợi ưu tiên.
- 💎 **Hệ sinh thái Thành viên 4 Bậc (Loyalty Program):**
  - Các cấp bậc: *Thành viên (Member) ➔ Bạc (Silver) ➔ Vàng (Gold) ➔ Bạch kim (Platinum)*.
  - Quy chế tích điểm: 1 điểm = 100 VNĐ giảm giá.
  - Tự động đánh giá nâng/hạ bậc hàng tháng và quản lý vòng đời điểm thưởng (hạn 12 tháng).
- 📊 **Báo cáo & Dashboard Doanh thu:** Phân tích lưu lượng khách hàng theo ngày/tuần/tháng, tỷ lệ lấp đầy khung giờ và hiệu quả doanh thu theo từng dịch vụ.

---

## 💻 Hướng dẫn Cài đặt & Khởi chạy (Getting Started)

### 1. Yêu cầu môi trường
- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9)
- Microsoft SQL Server 2019+ (hoặc SQL Server Express / LocalDB)
- Công cụ dòng lệnh `dotnet-ef`

### 2. Cấu hình & Chạy ứng dụng

```bash
# 1. Cấu hình chuỗi kết nối trong appsettings.json
# ConnectionStrings:DefaultConnection = "Server=localhost;Database=AutoWashPro;Trusted_Connection=True;TrustServerCertificate=True"

# 2. Khôi phục packages & áp dụng Migration
dotnet restore
dotnet ef database update --project AutoWashPro.DAL --startup-project AutoWashPro.API

# 3. Khởi chạy Web API
dotnet run --project AutoWashPro.API

# Truy cập Swagger UI tại: https://localhost:5001/swagger
```

---

## 👥 Tác giả & Đóng góp (Credits)

- **Dự án:** Hệ thống quản lý tiệm rửa xe máy thông minh AutoWash Pro.
- **Thực hiện:** Trung Kiên ([@tkiennt](https://github.com/tkiennt)) — Rà soát mã nguồn, kiểm tra kiến trúc API, đồng bộ và chuẩn hóa tài liệu dự án.
