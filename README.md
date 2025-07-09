# Disease X Detection Pipeline

Hi there 👋 This project focuses on detecting **Disease X** using a large classification dataset. It evaluates multiple machine learning models to identify the most effective approach for accurate disease detection.

---

## 📝 **Project Overview**

- **Dataset:** 110,000 samples with 90 predictor variables and 1 response variable.
- **Objective:** Find the best-fit model with high accuracy and a balanced confusion matrix, prioritizing **lower False Negatives** for better clinical relevance.

---

## 📊 **Data Exploration**

- No null values present.
- Imbalanced dataset with more ‘0’s than ‘1’s in the response variable.
- Minimal linear correlation among predictor variables (except slight relation between X20 and X22).

---

## ⚙️ **Preprocessing**

1. **Scaling & PCA:**  
   StandardScaler applied, followed by PCA with 88 components to reduce dimensionality while retaining variance.

2. **Handling Class Imbalance:**  
   Applied **SMOTE** to the training dataset to balance classes before model training.

---

## 🤖 **Model Selection & Results**

| Model | Key Findings | Accuracy | Notes |
|-------|--------------|----------|-------|
| **Logistic Regression** | Best threshold at 0.471 achieved balanced confusion matrix | 73.4% | Higher threshold (0.797) reduced accuracy to 61.87% due to increased False Negatives |
| **Decision Tree** | Depth=10 performed better than depth=8 | 68.77% | Slight improvement in True Positives |
| **Random Forest** | 200 estimators, bootstrap=True | 74.46% | Good balance between True Positives and False Positives |
| **Bagging / Adaptive / Gradient Boosting** | Similar performance across boosting models | ~70% | Accuracy slightly lower than Logistic Regression |
| **MLP Classifier** | Deep model with hidden layers (100,60,30,20) | 75.26% | Best accuracy with lowest False Negatives (11.38%) |
| **Naive Bayes** | High False Negatives despite quick runtime | 52.66% | Not acceptable for clinical deployment |
| **Support Vector Regression** | Best accuracy (76.54%) with threshold tuning | 76.54% | High False Negatives reduce clinical applicability |

---

## 🔬 **Key Learnings**

- **Model selection** critically impacts disease detection performance.
- **False Negatives** are prioritized over mere accuracy in healthcare settings.
- **MLP Classifier and SVR** yielded the best results, with MLP preferred due to its confusion matrix balance.

---

## 📁 **Project Structure**

| Folder/File | Description |
|-------------|-------------|
| `notebooks/` | Data exploration and model training notebooks |
| `src/` | Scripts for preprocessing and model evaluation |
| `outputs/` | Confusion matrices and performance metrics |
| `requirements.txt` | Dependencies |
| `README.md` | Project documentation |

---

## 🚀 **How to Run**

Clone the repo:

```bash
git clone https://github.com/yourusername/disease-x-detection.git
cd disease-x-detection

