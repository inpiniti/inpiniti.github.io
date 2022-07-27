---
title: Data Wrangling
author: JUNG YoungKyun
date: 2022-06-22
category: 19 study
layout: post
---

# 3주차 : 데이터 랭그링(Data Wrangling)
1. 데이터 설명
    - 데이터의 모든 열 이름 표시(힌트: columns 함수)
    - 각 열의 데이터 유형 표시(힌트: dtypes 함수)
2. 누락 데이터 (Missing Value)
    - 각 열에 대한 NaN 값을 포함하는 전체 행을 계산하고 표시하려면(힌트: isna() 함수)
    - 각 열에 대해 NULL 값을 포함하는 전체 행을 계산하여 표시하려면(힌트: isnull() 함수)
    - "?"가 포함된 총 행을 계산하고 표시하려면 각 열에 대한 값
    - 예상 출력 예 2(a,b)(총 NULL 값을 계산하여 표시)
3. 결측치 처리 (Data Imputation)
    - NaN 또는 NULL 또는 "?"를 대체하려면 값:
        - 열 연령의 중앙값
        - 열 요금의 평균 값
        - Cabin 열의 경우 "0"(문자열)
4. 데이터 필터링 (Data Filtering)
    - 결측값이 많은 "body" 및 "homedest" 열을 제거합니다.
5. 데이터 시각화 (Data Visualization using seaborn)
    - BAR PLOT을 사용하여 "생존" 열에서 "생존" 및 "생존하지 않은" 승객 수를 플로팅합니다.
    - BAR PLOT을 사용하여 "성별" 열의 남성 및 여성 승객 수를 플로팅합니다.
    - BAR PLOT을 사용하여 "pclass"의 승객 수를 플로팅합니다.
    - "나이" 열의 HISTOGRAM 차트를 플로팅합니다.

```python
! pip install pandas
! pip install numpy
! pip install matplotlib
```
`out`

    Collecting pandas
      Using cached pandas-1.4.2-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (11.7 MB)
    Requirement already satisfied: pytz>=2020.1 in /opt/conda/lib/python3.9/site-packages (from pandas) (2021.3)
    Collecting numpy>=1.18.5
      Using cached numpy-1.22.4-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (16.8 MB)
    Requirement already satisfied: python-dateutil>=2.8.1 in /opt/conda/lib/python3.9/site-packages (from pandas) (2.8.2)
    Requirement already satisfied: six>=1.5 in /opt/conda/lib/python3.9/site-packages (from python-dateutil>=2.8.1->pandas) (1.16.0)
    Installing collected packages: numpy, pandas
    Successfully installed numpy-1.22.4 pandas-1.4.2
    Requirement already satisfied: numpy in /opt/conda/lib/python3.9/site-packages (1.22.4)
    Collecting matplotlib
      Using cached matplotlib-3.5.2-cp39-cp39-manylinux_2_5_x86_64.manylinux1_x86_64.whl (11.2 MB)
    Requirement already satisfied: numpy>=1.17 in /opt/conda/lib/python3.9/site-packages (from matplotlib) (1.22.4)
    Requirement already satisfied: python-dateutil>=2.7 in /opt/conda/lib/python3.9/site-packages (from matplotlib) (2.8.2)
    Collecting fonttools>=4.22.0
      Using cached fonttools-4.33.3-py3-none-any.whl (930 kB)
    Requirement already satisfied: pyparsing>=2.2.1 in /opt/conda/lib/python3.9/site-packages (from matplotlib) (2.4.7)
    Collecting kiwisolver>=1.0.1
      Using cached kiwisolver-1.4.3-cp39-cp39-manylinux_2_12_x86_64.manylinux2010_x86_64.whl (1.6 MB)
    Collecting cycler>=0.10
      Using cached cycler-0.11.0-py3-none-any.whl (6.4 kB)
    Collecting pillow>=6.2.0
      Using cached Pillow-9.1.1-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.1 MB)
    Requirement already satisfied: packaging>=20.0 in /opt/conda/lib/python3.9/site-packages (from matplotlib) (21.2)
    Requirement already satisfied: six>=1.5 in /opt/conda/lib/python3.9/site-packages (from python-dateutil>=2.7->matplotlib) (1.16.0)
    Installing collected packages: pillow, kiwisolver, fonttools, cycler, matplotlib
    Successfully installed cycler-0.11.0 fonttools-4.33.3 kiwisolver-1.4.3 matplotlib-3.5.2 pillow-9.1.1

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```python
df = pd.read_csv('titanic-openml_01.csv')
```

## 3.1 데이터 설명
### 3.1.1 데이터의 모든 열 이름 표시(힌트: 열 함수)

```python
df.columns
```
`out`

    Index(['pclass', 'survived', 'name', 'sex', 'age', 'sibsp', 'parch', 'ticket',
           'fare', 'cabin', 'embarked', 'boat', 'body', 'homedest'],
          dtype='object')

### 3.1.2 각 열의 데이터 유형 표시(힌트: dtypes 함수)

```python
df.dtypes
```
`out`

    pclass        int64
    survived      int64
    name         object
    sex          object
    age          object
    sibsp         int64
    parch         int64
    ticket       object
    fare        float64
    cabin        object
    embarked     object
    boat         object
    body         object
    homedest     object
    dtype: object

## 3.2 누락 데이터 (Missing Value)

### 3.2.1 각 열에 대한 NaN 값을 포함하는 전체 행을 계산하고 표시하려면(힌트: isna() 함수)

```python
df.isna( ).sum( )
```
`out`

    pclass      0
    survived    0
    name        0
    sex         0
    age         0
    sibsp       0
    parch       0
    ticket      0
    fare        0
    cabin       0
    embarked    0
    boat        0
    body        0
    homedest    0
    dtype: int64

### 3.2.2각 열에 대해 NULL 값을 포함하는 전체 행을 계산하여 표시하려면(힌트: isnull() 함수)

```python
df.isnull().sum()
```
`out`

    pclass      0
    survived    0
    name        0
    sex         0
    age         0
    sibsp       0
    parch       0
    ticket      0
    fare        0
    cabin       0
    embarked    0
    boat        0
    body        0
    homedest    0
    dtype: int64

### 3.2.3 "?"가 포함된 총 행을 계산하고 표시하려면 각 열에 대한 값

```python
dfRe = df.replace('?', np.NaN)
dfRe.isna( ).sum( )
```
`out`

    pclass        0
    survived      0
    name          0
    sex           0
    age         139
    sibsp         0
    parch         0
    ticket        0
    fare          0
    cabin       717
    embarked      2
    boat        583
    body        905
    homedest    258
    dtype: int64

## 3.3 결측치 처리 (Data Imputation)
### 3.3.1 NaN 또는 NULL 또는 "?"를 대체하려면 값:
#### 3.3.1.1 열 연령의 중앙값

```python
dfRe['age'] = dfRe['age'].astype(float)
dfRe = dfRe.fillna(dfRe.median(numeric_only=True)['age':'age'])
dfRe
```
`out`
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pclass</th>
      <th>survived</th>
      <th>name</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>ticket</th>
      <th>fare</th>
      <th>cabin</th>
      <th>embarked</th>
      <th>boat</th>
      <th>body</th>
      <th>homedest</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>30.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>25.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>3</td>
      <td>0</td>
      <td>Markoff, Mr. Marin</td>
      <td>male</td>
      <td>35.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>996</th>
      <td>3</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>male</td>
      <td>33.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349257</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 14 columns</p>
</div>

### 3.3.1.2 열 요금의 평균 값

```python
dfRe = dfRe.fillna(dfRe.mean(numeric_only=True)['fare':'fare'])
dfRe
```
`out`

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pclass</th>
      <th>survived</th>
      <th>name</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>ticket</th>
      <th>fare</th>
      <th>cabin</th>
      <th>embarked</th>
      <th>boat</th>
      <th>body</th>
      <th>homedest</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>30.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>25.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>3</td>
      <td>0</td>
      <td>Markoff, Mr. Marin</td>
      <td>male</td>
      <td>35.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>996</th>
      <td>3</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>male</td>
      <td>33.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349257</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 14 columns</p>
</div>

### 3.3.1.3 Cabin 열의 경우 "0"(문자열)

```python
dfRe.loc[dfRe['cabin'] != dfRe['cabin'], 'cabin'] = 0
dfRe
```
`out`

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pclass</th>
      <th>survived</th>
      <th>name</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>ticket</th>
      <th>fare</th>
      <th>cabin</th>
      <th>embarked</th>
      <th>boat</th>
      <th>body</th>
      <th>homedest</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>30.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>25.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>3</td>
      <td>0</td>
      <td>Markoff, Mr. Marin</td>
      <td>male</td>
      <td>35.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>7.8958</td>
      <td>0</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>996</th>
      <td>3</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>male</td>
      <td>33.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349257</td>
      <td>7.8958</td>
      <td>0</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>0</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>0</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>0</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 14 columns</p>
</div>

## 3.4 데이터 필터링 (Data Filtering)
### 3.4.1 결측값이 많은 "body" 및 "homedest" 열을 제거합니다.

```python
dfRe = dfRe.drop(['body', 'homedest'], axis=1)

dfRe
```
`out`

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pclass</th>
      <th>survived</th>
      <th>name</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>ticket</th>
      <th>fare</th>
      <th>cabin</th>
      <th>embarked</th>
      <th>boat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>30.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>25.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>3</td>
      <td>0</td>
      <td>Markoff, Mr. Marin</td>
      <td>male</td>
      <td>35.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>7.8958</td>
      <td>0</td>
      <td>C</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>996</th>
      <td>3</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>male</td>
      <td>33.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349257</td>
      <td>7.8958</td>
      <td>0</td>
      <td>S</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>0</td>
      <td>C</td>
      <td>C</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>0</td>
      <td>C</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>0</td>
      <td>Q</td>
      <td>15 16</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 12 columns</p>
</div>

## 3.5 데이터 시각화 (Data Visualization using seaborn)
### 3.5.1 BAR PLOT을 사용하여 "survived" 열에서 "survived" 및 "non survived" 승객 수를 플로팅합니다.

```python
x = np.arange(2)

plt.bar(x, dfRe['survived'].value_counts())
plt.xticks(x, ['non survived', 'survived'])

plt.show()
```
`out`

![png](..\images\15.02 ai traning\02\output_24_0.png)

### 3.5.2 BAR PLOT을 사용하여 "성별" 열의 남성 및 여성 승객 수를 플로팅합니다.

```python
x = np.arange(2)

plt.bar(x, dfRe['sex'].value_counts())
plt.xticks(x, ['male', 'female'])

plt.show()
```
`out`

![png](..\images\15.02 ai traning\02\output_26_0.png)

### 3.5.3 BAR PLOT을 사용하여 "pclass"의 승객 수를 플로팅합니다.

```python
dfRe['pclass'].value_counts()

x = np.arange(3)

plt.bar(x, dfRe['pclass'].value_counts())
plt.xticks(x, ['3', '1', '2'])

plt.show()
```
`out`

![png](..\images\15.02 ai traning\02\output_28_0.png)

### 3.5.4 "나이" 열의 HISTOGRAM 차트를 플로팅합니다.

```python
dfRe['age']

plt.hist(dfRe['age'])

plt.show()
```
`out`
 
![png](..\images\15.02 ai traning\02\output_30_0.png)