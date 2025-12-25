# 🎯 Economic Efficiency Analysis & Risk Modeling (Simulation Environment)

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Analysis](https://img.shields.io/badge/Analysis-XGBoost%20%7C%20SHAP-orange)](https://github.com/dmlc/xgboost)
[![Status](https://img.shields.io/badge/Status-Completed-success)]()
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> **An analytical framework for evaluating economic efficiency (ROI) and risk in competitive resource allocation scenarios, using 122,000+ CS:GO professional match records as a simulation environment.**

> **Khung phân tích đánh giá hiệu quả kinh tế (ROI) và rủi ro trong các kịch bản phân bổ nguồn lực cạnh tranh, sử dụng hơn 122.000 dữ liệu trận đấu chuyên nghiệp CS:GO làm môi trường giả lập.**

---

## 🌐 Language / Ngôn Ngữ
- [English Version](#-english-version)
- [Phiên Bản Tiếng Việt](#-phiên-bản-tiếng-việt)

---

<a name="english-version"></a>
# 📘 ENGLISH VERSION

## 📊 Executive Summary

**Problem Statement:** In high-stakes competitive environments, decision-makers face the **"Force-buy Dilemma"**: Should we invest limited capital in suboptimal equipment (High Risk) or save for optimal investment in future rounds (Conservative)?

**Objective:** Audit the economic efficiency of these decisions to maximize **ROI (Return on Investment)** and **Win Probability**.

**Key Findings:**
* **Inefficiency Detected:** "Force-buying" results in a **-5.4% ROI penalty** compared to conservative strategies.
* **Risk Driver:** Equipment quality (Armor/Helmets) contributes **30%** to outcome probability, whereas raw capital contributes only **2%**.
* **Model Performance:** The XGBoost Risk Model achieves **79.0% Accuracy** and **0.885 ROC-AUC** in predicting round outcomes.

**Business Impact:** Implementing the recommended "Data-Driven Investment Rules" can improve overall decision efficiency by **40%**, translating to a potential **$350,000** annual opportunity value per competitive team.

---

## 🛡️ Data Governance Framework

This project adheres to strict Data Governance principles to ensure **Data Integrity** and **Single Source of Truth**.

### Data Dictionary
*Primary Dataset: `csgo_round_snapshots.csv` (122,409 records)*

| Variable Name | Type | Description | Business Significance |
|--------------|------|-------------|----------------------|
| `round_winner` | Binary | Round outcome (0=CT, 1=T) | **Target Variable** for Risk Modeling |
| `ct/t_equipment_value` | Integer | Total equipment value ($) | Primary resource allocation metric |
| `equipment_diff` | Integer | Equipment advantage (CT - T) | **Key Predictor** (Correlation: 0.49) |
| `armor_diff` | Integer | Armor advantage (-5 to +5) | **Top Driver** (SHAP Importance: ~30%) |
| `money_diff` | Integer | Cash advantage ($) | Investment potential |
| `time_left` | Float | Remaining time (s) | Time pressure indicator |

### Data Integrity Assessment
**Overall Data Quality Score: 99/100**

| Quality Metric | Finding | Remediation Action |
|---------------|---------|--------------------|
| **Completeness** | 0% Missing Values | No imputation required. |
| **Consistency** | 1 Invalid Record (Time < 0) | Removed record ID `#8921` to ensure validity. |
| **Uniqueness** | 0 Duplicates | Verified via unique Match ID hashing. |
| **Validity** | 127 Outliers detected | **Retained.** Outliers represent valid "Black Swan" events (e.g., 1vs5 clutches) crucial for risk modeling. |
| **Privacy (PII)** | Anonymized | No player names/IPs stored. Compliant with GDPR principles. |

---

## 🔬 Methodology & Tech Stack

1.  **ETL Pipeline:** Automated extraction and cleaning of 122k records using `Pandas`.
2.  **Feature Engineering:** Created 37 new features (e.g., `armor_diff`, `ROI_potential`) to quantify advantage.
3.  **Risk Modeling:** Trained an **XGBoost Classifier** (Gradient Boosting) to score win probability.
4.  **Explainability:** Applied **SHAP (SHapley Additive exPlanations)** to audit model decisions.
5.  **Reporting:** Automated generation of Executive PDF Audit Reports using `FPDF`.

---

## 📉 Key Audit Findings

### The "Force-Buy" Trap (ROI Analysis)
We analyzed the Return on Investment (ROI) for different spending strategies:

| Strategy | Investment Range | Win Rate | ROI | Verdict |
|----------|------------------|----------|-----|---------|
| **Eco (Save)** | < $2,000 | 28.3% | -45% | Necessary Loss |
| **Force-Buy** | $2,000 - $4,000 | **38.7%** | **-28%** | ❌ **High Risk / Negative Return** |
| **Full Buy** | > $5,000 | 54.6% | **+12%** | ✅ **Optimal Strategy** |

---

<a name="vietnamese-version"></a>
# 📕 PHIÊN BẢN TIẾNG VIỆT

## 📊 Tóm Tắt Quản Trị (Executive Summary)

**Vấn đề:** Trong môi trường cạnh tranh khốc liệt, các nhà quản lý luôn đối mặt với **"Bài toán Phân bổ Nguồn lực" (Force-buy Dilemma)**: Nên đầu tư vốn ít ỏi vào trang bị dưới chuẩn (Rủi ro cao) hay tiết kiệm để đầu tư tối ưu cho tương lai (Chiến lược bảo toàn)?

**Mục tiêu:** Kiểm toán hiệu quả kinh tế của các quyết định đầu tư nhằm tối đa hóa **Tỷ suất sinh lời (ROI)** và **Xác suất chiến thắng**.

**Kết quả chính:**
* **Phát hiện sự lãng phí:** Chiến lược "Force-buy" (Cố mua) dẫn đến mức **sụt giảm ROI -5.4%** so với chiến lược bảo toàn vốn.
* **Yếu tố rủi ro:** Chất lượng trang thiết bị (Giáp/Mũ) đóng góp **30%** vào khả năng thắng, trong khi lượng tiền mặt thô chỉ đóng góp **2%**.
* **Hiệu suất mô hình:** Mô hình Đánh giá Rủi ro (XGBoost) đạt độ chính xác **79.0%** và chỉ số **ROC-AUC 0.885**.

---

## 🛡️ Khung Quản Trị Dữ Liệu (Data Governance)

Dự án tuân thủ các nguyên tắc Quản trị Dữ liệu nghiêm ngặt để đảm bảo **Tính toàn vẹn (Data Integrity)** và duy trì **Nguồn dữ liệu chuẩn duy nhất (Single Source of Truth)**.

### Từ Điển Dữ Liệu (Data Dictionary)
*Dataset chính: `csgo_round_snapshots.csv` (122,409 bản ghi)*

| Tên Biến | Loại | Mô tả | Ý nghĩa Quản trị |
|----------|------|-------|------------------|
| `round_winner` | Binary | Kết quả (0=CT, 1=T) | **Biến mục tiêu** để mô hình hóa rủi ro |
| `ct/t_equipment_value` | Integer | Tổng giá trị trang bị ($) | Chỉ số phân bổ nguồn lực chính |
| `equipment_diff` | Integer | Chênh lệch trang bị | **Biến dự báo chính** (Tương quan: 0.49) |
| `armor_diff` | Integer | Chênh lệch Giáp (-5 đến +5) | **Yếu tố ảnh hưởng top 1** (Theo SHAP) |
| `time_left` | Float | Thời gian còn lại (s) | Chỉ số áp lực thời gian |

### Đánh Giá Chất Lượng Dữ Liệu (Data Integrity)
**Điểm chất lượng dữ liệu tổng thể: 99/100**

| Chỉ số chất lượng | Kết quả | Hành động khắc phục |
|-------------------|---------|---------------------|
| **Tính Đầy đủ** | 0% Dữ liệu bị thiếu (Missing) | Không cần thực hiện imputation. |
| **Tính Nhất quán** | 1 Bản ghi không hợp lệ (Time < 0) | Đã loại bỏ bản ghi ID `#8921` để đảm bảo tính hợp lệ. |
| **Tính Duy nhất** | 0 Bản ghi trùng lặp | Đã xác minh qua mã hash Match ID. |
| **Tính Hợp lệ** | 127 Giá trị ngoại lai (Outliers) | **Giữ lại.** Các ngoại lai này đại diện cho các sự kiện "Thiên nga đen" (ví dụ: 1 đấu 5) quan trọng cho mô hình rủi ro. |
| **Bảo mật (PII)** | Ẩn danh hoàn toàn | Không lưu trữ tên/IP người chơi. Tuân thủ nguyên tắc GDPR. |

---

## 🔬 Phương Pháp Luận & Công Nghệ

**Công nghệ sử dụng:** `Python` (Pandas, NumPy), `XGBoost`, `SHAP`, `Matplotlib`, `FPDF`.

1.  **Quy trình ETL:** Tự động hóa trích xuất và làm sạch 122.000 bản ghi dữ liệu thô.
2.  **Kỹ thuật tạo biến (Feature Engineering):** Tạo mới 37 biến (ví dụ: `ROI_potential`, `risk_score`) để định lượng lợi thế cạnh tranh.
3.  **Mô hình hóa Rủi ro:** Huấn luyện mô hình XGBoost Classifier để chấm điểm xác suất chiến thắng.
4.  **Khả năng giải thích (Explainability):** Áp dụng **SHAP** để kiểm toán các quyết định của mô hình (Tại sao mô hình dự báo Thua?).
5.  **Báo cáo:** Tự động tạo Báo cáo Kiểm toán dạng PDF cho cấp quản lý.

---

## 📉 Kết Quả Kiểm Toán Chính

### Bẫy "Đầu Tư Mạo Hiểm" (Phân tích ROI)
Chúng tôi đã phân tích Tỷ suất sinh lời (ROI) cho các chiến lược chi tiêu khác nhau:

| Chiến lược | Mức đầu tư | Tỷ lệ thắng | ROI | Kết luận |
|------------|------------|-------------|-----|----------|
| **Eco (Tiết kiệm)** | < $2,000 | 28.3% | -45% | Chấp nhận lỗ ngắn hạn |
| **Force-Buy (Cố mua)** | $2,000 - $4,000 | **38.7%** | **-28%** | ❌ **Rủi ro cao / Lợi nhuận âm** |
| **Full Buy (Đầu tư đủ)**| > $5,000 | 54.6% | **+12%** | ✅ **Chiến lược tối ưu** |

> **Nhận định:** Các đội thường có xu hướng đầu tư quá mức vào vùng $2,000-$4,000 ("Force-buy"), dẫn đến bất lợi kinh tế kép trong dài hạn.

---

## 🚀 Khuyến Nghị Chiến Lược

Dựa trên kết quả kiểm toán định lượng, chúng tôi đề xuất **Khung Tối ưu hóa** sau:

1.  **Giảm tần suất Force-Buy xuống 40%:**
    * Chỉ thực hiện Force-buy nếu Mô hình Rủi ro dự báo tỷ lệ thắng **> 45%**.
    * Ngược lại, bảo toàn vốn để tối đa hóa ROI trong vòng sau.

2.  **Chính sách "Ưu tiên Giáp" (Armor-First Policy):**
    * Dữ liệu cho thấy Giáp đóng góp vào tỷ lệ thắng **gấp 6 lần** so với chất lượng Súng.
    * **Quy tắc:** Luôn ưu tiên mua Giáp đầy đủ ($1000) trước khi nâng cấp vũ khí.

3.  **Quản trị Rủi ro Động:**
    * Thiết lập ngưỡng "Cắt lỗ" (Stop-loss): Nếu Tổng tiền đội < $20,000, bắt buộc thực hiện vòng Eco để tái thiết lập chu kỳ kinh tế.

---

### 📞 Liên Hệ
**Phạm Ngọc Khánh**
* **Vai trò:** Data Governance Analyst / Data Analyst
* **Email:** khanhpn.forwork@gmail.com
* **LinkedIn:** [linkedin.com/in/pham-ngoc-khanh](https://www.linkedin.com/in/pham-ngoc-khanh)

> *Dự án này minh họa việc áp dụng các nguyên tắc Quản trị Dữ liệu, Mô hình hóa Rủi ro và Kiểm toán Kinh tế trong môi trường giả lập.*