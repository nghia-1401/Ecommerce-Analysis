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

## 📂 Cấu Trúc Dữ Liệu 

Dữ liệu được tổ chức theo mô hình **Star Schema** để tối ưu hóa cho việc truy vấn phân tích, bao gồm 1 bảng Fact trung tâm và 5 bảng Dimension:

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

## 📖 Tổng Quan 

Dựa trên dữ liệu phân tích từ hơn **1 triệu giao dịch**, dự án đã tổng hợp các chỉ số chính:

* **Tổng doanh thu (2014-2021):** $105.4M.
* **Tổng sản lượng:** ~6 Triệu đơn vị sản phẩm.
* **Giá trị đơn hàng trung bình (AOV):** $105.4.
* **Tăng trưởng:** Doanh thu tăng trưởng 5.3% vào năm 2015, sau đó duy trì mức ổn định (dao động ±1%) quanh mốc $14 – $15M mỗi năm.

### 1. Xu hướng doanh thu
* **Theo Năm:** Doanh thu giao động ổn định từ $14 – $15M mỗi năm.
* **Theo Quý:** Doanh thu tăng dần từ Q1 ($26M) và đạt đỉnh vào **Q3 ($26.7M)** trước khi giảm nhẹ vào Q4.
* **Theo Tháng:** Nửa đầu năm thị trường biến động mạnh, trong khi nửa cuối năm doanh thu ổn định hơn.

### 2. Doanh thu theo vị trí
* **Sự thống trị của Dhaka:** Khu vực Dhaka là động lực tăng trưởng chính với **$41 Triệu doanh thu**, vượt trội hoàn toàn so với các vùng khác (chỉ từ $6M – $20M).

### 3. Hiệu suất Sản phẩm 
* **Top Categories:** *Beverage – Energy/Protein* và *Food – Healthy* dẫn đầu, với doanh thu trung bình đạt khoảng $1.4 - $1.5M. Điều này phản ánh xu hướng tiêu dùng mạnh mẽ đối với các sản phẩm tốt cho sức khỏe.

### 4. Doanh thu theo khách hàng
Doanh thu theo khách hàng nằm trong khoảng $6,986.5 (77 giao dịch) đến $17,104.5 (137 giao dịch): khách hàng chi tiêu cao hơn thường cũng có tần suất giao dịch cao hơn, cho thấy mối quan hệ khá rõ giữa loyalty và giá trị đóng góp.

---

## 📊 Phân Tích & Insights Chính

### 1. Doanh thu theo vị trí cửa hàng
* Doanh thu giữa các division tương đối ổn định qua các năm.
* Ở cấp độ upazila, sự chênh lệch giữa các cửa hàng không lớn.               
   
**Insights:**
   * Sự phân bổ doanh thu khá đồng đều cho thấy năng lực kinh doanh không phụ thuộc quá nặng vào khu vực riêng lẻ, giảm rủi ro địa lý.
   * Tuy nhiên, việc Dhaka chiếm tỷ trọng cao gợi ý tiềm năng mở rộng hoặc cải thiện hiệu suất ở các vùng có doanh thu thấp hơn.
   * Doanh thu ổn định giữa các năm/vị trí cho thấy hệ thống cửa hàng vận hành bền vững, nhưng chưa có vùng đột phá.

### 2. Doanh thu theo danh mục sản phẩm
* Hiệu suất sản phẩm:
   * **Beverage – Soda:** giá trung bình thấp (~10 USD), doanh thu cao nhờ sản lượng lớn.
   * **Coffee K-Cups:** giá trung bình cao (~46.5 USD), doanh thu tương đương Soda do ít danh mục con hơn.
* Một số sản phẩm nổi bật về sản lượng:
   * *Muscle Milk Protein Shake Van. 11oz* (45,665 đơn).
   * *Pepsi 12oz (46,837)*, *Diet Coke 12oz (45,202)*, *Coke Classic 12oz (45,501)*, *Sprite 12oz (45,140)*.
   
**Insights:**
   * Doanh thu khác biệt chủ yếu do giá, không phải sản lượng — cho thấy cơ hội định giá linh hoạt để tối ưu doanh thu tổng.
   * Các sản phẩm có sản lượng cao mang tính đại chúng, hỗ trợ tốt cho mục tiêu lan tỏa thương hiệu.
   * **Coffee K-Cups** (giá trị cao, ít sản phẩm con) là cơ hội để phát triển mảng cao cấp hoặc sản phẩm bundling (combo).

### 3. Phân khúc Khách hàng 
Dựa trên mô hình RFM, tập khách hàng (9,191 người) chủ yếu được chia thành các nhóm hành vi:

| Phân khúc | Đặc điểm hành vi | Insight |
| :--- | :--- | :--- |
| **Champions (551)** | Mua nhiều, chi tiêu lớn | Nhóm tinh hoa, đóng góp phần lớn doanh thu. |
| **Potential Loyalists (4614)** | Mua gần đây, chi tiêu khá | Có tiềm năng trở thành Champions nếu tăng tần suất mua. |
| **Emerging Loyalists (2681)** | Khách mới | Cần được "nuôi dưỡng" để tăng giá trị vòng đời. |

---

## 🚀 Khuyến Nghị Chiến Lược

Dựa trên các insight trên, dự án đề xuất các chiến lược sau:

1.  **Chiến lược Sản phẩm:**
    * Áp dụng phân khúc giá: duy trì danh mục bình dân (Soda) và đẩy mạnh danh mục cao cấp (Coffee K-Cups).
    * Thiết kế các gói combo/bundling xoay quanh nhóm sản phẩm trụ cột: Kết hợp Coffee K-Cups với Food – Healthy hoặc Energy/Protein để tạo combo “cao cấp/tiện lợi” giúp tăng giá trị mỗi đơn hàng.

2.  **Mở rộng & Tối ưu địa điểm:**
    * Đánh giá tiềm năng thị trường ở các division ngoài Dhaka để mở rộng hoặc cải thiện tỷ trọng doanh thu.
    * Áp dụng mô hình hiệu suất của các cửa hàng top 10 vào các cửa hàng bottom 10 để rút ngắn khoảng cách hiệu quả.
    * Khai thác dữ liệu địa điểm (foot traffic, demographic) để tối ưu hóa vị trí mở mới cửa hàng.

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
