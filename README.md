# Data-Driven Optimization of Healthcare Operations & Financial Performance

## 📌 Project Overview
This project identifies systemic revenue leakage, operational bottlenecks, and scheduling inefficiencies across a multi-department clinic network. Utilizing a data pipeline spanning Python, Excel, and Tableau, the project delivers an audit of patient scheduling patterns, department level financial loss, evaluates emergency compliance metrics, and structures the findings into an executive dashboard.

---

## 🛠️ Data Pipeline & Technical Methodology

### 1. Data Exploration, Feature Engineering, & Statistical Testing (Python)
The pipeline began in Python utilizing the `pandas`, `numpy`, and `scipy.stats` libraries to perform data wrangling, derive operational metrics, and mathematically validate core operational hypotheses.

* **Data Exploration & Text Normalization:** Processed the raw dataset, verified integrity, and applied structural string cleaning across categorical columns. This involved stripping hidden trailing whitespaces and resolving case inconsistencies to ensure exact programmatic grouping downstream.
* **Feature Engineering:** Constructed calculated indicators to deepen the analytical framework:
  * **Age Segmentation:** Binned patients into defined age brackets to capture behavioral compliance variations.
  * **Strategic Compliance Flags:** Formulated explicit indicators, such as targeting critical triage failure metrics, to identify service-level agreement breaches.
* **Statistical Hypothesis Testing:** Executed validation tests to prove the operational variances observed across groups were statistically meaningful before building visual components:
  * **Two-Sample T-Test:** Analyzed wait times between emergency and standard care classifications. The resulting $p$-value was **0.1444**, leading to a verdict of *not statistically significant*, proving that the hospital's triage flow was failing to prioritize urgent cases over routine visits.
  * **Chi-Square Test of Independence:** Evaluated attendance outcomes across chronic disease groups. With a calculated $p$-value of **0.1780**, the relationship was *not statistically significant*, showing that appointment no-shows were uniformly distributed rather than isolating to specific high-risk patient health profiles.

### 2. Analytical Scope & Financial Modeling (Excel)
Following Python processing, the dataset was moved to Excel to establish risk guardrails and audit revenue leakage.

* **Administrative Scope:** Enforced a structural baseline constraint that the data represents a **single hospital system**. Restricting the scope to a unified entity layout locked down the operational logic and prevented invalid cross-facility comparison metrics.
* **Revenue Leakage Formulation:** The raw data lacked visibility into true financial damage from missed slots. Custom logic columns were engineered to model the realized loss by mapping department specific baseline appointment fees against historical no-show and cancellation entries, establishing the true financial exposure per clinic.

### 3. Dashboard Architecture & Visual Design (Tableau)
The finalized metrics were compiled and moved into Tableau to produce an executive dashboard optimized for scannability and fast administrative triage.

* **Grid Structure & Hierarchy:** Created a structured layout to display the financial loss in the upper left quadrant as this is crucial to be viewed first, followed by wait-time compliance thresholds in the bottom left quadrant, and operation capacity vs. no-show on the right.
* **Color Palette:** Set the visual palette to maintain high informational density without causing cognitive fatigue, and to maintain colorblind accessibility. The palette consists of blue to represent standard metrics, with an orange accent color reserved for compliance violations and high no-show risk profiles.
* **Polishing Details:** Cleaned up the layout by hiding redundant `Department` row labels, adding filter options, cropping the scatter plot axis boundaries to focus on the tightest data clusters, and established an automatic canvas sizing to support responsive scaling across desktop and mobile displays.

---

## 💡 Analytical Insights & Proposed Interventions

### 1. Revenue Leakage Analysis
> **The Findings:** Cardiology (\$1,665,111 in losses) and Gynecology (\$1,514,960 in losses) represent the highest financial exposure across the organization. Conversely, Cardiology demonstrated strong operational efficiency, maintaining the lowest overall failure rate at 15.1% while processing the highest volume of total appointments (1,075).
> 
> **Proposed Intervention:** Implement an automated communication loop consisting of multi-tiered SMS text messaging reminders (T-72hr, T-24hr, T-2hr) specifically for these high-exposure sectors.

### 2. Behavioral Outlier Profiling
> **The Findings:** Ophthalmology emerged as a critical operational outlier on the scatter plot. While managing the second highest appointment volume (1,044), it suffered from the highest no-show rate in the entire system at 18.3%.
> 
> **Proposed Intervention:** This distinct variance points to a specific departmental friction unique to eye care, such as patient compliance barriers surrounding post-procedure vision impairment or lack of transport home. Administration should deploy a targeted survey to this patient group or establish a non-emergency medical transportation partnership to help mitigate this obstacle.

### 3. Service Bottlenecks & Triage Strain
> **The Findings:** Pulmonology is experiencing severe operational stress, leading the hospital system with 496 total wait-time violations (422 standard care delays and 74 emergency care delays). General Medicine and Neurology present acute operational risks, recording 78 and 71 emergency care violations.
> 
> **Proposed Intervention:** Delays in emergency care wait times represent a critical compliance and clinical safety risk. Administration must adjust provider shift schedules to establish a dedicated emergency triage team during peak volume windows. This ensures emergency arrivals are absorbed immediately without bottlenecking standard care tracks.
