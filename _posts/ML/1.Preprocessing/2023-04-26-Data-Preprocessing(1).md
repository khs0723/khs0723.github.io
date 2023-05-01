---
layout: post
title: Data Preprocessing(1)
subtitle:
categories: Machine-Learning
tags: [Machine-Learning]
---

## Independent and dependent variables

Independent is literally an input value. A variable with information that allows you to predict what you want to predict, and the variable with the predicted value is dependent.

## Importing dataset

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

dataset = pd.read_csv('Data.csv')
# iloc(index location)[row, col], ":" is range.
# every row, every col excpt last col
X = dataset.iloc[:, :-1].values # independent
# every row, and last col
y = dataset.iloc[:, -1].values # dependent
print(X)
print(y)
```

## Control missing data

If there are missing value on the data set, we need to handle null value. Actually, if about 1% of the data set is null, it doesn't have a significant impact on the outcome. However, if it is not, it must be handled for null value.

```python
# The most representative way to handle with missing value
from sklearn.impute import SimpleImputer

# Class instance
imputer = SimpleImputer(missing_values = np.nan, strategy = "mean")

# Find the missing cell in columns 1 and 2 except for string columns (categorical)
# If fit() finds all empty values, give the average value of this column
imputer.fit(X[:, 1:3])

# Transform will replace the missing value with the average value.
X[:, 1:3] = imputer.transform(X[:, 1:3])

print(X)
```
