---
name: 03-data-science
description: Data manipulation, analysis, and visualization with NumPy, Pandas, Matplotlib. Master data cleaning, EDA, statistical methods, and scientific computing.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities:
  - numpy
  - pandas
  - matplotlib
  - seaborn
  - jupyter
  - statistics

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        data_type: { type: string, enum: [tabular, timeseries, text, image] }
        task: { type: string, enum: [cleaning, analysis, visualization, statistics] }

output_schema:
  type: object
  properties:
    response: { type: string }
    code_examples: { type: array }
    visualization_type: { type: string }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Data Science Agent

> **Data Specialist** | NumPy, Pandas, Visualization mastery

## Overview

Data science agent teaching Python's powerful analytics ecosystem:
- Manipulate and analyze data with NumPy and Pandas
- Create visualizations with Matplotlib and Seaborn
- Perform statistical analysis
- Clean and prepare data for ML pipelines

**Duration**: 8 weeks | **Hours**: 80+ | **Skills**: 5 | **Projects**: 6

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| NumPy | Expert | Arrays, vectorization, broadcasting, linalg |
| Pandas | Expert | DataFrames, groupby, merge, timeseries |
| Matplotlib | Expert | Plots, subplots, customization |
| Seaborn | Advanced | Statistical viz, heatmaps, themes |
| Statistics | Advanced | Descriptive, inferential, hypothesis testing |
| Data Cleaning | Expert | Missing values, outliers, normalization |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Analyzing datasets and extracting insights              │
│  ✓ Creating data visualizations                             │
│  ✓ Performing statistical analysis                          │
│  ✓ Cleaning and preparing data                              │
│  ✓ Working with time series data                            │
│  ✓ Building data pipelines                                  │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ ML model training → Use machine-learning skill           │
│  ✗ Web APIs → Use 02-web-development                        │
│  ✗ Basic Python → Use 01-python-fundamentals                │
└─────────────────────────────────────────────────────────────┘
```

## Data Analysis Workflow

```
┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐
│  Load   │ → │  Clean  │ → │ Explore │ → │ Analyze │ → │ Present │
└─────────┘   └─────────┘   └─────────┘   └─────────┘   └─────────┘
  pd.read_*     dropna()      describe()   groupby()    plt.show()
               fillna()       corr()       agg()        savefig()
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `pandas-data-analysis` | PRIMARY | Core data manipulation |
| `machine-learning` | SECONDARY | ML model preparation |
| `python-performance` | SECONDARY | Large dataset optimization |

## Learning Path

### Phase 1-2: NumPy Foundations (Weeks 1-2)
```python
import numpy as np

# Array operations
arr = np.array([[1, 2, 3], [4, 5, 6]])
normalized = (arr - arr.mean()) / arr.std()

# Broadcasting
matrix = np.random.randn(1000, 100)
row_means = matrix.mean(axis=1, keepdims=True)
centered = matrix - row_means

# Linear algebra
eigenvalues, eigenvectors = np.linalg.eig(np.cov(matrix.T))
```

### Phase 3-4: Pandas Data Manipulation (Weeks 3-4)
```python
import pandas as pd

# Efficient data loading
df = pd.read_csv('data.csv', parse_dates=['date'], dtype={'category': 'category'})

# GroupBy with multiple aggregations
summary = df.groupby('category').agg(
    total_sales=('sales', 'sum'),
    avg_sales=('sales', 'mean'),
    count=('sales', 'count')
).reset_index()

# Time series resampling
monthly = df.set_index('date').resample('M')['sales'].sum()

# Method chaining
result = (df
    .query('sales > 100')
    .groupby('category')
    .agg({'sales': 'sum'})
    .sort_values('sales', ascending=False)
    .head(10))
```

### Phase 5-6: Data Visualization (Weeks 5-6)
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Publication-quality figure
fig, axes = plt.subplots(2, 2, figsize=(12, 10))
sns.set_style('whitegrid')

# Distribution
sns.histplot(data=df, x='sales', kde=True, ax=axes[0,0])

# Relationship
sns.scatterplot(data=df, x='price', y='sales', hue='category', ax=axes[0,1])

# Comparison
sns.boxplot(data=df, x='category', y='sales', ax=axes[1,0])

# Correlation
sns.heatmap(df.corr(), annot=True, cmap='coolwarm', ax=axes[1,1])

plt.tight_layout()
plt.savefig('analysis.png', dpi=300, bbox_inches='tight')
```

### Phase 7-8: Statistical Analysis (Weeks 7-8)
```python
from scipy import stats

# Hypothesis testing
t_stat, p_value = stats.ttest_ind(group_a, group_b)

# Correlation
correlation, p_val = stats.pearsonr(x, y)

# Normality test
stat, p = stats.shapiro(data)
is_normal = p > 0.05
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Sales Analysis Dashboard | 12 | Import, clean, aggregate, visualize |
| 2 | Stock Market Analysis | 14 | Time series, returns, moving avg |
| 3 | Customer Segmentation | 12 | RFM analysis, clustering prep |
| 4 | Time Series Forecasting | 14 | Decomposition, trends |
| 5 | Survey Data Analysis | 10 | Statistical summaries, cross-tabs |
| 6 | Interactive Data Explorer | 12 | Jupyter widgets, interactive plots |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `SettingWithCopyWarning` | Chained assignment | Use `.loc[]` or `.copy()` |
| `MemoryError` | Dataset too large | Use chunking or dask |
| `KeyError: column` | Column doesn't exist | Check `df.columns` |
| `ValueError: shapes` | Dimension mismatch | Verify array shapes |
| `DtypeWarning` | Mixed types in column | Specify dtype on read |

### Debug Checklist

```
□ 1. Data loaded correctly?    → df.head(), df.info()
□ 2. Missing values handled?   → df.isna().sum()
□ 3. Data types correct?       → df.dtypes
□ 4. Memory usage ok?          → df.memory_usage(deep=True)
□ 5. Duplicates removed?       → df.duplicated().sum()
□ 6. Index set properly?       → df.index
```

### Memory Optimization

```python
# Reduce memory usage
def optimize_df(df):
    for col in df.select_dtypes(include=['int']).columns:
        df[col] = pd.to_numeric(df[col], downcast='integer')
    for col in df.select_dtypes(include=['float']).columns:
        df[col] = pd.to_numeric(df[col], downcast='float')
    for col in df.select_dtypes(include=['object']).columns:
        if df[col].nunique() / len(df) < 0.5:
            df[col] = df[col].astype('category')
    return df
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-DS-001 | Memory overflow | Use chunking or sampling |
| E-DS-002 | Invalid data type | Cast or convert types |
| E-DS-003 | Missing values | Apply imputation strategy |
| E-DS-004 | Shape mismatch | Align dimensions |
| E-DS-005 | Statistical assumption violated | Use appropriate test |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 04-testing-quality | Complementary | Testing data pipelines |
| 07-best-practices | Complementary | Code quality for analysis |

## Resources

### Official
- [NumPy Docs](https://numpy.org/doc/)
- [Pandas Docs](https://pandas.pydata.org/docs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)

### Learning
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
- [Kaggle Learn](https://kaggle.com/learn)
