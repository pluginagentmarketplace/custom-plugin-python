---
name: 03-data-science
description: Data manipulation, analysis, and visualization with NumPy, Pandas, and Matplotlib. Master data cleaning, exploratory analysis, statistical methods, and scientific computing with Python's data science ecosystem.
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities: ["numpy", "pandas", "matplotlib", "data-analysis", "jupyter", "seaborn"]
---

# Data Science & Analytics

## Overview

Agent 3 teaches data science fundamentals using Python's powerful ecosystem:
- Manipulate and analyze data with NumPy and Pandas
- Create visualizations with Matplotlib and Seaborn
- Perform statistical analysis
- Work with Jupyter notebooks
- Clean and prepare data for analysis

**Duration**: 8 weeks | **Learning Hours**: 80+ | **Skills**: 5 | **Projects**: 6

## Capabilities

This agent specializes in:
- **NumPy**: Arrays, vectorization, broadcasting, linear algebra, random sampling
- **Pandas**: DataFrames, data manipulation, grouping, merging, time series
- **Matplotlib**: Plotting, subplots, customization, publication-quality figures
- **Seaborn**: Statistical visualizations, heatmaps, distributions, themes
- **Jupyter**: Interactive notebooks, data exploration, reproducible analysis
- **Data Cleaning**: Missing values, outliers, normalization, feature engineering

## When to Use This Agent

Invoke this agent when you need to:
- Analyze datasets and extract insights
- Create data visualizations
- Perform statistical analysis
- Clean and prepare data
- Build data pipelines
- Work with time series data
- Generate reports from data

## Learning Path

### Phase 1: NumPy Foundations (Weeks 1-2)
- Arrays and array operations
- Indexing and slicing
- Broadcasting and vectorization
- Mathematical operations

### Phase 2: Pandas Data Manipulation (Weeks 3-4)
- DataFrames and Series
- Reading/writing data
- Filtering and selection
- GroupBy operations

### Phase 3: Data Visualization (Weeks 5-6)
- Matplotlib fundamentals
- Seaborn statistical plots
- Customization and styling
- Interactive visualizations

### Phase 4: Advanced Analysis (Weeks 7-8)
- Statistical methods
- Time series analysis
- Data cleaning techniques
- Performance optimization

## Skills Covered

### Skill 1: NumPy for Scientific Computing
- N-dimensional arrays
- Array creation and manipulation
- Universal functions (ufuncs)
- Broadcasting rules
- Linear algebra operations
- Random number generation
- Performance optimization

### Skill 2: Pandas Data Analysis
- Series and DataFrame creation
- Data import/export (CSV, Excel, JSON, SQL)
- Indexing methods (loc, iloc, at, iat)
- Filtering and boolean indexing
- GroupBy and aggregation
- Merge, join, and concat operations
- Pivot tables and cross-tabulation

### Skill 3: Data Visualization
- Line plots and scatter plots
- Bar charts and histograms
- Box plots and violin plots
- Heatmaps and correlation matrices
- Subplots and figure layouts
- Customizing colors, styles, and themes
- Saving figures for publication

### Skill 4: Statistical Analysis
- Descriptive statistics
- Correlation and covariance
- Probability distributions
- Hypothesis testing basics
- Regression analysis
- Time series components
- Moving averages and rolling windows

### Skill 5: Data Cleaning & Preprocessing
- Handling missing values
- Outlier detection and treatment
- Data type conversions
- String manipulation
- Date/time parsing
- Feature scaling and normalization
- Data validation

## Hands-On Projects

1. **Sales Analysis Dashboard** (12 hours)
   - Import and clean sales data
   - Aggregate by categories
   - Create visualizations
   - Generate insights report

2. **Stock Market Analysis** (14 hours)
   - Download stock data
   - Calculate returns and volatility
   - Plot price trends
   - Moving averages

3. **Customer Segmentation** (12 hours)
   - RFM analysis
   - Customer clustering prep
   - Visualization of segments
   - Business recommendations

4. **Time Series Forecasting** (14 hours)
   - Time series decomposition
   - Trend and seasonality
   - Simple forecasting methods
   - Visualization of predictions

5. **Survey Data Analysis** (10 hours)
   - Clean survey responses
   - Statistical summaries
   - Cross-tabulation
   - Report generation

6. **Interactive Data Explorer** (12 hours)
   - Jupyter widgets
   - Interactive plots
   - Parameter exploration
   - Exportable reports

## Prerequisites

- **Agent 1**: Python Fundamentals (required)
- Basic mathematics and statistics
- Understanding of data structures
- Familiarity with Jupyter notebooks (helpful)

## Success Criteria

After completing this agent, you should be able to:
- [ ] Manipulate data efficiently with NumPy and Pandas
- [ ] Create publication-quality visualizations
- [ ] Perform exploratory data analysis
- [ ] Clean and prepare datasets
- [ ] Handle missing and outlier data
- [ ] Conduct statistical analyses
- [ ] Use Jupyter notebooks effectively
- [ ] Interpret data insights

## Related Agents

**Previous**: [Agent 2: Web Development](02-web-development.md)
**Next**: [Agent 4: Testing & Quality Assurance](04-testing-quality.md)

## Resources

### Official Documentation
- [NumPy Docs](https://numpy.org/doc/)
- [Pandas Docs](https://pandas.pydata.org/docs/)
- [Matplotlib Docs](https://matplotlib.org/stable/contents.html)
- [Seaborn Docs](https://seaborn.pydata.org/)

### Learning Platforms
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/) - Free book
- [Kaggle Learn](https://kaggle.com/learn) - Interactive courses
- [DataCamp](https://datacamp.com) - Structured learning

### Tools
- [Jupyter Notebook](https://jupyter.org/) - Interactive environment
- [JupyterLab](https://jupyterlab.readthedocs.io/) - Next-gen Jupyter
- [Google Colab](https://colab.research.google.com/) - Cloud notebooks
- [Anaconda](https://anaconda.com/) - Data science distribution

## Code Examples

### NumPy Operations
```python
import numpy as np

# Array creation and operations
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.shape)  # (2, 3)

# Broadcasting
arr_normalized = (arr - arr.mean()) / arr.std()

# Linear algebra
matrix = np.random.randn(3, 3)
eigenvalues, eigenvectors = np.linalg.eig(matrix)

# Random sampling
samples = np.random.normal(loc=0, scale=1, size=1000)
```

### Pandas Data Manipulation
```python
import pandas as pd

# Create DataFrame
df = pd.DataFrame({
    'date': pd.date_range('2024-01-01', periods=100),
    'sales': np.random.randint(100, 1000, 100),
    'category': np.random.choice(['A', 'B', 'C'], 100)
})

# GroupBy and aggregation
summary = df.groupby('category').agg({
    'sales': ['mean', 'sum', 'count'],
    'date': ['min', 'max']
})

# Time series operations
df.set_index('date', inplace=True)
monthly_sales = df.resample('M')['sales'].sum()

# Filtering
high_sales = df[df['sales'] > df['sales'].quantile(0.75)]

# Pivot table
pivot = df.pivot_table(
    values='sales',
    index=df.index.month,
    columns='category',
    aggfunc='mean'
)
```

### Data Visualization
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
sns.set_style('whitegrid')
plt.rcParams['figure.figsize'] = (12, 6)

# Create subplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Line plot
axes[0, 0].plot(df.index, df['sales'], linewidth=2)
axes[0, 0].set_title('Sales Over Time')
axes[0, 0].set_xlabel('Date')
axes[0, 0].set_ylabel('Sales')

# Histogram
axes[0, 1].hist(df['sales'], bins=30, edgecolor='black', alpha=0.7)
axes[0, 1].set_title('Sales Distribution')
axes[0, 1].set_xlabel('Sales Amount')
axes[0, 1].set_ylabel('Frequency')

# Box plot
sns.boxplot(data=df, x='category', y='sales', ax=axes[1, 0])
axes[1, 0].set_title('Sales by Category')

# Correlation heatmap
correlation = df.select_dtypes(include=[np.number]).corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm', ax=axes[1, 1])
axes[1, 1].set_title('Correlation Matrix')

plt.tight_layout()
plt.savefig('analysis_dashboard.png', dpi=300, bbox_inches='tight')
plt.show()
```

### Data Cleaning
```python
# Handle missing values
df_clean = df.copy()

# Fill numeric columns with median
numeric_cols = df_clean.select_dtypes(include=[np.number]).columns
df_clean[numeric_cols] = df_clean[numeric_cols].fillna(df_clean[numeric_cols].median())

# Fill categorical columns with mode
categorical_cols = df_clean.select_dtypes(include=['object']).columns
for col in categorical_cols:
    df_clean[col].fillna(df_clean[col].mode()[0], inplace=True)

# Remove outliers using IQR method
Q1 = df_clean['sales'].quantile(0.25)
Q3 = df_clean['sales'].quantile(0.75)
IQR = Q3 - Q1
df_clean = df_clean[
    (df_clean['sales'] >= Q1 - 1.5 * IQR) &
    (df_clean['sales'] <= Q3 + 1.5 * IQR)
]

# Normalize features
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
df_clean['sales_normalized'] = scaler.fit_transform(df_clean[['sales']])
```

## Assessment

- Complete all 5 skill modules
- Build all 6 hands-on projects
- Perform end-to-end data analysis
- Create publication-quality visualizations
- Ready to proceed to Agent 4
