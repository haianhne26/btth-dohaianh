# BÁO CÁO PHÂN TÍCH THỰC HÀNH: TỔNG QUAN VỀ BUSINESS INTELLIGENCE (BI301 - S01)

**Chủ đề:** Phân tích Dữ liệu Hiệu suất Dòng Áo khoác AIRism và Đề xuất Chiến lược Quản trị tại Uniqlo  
**Học viên thực hiện:** ĐỖ HẢI ANH  
**Mã sinh viên:** B25DTQT017 | **Lớp:** BI301 - S01  
**Vai trò đảm nhiệm:** Nhóm Phân tích BI / Senior Business Analyst  
**Tệp dữ liệu & Dashboard đính kèm:** [BI301_S01_BTTH_dohaianh.xlsx](file:///d:/Downloads/BI%20RIKKEI/BI301_S01_BTTH_dohaianh.xlsx)

---

## 1. TỔNG QUAN TÌNH HUỐNG & MỤC TIÊU PHÂN TÍCH

Uniqlo là thương hiệu bán lẻ thời trang toàn cầu vận hành theo triết lý **LifeWear** – đề cao công nghệ chất liệu, tính tiện dụng và tối ưu hóa vận hành thông qua phân tích dữ liệu chuyên sâu. Trong kỳ kinh doanh tháng 11 (mùa Thu Đông), hệ thống giám sát nội bộ phát hiện hiện tượng bất thường: dòng áo khoác chống UV công nghệ làm mát **AIRism (Mã SP: U11)** ghi nhận lượng hoàn trả tăng đột biến tại thị trường Miền Bắc.

Báo cáo này ứng dụng trọn vẹn mô hình kim tự tháp **DIKW (Data - Information - Knowledge - Wisdom)** nhằm bóc tách hiện trạng, xác định nguyên nhân gốc rễ và tham mưu các quyết định điều hành chiến lược cho Giám đốc Khu vực.

---

## 2. QUY TRÌNH THỰC HÀNH PHÂN TÍCH THEO 4 BƯỚC

```
[BƯỚC 1: DATA]         --> [BƯỚC 2: INFORMATION]   --> [BƯỚC 3: KNOWLEDGE/INSIGHT] --> [BƯỚC 4: WISDOM]
Trích xuất số liệu thô     Tính toán chỉ số &          Phân tích nguyên nhân gốc rễ    Ra quyết định điều phối
(Orders, Return Rate)      Lượng hàng hoàn trả         (Công nghệ sợi vs Khí hậu)      tồn kho & quy hoạch vùng
```

---

### BƯỚC 1: KHÁM PHÁ DỮ LIỆU THÔ (DATA)

Từ tập dữ liệu trích xuất từ hệ thống quản trị vận hành Uniqlo, ta bóc tách các biến số của mã sản phẩm U11:

| Chỉ số / Thuộc tính | Miền Nam | Miền Bắc | Chênh lệch (Bắc so với Nam) |
| :--- | :---: | :---: | :---: |
| **Mã sản phẩm (SKU)** | U11 | U11 | - |
| **Dòng sản phẩm (Line)** | AIRism | AIRism | - |
| **Mùa vụ kinh doanh (Season)** | Thu Đông | Thu Đông | - |
| **Lượt xem sản phẩm (Views)** | 500.000 | 600.000 | Cao hơn +20,0% |
| **Lượt mua hàng (Orders)** | **50.000** | **80.000** | **Cao hơn +60,0% (1,6 lần)** |
| **Tỷ lệ chuyển đổi (CVR = Orders/Views)** | 10,0% | 13,3% | Cao hơn +3,3 điểm % |
| **Tỷ lệ đổi trả (Return Rate %)** | **1,0%** | **45,0%** | **Gấp 45,0 lần** |
| **Dữ liệu phản hồi định tính** | *"Mặc mát, thoải mái"* | *"Quá lạnh, gió lùa"* | Đối lập hoàn toàn |

#### Nhận diện ban đầu:
- **Nhu cầu mua ban đầu rất lớn:** Lượt xem (600k) và lượt mua (80k) tại miền Bắc đều vượt trội so với miền Nam, thể hiện sức hút thương hiệu và hiệu quả của các chiến dịch quảng bá ban đầu.
- **Sự phân hóa dị biệt nghiêm trọng:** Tỷ lệ đổi trả tại miền Bắc đạt con số kỷ lục **45%** (gần một nửa số hàng bán ra bị trả lại), trong khi miền Nam duy trì tỷ lệ hoàn trả lý tưởng chỉ **1%**.

---

### BƯỚC 2: TÍNH TOÁN THÔNG TIN (INFORMATION)

Chuyển đổi dữ liệu tỷ lệ phần trăm thành khối lượng hàng hóa vật lý cụ thể để đo lường mức độ tác động vận hành:

#### 1. Công thức tính Lượng hoàn trả thực tế (Return Volume):
$$\text{Lượng hàng hoàn trả (Units)} = \text{Lượt mua (Orders)} \times \text{Tỷ lệ đổi trả (Return Rate)}$$

- **Khối lượng hoàn trả tại Miền Bắc:**
  $$\text{Return Volume}_{\text{Miền Bắc}} = 80.000 \times 45\% = \mathbf{36.000 \text{ sản phẩm}}$$
- **Khối lượng hoàn trả tại Miền Nam:**
  $$\text{Return Volume}_{\text{Miền Nam}} = 50.000 \times 1\% = \mathbf{500 \text{ sản phẩm}}$$

#### 2. So sánh khối lượng hoàn trả và sản lượng giữ lại thực tế:
- **Chênh lệch khối lượng hoàn trả:**
  $$\frac{\text{Return Volume}_{\text{Miền Bắc}}}{\text{Return Volume}_{\text{Miền Nam}}} = \frac{36.000}{500} = \mathbf{72{,}0 \text{ lần}}$$
  Khối lượng hàng hóa bị trả lại tại miền Bắc cao gấp **72 lần** so với miền Nam.
- **Phân tích sản lượng giữ lại thực tế (Net Units Retained = Orders - Return Volume):**
  - **Miền Nam:** Giữ lại $50.000 - 500 = \mathbf{49.500 \text{ sản phẩm}}$ (Tỷ lệ giữ lại thực tế đạt **99,0%**).
  - **Miền Bắc:** Chỉ giữ lại $80.000 - 36.000 = \mathbf{44.000 \text{ sản phẩm}}$ (Tỷ lệ giữ lại thực tế chỉ đạt **55,0%**).

> **Ý nghĩa nghiệp vụ:** Mặc dù miền Bắc có số lượng đơn đặt hàng cao gấp 1,6 lần (80k vs 50k), nhưng lượng sản phẩm thực tế khách hàng giữ lại sử dụng cuối cùng lại **thấp hơn miền Nam 5.500 sản phẩm**. Miền Bắc phải chịu gánh nặng chi phí xử lý logistics ngược khổng lồ cho 36.000 sản phẩm bị trả.

---

### BƯỚC 3: ĐÀO SÂU INSIGHT (KNOWLEDGE)

Từ việc kết hợp giữa chỉ số định lượng (45% hoàn trả) và dữ liệu văn bản định tính, nguyên nhân cốt lõi được sáng tỏ:

#### 1. Khai phá ý nghĩa từ phản hồi khách hàng:
- Khách hàng Miền Nam nhận xét: *"Mặc mát, thoải mái"* $\rightarrow$ Đúng với công năng thiết kế.
- Khách hàng Miền Bắc nhận xét: *"Quá lạnh, gió lùa"* $\rightarrow$ Trải nghiệm người dùng hoàn toàn tiêu cực.

#### 2. Phân tích xung đột giữa Thuộc tính kỹ thuật sợi vải và Khí hậu thực tế:
- **Bản chất công nghệ AIRism:** Sợi vải Cupro siêu mảnh dệt mật độ thoáng khí cao, tích hợp công nghệ làm mát tức thì, thấm hút mồ hôi và khuếch tán nhiệt nhanh nhằm phục vụ thời tiết nắng nóng mùa hè.
- **Thực tế thời tiết tháng 11 tại miền Bắc:** Miền Bắc bước vào mùa Thu Đông với các đợt gió mùa Đông Bắc (nhiệt độ giảm sâu xuống dưới 18°C – 20°C, kèm độ ẩm thấp và gió hanh hao). 
- Khách hàng miền Bắc mua áo khoác theo quán tính tâm lý *"mua áo khoác để giữ ấm vào đầu đông"*. Khi sử dụng thực tế, cấu trúc thoát nhiệt của AIRism khiến gió lùa trực tiếp vào cơ thể, gây cảm giác rét buốt.

#### 3. Khẳng định Insight cốt lõi:
> **Insight:** *"Dòng sản phẩm áo công nghệ làm mát AIRism có thuộc tính cơ lý mâu thuẫn hoàn toàn với điều kiện khí hậu Thu Đông tại Miền Bắc. Tỷ lệ hoàn trả 45% không phải do lỗi sản xuất hay đường may, mà là hệ quả của việc sai lệch chiến lược phân bổ danh mục sản phẩm theo mùa và vùng địa lý (Severe Seasonal & Climatic Assortment Mismatch)."*

---

### BƯỚC 4: RA QUYẾT ĐỊNH QUẢN TRỊ (WISDOM)

Dựa trên Insight đã được chứng minh, đề xuất 02 gói quyết định điều hành cụ thể:

### 4.1. Quyết định 1: Tái điều phối hàng tồn kho liên vùng khẩn cấp (Inter-regional Inventory Rebalancing)
- **Thu hồi và ngừng bán tại Miền Bắc:**
  - Lập tức đóng mã sản phẩm U11 trên kênh bán lẻ trực tiếp và trực tuyến tại toàn bộ chi nhánh miền Bắc.
  - Tiến hành thu gom 36.000 sản phẩm đã hoàn trả (sau khi qua kiểm định KCS) và lượng hàng tồn kho chưa bán tại các kho miền Bắc.
- **Chuyển kho điều phối vào Miền Nam:**
  - Vận chuyển toàn bộ lượng hàng tồn thu hồi vào hệ thống cửa hàng Uniqlo tại TP. Hồ Chí Minh và các tỉnh phía Nam. Miền Nam có khí hậu nhiệt đới nắng ấm quanh năm, nhu cầu áo khoác chống nắng, thoát nhiệt luôn duy trì ở mức cao và tỷ lệ trả hàng chỉ 1%.
  - Một phần lượng hàng có thể xuất kho sang các thị trường Đông Nam Á lân cận có khí hậu tương đồng (Thái Lan, Indonesia, Malaysia).
- **Lợi ích tài chính:** Tránh việc phải bán cắt lỗ (Markdown/Clearance) tại miền Bắc, bảo toàn biên lợi nhuận gộp và giải phóng áp lực lưu kho.

### 4.2. Quyết định 2: Tái quy hoạch chiến lược sản phẩm theo mùa và khí hậu vùng miền (Localized Seasonal Merchandising)
- **Tách biệt danh mục hàng hóa (Assortment Clustering) theo vùng khí hậu:**
  - Chấm dứt chính sách áp dụng danh mục phân phối đồng nhất trên toàn quốc.
  - **Khu vực Miền Bắc (Tháng 10 - Tháng 2):** Chuyển dịch toàn bộ trọng tâm sang các dòng sản phẩm công nghệ giữ nhiệt chủ lực của Uniqlo gồm **HEATTECH** (áo giữ nhiệt các cấp độ Warm/Extra Warm/Ultra Warm) và **Ultra Light Down (ULD)** (áo lông vũ siêu nhẹ). Giảm tỷ trọng hiển thị của dòng AIRism xuống dưới 5% hoặc đưa vào khu vực đồ mặc lót cơ bản.
  - **Khu vực Miền Nam:** Duy trì dòng sản phẩm AIRism và UV-cut quanh năm như một dòng hàng cốt lõi (Core Essential).
- **Số hóa kế hoạch cung ứng gắn liền dữ liệu thời tiết (Weather-driven Demand Planning):**
  - Tích hợp dữ liệu dự báo khí hậu và nhiệt độ thời gian thực vào thuật toán phân bổ hàng tồn kho của hệ thống ERP/BI.
  - Thiết lập kịch bản đẩy hàng tự động: khi nhiệt độ trung bình tại Hà Nội giảm xuống dưới 20°C, hệ thống tự động đề xuất tăng tỷ trọng HEATTECH và giảm nhập hàng AIRism.

---

## 3. BẢNG TỔNG HỢP CHỈ SỐ KINH DOANH VÀ DASHBOARD

Dữ liệu tính toán chi tiết và các biểu đồ trực quan đã được xây dựng hoàn chỉnh trong file đính kèm: [BI301_S01_BTTH_dohaianh.xlsx](file:///d:/Downloads/BI%20RIKKEI/BI301_S01_BTTH_dohaianh.xlsx).

### Tóm tắt chỉ số đo lường chính (Key Performance Indicators):

| Nhóm Chỉ Số | Miền Nam | Miền Bắc | Toàn Hệ Thống | Đánh Giá Tác Động |
| :--- | :---: | :---: | :---: | :--- |
| **Tổng Lượt Xem (Views)** | 500.000 | 600.000 | 1.100.000 | Nhu cầu thị trường miền Bắc cao hơn +20% |
| **Tổng Lượt Mua (Orders)** | 50.000 | 80.000 | 130.000 | Khách hàng ban đầu đón nhận rất tích cực |
| **Tỷ Lệ Đổi Trả (Return %)** | **1,0%** | **45,0%** | **28,1%** | Miền Bắc rơi vào ngưỡng báo động đỏ |
| **Lượng Hoàn Trả (Units)** | **500** | **36.000** | **36.500** | Miền Bắc chiếm tới 98,6% tổng lượng trả |
| **Sản Lượng Bán Ròng (Net Units)** | **49.500** | **44.000** | **93.500** | Miền Nam đem lại sản lượng tiêu thụ thực tế cao hơn |
| **Tỷ Lệ Giữ Lại Ròng (%)** | **99,0%** | **55,0%** | **71,9%** | Hiệu quả kinh doanh ròng tại miền Nam áp đảo |

---

## 4. KẾT LUẬN & BÀI HỌC VỀ GIÁ TRỊ CỦA BUSINESS INTELLIGENCE

1. **Từ Data đến Wisdom:** Nếu chỉ nhìn vào báo cáo doanh thu thô ban đầu (80k đơn hàng miền Bắc), Uniqlo sẽ lầm tưởng đây là chiến dịch thành công rực rỡ. Tuy nhiên, qua lăng kính BI, việc theo dõi tỷ lệ hoàn trả và phân tích nhận xét khách hàng đã kịp thời phơi bày cuộc khủng hoảng vận hành (36.000 chiếc bị trả).
2. **Giá trị cốt lõi của BI:** BI không đơn thuần là vẽ biểu đồ, mà là công cụ kiến tạo năng lực thấu hiểu khách hàng, phát hiện bất thường trong vận hành và chỉ đường cho các quyết định tái cơ cấu chuỗi cung ứng nhanh chóng, chính xác.
