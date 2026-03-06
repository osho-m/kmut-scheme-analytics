#  Kalaignar Magalir Urimai Thittam (KMUT) — Tamil Nadu Women's Welfare Scheme Dataset

## About This Dataset

This dataset contains **50,000 synthetic records** simulating applicant data for the **Kalaignar Magalir Urimai Thittam (KMUT)** — a Tamil Nadu Government scheme that provides **Rs. 1,000/month** to eligible female heads of households.

The data is synthetically generated to realistically reflect Tamil Nadu's demographic, socioeconomic, and administrative characteristics, based on publicly available scheme documentation.

---

## Files in This Dataset

| File | Rows | Columns | Description |
|------|------|---------|-------------|
| `kmut_dataset.csv` | 50,000 | 44 | Raw applicant dataset |
| `kmut_ml_dataset.csv` | 50,000 | 53 | ML-ready dataset with engineered features |
| `kmut_coverage_gap.csv` | 35 | 7 | District-level coverage analysis |
| `kmut_model_results.csv` | 7 | 5 | ML model comparison results |
| `kmut_rag_system.json` | - | - | GenAI RAG knowledge base & test queries |

---

## Dataset Features

### Demographics
- `applicant_id` — Unique ID (KMUT000001–KMUT050000)
- `district` — One of Tamil Nadu's 35 districts
- `area_type` — Urban / Rural / Semi-Urban / Semi-Rural
- `age` — Applicant age (21–74 years)
- `marital_status` — Married / Widowed / Divorced / Single / Transgender
- `social_category` — SC / ST / OBC / General / MBC
- `education_level` — Illiterate to Post-Graduate
- `occupation` — 16 occupation categories
- `family_size` — 1–12 members

### Socioeconomic Indicators
- `annual_income_inr` — Annual household income in INR
- `wet_land_acres` — Irrigated agricultural land
- `dry_land_acres` — Rainfed agricultural land
- `electricity_units_year` — Annual household electricity consumption
- `is_bpl` — Below Poverty Line card holder
- `has_bank_account` — Bank account availability
- `has_smartphone` — Smartphone ownership
- `digital_literacy` — None / Basic / Intermediate / Advanced
- `fps_distance_km` — Distance to Fair Price Shop

### Eligibility Flags (based on scheme rules)
- `income_eligible` — Annual income < Rs. 2.5L
- `land_eligible` — Wet < 5 acres AND Dry < 10 acres
- `electricity_eligible` — Units/year < 3,600
- `has_four_wheeler` — Owns car/jeep/tractor
- `has_govt_employee_family` — Govt/PSU employee in family
- `has_income_tax_filer` — Files income tax
- `has_gst_business` — GST-registered business with turnover >50L
- `already_receiving_pension` — Receiving social security pension
- `final_eligible` — **Final eligibility** (all criteria combined)

### Administrative Outcomes
- `applied_for_scheme` — Whether applicant submitted an application
- `application_status` — Approved / Pending / Rejected / Under Review / Not Applied
- `application_date` — Date of application submission
- `approval_date` — Date of approval (if applicable)
- `processing_days` — Days from application to approval
- `rejection_reason` — Reason for rejection (if rejected)
- `monthly_benefit_inr` — Monthly benefit (Rs. 1000 if approved, else 0)
- `months_benefit_received` — Total months benefit received
- `total_benefit_received_inr` — Cumulative benefit received
- `satisfaction_score` — 1–5 satisfaction rating (approved beneficiaries only)
- `grievance_filed` — Whether a grievance was filed
- `grievance_resolved` — Whether the grievance was resolved

### Engineered Features (in `kmut_ml_dataset.csv`)
- `vulnerability_index` — Composite vulnerability score (0–11)
- `digital_inclusion_score` — Digital access composite (0–7)
- `income_threshold_ratio` — Income / 2.5L threshold
- `land_pressure` — Family size / (total land + 1)
- `electricity_per_capita` — Electricity / family size
- `ineligibility_count` — Number of disqualifying flags (0–5)
- `cluster` — K-Means cluster (0–4)
- `cluster_name` — Descriptive cluster label
- `is_anomaly` — Isolation Forest anomaly flag

---

## Key Statistics

| Metric | Value |
|--------|-------|
| Total Records | 50,000 |
| Eligible Households | 39,450 (78.9%) |
| Total Applied | 31,220 (62.4%) |
| Total Approved | 20,975 (41.9%) |
| Total Benefit Disbursed | Rs. 26.12 Crores |
| Avg Processing Time | 37.6 days |
| Coverage Gap | 9,819 eligible but unapplied |
| Anomalies Detected | 2,500 (5%) |
| Districts Covered | 35 |

---

## Suggested Tasks

###  Classification
- Predict household **eligibility** for the scheme
- Predict **application approval** given socioeconomic features
- Classify **risk of grievance** filing

###  Regression
- Predict **number of months** benefit will be received
- Predict **processing time** for applications

###  Clustering
- Segment **beneficiary profiles** for targeted outreach
- Identify **underserved geographic zones**

###  Anomaly Detection
- Detect **potential fraud** or data entry errors
- Flag **outlier beneficiary profiles** for audit

###  NLP / GenAI
- Build a **policy Q&A chatbot** using RAG
- Classify **rejection reasons** from free text
- Summarize **district-level performance**

---

## Methodology

The dataset was generated using Python with NumPy and Pandas, following realistic statistical distributions:
- Income: Log-normal (μ=10.5, σ=0.8), clipped to Rs. 15K–5L
- Land: Exponential distribution with 65% having no land
- Electricity: Normal distribution (μ=2200, σ=900 units)
- Application outcomes: Conditional probabilities based on eligibility flags

Demographic distributions are calibrated to Tamil Nadu Census 2011 approximate ratios for district populations, social categories, and urban/rural splits.

---

## Scheme Background

The **Kalaignar Magalir Urimai Thittam** was announced by Tamil Nadu Chief Minister as part of the government's commitment to gender equality. Key features:

- **Benefit**: Rs. 1,000/month via Direct Benefit Transfer (DBT)
- **Beneficiary**: Female head of household
- **Application**: At Fair Price Shop (FPS) registration camps
- **Implementing Department**: Special Programme Implementation Department
- **Coverage Unit**: Ration card (one per family)

---

## License

This is a **synthetic dataset** created for educational and research purposes. It does not contain any real personal information. Created under the assumption of fair use for academic and data science research.

---

## Citation

If you use this dataset, please cite:
```
KMUT Scheme Synthetic Dataset (2026). Kalaignar Magalir Urimai Thittam Analytics.
Tamil Nadu Government Welfare Scheme Data Science Project.
Generated using Python (NumPy, Pandas) based on official scheme documentation.
```
