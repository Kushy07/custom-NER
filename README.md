# custom-NER

# 🍽️ Recipe Ingredient Named Entity Recognition using Conditional Random Fields (CRF)

A Machine Learning project that automatically extracts structured information from unstructured recipe ingredient text using **Conditional Random Fields (CRF)**.

The model identifies three important entities from recipe ingredient lists:

- **Quantity**
- **Unit**
- **Ingredient**

This project demonstrates how sequence labeling techniques can transform free-text recipe data into structured information suitable for downstream Natural Language Processing (NLP) applications.

---

## 📌 Project Overview

Recipe ingredient lists are typically written as free text without a fixed grammatical structure. Before recipes can be used for recommendation systems, nutrition analysis, or grocery list generation, important entities need to be extracted automatically.

This project builds a **Named Entity Recognition (NER)** system using **Conditional Random Fields (CRF)** to label each token in an ingredient sequence.

Example:

**Input**

```text
2 cups rice 1 teaspoon cumin seeds
```

**Output**

| Token | Entity |
|-------|---------|
| 2 | Quantity |
| cups | Unit |
| rice | Ingredient |
| 1 | Quantity |
| teaspoon | Unit |
| cumin | Ingredient |
| seeds | Ingredient |

---

# Features

- Named Entity Recognition (NER)
- Conditional Random Fields (CRF) model
- Context-aware feature engineering
- Automatic extraction of:
  - Quantity
  - Unit
  - Ingredient
- Model evaluation with Precision, Recall, F1-score, and Accuracy
- Error analysis on validation data

---

# Dataset

The dataset consists of recipe ingredient lists stored in **JSON** format.

Each sample contains:

```json
{
    "input": "2 cups rice 1 teaspoon cumin seeds",
    "pos": [
        "Quantity",
        "Unit",
        "Ingredient",
        "Quantity",
        "Unit",
        "Ingredient",
        "Ingredient"
    ]
}
```

Each token has a corresponding entity label, making the dataset suitable for supervised sequence labeling.

---

# Technologies Used

- Python
- pandas
- NumPy
- scikit-learn
- sklearn-crfsuite
- python-crfsuite
- spaCy
- Matplotlib

---

# Project Workflow

1. Data Loading
2. Data Validation
3. Tokenization
4. Feature Engineering
5. Train–Validation Split
6. CRF Model Training
7. Prediction
8. Model Evaluation
9. Error Analysis

---

# Feature Engineering

The CRF model uses contextual features including:

- Current word
- Lowercase form
- Prefixes
- Suffixes
- Word length
- Digit information
- Uppercase information
- Title case information
- Previous token
- Next token
- Beginning of sentence indicator
- End of sentence indicator

These contextual features enable the model to learn relationships between neighboring tokens.

---

# Model Performance

## Training Performance

| Entity | Precision | Recall | F1-Score |
|---------|-----------|--------|----------|
| Quantity | 1.00 | 1.00 | 1.00 |
| Unit | 1.00 | 1.00 | 1.00 |
| Ingredient | 1.00 | 1.00 | 1.00 |

**Training Accuracy:** **100%**

---

## Validation Performance

| Entity | Precision | Recall | F1-Score |
|---------|-----------|--------|----------|
| Quantity | 0.99 | 1.00 | 0.99 |
| Unit | 0.99 | 0.99 | 0.99 |
| Ingredient | 1.00 | 1.00 | 1.00 |

**Overall Validation Accuracy:** **99.83%**

Only **5 prediction errors** were observed across **2,876 validation tokens**.

---

# Error Analysis

Most prediction errors occurred due to ambiguous contextual words such as:

- "to" (e.g., *10 to 12*)
- "into" (e.g., *French cut into*)

Despite these challenges, the model maintained excellent generalization performance.

---

# Applications

This model can be integrated into:

- Recipe Recommendation Systems
- Smart Grocery List Generation
- Nutrition Information Extraction
- Food Knowledge Graphs
- Recipe Search Engines
- Cooking Assistants
- Meal Planning Applications
- Ingredient Standardization Pipelines

---

# Limitations

- Trained specifically on recipe ingredient data
- Rare ingredient names may reduce accuracy
- Sensitive to highly irregular formatting
- Does not recognize:
  - Cooking methods
  - Preparation instructions
  - Temperatures
  - Cooking durations

---

# Future Improvements

- Train on larger multi-cuisine datasets
- Add more entity categories
- Hyperparameter optimization
- Compare with Transformer models (BERT)
- Incorporate contextual embeddings
- Perform cross-validation

---

# Repository Structure

```
├── data/
│   └── recipe_dataset.json
├── notebooks/
│   └── recipe_ner.ipynb
├── models/
├── results/
├── README.md
└── requirements.txt
```

---

# Installation

Clone the repository:

```bash
git clone https://github.com/your-username/recipe-ingredient-ner.git
cd recipe-ingredient-ner
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Run the Project

Launch the Jupyter Notebook:

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

Open the notebook and execute all cells to train and evaluate the CRF model.

---

# Results

The CRF model successfully learned contextual dependencies between quantities, measurement units, and ingredient names, achieving **99.83% validation accuracy** while demonstrating excellent generalization with minimal prediction errors.

---

# License

This project is intended for educational and research purposes.

---

# Author

**Kushagra Vats**

Machine Learning • Natural Language Processing • Named Entity Recognition
