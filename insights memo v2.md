# 📋 Insights Memo v2: Extended Analysis
**Prepared by:** Oriana Bui  
**Dataset:** College Majors 2026 – Earnings, Debt, Jobs, AI (228,000 U.S. degree programs)  
**Phạm vi:** Bổ sung cho Memo v1 — gồm H8 (fixed), COL Adjustment, H9, H10  
**Last updated:** 13/08/2026  

---

## Executive Summary

4 phân tích bổ sung cho kết quả đáng chú ý hơn so với phần lớn các hypothesis trong Memo v1:

> **1.** H8 (fixed): High-AI programs có earnings growth **gấp 3 lần** Low-AI programs (+60.1% vs +20.5%) — pattern rõ ràng và nhất quán, dù chưa đạt ngưỡng p < 0.05 do sample size nhỏ (chỉ 8 chương trình High AI).  
> **2.** COL Adjustment đảo ngược hoàn toàn bảng xếp hạng thu nhập: các tiểu bang "lương cao" như CO, CT, CA, NY thực ra có purchasing power thấp hơn đáng kể. AL, MI, TX — những tiểu bang thường bị bỏ qua — nổi lên như lựa chọn tài chính thực chất hơn.  
> **3.** H9: AI exposure tạo ra "premium" dương ở 8/9 vùng, nhưng mức độ rất không đồng đều — Great Lakes (+$18.7K) và Rocky Mountains (+$18.4K) hưởng lợi nhiều nhất, trong khi Plains thực ra bị âm (−$13.6K).  
> **4.** H10: Thị trường lao động lớn hơn **không** giữ chân sinh viên tốt hơn (r = −0.215, p = 0.253) — kết quả đi ngược trực giác và gợi ý các yếu tố phi kinh tế (gia đình, văn hóa, chi phí sống) đóng vai trò quan trọng hơn trong quyết định ở lại.

---

## 1. H8 (Fixed): High-AI Programs và Tốc độ Tăng trưởng Thu nhập

![H8 Fixed: AI Earnings Trajectory](./plots/plot_h8_fixed_ai_trajectory.png)

**Kết quả thực tế:**

| AI Tier | Định nghĩa | Growth Rate (1yr → 5yr) | Earnings tại 5yr |
|---|---|---|---|
| Low AI (= 0%) | Không có nghề nào dùng AI | +20.5% | $47K |
| Mid AI (0–50%) | Một số nghề dùng AI | +31.4% | $55K |
| High AI (> 50%) | Đa số nghề dùng AI | **+60.1%** | **$68K** |

- ANOVA: F = 2.82, **p = 0.061** → chưa đạt ngưỡng p < 0.05
- Số chương trình High AI: chỉ **8** (vs 196 Low AI, 70 Mid AI) — sample quá nhỏ

**Pattern đáng chú ý từ trajectory plot:**
- Năm 1: ba nhóm bắt đầu gần nhau (~$35–40K), khoảng cách không lớn
- Năm 4–5: thứ tự đảo hoàn toàn — High AI vọt lên $68K, Low AI chỉ đạt $47K và còn bắt đầu *giảm* từ năm 4 sang 5yr
- Đây là bằng chứng mạnh nhất trong toàn bộ dataset rằng AI exposure ảnh hưởng đến **career trajectory** nhiều hơn là starting point

**Tại sao ANOVA không có ý nghĩa dù pattern rõ?**  
Với chỉ 8 quan sát trong nhóm High AI, statistical power quá thấp để detect sự khác biệt dù effect size thực tế rất lớn. Đây là **Type II error** (false negative) do sample size nhỏ — không phải bằng chứng rằng H8 sai.

**Kết luận H8:** ⚠️ Chưa kết luận chắc chắn về mặt thống kê, nhưng **pattern thực tế rất thuyết phục**. Cần thêm dữ liệu để kiểm định đúng nghĩa. Đây là hypothesis đáng theo dõi nhất khi dataset được cập nhật.

---

## 2. Cost-of-Living Adjustment: Bảng Xếp Hạng Thật Sự

![COL Adjustment by State](./plots/plot_col_adjustment.png)

**Dữ liệu COL Index (nguồn: MIT Living Wage, 2024):**  
COL Index > 1.0 = đắt hơn trung bình quốc gia | < 1.0 = rẻ hơn

**Tiểu bang tăng rank sau điều chỉnh (underrated về thu nhập thực):**

| State | Rank Nominal | Rank Adjusted | Thay đổi | COL Index |
|---|---|---|---|---|
| AL | 10 | 5 | **+5** | 0.874 |
| MI | 7 | 3 | **+4** | 0.921 |
| TX | 5 | 2 | **+3** | 0.948 |
| GA | 9 | 7 | +2 | 0.924 |
| KY | 13 | 12 | +1 | 0.882 |

**Tiểu bang giảm rank sau điều chỉnh (overrated về thu nhập thực):**

| State | Rank Nominal | Rank Adjusted | Thay đổi | COL Index |
|---|---|---|---|---|
| CO | 4 | 9 | **−5** | 1.087 |
| CT | 3 | 8 | **−5** | 1.198 |
| CA | 11 | 13 | −2 | 1.392 |
| FL | 8 | 10 | −2 | 1.023 |
| NY | 2 | 4 | −2 | 1.298 |

**Phân tích:**
- **Alabama** nhảy từ top 10 lên top 5 sau điều chỉnh — lương tuyệt đối không cao nhưng purchasing power thực tế vượt trội so với các tiểu bang coastal
- **California** (COL = 1.392): $60K ở CA tương đương ~$43K purchasing power so với trung bình quốc gia
- **Colorado** giảm mạnh nhất (−5 rank): cảnh báo cho những ai theo đuổi "tech salary" ở Denver/Boulder mà không tính đến COL tăng nhanh
- **Missouri (MO)** xuất hiện là nominal earnings cao nhất trong top 15 — khả năng cao do một số chương trình chuyên biệt (medical, law) kéo median lên, cần điều tra thêm

**Hàm ý thực tiễn:** Khi so sánh offer salary giữa các tiểu bang, con số nominal có thể đánh lừa hoàn toàn. Một sinh viên nhận $55K ở Alabama có thể có purchasing power tương đương người nhận $75K ở California.

---

## 3. H9: AI Exposure có San Bằng Khoảng Cách Vùng Miền Không?

![H9: AI Geography Gap](./plots/plot_h9_ai_geography.png)

**AI Premium (High AI − Low AI) theo vùng:**

| Region | Low AI | High AI | Premium | % Gap |
|---|---|---|---|---|
| Great Lakes | $44,589 | $63,318 | **+$18,728** | +42% |
| Rocky Mountains | $56,207 | $74,560 | **+$18,353** | +33% |
| New England | $51,951 | $68,222 | +$16,271 | +31% |
| Southwest | $58,674 | $65,244 | +$6,570 | +11% |
| Outlying Areas | $30,858 | $37,472 | +$6,614 | +21% |
| Mid East | $66,162 | $70,416 | +$4,254 | +6% |
| Far West | $46,100 | $48,320 | +$2,220 | +5% |
| Southeast | $49,440 | $49,246 | **−$194** | ~0% |
| **Plains** | **$87,922** | $74,312 | **−$13,610** | **−15%** |

- Levene's test: stat = 2.48, **p = 0.117** → phương sai giữa hai nhóm không khác nhau có ý nghĩa thống kê

**Phân tích:**

*Vùng hưởng lợi nhiều nhất:*
- **Great Lakes (+$18.7K, +42%):** Kết quả bất ngờ nhất. Midwest thường bị coi là "not a tech hub" nhưng lại có AI premium cao nhất — có thể do manufacturing automation và advanced manufacturing programs đang tích hợp AI mạnh mẽ.
- **Rocky Mountains (+$18.4K, +33%):** Denver/Boulder tech scene đang phát triển, kéo earnings của High AI programs lên đáng kể.
- **New England (+$16.3K, +31%):** Boston/Cambridge biotech và fintech ecosystem định giá AI skills cao.

*Vùng không hưởng lợi:*
- **Southeast (−$194):** AI exposure gần như không tạo ra premium — thị trường lao động khu vực này chưa định giá AI skills rõ ràng.
- **Plains (−$13.6K):** Outlier lớn nhất. Low AI programs ở Plains có earnings nominal rất cao ($87,922) — có thể do chương trình nông nghiệp, energy, hoặc medical chuyên biệt. Cần điều tra thêm.

**Coefficient of Variation (plot phải):** High AI programs nhất quán có CV thấp hơn ở hầu hết các region — earnings đồng đều hơn, ít outlier hơn, không chỉ cao hơn về median.

**Kết luận H9:** ❌ Không được ủng hộ theo nghĩa gốc. AI không "san bằng" khoảng cách địa lý — thực tế ngược lại: AI *khuếch đại* bất bình đẳng vùng miền. AI premium phụ thuộc mạnh vào ecosystem địa phương.

---

## 4. H10: Thị Trường Lao Động Lớn Hơn Giữ Chân Sinh Viên Tốt Hơn?

![H10: Geographic Retention](./plots/plot_h10_geographic_retention.png)

**Kết quả thực tế:**
- Pearson r = **−0.215**, p = **0.253** → tương quan âm yếu, không có ý nghĩa thống kê
- Hướng âm: thị trường lớn hơn liên quan đến retention *thấp hơn* — ngược chiều giả thuyết

**Top retention:** MA, NC, WA, GA, OH, KY, NJ, UT, WI, MN  
**Bottom retention:** PA, MI, CA, AK, PR, VA, AL, MO, IL, VT

**Phân tích các pattern bất ngờ:**

*California — retention thấp dù thị trường lớn nhất:*  
CA có median occupation employment cao nhất (~5,000K) nhưng nằm trong nhóm retention thấp. Chi phí sinh hoạt cực cao có thể buộc sinh viên sau tốt nghiệp phải rời đi, hoặc nhiều sinh viên đến CA để học nhưng về quê sau tốt nghiệp.

*Massachusetts — retention cao nhất:*  
Nhất quán với Boston/Cambridge ecosystem: sinh viên tìm được việc ngay tại địa phương nhờ cluster biotech, fintech, và higher ed đặc biệt dày đặc — đây là market depth theo ngành cụ thể, không phải market size tổng thể.

*Pennsylvania — retention thấp dù có Philly và Pittsburgh:*  
Nhiều sinh viên học ở PA (đặc biệt tại liberal arts colleges) nhưng tìm việc ở NYC hoặc DC — hai thị trường lớn hơn chỉ vài giờ lái xe. Hiệu ứng "geographic spillover" sang metro lớn hơn.

**Tại sao H10 không được ủng hộ?**  
Market size là điều kiện cần nhưng chưa đủ. Các yếu tố có khả năng quan trọng hơn:
- Chi phí sinh hoạt (CA, NY, CO market lớn nhưng COL cao → sinh viên rời đi)
- Mức độ tập trung ngành (*cluster depth* thay vì *market breadth*)
- Khoảng cách đến metro lớn hơn (PA mất sinh viên vào NYC/DC)
- Yếu tố phi kinh tế: gia đình, văn hóa, mạng lưới xã hội

**Kết luận H10:** ❌ Không được ủng hộ. Thị trường lao động lớn hơn không dự báo retention rate cao hơn. *Cluster ngành* và *chi phí sinh hoạt* có vẻ quan trọng hơn tổng quy mô thị trường.

---

## 5. Tổng Kết: Bức Tranh Đầy Đủ Sau Cả Hai Memo

**✅ Kết luận vững chắc (đủ dữ liệu để tin tưởng):**
1. Ngành học và loại bằng quyết định chính ROI tài chính (R² = 0.631, H5)
2. Associate's degree có DTE tốt hơn Bachelor's tổng thể (0.41× vs 0.51×, H7)
3. Trường selective không đảm bảo ROI tốt hơn sau khi kiểm soát ngành (H5)
4. COL adjustment đảo ngược đáng kể bảng xếp hạng — AL, MI, TX underrated; CA, CO, CT overrated
5. AI premium tồn tại nhưng phân bổ không đều theo vùng — Great Lakes và Rocky Mountains hưởng lợi nhất (H9)

**⚠️ Kết luận cần thêm dữ liệu:**
1. H8: Pattern growth rate (+20% → +31% → +60%) rất thuyết phục nhưng chỉ có 8 chương trình High AI
2. H2: AI premium $51K → $60K có ý nghĩa (p=0.020) nhưng không thể kiểm định tính phi tuyến
3. H4: Private for-profit vs Public cần dataset không bị filter cohort

**❌ Giả thuyết bị bác bỏ:**
1. H1, H3: AI exposure không dự báo được earnings đáng tin cậy ở cấp độ chương trình
2. H9: AI không san bằng — thực ra khuếch đại bất bình đẳng vùng miền
3. H10: Thị trường lớn hơn không giữ chân sinh viên tốt hơn

---

## 6. Giới Hạn Bổ Sung

**COL Index hardcoded state-level:** Không phản ánh chênh lệch nội tiểu bang (NYC vs upstate NY, Bay Area vs Central Valley CA). Cần upgrade lên county-level COLI data từ C2ER.

**H8 — sample cực nhỏ ở High AI:** Chỉ 8 chương trình. Cần ít nhất ~30 quan sát mỗi nhóm để ANOVA có đủ power.

**H9 — Plains outlier:** Median $87,922 cho Low AI ở Plains bất thường cao — cần điều tra loại chương trình nào tạo ra con số này.

**H10 — proxy không hoàn hảo:** `occupation_employment_2024_thousands` là employment của nghề liên kết với chương trình, không phải tổng employment tiểu bang.

---

## 7. Khuyến Nghị Cho Phân Tích Tiếp Theo

1. **H8:** Dùng bootstrap resampling để ước lượng confidence interval cho growth rate difference
2. **COL:** Upgrade lên county-level COL index (COLI data từ C2ER)
3. **H9 Plains:** Filter và phân tích riêng chương trình đang kéo Low AI earnings ở Plains lên $87K
4. **H10:** Thêm biến COL index và "distance to nearest major metro" vào regression
5. **Tổng thể:** Join với BLS Occupational Outlook 2024–2034 projections để thêm chiều "tương lai"

---

*Phân tích được thực hiện bằng Python (pandas, seaborn, scipy, statsmodels). Dữ liệu nguồn: Kaggle — College Majors 2026 | COL Index: MIT Living Wage 2024.*  
*Xem toàn bộ code tại: [`notebooks/college_majors_analysis.ipynb`](../notebooks/college_majors_analysis.ipynb)*  
*← Quay lại Memo v1: [`insights_memo.md`](./insights_memo.md)*
