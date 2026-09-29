# AWS Certified AI Practitioner (AIF-C01) — The Complete 30-Page Master Review
> **Updated for AWS AIF-C01 Guide v1.1 (September 2026 Revisions)**  
> 20-Page Keyword Reviewer · 68 Exam Traps · 40 Guided Ordering Flowcharts

---

## 📑 Table of Contents
1. [Domain 1: AI and Machine Learning Fundamentals (20%)](#domain-1-ai-and-ml-fundamentals)
2. [Domain 2: Generative AI and Model Mechanics (24%)](#domain-2-generative-ai-and-model-mechanics)
3. [Domain 3: Foundation-Model Applications & RAG (28%)](#domain-3-foundation-model-applications)
4. [Domain 4: Guidelines for Responsible AI (14%)](#domain-4-guidelines-for-responsible-ai)
5. [Domain 5: Security, Compliance, and Governance (14%)](#domain-5-security-compliance-and-governance)
6. [AWS Service Atlas: Complete In-Scope Inventory](#aws-service-atlas)
7. [68 Exam Traps: Last-Minute Decision Checks](#68-exam-traps)
8. [Flowchart Lab: 40 Guided Ordering Sequences](#flowchart-lab-40-guided-ordering-sequences)

---

## Domain 1: AI and ML Fundamentals (20%)

### Core Concepts & Hierarchy
* **Artificial Intelligence (AI):** Computer systems performing intelligence-like tasks. *(e.g., A bank uses AI to flag unusual account activity).*
* **Machine Learning (ML):** Systems learning patterns from data rather than hand-coded rules. *(e.g., A store trains a model on historical customer purchases).*
* **Deep Learning (DL):** ML utilizing multilayer artificial neural networks. *(e.g., A hospital analyzes medical MRI/CT scans).*
* **Neural Network:** Connected layers of weighted artificial neurons learning nonlinear boundaries.
* **Input Layer:** Receives raw feature values *(age, income, repayment history)*.
* **Hidden Layer:** Learns increasingly abstract representations *(edges -> shapes -> objects)*.
* **Output Layer:** Produces predictions, class probabilities, or generated tokens.
* **Weights and Biases:** Trainable parameters adjusted during optimization.
* **Activation Function:** Introduces nonlinearity *(e.g., ReLU, Sigmoid)* enabling curved classification boundaries.

### Learning Paradigms & Data
* **Supervised Learning:** Trains on inputs with known target labels *(e.g., Fraud detection, price regression)*.
* **Unsupervised Learning:** Discovers hidden structures or clusters without labels *(e.g., Customer segmentation)*.
* **Reinforcement Learning (RL):** Agent learns sequential actions through reward/penalty feedback *(e.g., Warehouse routing robot, algorithmic trading)*.
* **Self-Supervised Learning:** Derives training signals from the input itself *(e.g., Masked language modeling)*.
* **Transfer Learning:** Adapts pre-trained representations to a related downstream task.
* **Data Leakage:** Future or unauthorized target information improperly enters training data, causing unrealistic validation metrics.

### Evaluation Metrics & Failure Modes
* **Precision ($\frac{TP}{TP + FP}$):** Prioritizes minimizing false alarms *(e.g., High cost of unnecessary manual investigation)*.
* **Recall / Sensitivity ($\frac{TP}{TP + FN}$):** Prioritizes catching every positive case *(e.g., Cancer screening, credit card fraud)*.
* **F1 Score:** Harmonic mean of precision and recall; balances imbalanced workloads.
* **High Bias (Underfitting):** Model is too simplistic; poor performance on both training and test data.
* **High Variance (Overfitting):** Model memorizes training noise; high training accuracy but poor unseen test generalization.
* **Data Drift:** Feature input distributions change over time ($P(X)$ shifts) while input-to-target mapping remains unchanged.
* **Concept Drift:** The statistical relationship between inputs and targets changes ($P(Y|X)$ shifts).

---

## Domain 2: Generative AI and Model Mechanics (24%)

### Foundations & Token Mechanics
* **Foundation Model (FM):** Broadly pre-trained, reusable base model adaptable to diverse downstream tasks.
* **Transformer Architecture:** Self-attention mechanism that weighs relationships between token positions across long sequences.
* **Tokenization & Context Window:** Text split into numerical tokens; context window defines maximum active working memory.
* **Embeddings & Vector Spaces:** High-dimensional semantic numerical representations where distance reflects conceptual similarity.
* **Temperature:** Scaling parameter for sampling randomness (lower = deterministic/repeatable; higher = creative/diverse).
* **Top-P (Nucleus Sampling):** Samples from the smallest pool of tokens whose cumulative probability exceeds threshold $P$.
* **Top-K Sampling:** Restricts token selection to a fixed count $K$ of highest-probability tokens.
* **Prompt Caching:** Reuses pre-computed KV-cache for repeated static prefixes (lowers latency and token costs).

### Modern Agent Ecosystem (2026 Objectives)
* **Model Context Protocol (MCP):** Open standardized protocol connecting AI agents to external tools and data sources.
* **Strands Agents:** Open-source SDK for building and orchestrating model-driven agents.
* **Amazon Bedrock AgentCore:** Managed platform for hosting, executing, and securing autonomous agents at scale.
  * *AgentCore Runtime:* Managed serverless execution environment.
  * *AgentCore Identity:* Secure credential and role mapping for tool execution.
  * *AgentCore Policy:* Deterministic boundary rules (e.g., "Refuse refunds >$500").
  * *AgentCore Memory:* Persistent session and long-term state across interactions.
* **Kiro:** Agentic specification-driven developer environment for writing and testing software.
* **Amazon Quick:** Connected business AI workspace for enterprise search, research, and workflows.

---

## Domain 3: Foundation-Model Applications & RAG (28%)

### Retrieval-Augmented Generation (RAG) End-to-End
* **RAG Workflow:** Ingestion (Chunk -> Embed -> Vector Index) followed by Inference (Authenticate -> Authorize -> Retrieve -> Augment -> Generate -> Validate).
* **Chunking Strategies:** Fixed-size with overlap, semantic chunking, or hierarchy-aware parsing to preserve context across boundaries.
* **Vector Databases in Scope:** Amazon Bedrock Knowledge Bases, Amazon OpenSearch Service / Serverless, Amazon Aurora PostgreSQL (`pgvector`), Amazon RDS PostgreSQL, Amazon Neptune (graph + vectors), and Amazon DocumentDB.
* **Failure Layer Isolation:**
  * *Context Relevance Failure:* Retrieved chunks are off-topic.
  * *Context Coverage Gap:* Relevant chunks are on-topic but miss crucial exception clauses.
  * *Faithfulness / Groundedness Failure:* Model invents claims not substantiated by retrieved evidence.
  * *Citation Precision Failure:* Model cites an irrelevant source for a factual statement.

### Adaptation Ladder & Model Evaluation
* **Ladder of Customization (Least to Greatest Complexity):**
  1. Prompt Engineering (Zero-shot / Few-shot)
  2. Retrieval-Augmented Generation (RAG) for dynamic facts
  3. Supervised Fine-Tuning (SFT / PEFT / LoRA) for persistent style/behavior
  4. Continued Pre-training for broad, domain-specific vocabularies
* **Model Distillation:** Compresses a large, capable teacher model into a smaller, cost-effective student model.
* **Evaluation Metrics:** ROUGE (summarization n-gram overlap), BLEU (translation precision), BERTScore (semantic embedding similarity), LLM-as-a-Judge (rubric grading with bias calibration).

---

## Domain 4: Guidelines for Responsible AI (14%)

### Core Principles & Distinctions
* **Transparency vs. Explainability:** Transparency describes macro system documentation (Model Cards, intended uses, data provenance); Explainability clarifies micro individual decisions (e.g., SHAP feature attributions).
* **Bias Categories:** Representation bias (underrepresented groups), Label bias (inconsistent human raters), Sampling bias (unrepresentative collection), Measurement bias (faulty proxy metrics).
* **AWS Governance Artifacts:**
  * *SageMaker Model Cards:* Immutable documentation of customer-trained model architectures, risks, and evaluations.
  * *SageMaker Clarify:* Automated detection of pre-training and post-training bias, disparate impact, and SHAP explainability.
  * *AWS AI Service Cards:* AWS-published responsible-use documentation for AWS-managed AI services.
  * *Amazon Bedrock Guardrails:* Configurable runtime filters for denied topics, toxic content, and PII masking.
* **Human-in-the-Loop (HITL):** Enforces human verification for high-impact or ambiguous automated decisions.

---

## Domain 5: Security, Compliance, and Governance (14%)

### Foundational Controls & Architecture
* **AWS Shared Responsibility Model:** AWS secures the cloud infrastructure; the customer secures data, IAM permissions, prompt content, and encryption keys.
* **AWS PrivateLink (VPC Interface Endpoints):** Routes API traffic between VPCs and Amazon Bedrock entirely across AWS private backbone without internet exposure.
* **AWS KMS Customer Managed Keys:** Grants full control over key policies, usage auditing, and annual automated key rotation.
* **Amazon Macie:** Uses machine learning and pattern matching to discover and classify sensitive data (PII) in Amazon S3 buckets.
* **AWS CloudTrail:** Authoritative audit log capturing API actor identity, timestamp, and source IP for every Bedrock or SageMaker call.

### Threats & Adversarial Defense
* **Direct Prompt Injection:** Adversary inputs malicious instructions directly in the user prompt to override system directives.
* **Indirect Prompt Injection:** Untrusted instructions embedded inside external third-party sources (webpages, PDFs) retrieved via RAG.
* **Data Poisoning:** Tampering with training data or the retrieval knowledge base to corrupt outputs.
* **Defense-in-Depth:** Input sanitization, Bedrock Guardrails, least-privilege tool execution, and deterministic business policy verification.

---

## 68 Exam Traps

| # | Trap Concept | Critical Exam Distinction |
|---|--------------|---------------------------|
| 01 | **99% Accuracy** | Imbalanced classes can hide nearly all fraud misses. |
| 02 | **FP vs FN** | False positive = false alarm; False negative = missed real case. |
| 03 | **Precision vs Recall** | Precision lowers false alarms; Recall catches all actual positives. |
| 04 | **Train vs Test** | High training performance is never proof of generalization on unseen data. |
| 05 | **High Bias vs Variance** | Underfit = both poor; Overfit = strong train / poor test. |
| 06 | **Data vs Concept Drift** | Input distribution changes ($P(X)$) vs input-to-target relationship changes ($P(Y\|X)$). |
| 07 | **Delayed Labels** | Input drift is observable immediately; True model recall requires ground-truth labels. |
| 08 | **Features vs Hyperparameters** | Feature engineering transforms inputs; Hyperparameters configure training algorithms. |
| 09 | **Regression vs Classification** | Continuous numeric target vs discrete categorical target. |
| 10 | **Clustering vs RL** | Unsupervised grouping vs agent actions and reward feedback. |
| 11 | **Supervised vs Self-Supervised** | External human targets vs targets automatically derived from input data. |
| 12 | **Deterministic vs AI** | Exact business rules or math calculations do not require probabilistic GenAI. |
| 13 | **CV vs IDP** | Raw image recognition vs complete end-to-end document extraction workflows. |
| 14 | **Textract vs Comprehend** | Document OCR/tables/key-values vs semantic natural language meaning/sentiment. |
| 15 | **Transcribe vs Translate** | Audio-to-text conversion vs text translation across languages. |
| 16 | **Polly vs Transcribe** | Text-to-speech audio synthesis vs speech-to-text transcription. |
| 17 | **Lex vs Bedrock** | Conversational bot intent recognition vs foundation-model generative platform. |
| 18 | **Rekognition vs Generation** | Computer vision analysis does not itself generate synthetic marketing artwork. |
| 19 | **Bedrock vs SageMaker** | Serverless managed FM APIs vs fully custom ML development and infrastructure. |
| 20 | **JumpStart vs Bedrock** | Pre-trained models in SageMaker workflows vs managed FM application APIs. |
| 21 | **Quick vs Kiro** | Business AI enterprise workspace vs agentic software coding tool. |
| 22 | **Strands vs AgentCore** | Open-source agent SDK vs managed AWS runtime and operations infrastructure. |
| 23 | **MCP vs Authorization** | Tool connectivity standard is NOT a permission or access grant. |
| 24 | **Guardrails vs IAM** | Content safety policies are NOT resource access permissions. |
| 25 | **Prompt Rule vs Policy** | "Never refund >$500" in prompt text is not a hard security boundary. |
| 26 | **Context vs Prompt Engineering** | Selecting working data vs phrasing specific instructions. |
| 27 | **Context Window** | More tokens increase inference cost; larger windows do not ensure accuracy. |
| 28 | **Low Temperature** | Reduces sampling variation; never guarantees factual truth. |
| 29 | **Top-P vs Temperature** | Cumulative probability cutoff vs logit randomness scaling. |
| 30 | **Few-Shot vs Fine-Tuning** | In-context examples do NOT update model weights. |
| 31 | **Few-Shot vs Zero-Shot** | In-context examples frequently beat bare instructions with lower operational effort. |
| 32 | **RAG vs Fine-Tuning** | External dynamic facts with citations vs persistent learned behavior/tone. |
| 33 | **Fine-Tuning vs Pre-Training** | Task-specific adaptation vs broad domain language acquisition. |
| 34 | **Distillation vs Quantization** | Training a smaller student model vs reducing numeric weight precision. |
| 35 | **Prompt Caching** | Cost savings apply only to repeated, eligible static prefixes. |
| 36 | **Unsupported RAG Claim** | Correct evidence + fabricated statement = Faithfulness failure. |
| 37 | **Wrong Retrieval** | Irrelevant retrieved chunks = Context Relevance failure. |
| 38 | **Missing Evidence** | On-topic chunks that omit required exception clauses = Context Coverage gap. |
| 39 | **Citation != Grounding** | A cited reference must specifically support the adjacent sentence claim. |
| 40 | **S3 Vectors** | Dedicated S3 Vector index integration is distinct from standard S3 object storage. |
| 41 | **Neptune ML Trap** | Graph neural network prediction is not synonymous with vector search. |
| 42 | **ROUGE vs BLEU** | Summarization n-gram recall vs translation n-gram precision. |
| 43 | **BERTScore** | Semantic similarity embeddings evaluate paraphrases that share few exact words. |
| 44 | **LLM-as-a-Judge** | Scalable evaluation requires rubric calibration against position and verbosity bias. |
| 45 | **Human Evaluation** | High-impact consequential decisions require human review and calibration. |
| 46 | **Model Eval vs Guardrails** | Benchmarking model quality vs enforcing runtime content boundaries. |
| 47 | **Clarify vs Model Cards** | Bias/explainability analysis vs documented model fact sheets. |
| 48 | **AI Service vs Model Cards** | AWS-managed service disclosures vs customer-trained model documentation. |
| 49 | **Transparency vs Explainability** | System-level disclosure and limits vs specific rationale for an individual prediction. |
| 50 | **Accuracy vs Fairness** | High overall average accuracy cannot establish equitable subgroup performance. |
| 51 | **Safety vs Robustness** | Preventing harmful outputs vs maintaining stability under noisy inputs. |
| 52 | **Veracity vs Fluency** | Polished, confident text can still be completely factually wrong. |
| 53 | **AuthN vs AuthZ** | Authenticated identity verification vs authorization to read specific data. |
| 54 | **Authorize Before Retrieve** | Never retrieve all tenant data and filter later in the FM context. |
| 55 | **Macie vs Inspector** | S3 sensitive data/PII scanning vs EC2/ECR/Lambda vulnerability scanning. |
| 56 | **CloudTrail vs CloudWatch** | Who called which API and when vs system performance metrics and alarms. |
| 57 | **CloudTrail vs Config** | API event call history vs resource configuration state and compliance history. |
| 58 | **Artifact vs Config** | AWS compliance audit reports (SOC/ISO) vs customer resource compliance rules. |
| 59 | **KMS vs Secrets Manager** | Cryptographic key management vs database credential storage and rotation. |
| 60 | **PrivateLink vs Encryption** | Private network transit does not replace encryption at rest or IAM policies. |
| 61 | **Hash vs Authenticity** | A hash checks integrity against a reference; provenance proves author authenticity. |
| 62 | **Legacy Model Monitor** | Concept of monitoring drift remains; older feature replaced by modern tooling. |
| 63 | **Exam Weights** | Domain 3 is largest at 28%; no single domain has its own independent pass cutoff. |
| 64 | **Multi-Part Scoring** | All selections in MR, Order, and Match questions must be correct for credit. |
| 65 | **No Guessing Penalty** | Never leave questions blank; there is no negative marking on AWS exams. |
| 66 | **"Least Effort"** | Select simplest sufficient AWS managed service over custom infrastructure. |
| 67 | **"Current Facts"** | RAG retrieval consistently beats costly continuous model retraining. |
| 68 | **"Hard Business Rule"** | Deterministic software checks beat probabilistic natural-language prompt instructions. |

---

## Flowchart Lab: 40 Guided Ordering Sequences

### 01 Complete Supervised ML Lifecycle
1. State business goal and costly error types
2. Collect representative governed data
3. Split data and build meaningful features
4. Train, tune, and test on held-out cases
5. Deploy, monitor, and capture feedback  
*Order Key Why:* Never train before defining error costs; reserve an untouched final test set.

### 02 Fair Comparison: Train / Validate / Test
1. Define target and model success rules
2. Split examples with leakage controls
3. Fit candidates on training subset
4. Use validation to tune and select
5. Use untouched test data only for final check  
*Order Key Why:* Tuning repeatedly against the test set causes optimistic evaluation leakage.

### 03 Feature-Engineering Data Pipeline
1. Specify labels and approved sources
2. Split safely, respecting time order
3. Fit cleaning and scaling on training split only
4. Apply fitted transforms to validation/test splits
5. Train and evaluate without leakage  
*Order Key Why:* Preprocessing statistics must never leak from validation/test into training.

### 04 Classification Threshold Selection
1. Confirm target is categorical
2. Inspect class distribution and error costs
3. Choose suitable model and validation splits
4. Compute confusion matrix and precision/recall
5. Choose decision threshold against business costs  
*Order Key Why:* Class imbalance makes raw accuracy headline actively misleading.

### 05 Monitoring with Delayed Labels
1. Approve baseline metrics and live conditions
2. Monitor new inputs and predictions immediately
3. Join verified outcomes when available
4. Measure labeled accuracy and subgroup gaps
5. Investigate, approve, and monitor fixes  
*Order Key Why:* Without confirmed labels, true outcome recall cannot be calculated.

### 06 Comparing Two Fraud Models Fairly
1. Define false-negative vs false-alarm costs
2. Curate representative ground-truth labels
3. Separate development and final holdout sets
4. Train/tune using only development data
5. Compare holdout P/R and net business value  
*Order Key Why:* Optimize for the costly error (loss reduction vs investigation time).

### 07 Repeatable Production ML Pipeline
1. Version sources, code, and model settings
2. Process data and validate quality
3. Train and evaluate candidate versions
4. Register, review, and approve model in registry
5. Deploy, monitor, and trigger repeat cycle  
*Order Key Why:* Governance and reproducibility require versioned release gates.

### 08 Choose Inference Mode by Workload
1. Define response-time requirement
2. Estimate request size and processing duration
3. Measure volume and traffic intermittency
4. Compare real-time, async, batch, and serverless
5. Benchmark quality, SLA, and total cost  
*Order Key Why:* Interactive = real-time; Long-running = async; Bulk = batch; Bursty = serverless.

### 09 Context Engineering Request Flow
1. Identify goal and current task state
2. Select relevant memory, docs, and tools
3. Remove stale or redundant context
4. Assemble instruction plus useful context
5. Invoke model; measure quality and cost  
*Order Key Why:* Choose what the model sees before rewording prompts or inflating context.

### 10 Foundation Model Selection
1. List task, modality, and binding restrictions
2. Shortlist models; check Region and APIs
3. Test realistic quality, safety, and latency
4. Estimate input/output tokens and cost
5. Select compliant fit; monitor live results  
*Order Key Why:* Impressive benchmark scores cannot override required Region or compliance rules.

### 11 Lower Token Cost Without Degradation
1. Measure token counts, latency, and quality
2. Locate redundant history and shared prefixes
3. Trim context; test eligible prompt caching
4. Compare suitable smaller models and output limits
5. Release change; track task-cost and quality  
*Order Key Why:* Measure first; do not trim context so far that crucial evidence disappears.

### 12 Next-Token Generation Loop
1. Tokenize user prompt and active context
2. Run transformer attention/forward pass
3. Obtain candidate next-token probability scores
4. Choose token using decoding parameters (temperature/top-p)
5. Append token; repeat until stop sequence or limit  
*Order Key Why:* Decoding parameters control sampling; they do not alter model weights.

### 13 Controlled Agent Tool-Use Iteration
1. Receive goal and permitted user context
2. Plan next action within constraints
3. Check policy; invoke only approved tool
4. Observe tool result and update internal state
5. Validate outcome; finish or iterate  
*Order Key Why:* Permission checks must precede tool calls; tool outputs arrive after action.

### 14 Single Authorized Agent Round
1. Receive authenticated request
2. Select plan and tool within valid scope
3. Validate arguments; invoke approved API
4. Observe and verify API response
5. Respond with result or plan another step  
*Order Key Why:* MCP standardizes tool access; it does not grant execution permissions.

### 15 Voice-Assistant Architecture Pipeline
1. Capture customer speech safely
2. Transcribe speech to text with Amazon Transcribe
3. Interpret intent with Amazon Lex
4. Generate or select approved response text
5. Convert text to audio with Amazon Polly  
*Order Key Why:* Transcribe = Speech-to-Text; Lex = Intent/Bot; Polly = Text-to-Speech.

### 16 Agent Design to Live Operations
1. Define goal, safe tools, and stop criteria
2. Select model, framework, and context
3. Configure identity and policy boundaries
4. Test task completion and harmful edge cases
5. Deploy runtime; log, trace, and improve  
*Order Key Why:* Kiro = dev workflow; Strands = SDK; AgentCore = operational platform.

### 17 RAG Ingestion: Prepare Knowledge Base
1. Approve documents; attach access metadata
2. Parse, clean, and chunk source files
3. Create embeddings for each chunk
4. Store vectors plus source metadata in index
5. Sync updates; verify index readiness  
*Order Key Why:* Chunk -> Embed -> Index must occur before passages can be retrieved.

### 18 RAG Query: Return Evidence-Based Answer
1. Authenticate and authorize requester
2. Embed and query user question
3. Search and retrieve permitted passages
4. Augment foundation model prompt with evidence
5. Generate, verify grounding, and cite sources  
*Order Key Why:* Document embeddings are precomputed; query embeddings occur at runtime.

### 19 RAG Document Update and Resync
1. Detect new, changed, or deleted documents
2. Validate content, permissions, and versions
3. Sync: reparse and rechunk changed files
4. Re-embed and update vector index as needed
5. Test that newly authorized facts retrieve properly  
*Order Key Why:* Adding files to an S3 bucket does not automatically update vector indexes.

### 20 RAG Quality Diagnostic Checklist
1. Test whether retrieved chunks are on topic (Context Relevance)
2. Check whether required evidence is complete (Context Coverage)
3. Check generated claims against evidence (Faithfulness)
4. Check each citation supports its associated claim (Citation Precision)
5. Correct the failing retrieval or generation layer  
*Order Key Why:* Checklist hierarchy: Relevance -> Coverage -> Faithfulness -> Citations.

### 21 Governed Prompt Release / Versioning
1. Specify behavior, evidence, and constraints
2. Version initial prompt and representative tests
3. Evaluate safety, grounding, and quality
4. Approve and publish tested prompt version
5. Monitor production issues and revise under control  
*Order Key Why:* Untested prompt edits can alter safety and output schema unexpectedly.

### 22 Lowest-Complexity GenAI Solution Ladder
1. TRY zero-shot clear instruction
2. IF inadequate, ADD few-shot examples
3. IF dynamic facts missing, CONSIDER RAG
4. IF persistent behavior required, CONSIDER Fine-Tuning
5. IF broad domain gap, CONSIDER Continued Pre-Training  
*Order Key Why:* Always test lower-cost prompt techniques before funding model training.

### 23 Model Distillation Experiment
1. Set accepted quality, latency, and cost targets
2. Select strong teacher and smaller student candidate
3. Prepare prompts; obtain high-quality teacher responses
4. Train student; evaluate against held-out benchmarks
5. Compare savings and deploy only if targets are met  
*Order Key Why:* Student efficiency is the goal; teacher quality does not guarantee parity.

### 24 Supervised Fine-Tuning Workflow
1. Define persistent behavior and success metrics
2. Collect licensed, representative training pairs
3. Split data and format instruction pairs
4. Train and tune supported FM customization
5. Evaluate safety/quality; approve release  
*Order Key Why:* Fine-tuning changes model weights; prompting merely supplies working context.

### 25 Compare Candidate Foundation Models
1. Define business tasks and failure costs
2. Choose representative held-out test prompts
3. Run candidate models under identical settings
4. Score quality, safety, latency, and token cost
5. Review failure groups and document limitations  
*Order Key Why:* Uncalibrated leaderboards cannot replace workload-specific benchmark testing.

### 26 Retrieval-to-Citation Test Sequence
1. Send representative question to pipeline
2. Score relevance of retrieved passages
3. Check missing crucial evidence / coverage
4. Check answer faithfulness against evidence
5. Verify citation support; log failures  
*Order Key Why:* Relevance/coverage diagnose retrieval; faithfulness diagnoses generation.

### 27 Sensitive Human-Review Workflow
1. Identify high-impact or low-confidence cases
2. Prepare model answer plus available sources
3. Route case to an authorized human reviewer
4. Apply reviewer corrections or approve outcome
5. Log results to improve future evaluation sets  
*Order Key Why:* Human oversight protects high-risk cases; it does not replace base testing.

### 28 Improve a Weak RAG Assistant
1. Collect failing queries and expected evidence
2. Measure retrieval relevance and coverage
3. Fix metadata, chunking, or ranking as indicated
4. Evaluate generated faithfulness and citations
5. Retest real tasks and monitor cost  
*Order Key Why:* Fix the diagnosed layer; a larger FM cannot compensate for missing context.

### 29 Responsible High-Stakes AI Lifecycle
1. Identify stakeholders and unsafe uses
2. Assess data representativeness and provenance
3. Test subgroup metrics, safety, and veracity
4. Deploy with disclosure and human review
5. Monitor real-world impacts; remediate failures  
*Order Key Why:* Responsible AI begins before data collection and continues post-deployment.

### 30 Response to Subgroup Disparity
1. Confirm disparity on valid group samples
2. Inspect labels and training data coverage
3. Develop targeted mitigation or alternative workflow
4. Retest overall quality and subgroup outcomes
5. Document decisions and monitor post-release impacts  
*Order Key Why:* High overall accuracy does not prove fairness across demographic cohorts.

### 31 Calibrate an LLM-as-a-Judge
1. Write explicit scoring rubric; compile human gold set
2. Judge examples with balanced answer ordering
3. Check agreement and measure position/verbosity bias
4. Adjust criteria and calibration samples
5. Retest on held-out cases before relying on scores  
*Order Key Why:* LLM evaluators suffer from verbosity bias and ordering bias without calibration.

### 32 Explain an Individual Model Decision
1. Identify adverse decision and user need
2. Find trustworthy input features and model version
3. Produce valid feature attribution / explanation (e.g. SHAP)
4. Review fairness, limitations, and recourse options
5. Communicate clearly; log any customer appeal  
*Order Key Why:* A model card provides transparency; explaining a decision requires local attribution.

### 33 Sensitive Agent Action Approval
1. Authenticate user and agent identities
2. Authorize document and tool permissions
3. Retrieve only permitted information
4. Apply deterministic rule to proposed action
5. Execute allowed action and log outcome  
*Order Key Why:* Prompt instructions ("Never refund >$500") do not constitute hard authorization.

### 34 Secure RAG: Request to Response
1. Authenticate requesting user identity
2. Authorize resource and document access scope
3. Retrieve ONLY permitted relevant context
4. Generate completion from authorized evidence
5. Validate/filter answer; keep immutable audit logs  
*Order Key Why:* Never retrieve unauthorized tenant documents and rely on an FM to hide them.

### 35 Suspected Training-Data Tampering
1. Preserve evidence; identify affected dataset
2. Check hashes against trusted baseline references
3. Trace data provenance and affected models
4. Remove/repair corrupted data and revoke access
5. Record incident; strengthen ingestion safeguards  
*Order Key Why:* A matching hash proves integrity against a reference, not author authenticity.

### 36 Governed Data Lifecycle
1. Inventory sources and record provenance
2. Classify sensitive data; authorize access
3. Encrypt at rest/transit; track transformation lineage
4. Monitor access, retention, and geographic residency
5. Delete/archive according to policy; audit records  
*Order Key Why:* Lineage = origin; Residency = location; Retention = duration; Integrity = untampered.

### 37 Memory Anchor: ML Development
1. BUSINESS: Define outcome and costly error types
2. DATA: Collect, govern, split, and prepare
3. TRAIN: Fit and tune using development split
4. TEST: Check untouched final holdout data
5. OPERATE: Deploy, monitor, and retrain  
*One-Line Memorization:* Problem -> Data -> Train -> Test -> Monitor.

### 38 Memory Anchor: RAG Preparation
1. SOURCE: Approved documents and access tags
2. CHUNK: Parse and segment source material
3. EMBED: Convert each text chunk to vectors
4. INDEX: Store vectors and metadata in index
5. SYNC: Verify index readiness and updates  
*One-Line Memorization:* Documents -> Chunks -> Embeddings -> Vector Index -> Sync.

### 39 Memory Anchor: RAG Query & Answer
1. IDENTIFY: Authenticate the requesting user
2. PERMIT: Authorize data and document access
3. RETRIEVE: Query permitted passages from index
4. GENERATE: Place evidence into FM prompt context
5. VERIFY: Validate, cite sources, and log  
*One-Line Memorization:* AuthN -> AuthZ -> Retrieval -> Generation -> Validation.

### 40 Memory Anchor: Model Release
1. REQUIREMENTS: Use case, risks, and Region
2. EVIDENCE: Representative test cases and rubric
3. COMPARE: Run candidate models at equal settings
4. REVIEW: Automated metrics and human quality tests
5. RELEASE: Document, approve, and monitor live  
*One-Line Memorization:* Requirements -> Cases -> Tests -> Review -> Operate.