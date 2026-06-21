# Chaos, Clouds, and Clusters — An NLP Journey
An enterprise-grade NLP pipeline designed to ingest unstructured text, engineer high-dimensional features, and map hidden thematic structures using advanced Clustering, Topic Modeling, and matrix factorization techniques.

TLDR; 

[![Tableau](https://img.shields.io/badge/Tableau-Live%20Dashboard-orange?style=for-the-badge&logo=tableau)]([YOUR_TABLEAU_PUBLIC_URL_HERE](https://public.tableau.com/app/profile/pagie.tomas/viz/AnNLPJourney-Clouds/Dashboard1))
_____________________________________________________________________________________________________________________________________________________________

## 📖 The Case Study: A STAR Approach

### 📍 Situation
In my travels, I have encountered plenty of brilliant people who get completely sidelined by raw data. Manual review becomes an exercise in eye strain and a massive waste of high-value time. 

This project started when a colleague holding a Ph.D. handed me a mountain of free-text survey results with some rather ambiguous directives:
* *"What's all this saying?"*
* *"I hold a Ph.D., this should not be what occupies my time!"*
* *"Whatever magic you do, just make sure it's readable and has some nice-looking charts, please."*

### 🎯 Task
To build an engineering solution that was scalable, interpretable, auditable, and malleable to other business needs—drastically reducing the time required to summarize a large corpus of unstructured text data.

### 🛠️ Action & The Core Problems Solved
Instead of "magic," I engineered a modular pipeline to address each specific pain point:

* **The Problem:** *"What's all this saying?"* <br>**The Solution:** I applied Topic Modeling and K-Means Clustering to automatically summarize, group, and extract the clear signal from the noise.
* **The Problem:** *"This shouldn't occupy my time."* <br>**The Solution:** Instead of a fragile, one-off script, I built a structured, reproducible pipeline that processes unstructured text systematically so the user never has to manually parse a sprawling spreadsheet again.
* **The Problem:** *"Make it readable with nice charts."* <br>**The Solution:** The pipeline engineered the data down to low-dimensional spatial coordinates ($x, y$), transforming abstract textual patterns into an executive-ready, interactive Tableau dashboard for rapid visual consumption.

### 📈 Result & Technical Impact
* **Operational Efficiency:** Created a production blueprint that compresses thousands of hours of manual text review down to minutes, drastically accelerating time-to-insight.
* **Zero Memory Latency:** Successfully eliminated local Jupyter Out-Of-Memory (OOM) kernel deadlocks by checkpointing intermediate clean states into compressed binary Parquet files, keeping RAM optimized during heavy modeling loops.
* **Commercial Extensibility:** Engineered the codebase to be entirely format-agnostic. Organizations can cleanly swap out the survey dataset for raw customer support logs or large corpora of corporate email streams to instantly unlock automated triage and trend detection.
* **Enterprise-Scale Cloud Expansion:** Successfully scaled the processing architecture from local limits up to 187,000 corporate documents. Migrated the pipeline to Databricks Serverless and converted the core engine to PySpark, expanding the framework to handle high-throughput corporate email streams.

## 🏗️ Technical Architecture & Stack

* **Languages & Core Math:** Python, Linear Algebra, Dimensionality Reduction, Latent Dirichlet Allocation (LDA), Non-Negative Matrix Factorization (NMF)
* **Machine Learning & NLP:** Feature Engineering, Scikit-Learn (`TfidfVectorizer` capturing up to trigrams; `CountVetorizer` capturing up to bigrams), Text Tokenization, Embedding Vectors, Cloud & Local LLMs (Meta Llama 3.1 70B via Databricks Foundation Endpoints / Local Ollama API parsing).
* **Data Engineering & Infrastructure:** Databricks Serverless Compute (Unity Catalog pathing), PySpark / Spark SQL, Pipeline Automation, Memory Management, Custom Data Cleansing, Schema Validation, Version Control (Git)
* **Data Visualization:** Tableau Public (Dynamic clustering layout and topic summaries)


## ☁️ Next Steps: Scaling to the Cloud (Databricks & PySpark Expansion)

To prove out the commercial extensibility of the architecture, I migrated the pipeline to a cloud infrastructure environment to process a high-volume enterprise dataset of **187,000 corporate emails**. Moving from a local workstation to **Databricks Serverless** introduced advanced enterprise data engineering challenges that required tactical optimization:

### 1. Navigating Memory Boundaries (`toPandas()` Optimization)
When converting massive, sparse distributed text matrix structures down to localized coordinates for downstream BI applications like Tableau, standard `toPandas()` execution can trigger fatal Spark Connect cache overflows. To guarantee extreme memory stability over serverless execution layers, I implemented a strict 60,000-row active threshold combined with proactive Python Garbage Collection (`gc.collect()`). This allowed the entire multi-model suite to train and compile locally in memory **in under 2 minutes.**

### 2. Eliminating Linear "Crowding" via High-Contrast Spatial Mapping
Standard linear reduction methods (like SVD) compress text data into a messy, indistinguishable central cloud when forced onto a 2D plot. To deliver clean, production-ready visual cluster "islands" for dashboard developers, I bypassed generic reductions and explicitly engineered coordinate configurations based on dominant probabilistic topic weights across three parallel models:
* **NMF Coordinate Layer:** Driven by the two strongest internal non-negative matrix topic weights to stretch data points cleanly away from the center.
* **LDA Coordinate Layer:** Driven by probabilistic structural themes.
* **K-Means Coordinate Layer:** Driven by exact geometric distance matrices to dense centroids.

### 3. Handling Cloud Quota Constraints & Resilient Failovers
During the production run, the high-volume data pipeline successfully pushed through hard daily sandbox resource and token ceilings on the serverless cluster. To maintain delivery SLAs, the deployment was built with an automated local fallback layer, demonstrating infrastructure resilience by shifting file outputs cleanly while keeping the automated Unity Catalog table definitions (`workspace.default...`) prepared for live Tableau Serverless JDBC polling.

### 4. Preprocessing Foundation for Deep Learning & Transformers (PyTorch Pipeline)
To scale this architecture for advanced semantic document analysis (such as medical record classification), this PySpark pipeline serves as the foundational, high-throughput ETL and Exploratory Data Analysis (EDA) layer. The clean, tokenized data outputs are structurally optimized to stream directly into deep learning models—allowing teams to swap out the TF-IDF/NMF layers for PyTorch-based Transformer architectures (like BERT or custom HuggingFace embeddings) to fine-tune deep neural networks on highly dense contextual text.

---
## 📬 Connect With Me
* **LinkedIn:** linkedin.com/in/pagiethomas
* **Email:** pagie.l.thomas@gmail.com
