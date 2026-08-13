# 🎓 College Majors 2026: Phân Tích & Góc Nhìn

> Vào một ngày nắng ơi là nắng, tui đã tìm được dataset ưng ý...  
> Và đây là thứ tui làm với nó.

---

## 📌 Tổng quan

Project này phân tích **228.000 chương trình đào tạo đại học tại Mỹ** :bao gồm dữ liệu về thu nhập sau tốt nghiệp, nợ sinh viên, tỷ lệ việc làm, và mức độ phơi nhiễm AI trong các ngành nghề liên quan.

Câu hỏi thật sự tui muốn trả lời không phải là "ngành nào lương cao nhất" mà chính là:

> **Trong thời đại AI đang định hình lại thị trường lao động, ngành học nào thực sự đáng đầu tư và đáng theo cách nào?**

---

## 🔍 Các câu hỏi được khai thác

- Ngành nào có thu nhập tốt nhất sau 4 năm tốt nghiệp  và ngành nào có rủi ro tài chính cao nhất?
- AI exposure trong nghề nghiệp liên kết có thực sự dự báo thu nhập cao hơn không?
- Tỷ lệ nợ trên thu nhập (debt-to-earnings) thay đổi như thế nào theo loại trường, loại bằng, và vùng địa lý?
- Chương trình nào mang lại giá trị tài chính tốt nhất so với chi phí bỏ ra?

---

## 📁 Cấu trúc thư mục

```
college-major-2026/
│
├── data/
│   ├── college_majors_2026.csv          # Dữ liệu gốc (nguồn: xem bên dưới)
│   └── cleaned_college_majors.csv       # Dữ liệu sau khi làm sạch
│
├── notebooks/
│   └── college_majors_analysis.ipynb    # Notebook phân tích đầy đủ (chạy được trên Colab)
│
├── dashboard/
│   └── college_majors_powerbi.pbix      # Dashboard Power BI tương tác
│
├── memo/
│   └── insights_memo.md                 # Tổng hợp insight theo dạng business memo
│
├── README.md                            # Bản tiếng Việt (file này)
└── README_EN.md                         # Bản tiếng Anh
```

---

## 🛠️ Công nghệ & Kỹ năng thể hiện

| Mảng | Công cụ / Phương pháp |
|---|---|
| Làm sạch & xử lý dữ liệu | Python, pandas  xử lý 228K dòng, quoted fields, missing values, ép kiểu dữ liệu |
| Phân tích khám phá (EDA) | seaborn, matplotlib  phân phối, tương quan, phát hiện outlier |
| Phân tích thống kê | Pearson correlation, lọc cohort, so sánh theo phân vị |
| Business insight | Framing debt-to-earnings, phân khúc theo AI exposure, so sánh vùng miền |
| Trực quan hóa dữ liệu | Power BI  dashboard tương tác với bộ lọc theo ngành, tiểu bang, loại bằng |

---

## 💡 Một số phát hiện đáng chú ý

> Phân tích đầy đủ có tại [`memo/insights_memo.md`](./memo/insights_memo.md)

- **Engineering và Computer Science** liên tục vượt median thu nhập quốc gia  nhưng khoảng cách này thu hẹp đáng kể khi tính đến mức nợ sinh viên.
- **AI exposure không phải yếu tố dự báo thu nhập mạnh** (Pearson r ≈ 0.18–0.25). Nhóm ngành và loại bằng giải thích phần lớn sự biến động thu nhập hơn.
- **Trường tư thục vì lợi nhuận (private for-profit)** có tỷ lệ debt-to-earnings tệ nhất trung bình  dù thu nhập đầu ra tương đương trường công trong cùng nhóm ngành CIP.
- Một số **chương trình certificate ngắn hạn** trong lĩnh vực y tế hỗ trợ và nghề kỹ thuật có ROI tài chính tốt hơn bằng cử nhân 4 năm  kết quả đi ngược trực giác và đáng suy nghĩ.

---

## 📊 Dashboard Power BI

> *Import file `college_majors_powerbi.pbix` để khám phá tương tác*

Dashboard bao gồm:
- Phân phối thu nhập theo nhóm ngành và loại bằng
- Heatmap debt-to-earnings theo loại trường × vùng địa lý
- Scatter AI exposure vs. thu nhập với bộ lọc ngành
- Top / bottom 10 chương trình theo ROI tài chính

---

## 📂 Dataset

**Nguồn:** https://www.kaggle.com/datasets/kylefengkfeng209/college-majors-2026-earnings-debt-jobs-ai  
**Kích thước:** ~228.000 dòng × 72 cột  
**Phạm vi:** Các chương trình đại học tại Mỹ, kết quả đo lường sau 1, 4 và 5 năm tốt nghiệp  
**Cột chính:** `median_earnings_4yr_usd`, `median_debt_usd`, `debt_to_earnings_4yr`, `ai_software_occupation_share`

---

## 🚀 Tự chạy thử

Notebook được thiết kế để chạy trên **Google Colab**, không cần cài đặt:

1. Upload file `college_majors_2026.csv` lên phiên Colab
2. Mở `notebooks/college_majors_analysis.ipynb`
3. Run all cells  file CSV đã làm sạch và các biểu đồ sẽ tự động xuất

```python
# Hoặc load từ Google Drive
from google.colab import drive
drive.mount('/content/drive')
df = pd.read_csv('/content/drive/MyDrive/college_majors_2026.csv', low_memory=False)
```

---

## 👤 Về tác giả

**6 tháng kinh nghiệm làm Business Analyst**  project này phản ánh cách tui tiếp cận công việc phân tích: bắt đầu từ một câu hỏi thật sự, không phải từ một dataset. Tui quan tâm đến những vị trí mà phân tích dữ liệu kết nối trực tiếp với quyết định kinh doanh.

📎 [LinkedIn](#) · 📧 [Email](#)

*Dữ liệu được sử dụng cho mục đích phân tích học thuật và định hướng nghề nghiệp.*
