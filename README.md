# AI Chatbot for Financial Literacy Education
### Master’s Thesis | MS in Machine Learning & AI | Liverpool John Moores University

[![Model: Qwen2.5-1.5B](https://img.shields.io/badge/Model-Qwen2.5--1.5B-blue)](https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct)
[![Hardware: T4 GPU Ready](https://img.shields.io/badge/Hardware-T4%20GPU%20Ready-orange)](#)
[![Accuracy: 95.4%](https://img.shields.io/badge/Accuracy-95.4%25-green)](#)

## 📌 Project Overview
This repository contains the source code and primary datasets for a high-precision, resource-efficient financial QA pipeline. This research addresses the **"Trust Gap"** in generative AI—where models often "hallucinate" or drift during numeric extraction—by shifting the technical focus from conversational fluency to **Numeric Faithfulness**.

The project demonstrates that **Small Language Models (SLMs)**, specifically the 1.5-billion parameter Qwen2.5 architecture, can achieve enterprise-level precision (95%+) on consumer-grade hardware through rigorous **Evaluation Design** and **Deterministic Grounding**.

## 📂 Repository Contents
To maintain academic transparency and ease of reproducibility, this repository is focused on the core components required for the thesis defense:

* **`Notebook\financial_qa_evaluation_pipeline.ipynb`**: The complete end-to-end source code. This notebook handles:
    1.  **Automated Extraction:** Parsing the included OECD/World Bank PDFs using `PyMuPDF`.
    2.  **Dataset Construction:** Segmenting 500+ pages into 531 structured, verifiable QA pairs using **Regex-based splitting**.
    3.  **Model Inference:** Executing **Qwen2.5-1.5B-Instruct** with **4-bit NF4 Quantization** for efficiency.
    4.  **Metric Evaluation:** Applying the **Hybrid F1** metric, **Exact Match (EM)**, and **Numeric Faithfulness** scores.
* **`Data/`**: A directory containing the original, authoritative PDF policy reports from the **World Bank (2025 Global Findex)** and **OECD (2023)** used as the "Ground Truth" for the AI.

## 🚀 Performance Benchmarks
The framework was rigorously tested against **531 structured QA pairs** with the following deterministic outcomes:

| Metric | Score | Technical Insight |
| :--- | :--- | :--- |
| **Exact Match (EM)** | 94.5% | Zero "word drift"; model adheres strictly to evidence. |
| **Numeric Faithfulness** | 94.6% | High precision in isolating and matching specific digits. |
| **Hybrid F1 (Composite)** | **95.4%** | Peak performance when **Length Guardrails** are applied. |
| **Fact Verification** | **97.2%** | Near-perfect reliability on Boolean/Truth logic. |

## 🛠️ Requirements & Setup
The source code is optimized for **Google Colab** or any local Jupyter environment equipped with an **NVIDIA T4 GPU** (or equivalent with at least 16GB VRAM).

1.  **Clone/Download** this repository.
2.  **Ensure the Folder Structure:** The notebook expects the PDFs to be located in the `datasets/` sub-folder.
3.  **Install Dependencies:** The initial cell in the notebook handles the installation of:
    ```bash
    pip install transformers bitsandbytes accelerate pymupdf scikit-learn
    ```
4.  **Execution:** Run all cells to trigger the 5-stage construction pipeline and generate the final accuracy report.

## 🎯 Architectural Significance
This project proves that **Evaluation Design is as vital as Model Scale**. By utilizing a **±1 Sentence Context Window** and **Deterministic Decoding (Temperature = 0)**, we successfully mitigated "Context Degradation" and "Numeric Drift." This allows for a model 100x smaller than GPT-4 to provide reliable, verifiable financial education, making high-quality AI tools accessible for global financial literacy initiatives.

## 🎓 Author
**Krishna Sai Sangaraju** MS in Machine Learning & AI Student (LJMU)

---
*This repository serves as the technical source code and dataset for a Master's Thesis defense. It is designed to be fully reproducible and verifiable.*
