# 📋 Insights Memo: College Majors 2026
**Prepared by:** Oriana Bui  
**Dataset:** College Majors 2026 – Earnings, Debt, Jobs, AI (228,000 U.S. degree programs)  
**Last updated:** 2026  

---

## Executive Summary

Phân tích 228.000 chương trình đào tạo đại học Mỹ cho thấy ba kết luận cốt lõi:

> **1.** AI exposure **không** phải yếu tố dự báo thu nhập mạnh khi đứng một mình — nhưng có tác động dương có ý nghĩa thống kê sau khi kiểm soát nhóm ngành.  
> **2.** Loại trường (đặc biệt Private for-profit) là yếu tố rủi ro tài chính nhất quán nhất, vượt qua cả lựa chọn ngành học.  
> **3.** Một số chương trình certificate ngắn hạn có ROI tài chính vượt trội so với bachelor's degree trong cùng ngành — kết quả đi ngược trực giác phổ biến.

---

## 1. Bối cảnh & Câu hỏi Nghiên cứu

Trong bối cảnh AI đang tái định hình thị trường lao động, quyết định chọn ngành học không còn đơn giản là "ngành nào lương cao?" mà còn phải trả lời: *ngành nào lương cao so với chi phí đào tạo, và liệu AI có làm thay đổi phương trình đó không?*

Phân tích này kiểm định 5 giả thuyết cụ thể:

| # | Giả thuyết | Kết quả |
|---|---|---|
| H1 | AI exposure dự báo thu nhập cao hơn, ngay cả sau khi kiểm soát nhóm ngành | ✅ Được ủng hộ (có ý nghĩa thống kê) |
| H2 | Mối quan hệ AI–earnings là phi tuyến (có ngưỡng) | ⚠️ Một phần — xem chi tiết |
| H4 | Private for-profit có debt-to-earnings tệ hơn Public trong cùng điều kiện | ✅ Được ủng hộ mạnh |
| H6 | Distance education có ROI tài chính tốt hơn on-campus | ⚠️ Hỗn hợp — phụ thuộc ngành |
| H7 | Certificate ngắn hạn có DTE tốt hơn Bachelor's trong cùng ngành | ✅ Được ủng hộ ở nhiều ngành |

---

## 2. Thu nhập theo Nhóm ngành

📊 *Xem: `plot1_earnings_by_field.png`*

**Phát hiện chính:**
- Khoảng cách thu nhập giữa nhóm cao nhất và thấp nhất sau 4 năm là rất lớn — nhóm Engineering/CS và Legal Professional vượt xa phần còn lại.
- Tuy nhiên, thu nhập tuyệt đối có thể gây hiểu lầm: một số ngành có thu nhập trung bình cao nhưng chi phí đào tạo cũng rất cao (ví dụ: Medical/Dental programs), dẫn đến debt-to-earnings không thuận lợi.
- Ngành **Health Professions** có số lượng chương trình lớn nhất nhưng phân phối thu nhập rất rộng — từ rất thấp (home health aide programs) đến rất cao (physician assistant, nursing anesthesia).

**Hàm ý:** Nhìn vào nhóm ngành cấp cao (CIP Family) để chọn ngành là chưa đủ — phải nhìn đến loại bằng và loại trường cụ thể.

---

## 3. H1: AI Exposure & Thu nhập — Mối quan hệ thật sự là gì?

📊 *Xem: `plot2_ai_vs_earnings.png` và `plot4_h1_within_field_corr.png`*

**Correlation tổng thể (raw):**  
Pearson r ≈ 0.18–0.25 — tương quan dương nhưng yếu. Nếu chỉ nhìn con số này, ta có thể kết luận AI không quan trọng. Nhưng đây là một **ví dụ điển hình của confounding bias**: các ngành lương cao (CS, Engineering) vừa có AI exposure cao vừa có lương cao vì nhiều lý do khác ngoài AI.

**Sau khi kiểm soát nhóm ngành (OLS Fixed Effects):**  
Khi thêm nhóm ngành vào regression model:
- Hệ số của `ai_software_occupation_share` vẫn dương và có ý nghĩa thống kê (p < 0.05)
- Nghĩa là: trong cùng một nhóm ngành, chương trình nào có AI exposure cao hơn thực sự có xu hướng cho thu nhập cao hơn
- R² của model tăng đáng kể so với model chỉ có AI exposure đơn thuần

**Within-field correlation (plot4):**  
Không phải ngành nào cũng cho cùng một pattern:
- Một số ngành có tương quan AI–earnings dương mạnh (ví dụ: Business, Computer Science)
- Một số ngành có tương quan âm hoặc gần 0 (ví dụ: Education, Social Sciences) — gợi ý rằng trong các ngành này, AI exposure chưa được "định giá" vào lương

**Hàm ý cho sinh viên:** AI exposure là một tín hiệu tốt, nhưng chỉ có ý nghĩa khi đặt trong bối cảnh cụ thể của từng ngành. Chọn ngành có AI exposure cao trong một lĩnh vực ít trả lương cho kỹ năng AI sẽ không cho kết quả mong đợi.

---

## 4. H2: Mối quan hệ Phi tuyến — Có ngưỡng AI không?

📊 *Xem: `plot5_h2_ai_nonlinear.png`*

**Phương pháp:** Chia toàn bộ chương trình thành 5 nhóm (quintile) theo AI exposure, so sánh median earnings và kiểm định bằng One-way ANOVA.

**Phát hiện:**
- Từ Q1 (AI thấp nhất) đến Q3 (trung bình), thu nhập tăng đều — khoảng cách mỗi bước khá nhất quán
- Từ Q4 lên Q5 (top 20% AI highest), thu nhập tăng **đột biến** hơn so với các bước trước — gợi ý có hiệu ứng ngưỡng ở mức AI exposure cao
- ANOVA cho p < 0.001: sự khác biệt giữa các nhóm có ý nghĩa thống kê, không phải ngẫu nhiên

**Hàm ý:** Không phải "càng nhiều AI exposure càng tốt" theo tuyến tính — nhưng ở mức rất cao (top quintile), phần thưởng tài chính tăng không tương xứng. Đây là khu vực đáng nhắm đến.

---

## 5. H4: Loại Trường và Rủi ro Tài chính

📊 *Xem: `plot6_h4_institution_dte.png`*

**Phát hiện:**
- **Private for-profit** có median debt-to-earnings cao nhất, và nhất quán trên hầu hết các nhóm ngành được kiểm tra
- **Public institutions** có DTE thấp nhất, mặc dù thu nhập đầu ra không khác biệt lớn so với private for-profit trong cùng CIP category
- **Private nonprofit** nằm ở giữa, nhưng phân phối rộng hơn — tức là có cả "rất tốt" và "rất tệ" trong cùng nhóm

**Kiểm định thống kê:** Kruskal-Wallis test cho thấy sự khác biệt giữa ba loại trường có ý nghĩa thống kê (p < 0.001).

**Kết quả đáng chú ý (within-field comparison):**  
Trong ngành Health Professions và Business — hai ngành có nhiều chương trình nhất — private for-profit cho DTE cao hơn đáng kể so với public, mặc dù thu nhập đầu ra tương đương. Sinh viên trả nhiều hơn nhưng không kiếm được nhiều hơn.

**Hàm ý cho chính sách:** Đây là bằng chứng hỗ trợ các lo ngại về private for-profit institutions trong hệ thống giáo dục Mỹ. Từ góc độ cá nhân: khi tất cả các yếu tố khác bằng nhau, loại trường có thể quan trọng hơn ngành học trong việc quyết định rủi ro tài chính.

---

## 6. H6: Distance Education — ROI Tốt hơn hay Không?

📊 *Xem: `plot7_h6_distance_education.png`*

**Phát hiện — kết quả hỗn hợp:**

*Điểm ủng hộ:*
- Học phí (tuition) của distance education programs thấp hơn rõ rệt so với on-campus
- Debt tích lũy nhìn chung thấp hơn

*Điểm phản bác:*
- Thu nhập sau tốt nghiệp của distance education programs cũng thấp hơn đáng kể ở một số nhóm ngành
- DTE không nhất thiết tốt hơn vì hai hiệu ứng (debt thấp hơn và earnings thấp hơn) gần như triệt tiêu nhau

**Nuance quan trọng:** Distance education programs tập trung nhiều ở các ngành vốn có lương thấp hơn. Khi kiểm soát ngành học, gap DTE giữa distance và on-campus thu hẹp lại đáng kể — gợi ý đây phần lớn là selection effect chứ không phải causal effect của việc học online.

**Hàm ý:** Học online có thể tiết kiệm chi phí nhưng không phải là "silver bullet" cho ROI — bối cảnh ngành học và chất lượng chương trình vẫn quan trọng hơn.

---

## 7. H7: Certificate vs. Bachelor's — Ai Thắng về ROI?

📊 *Xem: `plot8_h7_credential_dte.png`*

**Đây là phát hiện đi ngược trực giác nhất của toàn bộ phân tích.**

**Phát hiện tổng thể:**
- Certificate 1–2 năm có median DTE thấp hơn Bachelor's ở hầu hết các ngành được kiểm tra
- Sự chênh lệch lớn nhất xuất hiện ở **Health Professions** và **Mechanic & Repair Technologies** — hai ngành mà kỹ năng cụ thể được thị trường lao động định giá cao và không nhất thiết cần bằng 4 năm

**Ngành nào certificate thắng rõ nhất:**
- Skilled trades (điện, hàn, cơ khí)
- Allied health (medical coding, phlebotomy, dental hygiene)
- IT/Networking certifications

**Ngành nào Bachelor's vẫn thắng:**
- Engineering
- Computer Science (nhất là khi nhắm đến big tech)
- Business (khi tính đến career ceiling dài hạn)

**Hàm ý:** "Cần bằng 4 năm" là assumption cần được kiểm tra lại theo từng ngành cụ thể. Từ góc độ thuần túy financial ROI trong ngắn-trung hạn, certificate trong các ngành kỹ năng cụ thể có thể là lựa chọn tối ưu hơn.

---

## 8. H8: AI Exposure và Tốc độ Tăng trưởng Thu nhập

📊 *Xem: `plot9_h8_ai_earnings_trajectory.png`*

**Phát hiện:**
- Cả ba nhóm AI tier đều cho thấy earnings tăng từ 1yr → 5yr — pattern này nhất quán
- **Tốc độ tăng trưởng** (growth rate 1yr → 5yr) cao nhất ở nhóm **High AI tier**, không phải chỉ mức tuyệt đối
- Ở năm 1, khoảng cách giữa ba nhóm tương đối nhỏ. Đến năm 5, khoảng cách mở rộng đáng kể — gợi ý rằng AI exposure có ảnh hưởng lớn hơn đến *career trajectory* so với *starting salary*

**Hàm ý chiến lược:** Nếu tối ưu hóa cho long-term earnings, AI exposure quan trọng hơn cho quyết định ngành học so với nếu chỉ nhìn vào starting salary. Đây là góc độ thường bị bỏ qua khi so sánh các chương trình đào tạo.

---

## 9. Giới hạn của Phân tích

Một phân tích trung thực cần thừa nhận những gì nó **không** làm được:

**1. Correlation ≠ Causation**  
Tất cả các kết quả ở đây là tương quan. Việc một chương trình có AI exposure cao không *gây ra* thu nhập cao hơn — cả hai có thể cùng là kết quả của yếu tố thứ ba (ví dụ: chất lượng trường, địa lý, ngành).

**2. Missing data không ngẫu nhiên**  
Khoảng 60–80% dữ liệu earnings và debt bị missing. Các chương trình có dữ liệu đầy đủ có xu hướng là những chương trình lớn hơn, phổ biến hơn — có thể tạo ra systematic bias trong kết quả.

**3. Không có dữ liệu cá nhân**  
Dataset đo lường outcomes ở cấp độ chương trình (program-level), không phải cá nhân. Không thể rút ra kết luận về một sinh viên cụ thể từ dữ liệu này.

**4. Snapshot trong thời gian**  
Dữ liệu phản ánh outcomes của cohort đã tốt nghiệp từ trước 2026. AI landscape thay đổi rất nhanh — AI exposure của một ngành hôm nay có thể rất khác so với khi các sinh viên trong cohort này tốt nghiệp.

**5. Branch campus confounding**  
Một số outcomes được chia sẻ giữa nhiều branch campuses (cùng OPEID6), có nghĩa là không phải mọi dòng dữ liệu đều độc lập hoàn toàn.

---

## 10. Kết luận & Khuyến nghị

**Cho sinh viên đang chọn ngành:**
- Đừng chỉ nhìn vào thu nhập trung bình của ngành — nhìn vào debt-to-earnings của *chương trình cụ thể* tại *loại trường cụ thể*
- Private for-profit institutions cần được xem xét kỹ hơn trước khi lựa chọn
- Certificate trong ngành kỹ năng cụ thể có thể cho ROI tốt hơn bachelor's trong ngắn hạn
- AI exposure cao trong ngành mình chọn là tín hiệu tốt cho long-term earnings growth

**Cho nhà phân tích muốn đi sâu hơn:**
- Kiểm định H9 (AI và geography gap) và H10 (geographic retention) với dữ liệu đầy đủ
- Bổ sung cost-of-living adjustment theo tiểu bang để so sánh earnings thực sự
- Join với BLS Occupational Outlook data để dự báo job growth theo ngành

---

*Phân tích được thực hiện bằng Python (pandas, seaborn, scipy, statsmodels). Dữ liệu nguồn: Kaggle — College Majors 2026.*  
*Xem toàn bộ code tại: [`notebooks/college_majors_analysis.ipynb`](../notebooks/college_majors_analysis.ipynb)*
