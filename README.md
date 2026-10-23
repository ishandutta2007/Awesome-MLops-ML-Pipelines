# Awesome-MLops-ML-Pipelines

# Top MLOps & ML Pipelines Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Pipeline Orchestration, Experiment Tracking & Multi-Backend Compute Coordination*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **MLOps & ML Pipelines**. These tools coordinate the work of machine learning — scheduling training jobs across compute backends, tracking experiments and artifacts, managing model registries, and handing off to serving infrastructure — without stitching together a dozen disconnected scripts.

**Examples** include Kubeflow, MLflow, Metaflow, Apache Airflow, Dagster, Prefect, AWS SageMaker, Azure ML, Google Vertex AI, and Databricks (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, Kubernetes-native pipelines, and transparent experiment tracking — ideal for teams wanting data sovereignty and zero per-seat licensing without sacrificing reproducibility.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **AWS SageMaker** — **The most-mentioned MLOps platform in job listings for 2026** . **Full lifecycle coverage**: Pipelines, Studio, Model Registry, Endpoints, Model Monitor, Feature Store, and Clarify, all integrated with IAM, S3, VPC, and CloudWatch . **Strong foundation model story** via Bedrock and JumpStart, with mature governance through model cards, lineage tracking, and approval workflows for regulated industries . **The catch**: "twenty products in a trench coat" — figuring out which piece to use is its own learning curve, and costs add up fast if endpoint usage isn't monitored . **Best for AWS-native organizations of any size**, especially enterprises with compliance requirements .

- **Google Vertex AI** — **The most opinionated of the hyperscaler platforms, in a good way.** **Gemini-first** with first-party access to Google's foundation models . **Unified pipelines** built on Kubeflow Pipelines handle both classical ML and LLM workflows . **Model Garden** provides a curated catalog of open and proprietary models deployable in clicks, and **AutoML genuinely works** for tabular, vision, and text tasks without deep ML expertise . **The catch**: less mature than SageMaker on some governance and compliance fronts, and it locks you into GCP . **Best for GCP-native organizations** and teams building GenAI products on Gemini .

- **Azure Machine Learning** — **The governance leader through Azure Policy**, with broad compliance certifications (ISO, SOC, HIPAA, GDPR) and responsible AI dashboards for fairness, interpretability, and transparency . **Deep Azure DevOps integration** enables CI/CD extensions into continuous training and monitoring, with retraining triggered automatically from monitoring events . **The catch**: workflows are optimized for Microsoft services, reducing cross-cloud portability even though models and artifacts can be exported . **Best for Microsoft-committed enterprises** .

- **Databricks** — **The Lakehouse architecture unifying data engineering and ML pipelines** through the medallion schema (bronze, silver, gold) . **Delta Lake** manages dataset versioning and lineage, while **MLflow** provides experiment tracking, artifact logging, and model registry as a core component . **Databricks Asset Bundles and Terraform provider** express infrastructure as code for jobs, serving endpoints, and feature pipelines . **Best for organizations wanting one platform for data and ML** with reproducible feedback loops across data, model, and deployment pipelines .

## Open-Source GitHub Projects

- **Kubeflow** — **The Kubernetes-native ML toolkit.** **Kubeflow Pipelines (KFP)** orchestrates end-to-end workflows, with APIs, SDKs, and REST API for CI/CD integration . **The installation requires Kubernetes expertise** — a master node needs 4 vCPU and 16 GB RAM . **KFP components are defined as Docker containers or DSL-decorated functions**, which forces packaging files and dependencies into images . **Deployment options**: standalone dev flavor for experiments, community distribution for production with RBAC and multi-tenancy, or Kubernetes Native API mode storing pipeline definitions as Custom Resources for GitOps workflows . **PostgreSQL is only supported for development** — production KFP 2.18 uses MySQL-backed deployment because of a known concurrency limitation in MLMD's PostgreSQL backend . **Best for organizations already standardized on Kubernetes** wanting end-to-end ML pipelines .

- **MLflow** — **The open-source standard for experiment tracking and model registry**, created by Databricks. **Four core components**: Tracking, Projects, Models, and **Model Registry** with staging → production → archived workflows . **MLflow 3** (2025) fundamentally expanded for GenAI: **LoggedModel** as a first-class entity tracking a model's lifecycle across training and evaluation runs rather than per-run, **hierarchical tracing** for LLM calls and retrieval, and a **Prompt Registry** with A/B testing . **The hard limit**: you run the tracking server and backend database yourself — no vendor to call when Postgres falls over . **Best for teams with DevOps capacity** wanting zero per-seat fees and a central model registry .

- **Metaflow** — **The Python-loving data scientist's pipeline tool**, originally developed at Netflix to boost productivity across classical statistics and deep learning . **Human-friendly Python/R library** with **low learning curve** and **very easy DevOps** — it handles versioning, scaling, and deployment without requiring deep infrastructure knowledge . **Best for data scientists wanting to stay focused on modeling** rather than infrastructure, especially in Python-first teams .

- **Apache Airflow** — **The enterprise veteran with the largest ecosystem of ML compute backend integrations.** Provider packages include first-class integrations with **SageMaker, Vertex AI, Databricks, MLflow, Weights & Biases, Hugging Face, and Kubernetes execution backends** . **Deferrable operators** keep long-running training jobs from consuming worker slots while waiting for completion . **Multi-cloud deployment** supports teams training on different clouds, and **KubernetesPodOperator** gives full control over GPU requests and node affinity . **The catch**: **high learning curve and DevOps difficulty** — it's a general-purpose orchestrator, not ML-specific . **Best for ML platform teams supporting multiple model teams across multiple compute backends** with governance and lineage requirements .

- **Dagster** — **The asset-centric orchestrator for ML/AI pipelines.** **Asset-based design** maps cleanly to ML asset pipelines (datasets, features, trained models), with **best data lineage** for visualizing dependencies across the pipeline . **Type system catches errors before runtime**, and **built-in testing** makes unit testing pipelines easy . **Integrations with MLflow, Weights & Biases, and major ML compute backends** . **Best for RAG pipelines, embedding generation, and ML feature engineering** where asset-state-centric thinking matches the work . **Note**: Prefect has announced an agreement to acquire Dagster Labs (transaction not yet closed), with continuity commitments for now .

- **Prefect** — **The developer-friendly general-purpose orchestrator.** **Decorator-style flows** wrap ML training and inference logic with **low-to-medium learning curve** and **low complexity** . **Prefect Cloud provides managed orchestration**, while the hybrid model lets execution happen in customer infrastructure . **Best for small ML teams** wanting simpler setup than Airflow .

### Additional Strong Open-Source Options

- **Evidently AI** — Open-source library and platform for monitoring ML models in production, detecting data drift, prediction drift, and model quality degradation. **100+ built-in tests** and recent LLM observability support for RAG pipelines . Best for teams starting on monitoring with open-source ownership.
- **Flowdapt** — Platform for adaptive and reactive AI applications at large scale. **Auto-graph construction** builds Ray, Dask, or Local graphs automatically from vanilla Python, with scheduling and event-driven triggers . Best for many-model environments (e.g., weather forecasting for thousands of cities simultaneously) .

**Frameworks for building custom systems**: Combine **Kubeflow** for Kubernetes-native pipeline orchestration, **MLflow** for experiment tracking and model registry, **Metaflow** for Python-friendly data science workflows, **Dagster** for asset-centric ML pipelines with strong lineage, and **Apache Airflow** for multi-backend compute coordination with the broadest integration ecosystem — to build an MLOps stack tailored to your team's DevOps capacity, compute backends, and governance requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- MLOps platforms differ significantly in scope, operational burden, and pricing model. **Kubeflow is powerful but not beginner-friendly** — it requires Kubernetes expertise and a master node with 4 vCPU and 16 GB RAM . **MLflow is a tracker and registry, not a full orchestration tool** — light orchestration requires additional wiring . **Apache Airflow has the broadest ML integration ecosystem** but a high learning curve; **Dagster is asset-centric** with better lineage but a smaller integration ecosystem; **Prefect is simpler** for small teams . **Metaflow has the easiest DevOps experience** for Python data scientists . **SageMaker is "twenty products in a trench coat"** — sprawling surface area is its own learning curve . **Cloud platforms lock you in** — Azure ML workflows are optimized for Microsoft services with reduced cross-cloud portability, and Vertex AI locks you into GCP .
- Self-hosted open-source solutions require proper Kubernetes cluster configuration (for Kubeflow), database backend management (MySQL for production KFP, Postgres for MLflow), and someone on the team who owns the infrastructure — "free" self-hosted still has a headcount cost.

---

**Made for ML engineers and platform teams managing the model lifecycle without vendor lock-in.**
Let's make MLOps and ML pipelines more open, self-hostable, and compute-aware.
