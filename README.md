# 🏨 Multilingual Hotel Review Topic Classification

> **Automatic Topic Detection in Multilingual Hotel Reviews using XLM-RoBERTa-Large**

This project focuses on a multi-label classification system designed to categorize hotel reviews into 20 distinct topics across 5 languages (DE, ES, FR, GB, MX). A key challenge of this task is the **zero-shot** requirement for Italian (IT) and Dutch (NL), which were handled through strategic data augmentation and cross-lingual model transfer.

---

## 🚀 Key Features

* **Model**: `xlm-roberta-large` (fine-tuned for multi-label classification).
* **Semantic Headers**: Enhanced context awareness by prefixing reviews with `[LIKED]` and `[DISLIKED]` tags based on the Booking.com review structure.
* **Data Augmentation**: Used `deep_translator` for Back-translation to generate synthetic training data for Italian and Dutch, mitigating the zero-shot cold start problem.
* **Optimization**: Implemented **Label-specific Threshold Optimization** (Grid Search 0.1–0.9) to maximize the Macro F1 Score instead of using a fixed 0.5 threshold.
* **Class Imbalance Handling**: Applied `MultilabelStratifiedShuffleSplit` for data consistency and class-weighted loss during training.

---

## 📊 Final Performance

* **Validation Macro F1 Score**: **0.7572**
* **Key Strengths**: High precision in frequent labels like `staff` (0.92) and `hotel-location` (0.95).

---

## 📁 Project Structure

```text
├── preprocessing.ipynb      # Data cleaning, Back-translation, and Stratified splitting
├── model.ipynb              # Model training and Threshold optimization logic
├── inference.ipynb          # Final prediction pipeline for submission
├── best_thresholds.npy      # Optimized threshold values for each of the 20 labels
├── train_data.csv           # Final training dataset
└── val_data.csv             # Final validation dataset

```

---

## 🛠 Installation & Quick Start

### 1. Requirements

```bash
pip install pandas torch transformers scikit-learn openpyxl tqdm

```

### 2. How to Run Inference

1. Ensure `test_data.xlsx` and `best_thresholds.npy` are in the root directory.
2. Run all cells in `inference.ipynb`.
3. The predictions will be saved as `output.xlsx`.

---

## 🔗 Resources

* **Hugging Face Model**: [ainniy/xlm-roberta-hotel-topics](https://huggingface.co/ainniy/xlm-roberta-hotel-topics)
* **Methodology**: Detailed analysis can be found in the attached System Description Paper.

```
