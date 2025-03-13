---
layout: project
type: project
image: img/CovidData.jpg
title: "Extraction and Analysis of COVID-19 Patient Records"
date: 2025-03-12  # Adjust as necessary
published: true
labels:
- Healthcare
- Data Engineering
- Apache Spark
- LLM
- FAISS
- Pydantic
- Parquet
- Data Analysis
summary: "A comprehensive, end-to-end pipeline that leverages LLM-driven text parsing, FAISS-based medication matching, Pydantic validation, and Apache Spark analytics to transform unstructured COVID-19 patient records into actionable insights."
---

# Processing, Structuring, and Analyzing COVID-19 Medical Records

## 1. Introduction

The overarching aim of this project is to convert large volumes of **unstructured or semi-structured medical records** into **structured, queryable datasets**, and to perform advanced analytical operations that yield actionable insights into **COVID-19 patient outcomes, comorbidities, and treatment patterns**.

This process involves:

1. **Extracting** crucial clinical details from free-text encounter notes using **Large Language Models (LLMs)**.
2. **Standardizing** clinical terminologies (e.g., ICD-10 codes, RxNorm) to ensure consistent, interoperable records.
3. **Storing** the output in robust formats (e.g., **Parquet**) for efficient reading and manipulation in **Apache Spark**.
4. **Enabling** advanced analytics such as **demographic breakdowns**, **medication frequency analysis**, **co-morbidity insights**, and **machine learning classification**.

Key technologies include **PySpark** for distributed data processing, **FAISS** (Facebook AI Similarity Search) for medication mapping, and **visualization** libraries for rendering clear, interpretable results.

---

## 2. Data Ingestion and Unstructured Note Processing

### 2.1 Input Sources

- **Multiple .txt Files**: Each file contains semi-structured encounter notes (SOAP format) and free-text observations on demographics, vitals, lab results, and treatments.
- **Batch Ingestion**: For large deployments, an automated pipeline can iterate through directories, reading thousands of text files in parallel.

### 2.2 LLM-Driven Data Extraction

Leveraging LLMs (e.g., GPT-based APIs) via prompt engineering:

- **Entity Recognition**: Identifies patient name, DOB, address, insurance, symptoms, conditions, and lab results.
- **Structured JSON Output**: The pipeline instructs the model to output hierarchical JSON covering demographics, SOAP notes, medical history, etc.
- **Fallback Defaults**: Missing or ambiguous fields are marked with placeholders like `"unknown"` or `0` to maintain a consistent schema.

### 2.3 Validation via Pydantic Models

- Once the LLM outputs JSON, **Pydantic** schemas enforce strict typing (e.g., `float` for BMI, `List[str]` for diagnoses).
- Invalid or incomplete data triggers errors, ensuring contaminated records do not proceed further.

---

## 3. Data Structuring and Schema Design

### 3.1 Hierarchical Schema

Data is organized into nested fields:
1. **Encounter Information** (date, duration, provider, facility).
2. **Demographics** (name, DOB, gender, address, insurance, MRN).
3. **Conditions** (ICD-10-coded problems, co-morbid diagnoses).
4. **Medications** (RxNorm-mapped, usage frequency).
5. **Vitals** (temperature, heart rate, BP, oxygen saturation).
6. **Laboratory Results** (COVID-19 tests, influenza panels).
7. **Plan** (treatments, follow-ups, patient education).

### 3.2 Transformation into Parquet

- The validated JSON is flattened into tabular columns using a schema definition.
- Data is written to **Apache Parquet**:
    - **Columnar storage** for faster reads and queries in Spark.
    - **Compression** advantages reducing I/O overhead.

---

## 4. Semantic Enrichment Using FAISS

One central challenge is **free-text medication descriptions**. To standardize these:

1. **Embedding Generation**: A specialized model (e.g., OpenAI Embeddings) converts each medication name into a vector.
2. **FAISS Index**: Builds a similarity index of known medication names or codes (e.g., RxNorm, brand names, generics).
3. **Vector Search**: Maps each free-text mention to its nearest standard medication entry, even handling spelling variations or brand/generic differences.

This ensures consistency when counting medication frequencies or analyzing prescription patterns.

---

## 5. PySpark Workflow and Analytical Processes

### 5.1 Large-Scale Data Handling

- **Spark DataFrames**: Efficiently processes the flattened Parquet data.
- **SQL-like Transformations**: Complex filtering, grouping, and aggregation logic is performed without enumerating raw code, harnessing Spark’s distributed engine.
- **Schema Inference**: Spark respects the nested structure defined earlier for robust read operations.

### 5.2 Demographic and Comorbidity Analysis

- **COVID-19 Subset Extraction**: Filters lab results or conditions to focus on positive COVID-19 patients.
- **Age Binning**: Groups patients into brackets such as `[0-5], [6-10], [11-17], [18-30], [31-50], [51-70], [71+]` for demographic distribution visualizations.
- **Comorbidity Pairs**: Self-join or cross-tab on patient conditions to rank comorbid pairs (e.g., Hypertension & Diabetes), employing lexicographical ordering to avoid duplications.

### 5.3 Medication Usage Patterns

- **Medication Frequency**: Ranks prescriptions by usage count among COVID-19 patients.
- **Cross-Matching**: Cross-tabulates top diagnoses vs. top medications, revealing which treatments are common for each condition.

### 5.4 Vital Signs and Disease Severity

- **Flattened Vitals**: Temperature, respiratory rate, heart rate, O2 saturation, and blood pressure are extracted into columns.
- **Correlation Analysis**: Compares vital sign anomalies with severity markers (e.g., ICU admission).
- **Time-Series or Seasonal Trends**: If date/time data is present, analyses can show daily or monthly case evolutions.

---

## 6. Data Visualization and Advanced Insights

### 6.1 Visualization Approaches

- **Bar Charts**: Show top comorbidities, medication frequencies, or age-group distributions.
- **Heatmaps**: Display correlations between multiple numeric features (e.g., age, O2 saturation, heart rate) or relationships between conditions and prescribed medications.
- **Line/Area Charts**: Illustrate cumulative case counts or time series of new positives.

### 6.2 Complex Analyses

- **ICU vs. Non-ICU Patient Comparisons**: Summarize differences in symptom clusters, vitals, and comorbidities.
- **Obesity and COVID-19 Severity**: Test the correlation between BMI and adverse outcomes or ICU admissions.
- **Hypothesis Testing**: T-tests or chi-square tests for differences in medication usage across demographic groups.

---

## 7. Key Technical Challenges and Solutions

1. **Nested JSON**: Addressed via Pydantic for structure, then PySpark’s flattening functions.
2. **Multiple `explode()` Constraints**: Solved by carefully staging transformations or using sub-DataFrames.
3. **FAISS Optimization**: Tuning vector dimensions, indexing parameters, and similarity thresholds for medication matching.
4. **Missing Data**: Dealt with placeholders (`unknown`, `[]`, or `0`), plus filtering out incomplete rows for certain statistical analyses.
5. **Performance**:
    - Parquet format for efficient data scanning and compression.
    - Spark caching to reduce repeated transformations.
    - Partition pruning to limit memory usage.

---

## 8. Conclusion

By merging unstructured textual encounter notes with robust validation, standard taxonomy mapping, and advanced Spark-based analytics, this project delivers a **scalable, end-to-end system** for healthcare data intelligence. The **LLM pipeline** transforms semi-structured notes into high-fidelity JSON records, **FAISS** enforces consistent medication naming, and **PySpark** fosters seamless large-scale queries. Researchers and clinicians can then **visualize** data on demographics, comorbidities, and treatments, supporting critical decision-making in COVID-19 patient care.

Looking forward, the pipeline can expand to real-time ingestion for **ongoing epidemiological surveillance**, incorporate **additional medical taxonomies** like UMLS or SNOMED CT, and implement **predictive modeling** to forecast patient outcomes. Ultimately, it serves as a blueprint for transforming messy clinical data into actionable insights that drive informed policy and evidence-based medicine.
