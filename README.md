# Ecommerce-Analysis
# 🛒 Retail Sales Analysis 

![Status](https://img.shields.io/badge/Status-Completed-success)
![Data Model](https://img.shields.io/badge/Data_Model-Star_Schema-blue)
![Tools](https://img.shields.io/badge/Tools-PowerBI-orange)

Dự án này tập trung vào việc phân tích hiệu suất kinh doanh của một chuỗi bán lẻ (giai đoạn 2014–2021). Mục tiêu là chuyển đổi dữ liệu thô thành các insight chiến lược về hành vi khách hàng, hiệu suất sản phẩm và xu hướng doanh thu.

---

## 🎯 Mục tiêu Phân tích

Dự án này được thực hiện nhằm giải quyết 4 câu hỏi kinh doanh cốt lõi:

1.  **Đánh giá Sức khỏe Kinh doanh:** Xu hướng doanh thu thay đổi như thế nào theo thời gian (mùa vụ, năm)? Đâu là thời điểm vàng để tung ra các chiến dịch khuyến mãi?
2.  **Tối ưu hóa Danh mục Sản phẩm:** Xác định đâu là sản phẩm chủ lực mang lại lợi nhuận và đâu là sản phẩm thu hút khách hàng?
3.  **Hiệu suất Cửa hàng & Địa lý:** Đánh giá chênh lệch hiệu suất giữa khu vực thủ đô (Dhaka) và các tỉnh khác. Cần phân bổ nguồn lực ra sao?
4.  **Thấu hiểu Khách hàng:** Phân khúc khách hàng dựa trên hành vi mua sắm (RFM) để thiết kế chương trình Loyalty phù hợp.


---

## 📖 Tổng Quan 

Dựa trên dữ liệu phân tích từ hơn **1 triệu giao dịch**, dự án đã tổng hợp các chỉ số chính:

* **Tổng doanh thu (2014-2021):** $105.4 Triệu USD.
* **Tổng sản lượng:** ~6 Triệu đơn vị sản phẩm.
* **Giá trị đơn hàng trung bình (AOV):** $105.4.
* **Tăng trưởng:** Doanh thu tăng trưởng 5.3% vào năm 2015, sau đó duy trì mức ổn định (dao động ±1%) quanh mốc 14–15 triệu USD/năm.

---

## 📂 Cấu Trúc Dữ Liệu 

Dữ liệu được tổ chức theo mô hình **Star Schema** để tối ưu hóa cho việc truy vấn phân tích, bao gồm 1 bảng Fact trung tâm và 5 bảng Dimension vệ tinh:

### 1. Fact Table
* **`fact_table.csv`**: Chứa dữ liệu giao dịch chi tiết.
    * *Metrics:* `quantity`, `unit_price`, `total_price`.
    * *Foreign Keys:* Kết nối tới Customer, Item, Store, Time, Payment.

### 2. Dimension Tables
* **`customer_dim.csv`**: Hồ sơ khách hàng (Tên, SĐT, NID).
* **`item_dim.csv`**: Thông tin sản phẩm (Tên, Danh mục, Quốc gia SX, Nhà cung cấp).
* **`store_dim.csv`**: Địa điểm cửa hàng (Division, District, Upazila).
* **`time_dim.csv`**: Chiều thời gian chi tiết (Giờ, Ngày, Tuần, Tháng, Quý, Năm).
* **`Trans_dim.csv`**: Phương thức thanh toán (Tiền mặt/Thẻ, Tên ngân hàng).

---

## 📊 Phân Tích & Insights Chính

### 1. Xu hướng doanh thu
* **Theo Quý:** Doanh thu có tính mùa vụ rõ rệt, tăng dần từ Q1 ($26M) và đạt đỉnh vào **Q3 ($26.7M)** trước khi giảm nhẹ vào Q4.
* **Theo Tháng:** Nửa đầu năm thị trường biến động mạnh, trong khi nửa cuối năm doanh thu ổn định hơn.

### 2. Hiệu suất theo Địa lý 
* **Sự thống trị của Dhaka:** Khu vực Dhaka là động lực tăng trưởng chính với **$41 Triệu doanh thu**, vượt trội hoàn toàn so với các vùng khác (chỉ từ $6M – $20M).
* **Tính ổn định:** Doanh thu giữa các vùng địa lý khác tương đối đồng đều, cho thấy hệ thống vận hành ổn định nhưng thiếu các điểm bứt phá mới ngoài thủ đô.

### 3. Hiệu suất Sản phẩm 
* **Top Categories:** *Beverage – Energy/Protein* và *Food – Healthy* dẫn đầu, chiếm ~20% tổng doanh thu. Điều này phản ánh xu hướng tiêu dùng mạnh mẽ đối với các sản phẩm tốt cho sức khỏe.
* **Volume vs. Value:**
    * *Traffic Drivers:* Các loại Soda (Pepsi, Coke) có giá thấp (~$10) nhưng sản lượng cực lớn (>45k đơn vị/loại).
    * *Profit Drivers:* Coffee K-Cups có giá trị cao (~$46.5) mang lại doanh thu lớn dù số lượng bán ra ít hơn.

### 4. Phân khúc Khách hàng 
Dựa trên mô hình RFM, tập khách hàng (9,191 người) được chia thành các nhóm hành vi:

| Phân khúc | Đặc điểm hành vi | Insight |
| :--- | :--- | :--- |
| **Champions (6%)** | Mua nhiều, chi tiêu lớn | Nhóm tinh hoa, đóng góp phần lớn doanh thu. |
| **Potential Loyalists** | Mua gần đây, chi tiêu khá | Có tiềm năng trở thành Champions nếu tăng tần suất mua. |
| **Emerging Loyalists** | Khách mới | Cần được "nuôi dưỡng" để tăng giá trị vòng đời. |

---

## 🚀 Khuyến Nghị Chiến Lược

Dựa trên các insight trên, dự án đề xuất các chiến lược sau:

1.  **Chiến lược Sản phẩm:**
    * Kết hợp sản phẩm "Traffic" (Soda/Healthy Food) với sản phẩm "Lợi nhuận" (Coffee K-Cups) tạo thành các gói Combo Tiện lợi.
    * Mục tiêu: Tăng giá trị đơn hàng trung bình (AOV) và giới thiệu dòng sản phẩm cao cấp cho khách hàng phổ thông.

2.  **Mở rộng & Tối ưu địa điểm:**
    * Giảm sự phụ thuộc vào Dhaka bằng cách đánh giá tiềm năng tại các division có doanh thu thấp ($6M-$10M).
    * Áp dụng quy trình vận hành của Top 10 Store tại Dhaka cho các cửa hàng hoạt động kém hiệu quả.

3.  **Cá nhân hóa theo khách hàng:**
    * **Với Champions:** Triển khai đặc quyền VIP (ưu tiên thanh toán, quà sinh nhật) để giữ chân.
    * **Với Potential Loyalists:** Chương trình thưởng theo tần suất (Ví dụ: "Mua 3 lần/tháng nhận voucher") để thói quen mua sắm ổn định hơn.
    * **Với Emerging Loyalists:** Remarketing các sản phẩm Hot Deal trong vòng 30 ngày đầu tiên.

---

## 🛠 Công cụ sử dụng
* **ETL & Visualization:** Power BI 
---
*Author: Huỳnh Hữu Nghĩa*
*Contact: nghiahuynhhuu6@gmail.com*
