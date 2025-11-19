---
name: data-ai-systems
description: Master machine learning, data science, and AI engineering. Covers Python, TensorFlow, PyTorch, data analysis, ML pipelines, LLMs, and AI systems development.
---

# Data, AI & Machine Learning Skill

Build intelligent systems with machine learning and AI.

## Quick Start

Train a simple classification model with Scikit-learn:

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

# Load data
iris = load_iris()
X, y = iris.data, iris.target

# Split into train/test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Train model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy:.2f}")
```

## Machine Learning Pipeline

### 1. Data Collection & Preparation
```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('data.csv')

# Explore data
print(df.info())
print(df.describe())
print(df.isnull().sum())

# Handle missing values
df = df.fillna(df.mean())

# Feature scaling
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

### 2. Feature Engineering
- Select relevant features
- Create new features from existing ones
- Encode categorical variables
- Handle outliers

### 3. Model Selection
- **Classification**: Logistic Regression, Random Forest, SVM, Neural Networks
- **Regression**: Linear Regression, Ridge/Lasso, Gradient Boosting
- **Clustering**: K-means, DBSCAN, Hierarchical
- **Dimensionality Reduction**: PCA, t-SNE, UMAP

### 4. Model Training & Validation
```python
from sklearn.model_selection import cross_val_score

# Cross-validation
scores = cross_val_score(model, X, y, cv=5)
print(f"Mean Score: {scores.mean():.3f} (+/- {scores.std():.3f})")

# Hyperparameter tuning
from sklearn.model_selection import GridSearchCV

params = {
    'n_estimators': [50, 100, 200],
    'max_depth': [5, 10, 15]
}
grid = GridSearchCV(RandomForestClassifier(), params, cv=5)
grid.fit(X_train, y_train)
print(f"Best params: {grid.best_params_}")
```

## Deep Learning with PyTorch

```python
import torch
import torch.nn as nn
from torch.utils.data import DataLoader, TensorDataset

# Define model
class SimpleNN(nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = nn.Linear(784, 128)
        self.fc2 = nn.Linear(128, 64)
        self.fc3 = nn.Linear(64, 10)
        self.relu = nn.ReLU()

    def forward(self, x):
        x = self.relu(self.fc1(x))
        x = self.relu(self.fc2(x))
        return self.fc3(x)

# Create model, loss, optimizer
model = SimpleNN()
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# Training loop
for epoch in range(10):
    for batch_x, batch_y in train_loader:
        optimizer.zero_grad()
        outputs = model(batch_x)
        loss = criterion(outputs, batch_y)
        loss.backward()
        optimizer.step()
```

## NLP with Transformers

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

# Load pre-trained model
model_name = "bert-base-uncased"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name)

# Tokenize text
text = "This movie is amazing!"
inputs = tokenizer(text, return_tensors="pt")

# Get predictions
with torch.no_grad():
    outputs = model(**inputs)
    predictions = torch.nn.functional.softmax(outputs.logits, dim=-1)
```

## AI Agents & RAG

### Retrieval-Augmented Generation (RAG)
```python
from langchain.embeddings import OpenAIEmbeddings
from langchain.vectorstores import Chroma
from langchain.chat_models import ChatOpenAI
from langchain.chains import RetrievalQA

# Create vector store
embeddings = OpenAIEmbeddings()
vectorstore = Chroma.from_documents(documents, embeddings)

# Create RAG chain
qa = RetrievalQA.from_chain_type(
    llm=ChatOpenAI(),
    chain_type="stuff",
    retriever=vectorstore.as_retriever()
)

# Query
answer = qa.run("What is in the documents?")
```

## Evaluation Metrics

### Classification
- **Accuracy**: Correct predictions / Total predictions
- **Precision**: TP / (TP + FP)
- **Recall**: TP / (TP + FN)
- **F1-Score**: 2 * (Precision * Recall) / (Precision + Recall)

### Regression
- **MAE**: Mean Absolute Error
- **MSE**: Mean Squared Error
- **RMSE**: Root Mean Squared Error
- **R²**: Coefficient of determination

## Tools & Libraries

**Data**: Pandas, NumPy, Polars
**Visualization**: Matplotlib, Seaborn, Plotly
**ML**: Scikit-learn, XGBoost, LightGBM
**Deep Learning**: TensorFlow/Keras, PyTorch, JAX
**NLP**: Transformers, spaCy, NLTK
**MLOps**: MLflow, Weights & Biases, DVC
**LLMs**: OpenAI API, Hugging Face, LangChain

## Practice Resources

- [Kaggle Competitions](https://kaggle.com/competitions)
- [Fast.ai Courses](https://fast.ai)
- [Google Colab](https://colab.research.google.com)
- [Hugging Face Hub](https://huggingface.co)

## Common Pitfalls

❌ Data leakage from test set
✅ Proper train/test split

❌ Ignoring class imbalance
✅ Use appropriate sampling or loss weighting

❌ Overfitting to training data
✅ Use cross-validation and regularization

❌ Not scaling features
✅ Normalize/standardize numerical features
