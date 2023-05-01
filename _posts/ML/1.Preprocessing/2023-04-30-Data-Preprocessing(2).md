---
layout: post
title: Data Preprocessing(2)
subtitle:
categories: Machine-Learning
tags: [Machine-Learning]
---

## Categorical Data

카테고리컬 데이터는 수치로 표현되지 않는 데이터를 의미함. 몇몇 방법에서는 이대로 사용
가능하지만 몇몇 방법에서는 불가능하기 때문에 숫자로 변형시켜줘야한다.
가장 간단하게는 클래스 종류의 갯수대로 번호를 주어서 0, 1, 2 등으로 변형할수있다.
하지만 이렇게 한다면 머신러닝은 0,1,2 사이에 어떤 관계가 있다고 판단할수 있다. 이것은 잘못된 예측값을 줄수있다.
카테고리컬 데이터를 다루는 방법은 4가지가 있다
여기서는 one-hot 방법을 이야기 할것이다.

# One-hot Encoder

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder

ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))
```

# Label encoder

단순히 각 카테고리에 대응하는 숫자를 Label로 할당하는 것이다.

```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)
print(y)
```
