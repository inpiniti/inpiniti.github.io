---
title: 03 week5 workbook
author: JUNG YoungKyun
date: 2022-07-06
category: 15.02 ai training
layout: post
---

5주차 : Python Function

1. 파이썬 함수를 만드는 방법에 대해 알아보십시오.
    1. 함수를 만드는 방법과 사용하는 방법에 대한 기사를 읽으십시오. [source](https://wikidocs.net/24)
    2. python "main" 기능 및 사용 방법에 대한 기사를 읽으십시오.
2. 함수 정의: 데이터 로더 함수
    1. 이전에 데이터 세트를 로드하기 위한 명령을 이미 작성했습니다(예: pd.read_csv …)
    2. 이제 여러 csv 파일을 로드하고 DataFrame에 저장하는 함수를 정의합니다(예: def data_loader).
    3. 출력의 기능은 DataFrame입니다.
3. 기능 정의: 상태 식별 기능
    1. 상태 식별을 위한 이전 코드(작업 번호 2)를 함수로 변경하십시오!
4. 기능 정의: 운임 유형 식별 기능
    1. 운임 구분을 위한 이전 코드(작업 4번)를 함수로 변경 !
5. 기능 변환: 데이터 메트릭(데이터 표준화)
    1. "연령"과 "운임"의 값을 표준화(힌트: StandardScaler 기능 사용)
6. Feature Transformation: 시퀀스 데이터 복구(Ordinal encoding)
    1. "상태 및 요금_유형" 열의 값을 서수로 인코딩합니다(힌트: OrdlinalEncoder 사용).
    2. 결과 표시
7. 기능 변환: 원핫(One-hot) 인코딩
    1. one-hot 인코딩을 사용하여 "sex, pclass, embarked 및 status" 열의 값을 인코딩합니다(힌트: OneHotEncoder 사용).
    2. 결과 표시
8. (선택 사항) 데이터 분할: 데이터를 학습 및 테스트 데이터 세트로 분할
    1. 훈련 세트와 테스트 세트가 무엇인지 사전에 읽으십시오(예: 기능이 무엇인지, 대상 레이블이 무엇인지)
    2. 사전 처리된 데이터 세트를 훈련 세트(80%)와 테스트 세트(20%)로 분할합니다(힌트: train_test_split 사용).

과제전. 설치

```python
#!pip install category_encoders
```

과제전. 라이브러리 불러오기


```python
import pandas as pd
import numpy as np
import sklearn
from category_encoders import OrdinalEncoder
from sklearn.preprocessing import StandardScaler
from category_encoders import OneHotEncoder
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score
```

1. 파이썬 함수를 만드는 방법에 대해 알아보십시오.
    1. 함수를 만드는 방법과 사용하는 방법에 대한 기사를 읽으십시오. [source](https://wikidocs.net/24)
    2. python "main" 기능 및 사용 방법에 대한 기사를 읽으십시오.


```python
#def 함수이름(매개변수):
#    <수행할 문장>
#    ...
#    return 결과값

# 다음은 일반 함수의 전형적인 예이다.
#def add(a, b): 
#    result = a + b 
#    return result

#>>> a = add(3, 4)
#>>> print(a)
#7
```

2. 함수 정의: 데이터 로더 함수
    1. 이전에 데이터 세트를 로드하기 위한 명령을 이미 작성했습니다(예: pd.read_csv …)
    2. 이제 여러 csv 파일을 로드하고 DataFrame에 저장하는 함수를 정의합니다(예: def data_loader).
    3. 출력의 기능은 DataFrame입니다.


```python
# 데이터 로더 함수 선언
def data_loader():
    # a. 데이터 세트 로드
    pd_read_csv = pd.read_csv('./Documents/titanic-openml_01.csv')
    # b. 데이터 저장
    return pd_read_csv
    
# 데이터 로더 함수 호출
dfs = data_loader()
# c. 출력
pd.DataFrame(dfs)
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



3. 기능 정의: 상태 식별 기능
    1. 상태 식별을 위한 이전 코드(작업 번호 2)를 함수로 변경하십시오!


```python
# age group
def male_female_child(passenger):
    age, sex = passenger
 
    if age < 1:
        return 'Infant'
    elif (age >= 1) and (age < 13):
        return 'Child'
    elif (age >= 13) and (age < 18):
        return 'Teen'
    elif (age >= 18) and (age <= 65):
        return 'Adult'
    elif age > 65:
        return 'Elderly'
    else:
        return sex

def data_loader_status():
    # age가 문자열이라
    dfs['age'] = dfs['age'].replace('?', np.nan).astype(float)
    # status 컬럼 추가
    dfs['status'] = dfs[['age','sex']].apply(male_female_child, axis=1)

data_loader_status()
pd.DataFrame(dfs)
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
      <td>?</td>
      <td>St Louis, MO</td>
      <td>Adult</td>
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
      <td>Infant</td>
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
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Child</td>
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
      <td>?</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>C</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
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
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>male</td>
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
      <td>?</td>
      <td>Q</td>
      <td>15 16</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 15 columns</p>
</div>



4. 기능 정의: 운임 유형 식별 기능
    1. 운임 구분을 위한 이전 코드(작업 4번)를 함수로 변경 !


```python
# fare group 
def fare_group(price):
    fare = price
 
    if price <= 8:
        return 'economy'
    elif (price > 8) and (price < 30):
        return 'business'
    else:
        return 'president'

def data_loader_fare():
    dfs['fare'] = dfs['fare'].replace('?', np.nan).astype(float)
    dfs['fare_type'] = dfs['fare'].apply(fare_group)

data_loader_fare()
dfs
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
      <td>?</td>
      <td>St Louis, MO</td>
      <td>Adult</td>
      <td>president</td>
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
      <td>Infant</td>
      <td>president</td>
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
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Child</td>
      <td>president</td>
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
      <td>?</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
      <td>president</td>
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
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
      <td>president</td>
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
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
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
      <td>?</td>
      <td>C</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
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
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>male</td>
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
      <td>?</td>
      <td>Q</td>
      <td>15 16</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
      <td>economy</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 16 columns</p>
</div>



5. 기능 변환: 데이터 메트릭(데이터 표준화)
    1. "연령"과 "운임"의 값을 표준화(힌트: StandardScaler 기능 사용)


```python
from sklearn.preprocessing import MinMaxScaler

dfs_ageFare = dfs[['age','fare']]

# StandardScaler객체 생성
scaler = StandardScaler()
# StandardScaler 로 데이터 셋 변환. fit( ) 과 transform( ) 호출.  
scaler.fit(dfs_ageFare)
output = scaler.transform(dfs_ageFare)

dfs_ageFare = pd.DataFrame(output, columns=dfs_ageFare.columns, index=list(dfs_ageFare.index.values))
dfs_ageFare
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
      <th>age</th>
      <th>fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.144838</td>
      <td>2.995777</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-2.096433</td>
      <td>1.954819</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-2.021151</td>
      <td>1.954819</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.075345</td>
      <td>1.954819</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.422810</td>
      <td>1.954819</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>0.272121</td>
      <td>-0.546341</td>
    </tr>
    <tr>
      <th>996</th>
      <td>0.133135</td>
      <td>-0.546341</td>
    </tr>
    <tr>
      <th>997</th>
      <td>NaN</td>
      <td>-0.558020</td>
    </tr>
    <tr>
      <th>998</th>
      <td>NaN</td>
      <td>-0.546341</td>
    </tr>
    <tr>
      <th>999</th>
      <td>NaN</td>
      <td>-0.548879</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 2 columns</p>
</div>



6. Feature Transformation: 시퀀스 데이터 복구(Ordinal encoding)
    1. "상태 및 요금_유형" 열의 값을 서수로 인코딩합니다(힌트: OrdlinalEncoder 사용).
        1. 여기에서 OrdlinalEncoder 이란?
            1. Categorical feature(범주형 특성)에 대한 순서형 코딩이라고 하며, 각 범주들을 특성으로 변경하지 않고, 그 안에서 **1,2,3 등의 숫자로 변경**하는 방법이다
            2. 범주가 너무 많아 one hot encoding을 하기 애매한 상황에서 이용하기 좋은 인코딩 방법이다.
            3. 또한 트리모델은 중요한 feature가 상위 노드를 점하여 분할을 하게 되는데, one hot encoding을 한 특성은 뽑히기에 불리한 상태가 되므로 대안으로 Ordinal Encoding을 한다.
            4. 설치는 옆과 같이 작성하면 된다. `!pip install category_encoders`
            5. import 는 옆과 같이 작성하면 된다. `from category_encoders import OrdinalEncoder`
    2. 결과 표시


```python
enc1 = OrdinalEncoder(cols = ['age', 'fare'])
dfs = enc1.fit_transform(dfs)
dfs
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>1</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>?</td>
      <td>St Louis, MO</td>
      <td>Adult</td>
      <td>president</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>2</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Infant</td>
      <td>president</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>2</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Child</td>
      <td>president</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>male</td>
      <td>4</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>2</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
      <td>president</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>female</td>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>2</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>Adult</td>
      <td>president</td>
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
      <td>23</td>
      <td>0</td>
      <td>0</td>
      <td>349213</td>
      <td>169</td>
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
      <td>economy</td>
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
      <td>169</td>
      <td>?</td>
      <td>S</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>Adult</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>997</th>
      <td>3</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>female</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>2649</td>
      <td>172</td>
      <td>?</td>
      <td>C</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>998</th>
      <td>3</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>male</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>349255</td>
      <td>169</td>
      <td>?</td>
      <td>C</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>male</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>999</th>
      <td>3</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>female</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>383123</td>
      <td>180</td>
      <td>?</td>
      <td>Q</td>
      <td>15 16</td>
      <td>?</td>
      <td>?</td>
      <td>female</td>
      <td>economy</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 16 columns</p>
</div>



7. 기능 변환: 원핫(One-hot) 인코딩
    1. one-hot 인코딩을 사용하여 "sex, pclass, embarked 및 status" 열의 값을 인코딩합니다(힌트: OneHotEncoder 사용).
        
        1. 여기에서 OnHot 인코딩이란?
            1. '여자', '남자'처럼 순위도 연속성도 없다면 반드시 다른 의미로의 수치값으로 변환해야 하는데, 그 변환을  OrdinalEncoder 이라고 합니다.
        2. 여기에서 OrdinalEncoder는 범주형 데이터를 희소행렬(Sparse Matrix)로 그 결과를 반환합니다.
            1. 다시 이 희소행렬을 OneHot 인코딩을 시키기 위해 아래의 코드를 수행합니다.
            2. import 는 옆과 같이 작성하면 된다. `from category_encoders import OneHotEncoder`
    2. 결과 표시


```python
enc = OneHotEncoder(cols = ['sex', 'pclass', 'embarked', 'status'], use_cat_names = True)
dfs = enc.fit_transform(dfs)
dfs
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
      <th>pclass_1.0</th>
      <th>pclass_2.0</th>
      <th>pclass_3.0</th>
      <th>survived</th>
      <th>name</th>
      <th>sex_female</th>
      <th>sex_male</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>...</th>
      <th>body</th>
      <th>homedest</th>
      <th>status_Adult</th>
      <th>status_Infant</th>
      <th>status_Child</th>
      <th>status_Elderly</th>
      <th>status_male</th>
      <th>status_Teen</th>
      <th>status_female</th>
      <th>fare_type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>St Louis, MO</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>president</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>president</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>president</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>Allison, Mr. Hudson Joshua Creighton</td>
      <td>0</td>
      <td>1</td>
      <td>4</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>135</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>president</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>Allison, Mrs. Hudson J C (Bessie Waldo Daniels)</td>
      <td>1</td>
      <td>0</td>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>?</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>president</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Markoff, Mr. Marin</td>
      <td>0</td>
      <td>1</td>
      <td>23</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>?</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>996</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Markun, Mr. Johann</td>
      <td>0</td>
      <td>1</td>
      <td>33</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>?</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>997</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>Masselmani, Mrs. Fatima</td>
      <td>1</td>
      <td>0</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>998</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Matinoff, Mr. Nicola</td>
      <td>0</td>
      <td>1</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>economy</td>
    </tr>
    <tr>
      <th>999</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>McCarthy, Miss. Catherine 'Katie'</td>
      <td>1</td>
      <td>0</td>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>?</td>
      <td>?</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>economy</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 28 columns</p>
</div>



8. (선택 사항) 데이터 분할: 데이터를 학습 및 테스트 데이터 세트로 분할
    1. 훈련 세트와 테스트 세트가 무엇인지 사전에 읽으십시오(예: 기능이 무엇인지, 대상 레이블이 무엇인지)
        1. 훈련 세트
            1. 학습용 데이터
            2. Classification 은 지도학습 방법의 하나로 학습용 데이터로 학습을 함
            3. 그냥 함수를 하나 만드는데, 일반적으로는 사람이 짜야 되지만, 기계가 대신 함수를 짜주는거라고 생각하면 되고
            4. 그 기계가 함수를 짤때, 그냥 맘대로 짜는게 아니라 참조하는 데이터가 있어야 하며, 그 데이터가 학습용 데이터라고 생각하면 편한듯
        2. 테스트 세트
            1. 테스트용 데이터
            2. 학습 데이터로 학습된 모델이 얼마나 뛰어난 성능을 가지는 평가하기 위해 만듬
            3. 그냥 위에서 기계가 만든 함수의 제대로 된 함수가 맞는지 알아내기 위한 것임
        3. import
            1. 이건 분류할때 쓰는거 같고 `from sklearn.model_selection import train_test_split`
            2. 이건 학습할때 쓰는거 같음 `from sklearn.tree import DecisionTreeClassifier`
            3. 이건 정확도 인가? `from sklearn.metrics import accuracy_score`
    2. 사전 처리된 데이터 세트를 훈련 세트(80%)와 테스트 세트(20%)로 분할합니다(힌트: train_test_split 사용).


```python
dfs.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 28 columns):
     #   Column          Non-Null Count  Dtype 
    ---  ------          --------------  ----- 
     0   pclass_1.0      1000 non-null   int64 
     1   pclass_2.0      1000 non-null   int64 
     2   pclass_3.0      1000 non-null   int64 
     3   survived        1000 non-null   int64 
     4   name            1000 non-null   object
     5   sex_female      1000 non-null   int64 
     6   sex_male        1000 non-null   int64 
     7   age             1000 non-null   int32 
     8   sibsp           1000 non-null   int64 
     9   parch           1000 non-null   int64 
     10  ticket          1000 non-null   object
     11  fare            1000 non-null   int32 
     12  cabin           1000 non-null   object
     13  embarked_S      1000 non-null   int64 
     14  embarked_C      1000 non-null   int64 
     15  embarked_?      1000 non-null   int64 
     16  embarked_Q      1000 non-null   int64 
     17  boat            1000 non-null   object
     18  body            1000 non-null   object
     19  homedest        1000 non-null   object
     20  status_Adult    1000 non-null   int64 
     21  status_Infant   1000 non-null   int64 
     22  status_Child    1000 non-null   int64 
     23  status_Elderly  1000 non-null   int64 
     24  status_male     1000 non-null   int64 
     25  status_Teen     1000 non-null   int64 
     26  status_female   1000 non-null   int64 
     27  fare_type       1000 non-null   object
    dtypes: int32(2), int64(19), object(7)
    memory usage: 211.1+ KB
    


```python
# 오류가 계속 생겨 object는 제거함
df_x_data = dfs.drop(['age', 'name', 'homedest', 'fare_type', 'ticket', 'cabin', 'boat', 'body'],axis=1)
# y값이면 나이를 예측 해보고자 하는 거 같음
df_y_data = dfs['age']

X_train, X_test, y_train, y_test = train_test_split(df_x_data, df_y_data, 
                                                    test_size=0.2, random_state=11)

print('X_train')
print(X_train)

print('----------------------------------------------------------')

print('X_test')
print(X_test)

print('----------------------------------------------------------')

print('y_train')
print(y_train)

print('----------------------------------------------------------')

print('y_test')
print(y_test)

print('----------------------------------------------------------')

# DecisionTreeClassifier 객체 생성 
dt_clf = DecisionTreeClassifier(random_state=11)

# 학습 수행 
dt_clf.fit(X_train, y_train)

# 학습이 완료된 DecisionTreeClassifier 객체에서 테스트 데이터 세트로 예측 수행. 
pred = dt_clf.predict(X_test)

print('예측 정확도: {0:.4f}'.format(accuracy_score(y_test,pred)))
```

    X_train
         pclass_1.0  pclass_2.0  pclass_3.0  survived  sex_female  sex_male  \
    832           0           0           1         0           1         0   
    797           0           0           1         0           0         1   
    49            1           0           0         1           0         1   
    867           0           0           1         1           1         0   
    514           0           1           0         1           0         1   
    ..          ...         ...         ...       ...         ...       ...   
    337           0           1           0         1           1         0   
    91            1           0           0         1           0         1   
    80            1           0           0         0           0         1   
    703           0           0           1         0           0         1   
    921           0           0           1         0           0         1   
    
         sibsp  parch  fare  embarked_S  embarked_C  embarked_?  embarked_Q  \
    832      1      6   211           1           0           0           0   
    797      0      0   180           0           0           0           1   
    49       0      1    33           0           1           0           0   
    867      1      1   219           1           0           0           0   
    514      1      1    18           1           0           0           0   
    ..     ...    ...   ...         ...         ...         ...         ...   
    337      1      0    18           1           0           0           0   
    91       1      0    48           1           0           0           0   
    80       0      0     3           1           0           0           0   
    703      0      0   180           0           0           0           1   
    921      0      0   156           1           0           0           0   
    
         status_Adult  status_Infant  status_Child  status_Elderly  status_male  \
    832             1              0             0               0            0   
    797             1              0             0               0            0   
    49              1              0             0               0            0   
    867             1              0             0               0            0   
    514             0              0             1               0            0   
    ..            ...            ...           ...             ...          ...   
    337             1              0             0               0            0   
    91              1              0             0               0            0   
    80              0              0             0               0            1   
    703             1              0             0               0            0   
    921             0              0             0               0            1   
    
         status_Teen  status_female  
    832            0              0  
    797            0              0  
    49             0              0  
    867            0              0  
    514            0              0  
    ..           ...            ...  
    337            0              0  
    91             0              0  
    80             0              0  
    703            0              0  
    921            0              0  
    
    [800 rows x 20 columns]
    ----------------------------------------------------------
    X_test
         pclass_1.0  pclass_2.0  pclass_3.0  survived  sex_female  sex_male  \
    25            1           0           0         0           0         1   
    464           0           1           0         0           0         1   
    372           0           1           0         0           0         1   
    730           0           0           1         0           0         1   
    757           0           0           1         1           1         0   
    ..          ...         ...         ...       ...         ...       ...   
    278           1           0           0         1           0         1   
    449           0           1           0         1           1         0   
    221           1           0           0         0           0         1   
    741           0           0           1         0           0         1   
    572           0           1           0         1           1         0   
    
         sibsp  parch  fare  embarked_S  embarked_C  embarked_?  embarked_Q  \
    25       0      0    18           0           1           0           0   
    464      0      0   111           1           0           0           0   
    372      1      0    18           1           0           0           0   
    730      0      0   169           1           0           0           0   
    757      1      0   183           1           0           0           0   
    ..     ...    ...   ...         ...         ...         ...         ...   
    278      0      0    26           0           1           0           0   
    449      1      3   121           1           0           0           0   
    221      0      1    93           0           1           0           0   
    741      0      0   172           0           1           0           0   
    572      0      0   149           1           0           0           0   
    
         status_Adult  status_Infant  status_Child  status_Elderly  status_male  \
    25              1              0             0               0            0   
    464             1              0             0               0            0   
    372             1              0             0               0            0   
    730             1              0             0               0            0   
    757             0              0             0               0            0   
    ..            ...            ...           ...             ...          ...   
    278             1              0             0               0            0   
    449             1              0             0               0            0   
    221             1              0             0               0            0   
    741             1              0             0               0            0   
    572             1              0             0               0            0   
    
         status_Teen  status_female  
    25             0              0  
    464            0              0  
    372            0              0  
    730            0              0  
    757            0              1  
    ..           ...            ...  
    278            0              0  
    449            0              0  
    221            0              0  
    741            0              0  
    572            0              0  
    
    [200 rows x 20 columns]
    ----------------------------------------------------------
    y_train
    832    50
    797    85
    49     19
    867    28
    514     3
           ..
    337    22
    91     46
    80     16
    703    54
    921    16
    Name: age, Length: 800, dtype: int32
    ----------------------------------------------------------
    y_test
    25      5
    464    18
    372     1
    730    40
    757    16
           ..
    278    18
    449    48
    221    56
    741    82
    572    24
    Name: age, Length: 200, dtype: int32
    ----------------------------------------------------------
    예측 정확도: 0.1900
    

정확도 0.19라면 엄청 구데기인듯...