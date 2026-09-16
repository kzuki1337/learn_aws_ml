# AWS Machine Learning Certification — Learning Resources

## 1. General Video Courses & Practice Platforms

**Official AWS**
- [AWS Skill Builder](https://skillbuilder.aws) — free digital courses + official Exam Prep learning plan for MLA-C01, paid hands-on labs, and practice exams
- [SageMaker Studio Lab](https://studiolab.sagemaker.aws) — free SageMaker notebooks for real hands-on practice

**Paid Video Courses**
- Stephane Maarek (Udemy) — top-rated AWS cert instructor
- Frank Kane (Udemy) — dedicated ML Specialty/Associate course with hands-on labs
- [freeCodeCamp (YouTube)](https://www.youtube.com/@freecodecamp) — free full-length AWS ML cert walkthroughs
- A Cloud Guru / Pluralsight — video + built-in cloud sandboxes

**Practice Exams**
- Tutorials Dojo (Jon Bonso) — exam guides + practice tests
- Whizlabs — practice exams and labs

**Hands-on Practice**
- [aws/amazon-sagemaker-examples (GitHub)](https://github.com/aws/amazon-sagemaker-examples) — official SageMaker notebooks
- [Kaggle](https://www.kaggle.com) — datasets to practice the full data-prep → train → deploy pipeline

---

## 2. ML Engineer – Associate (MLA-C01) vs ML – Specialty (MLS-C01)

| | **ML Engineer – Associate (MLA-C01)** | **ML – Specialty (MLS-C01)** |
|---|---|---|
| Target audience | ~1 year ML/AWS experience | 2+ years building/running ML workloads |
| Focus | Practical/operational — SageMaker config, pipelines, deployment, monitoring | Theoretical/algorithmic — math, metrics, model selection |
| Math depth | Lighter | Requires formula memorization, deeper neural network understanding |
| Modeling domain weight | ~26% of exam | ~36% of exam |
| Format | 65 questions, 130 min, $150 | Similar length/format |

- AWS does **not** consider the Associate a replacement for the Specialty — both coexist.
- Heavy overlap on SageMaker and the ML lifecycle; Associate leans "how do I configure and ship this," Specialty leans "do you understand the underlying ML science."
- A new **MLA-C02 (beta)** exists: 170 min, 85 questions, adds Generative AI (Bedrock/RAG), agentic AI, and foundation model content on top of existing domains.
- **Recommendation:** Start with ML Engineer – Associate unless a job specifically requires Specialty.

---

## 3. Do You Need Data Engineering Knowledge First?

Yes, at a foundational level — both exams open with a data domain. Be comfortable with:
- S3 storage classes and data formats (CSV, Parquet, JSON)
- Basic data cleaning/transformation (normalization, encoding, missing values)
- AWS Glue / Athena basics for querying and prepping data
- Feature engineering fundamentals

Spend 1–2 weeks here before diving into modeling content if this is new to you.

---

## 4. YouTube Tutorials by Topic

### Data Cleaning / Normalization / Encoding / Missing Values
- [Feature Engineering – All Techniques to Handle Missing Values (Krish Naik)](https://www.youtube.com/watch?v=dmt2R4A3W1Q) — mean/median/mode imputation, random sampling, end-of-distribution, live coding
- [Krish Naik — Grand Complete Data Science Guide (all playlists)](https://github.com/krishnaik06/The-Grand-Complete-Data-Science-Materials) — index of his Feature Engineering & EDA playlists (encoding, scaling, normalization)
- StatQuest with Josh Starmer (YouTube) — short, clear videos on feature scaling, PCA, regularization — good for building intuition

### AWS Glue / Athena
- [AWS Glue Full Course for Beginners (2026)](https://www.youtube.com/watch?v=Pigx0gReuT4) — crawlers, Data Catalog, ETL jobs, PySpark scripting
- [Query S3 Data with SQL: Amazon Athena and AWS Glue Tutorial](https://www.youtube.com/watch?v=XtHCr80wmR8) — Glue Catalog feeding Athena, querying S3 data lake with SQL

### Feature Engineering Fundamentals
- Same Krish Naik playlist above covers the full arc: cleaning → encoding → scaling → feature engineering → selection
- StatQuest for theory/intuition-focused supplementary viewing (useful for Specialty-level depth)

**Hands-on practice loop:** Upload a CSV to S3 → run a Glue crawler → query it in Athena → pull it into a SageMaker notebook and apply the cleaning/encoding techniques from the Krish Naik playlist. This one loop covers a large chunk of the "data" domain on both exams.

===================================================

# Manual notes from here

Start with Setting up Sagemaker AI - https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-quick-start.html