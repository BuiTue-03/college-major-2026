# college-major-2026
Vào một ngày nắng ơi là nắng, tui đã tìm được dataset ưng ý...
# 🎓 College Majors 2026: Analysis & Insights

Dự án phân tích dữ liệu về 228.000 chương trình đào tạo tại các trường đại học ở Mỹ. Dự án kết hợp phân tích Python trên Google Colab và trực quan hóa dữ liệu trên Power BI nhằm đánh giá mối tương quan giữa ngành học, thu nhập, nợ sinh viên và tác động của AI.

## 📊 Về dự án
Bộ dữ liệu được Mind Lab tổng hợp từ 5 nguồn dữ liệu công khai của chính phủ Mỹ (College Scorecard, BLS, O*NET, v.v.). Dự án tập trung vào việc trả lời câu hỏi thực tế: **"Liệu chuyên ngành này có đáng để đầu tư?"** thông qua việc so sánh thu nhập và nợ dựa trên từng trường đại học và ngành học cụ thể.

## 🚀 Các bước thực hiện
1. **Làm sạch dữ liệu**: Xử lý file CSV gốc (xử lý dấu phẩy trong dữ liệu, làm sạch giá trị thiếu, chuẩn hóa định dạng).
2. **Phân tích (EDA)**: Sử dụng Python trên Google Colab để tìm ra:
   - Các ngành có thu nhập cao nhất/thấp nhất.
   - Tương quan giữa chỉ số AI Exposure với thu nhập đầu ra.
   - Các chương trình có tỷ lệ nợ trên thu nhập (Debt-to-Earnings) an toàn.
3. **Trực quan hóa**: Xuất dữ liệu sạch để xây dựng Dashboard trên Power BI, giúp so sánh hiệu quả kinh tế giữa các bang và các nhóm ngành.

## 🛠️ Công nghệ
- **Ngôn ngữ**: Python (Pandas, Seaborn, Matplotlib).
- **Môi trường**: Google Colab.
- **Công cụ trực quan**: Power BI.

## 📂 Cấu trúc Repository
- `analysis.ipynb`: Notebook chứa toàn bộ mã nguồn xử lý và phân tích dữ liệu.
- `cleaned_college_majors.csv`: Dữ liệu đã làm sạch (dùng để import vào Power BI).
- `README.md`: Tài liệu hướng dẫn dự án.

## 💡 Kết quả nổi bật
- Thu nhập trung bình của các ngành kỹ thuật, dược phẩm đứng đầu danh sách.
- Mức độ tiếp xúc với AI (AI Exposure) là một trong những yếu tố dự báo thu nhập mạnh mẽ nhất, đứng ngay sau chỉ số tăng trưởng việc làm dự báo.
- Dữ liệu minh chứng rõ ràng sự phân hóa thu nhập khổng lồ giữa các trường cho cùng một ngành học.

---
*Dữ liệu được sử dụng cho mục đích phân tích học thuật và định hướng nghề nghiệp.*
