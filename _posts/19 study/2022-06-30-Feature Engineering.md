---
title: Feature Engineering
author: JUNG YoungKyun
date: 2022-06-22
category: 19 study
layout: post
---

# 피처 엔지니어링 (Feature Engineering)
1. Read the material on related to ML Workflows (i.e., Feature Engineering section) on the Teams channel folder (**mandatory), and answer these following questions:
(Teams 채널 폴더(**필수)에서 ML 워크플로 관련 자료(예: 기능 엔지니어링 섹션)를 읽고 다음 질문에 답하세요.)

    1. What is Feature Engineering? Feature engineering은 무엇인가요?
    (피쳐 엔지니어링이란 무엇입니까? 피처 엔지니어링)
        
    2. Why do we need Feature Engineering? 왜 하는 가요? 
    (기능 엔지니어링이 필요한 이유는 무엇입니까?)
        
    3. What is the goal of feature engineering? 목표는 무엇인가요?
    (피쳐 엔지니어링의 목표는 무엇입니까)

2. 특징 추출 (Feature Extraction)
    1. Create a new column called “status” to categorize the status of passenger with the following conditions:
    (다음 조건으로 승객의 상태를 분류하기 위해 "상태"라는 새 열을 만듭니다.)
        1. If age > 65 , then passenger is “elderly”
        (연령 > 65인 경우 승객은 "고령자"입니다.)
        2. If age >= 18 & age <= 65, then passenger is “adult”
        (연령 >= 18 & 연령 <= 65인 경우 승객은 "성인"입니다.)
        3. The rest is “child” passenger
        (나머지는 "어린이" 승객입니다.)
    2. Create a new column called “title” to extract the title of passenger from “name” column
    ("이름" 열에서 승객의 직위를 추출하기 위해 "제목"이라는 새 열을 만듭니다.)
        1. You might extract the title such as Mr, Miss, Lady, Master, etc
        (Mr, Miss, Lady, Master 등과 같은 제목을 추출할 수 있습니다.)

3. 데이터 인코딩 (Data Encoding)
    1. Encode value from “embarked” column into numerical value and save it as new column “embarked_enc”
    ("embarked" 열의 값을 숫자 값으로 인코딩하고 새 열 "embarked_enc"로 저장)
    2. For example: S -> 0, C -> 1
    (예: S -> 0, C -> 1)

4. 데이터 구간화 (Data Binning)
    1. Perform a data binning operation on the “fare” column (hint: use pandas cut/qcut function)
    ("fare" 열에 대한 데이터 비닝 작업 수행(힌트: pandas cut/qcut 기능 사용))
    2. Cut the fare values into 3 categories: “economy”, “business”, and “president” (hint: you can define the fare range (범위) by yourself)
    (요금 값을 "이코노미", "비즈니스", "대통령"의 3가지 범주로 나눕니다. (힌트: 요금 범위(도달)는 스스로 정의할 수 있습니다))
    3. Make a new column “fare_type” to represent the fare categories
    (요금 범주를 나타내는 새 열 "fare_type"을 만듭니다.)

5. 상관 계수 (Correlation Analysis)
    1. Perform a correlation analysis and show the result ! (hint : use the Spearman Rank Correlation)
    (상관 분석을 수행하고 결과를 보여줍니다! (힌트 : Spearman Rank Correlation 사용))
    2. (optional) Visualize the correlation analysis using heatmap (hint: you can use seaborn heatmap)
    ((선택사항) 히트맵을 사용하여 상관관계 분석 시각화(힌트: seaborn 히트맵을 사용할 수 있음))

6. CSV 파일로 내보내기 (CSV file data export)
    1. Please export the final data (i.e., preprocessed data) into a single .csv file ! (format : titanic_preprocessed_YOURNAME)
    (최종 데이터(즉, 전처리된 데이터)를 하나의 .csv 파일로 내보내십시오! (형식: titanic_preprocessed_YOURNAME))
    2. Save all the data into “dataset” folder at your directory (if you don’t have “dataset” folder, please make it in advance)
    (모든 데이터를 디렉토리의 "dataset" 폴더에 저장합니다. ("dataset" 폴더가 없다면 미리 만들어두세요))
    3. Upload all your results to server
    (모든 결과를 서버에 업로드)

## Teams 채널 폴더(**필수)에서 ML 워크플로 관련 자료(예: 기능 엔지니어링 섹션)를 읽고 다음 질문에 답하세요.
- What is Feature Engineering? Feature engineering은 무엇인가요?
- 피쳐 엔지니어링이란 무엇입니까? 피처 엔지니어링

```
답: 기계 학습 알고리즘에 사용할 수 있는 기능으로 변환하는 전처리 단계

Transforms raw data into a feature vector
Determines useful features for the training process.
```

- Why do we need Feature Engineering? 왜 하는 가요?
- 기능 엔지니어링이 필요한 이유는 무엇입니까?

```
답:
1. 머신 러닝 알고리즘과 호환되고 가장 적합한 입력 데이터 세트를 준비합니다.
2. 기계 학습 모델의 성능 개선

To prepare input data that is compatible with model
To improve the performance model (by giving more information to model)
```

- What is the goal of feature engineering? 목표는 무엇인가요?
- 피쳐 엔지니어링의 목표는 무엇입니까

```
답:
1. 비즈니스 문제에 맞춰 분석
2. 불필요한 데이터 제거
3. 모델의 확장성 촉진

To reduce the number of inputs of variables to reduce the computational cost 
To cut down the noise in data
In some cases, to improve the performance of the model
```


```python
import numpy as np
import pandas as pd
import seaborn as sns

df = pd.read_csv('C:/Users/ygjung/Documents/titanic-openml_01.csv')
df
```




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
      <td>29</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>?</td>
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
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>30</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>25</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
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
      <td>35</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>7.8958</td>
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
    </tr>
    <tr>
      <th>996</th>
      <td>3</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>male</td>
      <td>33</td>
      <td>0</td>
      <td>0</td>
      <td>349257</td>
      <td>7.8958</td>
      <td>?</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>?</td>
      <td>C</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>?</td>
      <td>Q</td>
      <td>15 16</td>
      <td>?</td>
      <td>?</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 14 columns</p>
</div>



## 특징 추출 (Feature Extraction)
- Create a new column called “status” to categorize the status of passenger with the following conditions:
- 다음 조건으로 승객의 상태를 분류하기 위해 "상태"라는 새 열을 만듭니다.
    - If age > 65 , then passenger is “elderly”
    - 연령 > 65인 경우 승객은 "고령자"입니다.
    - If age >= 18 & age <= 65, then passenger is “adult”
    - 연령 >= 18 & 연령 <= 65인 경우 승객은 "성인"입니다.
    - The rest is “child” passenger
    - 나머지는 "어린이" 승객입니다.


```python
dfRe = df.replace('?', np.NaN)

dfRe['age'] = dfRe['age'].astype(float)

dfRe['status'] = "child"
dfRe.loc[dfRe['age'] > 65, 'status'] = "elderly"
dfRe.loc[(dfRe['age'] >= 18) & (dfRe['age'] <= 65), 'status'] = "adult"

dfRe
```




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
      <th>status</th>
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
      <td>adult</td>
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
      <td>child</td>
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
      <td>child</td>
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
      <td>adult</td>
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
      <td>adult</td>
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
      <td>adult</td>
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
      <td>adult</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 15 columns</p>
</div>



- Create a new column called “title” to extract the title of passenger from “name” column
- "이름" 열에서 승객의 직위를 추출하기 위해 "제목"이라는 새 열을 만듭니다.
    - You might extract the title such as Mr, Miss, Lady, Master, etc
    - Mr, Miss, Lady, Master 등과 같은 제목을 추출할 수 있습니다.


```python
dfRe['title'] = "etc"

dfRe['name'] = dfRe['name'].astype(str)

dfRe.loc[dfRe['name'].str.contains('Mr', case=True, regex=False), 'title'] = "Mr"
dfRe.loc[dfRe['name'].str.contains('Miss', case=True, regex=False), 'title'] = "Miss"
dfRe.loc[dfRe['name'].str.contains('Lady', case=True, regex=False), 'title'] = "Lady"
dfRe.loc[dfRe['name'].str.contains('Master', case=True, regex=False), 'title'] = "Master"
dfRe
```




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
      <th>status</th>
      <th>title</th>
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
      <td>adult</td>
      <td>Miss</td>
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
      <td>child</td>
      <td>Master</td>
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
      <td>child</td>
      <td>Miss</td>
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
      <td>adult</td>
      <td>Mr</td>
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
      <td>adult</td>
      <td>Mr</td>
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
      <td>adult</td>
      <td>Mr</td>
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
      <td>adult</td>
      <td>Mr</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Miss</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 16 columns</p>
</div>



## 데이터 인코딩 (Data Encoding)
- Encode value from “embarked” column into numerical value and save it as new column “embarked_enc”
- "embarked" 열의 값을 숫자 값으로 인코딩하고 새 열 "embarked_enc"로 저장
- For example: S -> 0, C -> 1
- 예: S -> 0, C -> 1


```python
dfRe['embarked_enc'] = 2

dfRe['embarked'] = dfRe['embarked'].astype(str)

dfRe.loc[dfRe['embarked'] != dfRe['embarked'], 'embarked'] = ''

dfRe.loc[dfRe['embarked'].str.contains('S', case=True, regex=False), 'embarked_enc'] = 0
dfRe.loc[dfRe['embarked'].str.contains('C', case=True, regex=False), 'embarked_enc'] = 1
dfRe
```




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
      <th>status</th>
      <th>title</th>
      <th>embarked_enc</th>
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
      <td>adult</td>
      <td>Miss</td>
      <td>0</td>
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
      <td>child</td>
      <td>Master</td>
      <td>0</td>
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
      <td>child</td>
      <td>Miss</td>
      <td>0</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>1</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
      <td>1</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
      <td>1</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Miss</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 17 columns</p>
</div>



# 데이터 구간화 (Data Binning)
- Perform a data binning operation on the “fare” column (hint: use pandas cut/qcut function)
- "fare" 열에 대한 데이터 비닝 작업 수행(힌트: pandas cut/qcut 기능 사용)
- Cut the fare values into 3 categories: “economy”, “business”, and “president” (hint: you can define the fare range (범위) by yourself)
- 요금 값을 "이코노미", "비즈니스", "대통령"의 3가지 범주로 나눕니다. (힌트: 요금 범위(도달)는 스스로 정의할 수 있습니다)
- Make a new column “fare_type” to represent the fare categories
- 요금 범주를 나타내는 새 열 "fare_type"을 만듭니다.


```python
dfRe['fare_type'] = pd.cut(dfRe['fare'], 3, labels=['economy', 'business', 'president'])
dfRe
```




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
      <th>status</th>
      <th>title</th>
      <th>embarked_enc</th>
      <th>fare_type</th>
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
      <td>adult</td>
      <td>Miss</td>
      <td>0</td>
      <td>business</td>
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
      <td>child</td>
      <td>Master</td>
      <td>0</td>
      <td>economy</td>
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
      <td>child</td>
      <td>Miss</td>
      <td>0</td>
      <td>economy</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
      <td>economy</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
      <td>economy</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>1</td>
      <td>economy</td>
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
      <td>adult</td>
      <td>Mr</td>
      <td>0</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>7.2250</td>
      <td>NaN</td>
      <td>C</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
      <td>1</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>7.8958</td>
      <td>NaN</td>
      <td>C</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Mr</td>
      <td>1</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>7.7500</td>
      <td>NaN</td>
      <td>Q</td>
      <td>15 16</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>child</td>
      <td>Miss</td>
      <td>2</td>
      <td>economy</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 18 columns</p>
</div>



# 상관 계수 (Correlation Analysis)
- Perform a correlation analysis and show the result ! (hint : use the Spearman Rank Correlation)
- 상관 분석을 수행하고 결과를 보여줍니다! (힌트 : Spearman Rank Correlation 사용)


```python
# dfRe['fare'] = dfRe['fare'].astype(int)

# x = dfRe.embarked_enc.values
# y = dfRe.fare.values

#np.cov(x, y)[0, 1]

dfRe.corr()
```




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
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked_enc</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>pclass</th>
      <td>1.000000</td>
      <td>-0.307329</td>
      <td>-0.404092</td>
      <td>0.034437</td>
      <td>0.018783</td>
      <td>-0.538500</td>
      <td>-0.004776</td>
    </tr>
    <tr>
      <th>survived</th>
      <td>-0.307329</td>
      <td>1.000000</td>
      <td>-0.079531</td>
      <td>0.035458</td>
      <td>0.132062</td>
      <td>0.254126</td>
      <td>0.060786</td>
    </tr>
    <tr>
      <th>age</th>
      <td>-0.404092</td>
      <td>-0.079531</td>
      <td>1.000000</td>
      <td>-0.185850</td>
      <td>-0.153986</td>
      <td>0.169605</td>
      <td>0.088103</td>
    </tr>
    <tr>
      <th>sibsp</th>
      <td>0.034437</td>
      <td>0.035458</td>
      <td>-0.185850</td>
      <td>1.000000</td>
      <td>0.396863</td>
      <td>0.155269</td>
      <td>-0.121563</td>
    </tr>
    <tr>
      <th>parch</th>
      <td>0.018783</td>
      <td>0.132062</td>
      <td>-0.153986</td>
      <td>0.396863</td>
      <td>1.000000</td>
      <td>0.224579</td>
      <td>-0.102599</td>
    </tr>
    <tr>
      <th>fare</th>
      <td>-0.538500</td>
      <td>0.254126</td>
      <td>0.169605</td>
      <td>0.155269</td>
      <td>0.224579</td>
      <td>1.000000</td>
      <td>0.105584</td>
    </tr>
    <tr>
      <th>embarked_enc</th>
      <td>-0.004776</td>
      <td>0.060786</td>
      <td>0.088103</td>
      <td>-0.121563</td>
      <td>-0.102599</td>
      <td>0.105584</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



- (optional) Visualize the correlation analysis using heatmap (hint: you can use seaborn heatmap)
- (선택사항) 히트맵을 사용하여 상관관계 분석 시각화(힌트: seaborn 히트맵을 사용할 수 있음)


```python
sns.heatmap(df.corr())
```




    <AxesSubplot:>




    
![png](../images\15.02 ai traning\03\output_16_1.png)
    


# CSV 파일로 내보내기 (CSV file data export)
- Please export the final data (i.e., preprocessed data) into a single .csv file ! (format : titanic_preprocessed_YOURNAME)
- Save all the data into “dataset” folder at your directory (if you don’t have “dataset” folder, please make it in advance)
- Upload all your results to server
- 최종 데이터(즉, 전처리된 데이터)를 하나의 .csv 파일로 내보내십시오! (형식: titanic_preprocessed_YOURNAME)
- 모든 데이터를 디렉토리의 "dataset" 폴더에 저장합니다. ("dataset" 폴더가 없다면 미리 만들어두세요)
- 모든 결과를 서버에 업로드


```python
dfRe.to_csv('./dataset/titanic_preprocessed_young.csv')
```