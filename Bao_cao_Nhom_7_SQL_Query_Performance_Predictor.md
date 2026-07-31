# BÁO CÁO BÀI TẬP LỚN HỌC PHẦN

## HỆ THỐNG ĐÁNH GIÁ VÀ DỰ ĐOÁN HIỆU NĂNG TRUY VẤN CƠ SỞ DỮ LIỆU THỜI GIAN THỰC

### SQL Query Performance Predictor

**Đơn vị thực hiện:** Nhóm 7 (03 thành viên)  
**Trưởng nhóm:** Nguyễn Đăng Quang Anh – MSV: 24100455  
**Thành viên 2:** Cao Bá Sơn – MSV: 24100038  
**Thành viên 3:** Trần Doãn Việt Anh – MSV: 24100033  
**Lớp tín chỉ:** CSE702115-1-1-25(N01)  
**Hà Nội, năm 2026**

---

# MỤC LỤC

1. Giới thiệu  
   1.1 Tên dự án  
   1.2 Tổng quan dự án  
   1.3 Mục tiêu và phạm vi

2. Cơ sở lý thuyết  
   2.1 Hiệu năng truy vấn cơ sở dữ liệu  
   2.2 Các yếu tố ảnh hưởng đến thời gian thực thi  
   2.3 Bài toán phân loại truy vấn chậm  
   2.4 Mô hình học máy sử dụng trong bài toán

3. Phương pháp và quy trình thực hiện  
   3.1 Kiến trúc tổng thể của hệ thống  
   3.2 Phân chia module và nhiệm vụ  
   3.3 Quy trình huấn luyện và triển khai

4. Thu thập và tiền xử lý dữ liệu  
   4.1 Thiết kế dữ liệu mô phỏng  
   4.2 Sinh câu lệnh SQL ngẫu nhiên  
   4.3 Thu thập log thực thi  
   4.4 Gán nhãn truy vấn chậm/nhanh  
   4.5 Trích xuất đặc trưng

5. Môi trường phân tích  
   5.1 Công cụ và thư viện sử dụng  
   5.2 Môi trường thực thi

6. Mô hình dự đoán  
   6.1 Random Forest  
   6.2 XGBoost  
   6.3 Lý do lựa chọn XGBoost làm mô hình chính

7. Tải và kiểm tra dữ liệu  
   7.1 Nạp dữ liệu  
   7.2 Thông tin tổng quan về dữ liệu  
   7.3 Nhận xét ban đầu

8. Phân tích biến mục tiêu  
   8.1 Mô tả biến mục tiêu  
   8.2 Trực quan hóa biến mục tiêu

9. Phân tích và trực quan hóa dữ liệu  
   9.1 Phân loại đặc trưng  
   9.2 Phân tích đặc trưng phân loại  
   9.3 Phân tích đặc trưng số  
   9.4 Phân tích ngoại lệ

10. Trực quan hóa dữ liệu  
    10.1 Phân bố của các đặc trưng số  
    10.2 So sánh theo tình trạng truy vấn chậm  
    10.3 Phân tích đặc trưng phân loại  
    10.4 Phân tích ma trận tương quan  
    10.5 Biểu đồ cặp

11. Phân tích thống kê và nhận định  
    11.1 Mục tiêu kiểm định  
    11.2 Kiểm định với đặc trưng số  
    11.3 Kiểm định với đặc trưng phân loại  
    11.4 Kết luận thống kê

12. Tổng kết và nhận định chính  
    12.1 Tổng quan dữ liệu  
    12.2 Đặc trưng mục tiêu  
    12.3 Nhận xét về phân phối truy vấn  
    12.4 Yếu tố nguy cơ truy vấn chậm  
    12.5 Chất lượng dữ liệu  
    12.6 Hướng phát triển tiếp theo

13. Tiền xử lý dữ liệu  
    13.1 Xử lý giá trị khuyết  
    13.2 Kỹ thuật tạo đặc trưng  
    13.3 Kiểm định dữ liệu  
    13.4 Chuẩn bị cho mô hình

14. Huấn luyện và đánh giá  
    14.1 Chia dữ liệu huấn luyện và kiểm thử  
    14.2 Huấn luyện mô hình XGBoost  
    14.3 Đánh giá mô hình  
    14.4 Giải thích mô hình  
    14.5 Trực quan hóa kết quả

15. Đánh giá hiệu suất mô hình  
    15.1 Biểu đồ ROC  
    15.2 Ma trận nhầm lẫn  
    15.3 Biểu đồ độ quan trọng đặc trưng  
    15.4 Độ quan trọng theo SHAP/Permutation  
    15.5 Tổng kết mô hình

16. Lưu mô hình và kết quả  
    16.1 Lưu mô hình XGBoost  
    16.2 Lưu bộ chuẩn hóa  
    16.3 Lưu danh sách tên đặc trưng  
    16.4 Lưu kết quả và đánh giá  
    16.5 Hoàn tất giai đoạn huấn luyện

17. Kết luận và hướng phát triển  
    17.1 Kết luận  
    17.2 Hướng phát triển

18. Tổng kết

19. Ứng dụng minh họa  
    19.1 Giới thiệu hệ thống  
    19.2 Quy trình hoạt động  
    19.3 Kết quả minh họa  
    19.4 Ý nghĩa và ứng dụng thực tế  
    19.5 Định hướng phát triển

Tài liệu tham khảo

---

# 1. GIỚI THIỆU

## 1.1 Tên dự án

Hệ thống đánh giá và dự đoán hiệu năng truy vấn cơ sở dữ liệu thời gian thực (SQL Query Performance Predictor).

## 1.2 Tổng quan dự án

Trong các hệ thống cơ sở dữ liệu thực tế, tốc độ thực thi truy vấn ảnh hưởng trực tiếp đến trải nghiệm người dùng và tài nguyên máy chủ. Một truy vấn chậm có thể khiến toàn bộ hệ thống phản hồi kém, tăng độ trễ, làm nghẽn tài nguyên và gây khó khăn trong vận hành.

Dự án này xây dựng một hệ thống Machine Learning có khả năng dự đoán truy vấn SQL nào có nguy cơ chạy chậm trước khi được thực thi. Hệ thống mô phỏng quá trình tạo dữ liệu truy vấn, thu thập log thực thi, trích xuất đặc trưng, huấn luyện mô hình và xây dựng giao diện/API để cảnh báo truy vấn chậm.

## 1.3 Mục tiêu và phạm vi

Mục tiêu của đề tài gồm:

- Xây dựng pipeline thu thập dữ liệu truy vấn SQL mô phỏng.
- Tạo bộ dữ liệu log có các thuộc tính phản ánh đặc điểm truy vấn.
- Trích xuất đặc trưng từ câu lệnh SQL.
- Huấn luyện mô hình dự đoán truy vấn chậm/nhanh.
- Thiết kế giao diện hoặc API đánh giá và cảnh báo latency.
- Trực quan hóa và giải thích kết quả mô hình.

Phạm vi dự án tập trung vào truy vấn SQL dạng SELECT và các yếu tố liên quan đến hiệu năng như độ dài truy vấn, có/không có WHERE, GROUP BY, ORDER BY, LIKE, và số lượng dòng trả về.

---

# 2. CƠ SỞ LÝ THUYẾT

## 2.1 Hiệu năng truy vấn cơ sở dữ liệu

Hiệu năng truy vấn là khả năng hệ thống thực thi câu lệnh SQL trong thời gian ngắn, sử dụng tài nguyên hợp lý và trả về kết quả ổn định. Trong thực tế, thời gian thực thi chịu ảnh hưởng bởi cấu trúc truy vấn, dữ liệu đầu vào, chỉ mục, bộ nhớ đệm, và tải hệ thống.

## 2.2 Các yếu tố ảnh hưởng đến thời gian thực thi

Một số yếu tố phổ biến gồm:

- Độ dài truy vấn.
- Sử dụng SELECT \*.
- Có điều kiện lọc WHERE hay không.
- Có GROUP BY hoặc ORDER BY.
- Có LIKE hoặc wildcard scan.
- Số lượng dòng dữ liệu dự kiến trả về.
- Số bảng tham gia truy vấn.

## 2.3 Bài toán phân loại truy vấn chậm

Bài toán được mô hình hóa như một bài toán phân loại nhị phân:

- Nhãn 0: truy vấn nhanh.
- Nhãn 1: truy vấn chậm.

Mục tiêu là dự đoán xác suất một truy vấn có khả năng vượt ngưỡng thời gian cho phép.

## 2.4 Mô hình học máy sử dụng trong bài toán

Dự án sử dụng các mô hình cây quyết định dạng ensemble, trong đó XGBoost là mô hình chính nhờ khả năng xử lý tốt dữ liệu bảng, độ chính xác cao và khả năng giải thích bằng feature importance.

---

# 3. PHƯƠNG PHÁP VÀ QUY TRÌNH THỰC HIỆN

## 3.1 Kiến trúc tổng thể của hệ thống

Hệ thống gồm 3 giai đoạn chính:

1. Data Pipeline: tạo dữ liệu và thu thập log.
2. Model Training: tiền xử lý, tạo đặc trưng, huấn luyện mô hình.
3. API Benchmarking: tải mô hình, đánh giá truy vấn mới và đo latency.

## 3.2 Phân chia module và nhiệm vụ

Dự án được chia thành 3 notebook riêng biệt:

- `01_Data_Pipeline.ipynb`
- `02_ML_Model_Training.ipynb`
- `03_API_Benchmarking.ipynb`

Notebook `04_Model_Evaluation_And_Analysis.ipynb` được dùng cho phần đánh giá và minh họa lại kết quả từ pipeline đã huấn luyện.

## 3.3 Quy trình huấn luyện và triển khai

Quy trình tổng quát:

- Sinh truy vấn SQL ngẫu nhiên.
- Ghi log thực thi và tạo dataset.
- Tính toán đặc trưng tĩnh từ câu SQL.
- Chia train/test.
- Huấn luyện Random Forest và XGBoost.
- Chọn mô hình phù hợp để lưu và phục vụ dự đoán.
- Xây dựng giao diện benchmark để cảnh báo truy vấn chậm.

---

# 4. THU THẬP VÀ TIỀN XỬ LÝ DỮ LIỆU

## 4.1 Thiết kế dữ liệu mô phỏng

Dữ liệu được tạo dựa trên các bảng mô phỏng như:

- customers
- orders
- transactions
- products
- logs

Mỗi câu lệnh SQL được sinh ra từ tổ hợp ngẫu nhiên của bảng, cột, điều kiện lọc, group by, order by và LIKE.

## 4.2 Sinh câu lệnh SQL ngẫu nhiên

Một số mẫu truy vấn đại diện:

- `SELECT * FROM customers;`
- `SELECT amount, created_at FROM orders WHERE amount > 500;`
- `SELECT status, COUNT(*) FROM transactions GROUP BY status;`
- `SELECT * FROM logs WHERE name LIKE '%error%';`

[Sơ đồ minh họa kiến trúc sinh query]

## 4.3 Thu thập log thực thi

Với mỗi query, hệ thống ghi nhận:

- `sql_query`
- `execution_time_ms`
- `row_count`

Từ đó tạo ra file `dataset_raw.csv`.

## 4.4 Gán nhãn truy vấn chậm/nhanh

Dựa trên ngưỡng thời gian thực thi, truy vấn được gán nhãn:

- 0 nếu truy vấn nhanh.
- 1 nếu truy vấn chậm.

Ngưỡng được thiết kế theo dữ liệu mô phỏng và mục tiêu phân loại hiệu năng.

## 4.5 Trích xuất đặc trưng

Các đặc trưng được dùng trong mô hình gồm:

- `query_length`
- `has_where`
- `has_group_by`
- `has_order_by`
- `has_like`

Các đặc trưng này phản ánh cấu trúc truy vấn và liên quan trực tiếp đến thời gian thực thi.

[Ảnh bảng feature engineering]

---

# 5. MÔI TRƯỜNG PHÂN TÍCH

## 5.1 Công cụ và thư viện sử dụng

Các thư viện chính:

- `pandas`, `numpy` để xử lý dữ liệu.
- `matplotlib`, `seaborn` để trực quan hóa.
- `scikit-learn` để chia dữ liệu và đánh giá mô hình.
- `xgboost` để huấn luyện mô hình chính.
- `joblib` để lưu và tải mô hình.
- `ipywidgets` để xây dựng giao diện tương tác.

## 5.2 Môi trường thực thi

Môi trường được thiết lập trong Jupyter Notebook, sử dụng Python 3.12 và kernel trong virtual environment của workspace.

---

# 6. MÔ HÌNH DỰ ĐOÁN

## 6.1 Random Forest

Random Forest là mô hình ensemble dựa trên nhiều cây quyết định. Mô hình này ổn định, ít overfitting và phù hợp với dữ liệu bảng.

## 6.2 XGBoost

XGBoost là mô hình boosting mạnh, tối ưu tốt cho dữ liệu có cấu trúc và thường cho hiệu năng tốt trong bài toán phân loại nhị phân.

## 6.3 Lý do lựa chọn XGBoost làm mô hình chính

XGBoost được ưu tiên vì:

- Dễ đạt độ chính xác cao trên dữ liệu bảng.
- Hỗ trợ xác suất dự đoán.
- Có feature importance rõ ràng.
- Phù hợp với pipeline của đề tài.

---

# 7. TẢI VÀ KIỂM TRA DỮ LIỆU

## 7.1 Nạp dữ liệu

Dữ liệu đầu vào là file `dataset_raw.csv` được sinh từ notebook 01.

## 7.2 Thông tin tổng quan về dữ liệu

Các thống kê cần trình bày:

- Số dòng dữ liệu.
- Số cột.
- Kiểu dữ liệu.
- Giá trị thiếu.
- Phân phối nhãn.

## 7.3 Nhận xét ban đầu

Nhận xét cần nêu:

- Dữ liệu có cấu trúc bảng rõ ràng.
- Các đặc trưng đầu vào đều có ý nghĩa liên quan đến hiệu năng.
- Tập dữ liệu đủ để minh họa bài toán phân loại truy vấn chậm.

[Chèn ảnh bảng thống kê dữ liệu]

---

# 8. PHÂN TÍCH BIẾN MỤC TIÊU

## 8.1 Mô tả biến mục tiêu

Biến mục tiêu `is_slow_query` có hai giá trị:

- 0: truy vấn nhanh.
- 1: truy vấn chậm.

## 8.2 Trực quan hóa biến mục tiêu

Nên chèn biểu đồ cột thể hiện số lượng query nhanh/chậm và nhận xét cân bằng lớp.

[Chèn Hình 1: phân bố biến mục tiêu]

---

# 9. PHÂN TÍCH VÀ TRỰC QUAN HÓA DỮ LIỆU

## 9.1 Phân loại các đặc trưng

- Đặc trưng cấu trúc query: `query_length`, `has_where`, `has_group_by`, `has_order_by`, `has_like`.
- Đặc trưng liên quan đến chi phí thực thi: `row_count` nếu có trong phiên bản mở rộng.

## 9.2 Phân tích đặc trưng phân loại

Nhận xét theo từng đặc trưng:

- Query có `LIKE` thường tốn nhiều thời gian hơn.
- `GROUP BY` và `ORDER BY` làm tăng độ phức tạp.
- `WHERE` giúp lọc dữ liệu và đôi khi làm query nhanh hơn tùy điều kiện.

## 9.3 Phân tích đặc trưng số

Các thống kê mô tả nên trình bày:

- độ dài query trung bình
- row_count trung bình
- thời gian thực thi trung bình

## 9.4 Phân tích ngoại lệ

Nếu có giá trị ngoại lệ ở `execution_time_ms` hoặc `row_count`, cần nêu cách xử lý: giữ lại vì phản ánh truy vấn nặng, hoặc loại bỏ nếu là giá trị sinh lỗi.

[Chèn bảng/biểu đồ thống kê]

---

# 10. TRỰC QUAN HÓA DỮ LIỆU

## 10.1 Phân bố các đặc trưng số

Nên dùng histogram cho:

- `query_length`
- `execution_time_ms`
- `row_count`

## 10.2 So sánh đặc trưng theo trạng thái truy vấn chậm

Dùng box plot để so sánh:

- truy vấn nhanh vs chậm
- độ dài query
- row_count
- thời gian dự đoán

## 10.3 Phân tích đặc trưng phân loại

Dùng bar plot để so sánh tỷ lệ query chậm theo:

- `has_where`
- `has_group_by`
- `has_order_by`
- `has_like`

## 10.4 Phân tích ma trận tương quan

Cần trình bày heatmap giữa các feature và nhãn `is_slow_query`.

## 10.5 Biểu đồ cặp

Pair plot hoặc scatter matrix giúp quan sát các mối quan hệ giữa `query_length`, `row_count`, `execution_time_ms` và nhãn.

[Chèn Hình 2–6]

---

# 11. PHÂN TÍCH THỐNG KÊ VÀ NHẬN ĐỊNH

## 11.1 Mục tiêu

Kiểm tra các đặc trưng nào có khác biệt rõ ràng giữa truy vấn nhanh và chậm.

## 11.2 Kiểm định với đặc trưng số

Có thể kiểm định:

- độ dài query
- row_count
- execution_time_ms

## 11.3 Kiểm định với đặc trưng phân loại

Có thể dùng Chi-square để kiểm tra quan hệ giữa:

- `has_where`
- `has_group_by`
- `has_order_by`
- `has_like`

## 11.4 Kết luận thống kê

Kết luận dự kiến:

- `LIKE`, `GROUP BY`, `ORDER BY` thường liên quan mạnh đến truy vấn chậm.
- `WHERE` có tác động phụ thuộc điều kiện lọc.

---

# 12. TỔNG KẾT VÀ NHẬN ĐỊNH CHÍNH

## 12.1 Tổng quan dữ liệu

Dataset được tạo từ truy vấn SQL mô phỏng và log thực thi.

## 12.2 Đặc trưng mục tiêu

Tập trung vào dự đoán nhãn chậm/nhanh thay vì mô hình hồi quy.

## 12.3 Nhận xét về phân phối truy vấn

Nên nêu số lượng query nhanh/chậm, sự cân bằng hay mất cân bằng lớp.

## 12.4 Yếu tố nguy cơ truy vấn chậm

Các yếu tố nổi bật thường gồm:

- LIKE
- GROUP BY
- ORDER BY
- truy vấn quá dài
- row_count lớn

## 12.5 Chất lượng dữ liệu

Dataset đủ tốt để minh họa pipeline học máy và benchmark API.

## 12.6 Hướng phát triển tiếp theo

- Bổ sung đặc trưng từ execution plan.
- Thu thập dữ liệu thực tế từ DB engine.
- Mở rộng sang nhiều loại query hơn.
- Tối ưu mô hình và ngưỡng cảnh báo.

---

# 13. TIỀN XỬ LÝ DỮ LIỆU

## 13.1 Xử lý giá trị khuyết

Nếu có giá trị khuyết trong `row_count` hoặc log mô phỏng, cần xử lý bằng median hoặc loại bỏ.

## 13.2 Kỹ thuật tạo đặc trưng

Dự án đang dùng feature engineering dạng tĩnh từ câu SQL:

- query length
- presence of WHERE/GROUP BY/ORDER BY/LIKE

Có thể mở rộng thêm:

- số lượng từ khóa SQL
- có LIMIT hay không
- độ sâu nested query

## 13.3 Kiểm định dữ liệu

Cần xác thực:

- kiểu dữ liệu đúng
- nhãn không bị lỗi
- feature logic phù hợp

## 13.4 Chuẩn bị cho mô hình

Dữ liệu sau khi chuẩn bị được chia train/test với stratified split để giữ phân phối nhãn.

---

# 14. HUẤN LUYỆN VÀ ĐÁNH GIÁ

## 14.1 Chia dữ liệu huấn luyện và kiểm thử

Tập dữ liệu được chia theo tỷ lệ 80/20.

## 14.2 Huấn luyện mô hình XGBoost

Mô hình XGBoost được huấn luyện trên 5 đặc trưng chính.

## 14.3 Đánh giá mô hình

Cần trình bày:

- classification report
- accuracy
- AUC
- confusion matrix

## 14.4 Giải thích mô hình

Feature importance của mô hình dùng để xem yếu tố nào ảnh hưởng lớn nhất đến dự đoán.

## 14.5 Trực quan hóa kết quả

Nên chèn:

- ROC curve
- confusion matrix
- feature importance chart

[Chèn Hình 7–8]

---

# 15. ĐÁNH GIÁ HIỆU SUẤT MÔ HÌNH

## 15.1 Biểu đồ ROC

ROC curve thể hiện khả năng phân biệt query nhanh/chậm của mô hình.

## 15.2 Ma trận nhầm lẫn

Confusion matrix cho biết mô hình dự đoán đúng/sai ở từng lớp.

## 15.3 Biểu đồ độ quan trọng đặc trưng

Nên trình bày thứ tự feature importance của XGBoost.

## 15.4 Độ quan trọng theo SHAP/Permutation

Nếu có, thêm phần giải thích mô hình bằng phương pháp thay thế hoặc SHAP.

## 15.5 Tổng kết mô hình

Nêu kết luận ngắn gọn về hiệu năng, độ ổn định và ý nghĩa thực tiễn.

---

# 16. LƯU MÔ HÌNH VÀ KẾT QUẢ

## 16.1 Lưu mô hình XGBoost

Mô hình được lưu dưới dạng `sql_predictor.pkl`.

## 16.2 Lưu bộ chuẩn hóa

Nếu có scaler, cần lưu cùng mô hình để đảm bảo đầu vào đồng nhất.

## 16.3 Lưu danh sách tên đặc trưng

Cần lưu thứ tự feature để tránh lỗi schema khi dự đoán.

## 16.4 Lưu kết quả và đánh giá

Có thể lưu:

- accuracy
- AUC
- confusion matrix
- classification report

## 16.5 Hoàn tất giai đoạn huấn luyện

Chèn dòng xác nhận mô hình đã sẵn sàng dùng cho benchmark.

---

# 17. KẾT LUẬN VÀ HƯỚNG PHÁT TRIỂN

## 17.1 Kết luận

Dự án đã xây dựng được pipeline hoàn chỉnh cho bài toán dự đoán truy vấn SQL chậm. Từ dữ liệu mô phỏng, hệ thống có thể trích xuất đặc trưng, huấn luyện mô hình và đánh giá hiệu năng bằng các chỉ số phân loại.

## 17.2 Hướng phát triển

- Thêm dữ liệu thực từ DB engine.
- Trích xuất execution plan.
- Mở rộng mô hình dự đoán latency theo nhiều ngưỡng.
- Xây dựng dashboard cảnh báo thời gian thực.
- Tối ưu mô hình và đánh giá bằng cross-validation.

---

# 18. TỔNG KẾT

Hệ thống SQL Query Performance Predictor chứng minh rằng Machine Learning có thể hỗ trợ đánh giá hiệu năng truy vấn trước khi thực thi, giúp giảm thiểu rủi ro query chậm và hỗ trợ người dùng tối ưu câu lệnh SQL sớm hơn.

---

# 19. ỨNG DỤNG MINH HỌA

## 19.1 Giới thiệu hệ thống

Ứng dụng minh họa cho phép người dùng nhập nhiều câu SQL và nhận kết quả cảnh báo nhanh/chậm.

## 19.2 Quy trình hoạt động

- Nhập query.
- Trích xuất đặc trưng.
- Dự đoán xác suất query chậm.
- Hiển thị risk level, confidence và feature importance.

## 19.3 Kết quả minh họa

[Chèn ảnh giao diện API/benchmark]

Ví dụ kết quả:

- Low Risk: truy vấn đơn giản, không có LIKE/GROUP BY phức tạp.
- Medium Risk: truy vấn có một số dấu hiệu tốn tài nguyên.
- High Risk: truy vấn dài, dùng nhiều điều kiện hoặc phép gom nhóm/sắp xếp nặng.

## 19.4 Ý nghĩa và ứng dụng thực tế

Ứng dụng giúp:

- cảnh báo truy vấn chậm trước khi chạy
- hỗ trợ developer tối ưu SQL
- giảm latency tổng thể của hệ thống
- cải thiện trải nghiệm người dùng cuối

## 19.5 Định hướng phát triển

- Tích hợp vào CDSS nội bộ hoặc dashboard monitoring.
- Thêm hỗ trợ nhiều loại query hơn.
- Tự động gợi ý rewrite query.
- Thu thập feedback từ log thực tế.

---

# TÀI LIỆU THAM KHẢO

[1] AWS Machine Learning Foundations – tài liệu thực hành nội bộ của môn học.  
[2] XGBoost Documentation.  
[3] scikit-learn User Guide.  
[4] pandas Documentation.  
[5] Jupyter Notebook Documentation.

---

# PHỤ LỤC ẢNH / SƠ ĐỒ

- [Hình A] Sơ đồ kiến trúc tổng thể của hệ thống.
- [Hình B] Pipeline sinh dữ liệu và thu thập log.
- [Hình C] Phân bố nhãn query nhanh/chậm.
- [Hình D] Correlation heatmap.
- [Hình E] ROC curve và confusion matrix.
- [Hình F] Feature importance của mô hình.
- [Hình G] Giao diện benchmark/API.

> Ghi chú: Các hình trên có thể tạm thay bằng ảnh chụp notebook hoặc hình minh họa trong khi hoàn thiện báo cáo Word/PDF.
