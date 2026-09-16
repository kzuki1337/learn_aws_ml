# AWS Certified Machine Learning Engineer – Associate (MLA-C02) — 42-Day Study Plan

**Profile assumed:** Strong AWS background, new to ML concepts.
**Pace:** 2 hrs/day × 42 days (~84 hrs), reading-first (AWS docs), Pluralsight labs for hands-on, small videos only for abstract concepts.
**Target exam:** MLA-C02 (beta) — the only valid path going forward. See status below.

---

## 0. Certification Status (confirmed as of Sept 15, 2026)

| Cert | Status |
|---|---|
| ML – Specialty (MLS-C01) | **Retired.** Last exam date was March 31, 2026. Not obtainable by new candidates. |
| ML Engineer – Associate **MLA-C01** | **Retiring.** Last day in English: **Sept 28, 2026**. Still available in JP/KR/zh-CN until MLA-C02 reaches General Availability. |
| ML Engineer – Associate **MLA-C02** | **Current target.** Beta registration open now; beta exam delivery starts **Sept 29, 2026**. 85 questions (50 scored + 15 unscored), 170 min, $75 during beta. GA expected ~Jan 14, 2027. |

MLA-C02 keeps the same 4-domain structure as MLA-C01 but significantly expands scope to include **Amazon Bedrock, foundation models, RAG, fine-tuning, agentic AI, and GenAI-specific evaluation/monitoring/security** — on top of traditional ML. This plan is built for MLA-C02.

**Official exam guide (bookmark this — it's the single source of truth):**
https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02.html

---

## 1. Exam Content Outline (official, with weightings)

| Domain | Weight |
|---|---|
| 1. Data Preparation for ML and AI | 28% |
| 2. ML Model and Foundation Model (FM) Development | 24% |
| 3. Deployment and Orchestration of ML and AI Workflows | 24% |
| 4. Operating, Monitoring, and Securing ML and AI Solutions | 24% |

### Domain 1: Data Preparation for ML and AI
- **1.1 Collect and store data** — extraction (S3, EBS, EFS, RDS, DynamoDB, OpenSearch), storage decisions, streaming ingestion (Kinesis, Flink, Kafka), data formats (Parquet, JSON, CSV, ORC), merging data (Glue, Spark), **vector database configuration** (OpenSearch, RDS+pgvector, S3), ingesting diverse data types (text/image/audio), SageMaker Feature Store
- **1.2 Transform data, feature engineering, preprocessing** — AWS Glue/DataBrew/EMR/Data Wrangler, feature engineering (scaling, binning, log transform, normalization), **embedding models**, advanced text preprocessing (tokenization, augmentation), **RAG document prep** (chunking, metadata extraction), data masking/anonymization, prepping data for **fine-tuning/continuous pre-training/distillation**
- **1.3 Validate data quality and manage bias** — data quality validation, labeling/annotation, bias mitigation, multimodal bias metrics, class imbalance, **AI training data validation** (prompt-response pairs, content safety), data cleaning (outliers, missing data, dedup)

### Domain 2: ML Model and Foundation Model (FM) Development
- **2.1 Choose modeling approaches** — selecting FMs from Bedrock, fine-tuning strategies, comparing ML/GenAI models & algorithms, custom vs managed vs pre-trained vs FM tradeoffs, **RAG architecture patterns**, performance/cost/latency tradeoffs, AWS AI services (Textract, Rekognition, Comprehend, Transcribe)
- **2.2 Train, fine-tune, customize** — SageMaker built-in algorithms, script mode, hyperparameter optimization (AMT), training time reduction (early stopping, distributed training), overfitting/underfitting/catastrophic forgetting, model ensembling, core hyperparameters, **prompt engineering & fine-tuning**, retrieval/embedding optimization
- **2.3 Analyze and evaluate performance** — reproducible experiments (MLflow on SageMaker, Bedrock evaluations), baselines & drift detection, shadow vs production variants, explainability, convergence debugging, **NLP metrics** (BLEU, ROUGE, BERTScore, semantic similarity), human-in-the-loop evaluation, LLM-as-a-judge, RAG monitoring

### Domain 3: Deployment and Orchestration of ML and AI Workflows
- **3.1 Manage deployment infrastructure** — compute/deployment targets, multi-model/multi-container strategies, real-time vs batch inference, **FM deployment options**, importing external models (Bedrock Custom Model Import), **deploying and configuring agents**, RAG system configuration (retrieval, reranking)
- **3.2 Provision and configure resources** — on-demand vs provisioned, automation, containers, VPC-configured endpoints, SageMaker SDK/CLI/Boto3, auto-scaling metrics, **Bedrock knowledge bases** (vector DB config, indexing, retrieval), agent state management, GPU scaling, agentic workflow infrastructure
- **3.3 CI/CD and orchestration** — deployment/rollback automation, CodeBuild/CodeCommit/CodeDeploy/CodePipeline/CodeConnections, training/inference job config, automated testing in pipelines, retraining mechanisms, SageMaker Model Registry/MLflow versioning, **Bedrock Prompt Management**, agent deployment pipelines, FM version automation, RAG/knowledge-base refresh pipelines

### Domain 4: Operating, Monitoring, and Securing ML and AI Solutions
- **4.1 Monitor inference and performance** — CloudWatch GenAI observability, Bedrock Model Evaluation, drift detection, anomaly detection, A/B testing, **agent performance monitoring** (coordination failures, tool failures), FM-specific monitoring
- **4.2 Optimize cost/performance** — inference instance selection, CloudWatch/AgentCore Observability/X-Ray, dashboards, capacity optimization, cost management tools, purchasing options, FM inference cost, agent resource consumption, **token/embedding/vector-DB cost optimization**
- **4.3 Secure workloads and endpoints** — CI/CD security scanning (CodeGuru, Inspector), least-privilege access, IAM policies/roles, CloudTrail/Config, security troubleshooting, VPC/subnet/security group isolation, risk mitigation, **Bedrock API key vs IAM credential selection**, **Bedrock Guardrails** and responsible AI safeguards

---

## 2. Depth Guide (calibrated to your profile: strong AWS, new to ML)

| Depth | Meaning | Applies to |
|---|---|---|
| 🟢 Skim | You likely know this already; confirm exam-specific terminology only | S3/IAM basics, VPC/security groups, CI/CD tooling (CodePipeline etc.), CloudWatch/CloudTrail/X-Ray basics, Kinesis/Glue at a service level |
| 🟡 Medium | Familiar AWS surface, but needs ML-specific application understanding | SageMaker-specific deployment/scaling, cost optimization for ML/FM workloads, auto-scaling for inference, containers for ML |
| 🔴 Deep | New conceptual ground — spend the most time here | ML algorithm selection, bias-variance/overfitting, hyperparameter tuning, evaluation metrics (classical + NLP), feature engineering, embeddings, RAG architecture, fine-tuning strategies, GenAI evaluation (LLM-as-judge, BLEU/ROUGE), agentic AI concepts, Bedrock Guardrails/responsible AI |

Use this table as you go through the plan below — don't spend equal time on every topic.

---

## 3. 42-Day Plan

### Phase 0 — ML Foundations (Days 1–4, 8 hrs) 🔴
Since you're AWS-strong but ML-new, build core ML vocabulary *before* touching SageMaker specifics — everything downstream assumes this.

| Day | Topic | Resource |
|---|---|---|
| 1 | What is ML, supervised vs unsupervised vs reinforcement, regression vs classification | [AWS ML Concepts – SageMaker Dev Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/how-it-works-mlconcepts.html) |
| 2 | Bias-variance tradeoff, overfitting/underfitting, train/validation/test splits, cross-validation | [SageMaker Dev Guide – Model Tuning](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html) + video: search "StatQuest bias variance tradeoff" (short, ~10 min) |
| 3 | Evaluation metrics: accuracy, precision, recall, F1, AUC-ROC, RMSE/MAE | [SageMaker Dev Guide – Model Metrics](https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-model-quality-metrics.html); video: search "StatQuest ROC and AUC" |
| 4 | What are foundation models / LLMs, generative vs discriminative, intro to embeddings | [What is Amazon Bedrock – User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |

---

### Phase 1 — Domain 1: Data Preparation for ML and AI (Days 5–13, 18 hrs, 28% weight)

| Day | Topic | Depth | Resource |
|---|---|---|---|
| 5 | Data sources & ingestion (S3, EFS, RDS, DynamoDB, OpenSearch), formats (Parquet/JSON/CSV/ORC) | 🟢 | [Domain 1 official skills](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02-domain1.html); [S3 data formats for analytics](https://docs.aws.amazon.com/athena/latest/ug/data-sources.html) |
| 6 | Streaming ingestion (Kinesis, Flink, Kafka) + AWS Glue merging/ETL | 🟢 | [AWS Glue Developer Guide](https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html); [Kinesis Data Streams docs](https://docs.aws.amazon.com/streams/latest/dev/introduction.html); Pluralsight lab: Glue crawler + Athena query |
| 7 | Vector databases (OpenSearch, RDS+pgvector, S3) — new concept | 🔴 | [Amazon OpenSearch Service – Vector Search](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/knn.html); [Bedrock Knowledge Bases overview](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html) |
| 8 | SageMaker Feature Store, ingesting diverse data types (text/image/audio) | 🟡 | [SageMaker Feature Store docs](https://docs.aws.amazon.com/sagemaker/latest/dg/feature-store.html) |
| 9 | Feature engineering (scaling, standardization, binning, log transform, normalization) | 🔴 | [SageMaker Data Wrangler – Feature transforms](https://docs.aws.amazon.com/sagemaker/latest/dg/data-wrangler-transform.html); Pluralsight lab: Data Wrangler feature transforms |
| 10 | Embedding models (text/image → numerical), tokenization, text preprocessing | 🔴 | [Bedrock – Titan Embeddings](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html) |
| 11 | RAG document prep: chunking strategies, metadata extraction | 🔴 | [Bedrock Knowledge Bases – Chunking](https://docs.aws.amazon.com/bedrock/latest/userguide/kb-chunking.html) |
| 12 | Data masking/anonymization; prepping data for fine-tuning/continuous pre-training/distillation | 🔴 | [Bedrock – Custom Model Fine-tuning](https://docs.aws.amazon.com/bedrock/latest/userguide/model-customization.html); [SageMaker – Data anonymization with DataBrew](https://docs.aws.amazon.com/databrew/latest/dg/what-is.html) |
| 13 | Data quality, bias mitigation, class imbalance, cleaning (outliers/missing/dedup), AI training data validation | 🔴 | [AWS Glue Data Quality](https://docs.aws.amazon.com/glue/latest/dg/glue-data-quality.html); [SageMaker Clarify – Bias detection](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-detect-data-bias.html); Pluralsight lab: SageMaker Clarify bias report |

**Whitepaper checkpoint:** [Machine Learning Lens – AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html) — read the "Data" pillar sections (skim rest for now, revisit in Phase 5).

---

### Phase 2 — Domain 2: ML Model and FM Development (Days 14–24, 22 hrs, 24% weight — heaviest new content)

| Day | Topic | Depth | Resource |
|---|---|---|---|
| 14 | Selecting FMs from Bedrock; comparing ML algorithms/GenAI models by use case | 🔴 | [Bedrock – Supported foundation models](https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html) |
| 15 | SageMaker built-in algorithms overview (XGBoost, Linear Learner, k-NN, etc.) | 🔴 | [SageMaker – Built-in algorithms](https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html) |
| 16 | Custom vs managed vs pre-trained vs FM tradeoffs; cost/latency/performance tradeoffs | 🔴 | [SageMaker JumpStart docs](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html) |
| 17 | RAG architecture patterns (retrieval + generation design choices) | 🔴 | [Bedrock – RAG with Knowledge Bases](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base-retrieve-generate.html) |
| 18 | AWS AI services for specific problems (Textract, Rekognition, Comprehend, Transcribe) | 🟢 | [Amazon Comprehend docs](https://docs.aws.amazon.com/comprehend/latest/dg/what-is.html); [Amazon Textract docs](https://docs.aws.amazon.com/textract/latest/dg/what-is.html) |
| 19 | SageMaker script mode + frameworks; hyperparameter optimization (Automatic Model Tuning) | 🔴 | [SageMaker – Automatic Model Tuning](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning.html); Pluralsight lab: run an AMT tuning job |
| 20 | Training time reduction (early stopping, distributed training); overfitting/underfitting/catastrophic forgetting | 🔴 | [SageMaker – Distributed training](https://docs.aws.amazon.com/sagemaker/latest/dg/distributed-training.html) |
| 21 | Core hyperparameters (epoch, batch size, steps); model ensembling | 🔴 | [SageMaker – Hyperparameter tuning best practices](https://docs.aws.amazon.com/sagemaker/latest/dg/automatic-model-tuning-best-practices.html) |
| 22 | Prompt engineering & fine-tuning customization techniques; retrieval/embedding optimization | 🔴 | [Bedrock – Prompt engineering guidelines](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-engineering-guidelines.html) |
| 23 | Reproducible experiments (MLflow on SageMaker, Bedrock evaluations); baselines & drift detection; shadow vs production variants | 🔴 | [SageMaker – MLflow](https://docs.aws.amazon.com/sagemaker/latest/dg/mlflow.html); [SageMaker – Shadow tests](https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor-shadow-tests.html) |
| 24 | Explainability, convergence debugging, NLP metrics (BLEU/ROUGE/BERTScore/semantic similarity), human-in-the-loop, LLM-as-a-judge, RAG monitoring | 🔴 | [SageMaker Clarify – Explainability](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-model-explainability.html); [Bedrock – Model evaluation](https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation.html); video: search "StatQuest BLEU score" (short, if abstract) |

**Whitepaper checkpoint:** [Generative AI Lens – AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/generative-ai-lens/generative-ai-lens.html) — read "Model selection" and "Customization" sections.

---

### Phase 3 — Domain 3: Deployment and Orchestration (Days 25–31, 14 hrs, 24% weight)

| Day | Topic | Depth | Resource |
|---|---|---|---|
| 25 | Compute/deployment targets, multi-model/multi-container strategies, real-time vs batch inference | 🟡 | [SageMaker – Deploy models](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html); [SageMaker – Multi-model endpoints](https://docs.aws.amazon.com/sagemaker/latest/dg/multi-model-endpoints.html) |
| 26 | FM deployment options; importing external models (Bedrock Custom Model Import) | 🔴 | [Bedrock – Custom Model Import](https://docs.aws.amazon.com/bedrock/latest/userguide/model-customization-import-model.html) |
| 27 | Deploying and configuring agents; agent communication protocols | 🔴 | [Bedrock AgentCore – Overview](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html) |
| 28 | RAG system configuration (retrieval strategies, reranking) | 🔴 | [Bedrock Knowledge Bases – Reranking](https://docs.aws.amazon.com/bedrock/latest/userguide/kb-reranking.html) |
| 29 | Provisioning: on-demand vs provisioned, containers for ML, VPC-configured endpoints, SDK/CLI/Boto3 deployment | 🟡 | [SageMaker – VPC configuration](https://docs.aws.amazon.com/sagemaker/latest/dg/host-vpc.html); Pluralsight lab: deploy a SageMaker endpoint via Boto3 |
| 30 | Auto-scaling metrics; Bedrock knowledge bases (vector DB config, indexing); agent state management; GPU scaling | 🔴 | [SageMaker – Auto Scaling](https://docs.aws.amazon.com/sagemaker/latest/dg/endpoint-auto-scaling.html) |
| 31 | CI/CD: CodeBuild/CodeCommit/CodeDeploy/CodePipeline; automated testing, retraining, Model Registry/MLflow versioning, Bedrock Prompt Management, agent/FM pipeline automation | 🟢🔴 (tooling 🟢, ML-specific parts 🔴) | [SageMaker Pipelines docs](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html); [SageMaker Model Registry](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry.html); Pluralsight lab: build a SageMaker Pipeline with CI/CD |

---

### Phase 4 — Domain 4: Operating, Monitoring, Securing (Days 32–37, 12 hrs, 24% weight)

| Day | Topic | Depth | Resource |
|---|---|---|---|
| 32 | CloudWatch GenAI observability, Bedrock Model Evaluation, drift detection, anomaly detection | 🟡 | [SageMaker Model Monitor](https://docs.aws.amazon.com/sagemaker/latest/dg/model-monitor.html) |
| 33 | A/B testing; agent performance monitoring (coordination failures, tool failures) | 🔴 | [Bedrock AgentCore Observability](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/observability.html) |
| 34 | Inference instance selection; CloudWatch/X-Ray/AgentCore Observability; dashboards; capacity optimization | 🟢 | [SageMaker – Instance types for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/instance-types-inference.html) |
| 35 | Cost management, purchasing options, FM inference cost, token/embedding/vector-DB cost optimization | 🔴 | [Bedrock – Pricing and cost management](https://docs.aws.amazon.com/bedrock/latest/userguide/cost-management.html) |
| 36 | CI/CD security scanning (CodeGuru, Inspector); least-privilege IAM; CloudTrail/Config | 🟢 | [AWS Inspector docs](https://docs.aws.amazon.com/inspector/latest/user/what-is-inspector.html) |
| 37 | VPC/subnet isolation; Bedrock API keys vs IAM credentials; **Bedrock Guardrails** and responsible AI | 🔴 | [Bedrock Guardrails docs](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html) |

**Whitepaper checkpoint:** re-read [Machine Learning Lens – Security & Operational Excellence pillars](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/well-architected-framework-pillars.html); skim the new **Responsible AI Lens** (search "AWS Responsible AI Lens Well-Architected" — announced re:Invent 2025).

---

### Phase 5 — Consolidation & Whitepapers (Days 38–39, 4 hrs)

- Re-skim all four official exam guide domain pages end-to-end in one sitting each day, ticking off skills you're unsure of.
- Read (or re-skim) fully:
  1. [Machine Learning Lens – AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html)
  2. [Generative AI Lens – AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/generative-ai-lens/generative-ai-lens.html)
  3. [Comparison of MLA-C01 and MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-comparison.html) — useful gap-check since most study material online still targets MLA-C01
  4. [In-scope AWS services and features](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-in-scope-services.html) and [Out-of-scope services](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-out-of-scope-services.html) — sanity-check you haven't over- or under-studied

---

### Phase 6 — Practice Exams & Weak-Spot Review (Days 40–42, 6 hrs+)

- Day 40: Full-length practice exam #1 (85 Q, 170 min simulated) → review every wrong answer against the exam guide skill it maps to
- Day 41: Targeted re-study of weak domains identified in #1 (use the depth table in §2 to prioritize 🔴 gaps) → practice exam #2
- Day 42: Final review pass — re-read only the exam-guide bullet points you've marked uncertain across the whole plan; light review, no new material

**Practice exam sources:**
- Tutorials Dojo (Jon Bonso) — practice exams (check for MLA-C02-specific set; if only MLA-C01 sets exist when you get here, treat GenAI/Bedrock/agent questions as gaps to fill separately)
- Official AWS Practice Question Set (linked from the exam guide page)
- Your Pluralsight subscription's hands-on labs, used as spaced-repetition checkpoints after each phase rather than crammed at the end

---

## 4. Quick Reference — All Official AWS Docs Used Above

- [MLA-C02 Exam Guide (full)](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02.html)
- [SageMaker Developer Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html)
- [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html)
- [Bedrock AgentCore Developer Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [AWS Glue Developer Guide](https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html)
- [Machine Learning Lens (Well-Architected)](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html)
- [Generative AI Lens (Well-Architected)](https://docs.aws.amazon.com/wellarchitected/latest/generative-ai-lens/generative-ai-lens.html)

## 5. Small Videos Referenced (use only where a concept feels too abstract from text alone)

- StatQuest with Josh Starmer (YouTube) — search per topic: "bias variance tradeoff", "ROC and AUC", "BLEU score" — all short (5–15 min), intuition-focused, not AWS-specific

---

## Notes
- This plan assumes AWS docs as primary source per your preference; Pluralsight labs are placed right after the matching concept so you apply it immediately rather than batching labs at the end.
- MLA-C02 is in **beta** — expect some documentation/exam-guide pages to be updated as AWS refines the exam through late 2026. Re-check the exam guide URL above roughly weekly during your prep window.
- If at Day 40 you find Tutorials Dojo / third-party practice sets are still MLA-C01-only, lean more heavily on the **official AWS Practice Question Set** and the exam guide itself for GenAI/Bedrock/agent-specific questions, since third-party content typically lags a new exam by a few months.