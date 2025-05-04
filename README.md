````markdown
# 🧮 Pandas Arithmetic, Data Alignment, and Function Mapping

This project contains a comprehensive collection of **25+ solved problems** using `pandas` that demonstrate:

- Arithmetic operations on DataFrames
- Flexible data alignment
- Use of broadcasting and reverse arithmetic
- Mapping with functions
- Classification and transformation techniques

These are aimed at building a deeper understanding of how pandas handles data under the hood during computations and real-world scenarios.

---

## 🔧 Prerequisites

Make sure you have the following installed:

```bash
pip install pandas jupyter
````

---

## 📘 List of Problems and Solutions

### 1. Center Data (Mean Subtraction)

**Goal:** Subtract the mean of each numeric column.

```python
df[numeric_columns] = df[numeric_columns] - df[numeric_columns].mean()
```

---

### 2. Column-wise Standardization (Z-Score)

**Goal:** Subtract the mean and divide by standard deviation.

```python
df[numeric_columns] = (df[numeric_columns] - df[numeric_columns].mean()) / df[numeric_columns].std()
```

---

### 3. Element-wise Division with Alignment

**Goal:** Divide column `E` by `G` with alignment.

```python
df['E_div_G'] = df['E'].div(df['G'], fill_value=0)
```

---

### 4. Add Two Series with Mismatched Indexes

**Goal:** Add `Ro` and `pH` with alignment and fill NaN with 0.

```python
df['Ro_plus_pH'] = df['Ro'].add(df['pH'], fill_value=0)
```

---

### 5. Align and Subtract Rows

**Goal:** Subtract last 3 rows from top 3 rows of numeric columns.

```python
result = top_3_numeric_rows.subtract(bottom_3_numeric_rows, fill_value=0)
```

---

### 6. Reverse Arithmetic with `.rsub()`

**Goal:** Compute `mean - value` for column `Su`.

```python
df['su_rsub'] = df['Su'].rsub(df['Su'].mean())
```

---

### 7. Multi-column Arithmetic

**Goal:** Calculate average strength from `Su` and `Sy`.

```python
df['Strength_Index'] = (df['Su'] + df['Sy']) / 2
```

---

### 8. Broadcasting with Alignment

**Goal:** Subtract the median of each numeric column from the column.

```python
df_subtract_median = df[numeric_columns] - df[numeric_columns].median()
```

---

### 9. Min-Max Scaling

**Goal:** Normalize `E`, `G`, and `Ro` between 0 and 1.

```python
def normalize(x):
    return (x - x.min()) / (x.max() - x.min())
result = df[cols].apply(normalize, axis=0)
```

---

### 10. Quantile-based Classification

**Goal:** Classify `Su` into `Low`, `Medium`, `High`.

```python
def su_classification(su_value):
    if pd.isna(su_value): return 'Unknown'
    elif su_value <= low: return 'Low'
    elif su_value <= high: return 'Medium'
    else: return 'High'
df['su_classification_results'] = df['Su'].apply(su_classification)
```

---

### 11. Total Stiffness Score

**Goal:** Define `Total_Stiffness = E + G + Ro`.

```python
def total_stiffness(row):
    return row['E'] + row['G'] + row['Ro']
df['total_stiffness'] = df[cols].apply(total_stiffness, axis=1)
```

---

### 12. Group By and Compute Mean

**Goal:** Group by whether `Sy` is above or below median, then compute mean of `Su`, `E`, `Ro`.

```python
def sy_position(x):
    if pd.isna(x): return 'Unknown'
    elif x > sy_median: return 'Above'
    else: return 'Below'
df['Sy_position'] = df['Sy'].apply(sy_position)
result = df.groupby('Sy_position')[cols].mean().reset_index()
```

---

### 13. Create Category from Multiple Conditions

**Goal:** Classify material as `'Fragile'` if `mu < 0.3` and `Ro > 7000`, otherwise `'Stable'`.

```python
def get_material_type(row):
    return 'Fragile' if row['mu'] < 0.3 and row['Ro'] > 7000 else 'Stable'
df['material_type'] = df.apply(get_material_type, axis=1)
```

---

## ✅ What You’ll Learn

* How to apply vectorized operations in Pandas
* Handling missing data during math operations
* Custom row-wise logic using `apply()`
* Classification using quantiles and thresholds
* Scaling and normalization for modeling

---

## 📁 Repository Contents

* `pandas_arithmetic_data_alignment_function_mapping.ipynb` — Complete Jupyter notebook with all 13 problems and outputs
* `README.md` — This file

---

## 📎 Dataset

The problems use a materials dataset (`Data.csv`) with properties like:

* `Su`, `Sy`, `E`, `G`, `Ro`, `mu`, `pH`, etc.

These represent real-world physical properties (e.g., Strength, Elasticity) making the analysis practical for engineering or materials science students.

---

## 🔖 Tags

`pandas` `data-science` `arithmetic` `standardization` `groupby` `apply` `normalization` `classification` `data-alignment`

---

## 👩‍💻 Author

**Michelle Alzola**
📫 [www.python.michellealzoladesign.com](https://www.python.michellealzoladesign.com)
💻 [GitHub Portfolio](https://github.com/michellealzola)
🧠 Focus: Python · Pandas · AI in Energy · Engineering Dashboards

---

## 🔗 License

This project is open-source and available under the [MIT License](LICENSE).

```


```
