
# Healthcare Operational Efficiency & Patient Readmission Analytics

## 1️⃣ Project Overview & Objectives
Raw medical audit databases are highly prone to text formatting issues, casing dropouts, and structural missing values that completely crash downstream corporate reporting. This project establishes a production-grade data analytics pipeline designed to audit **4,000+ corporate clinical records** from a private Indian healthcare network.

### Key Objectives:
* **Data Engineering Optimization:** Standardize a highly fragmented dataset across 12 core clinical parameters (`Patient_ID`, `Age`, `Total_Charges` in INR, etc.) and handle structural null elements without losing historical transaction value.
* **Identify Operational Risk Bottlenecks:** Calculate rolling 30-day patient readmission spikes to highlight underperforming clinical departments.
* **Isolate Commercial Engines:** Aggregate gross hospital billings to provide data-backed department capacity recommendations to executive leadership.

---

## 2️⃣ Data Pipeline & Analytics Methodology

### Phase A: Python Data Engineering (Pandas & NumPy)
* **Missing Value Imputation:** Isolated 80 structural null records in the `Medical_Specialty` column and programmatically imputed them with a new standard `'Unspecified'` classification to preserve patient financial history.
* **Text Normalization:** Eradicated leading/trailing spaces via `.str.strip()` and enforced uniform title-casing across all string dimensions to remove duplicate categorical values (e.g., merging `cardiology` and `Cardiology`).
* **Demographic Binning:** Transformed raw numerical ages into clean clinical lifespan segments (`0-1 Infant`, `2-12 Pediatric`, `60-79 Senior`, etc.) using explicit boundary interval cuts.

### Phase B: Relational Database Aggregations (In-Memory SQLite)
* **SQL Schema Engine Deployment:** The optimized memory schema was migrated directly into an active relational SQL database engine inside the notebook environment.
* **Advanced Multi-Variable Matrix Aggregations:** Extracted production-grade business metrics by running a relational database query leveraging a **Common Table Expression (CTE)** and conditional aggregates (`CASE WHEN`) to process department performance rates efficiently without system compute overheads.

---

## 3️⃣ Key Findings & Strategic Business Insights
The relational SQL engine executed flawlessly (full query implementation and visual data outputs are available directly within the attached project notebook), yielding three critical insights for hospital operational strategies:

* **High-Risk Bottleneck Isolated (Cardiology):** The **Cardiology department** exhibits the highest patient operational risk profile with a **13.32% readmission rate** (87 readmissions out of 653 patients). This highlights a strong commercial need to optimize discharge planning and post-operation follow-up tracks.
* **Financial Powerhouse Identified (General Medicine):** **General Medicine** stands out as the primary commercial engine for the hospital network, managing the largest operational footprint (**2,062 total patients**) and generating a massive **₹110.03 Crore** in gross revenue.
* **Clinical Stability Leader (Pediatrics):** The **Pediatrics** department demonstrates the highest operational stability and patient recovery index, maintaining a minimal readmission rate of just **7.09%**.
  
