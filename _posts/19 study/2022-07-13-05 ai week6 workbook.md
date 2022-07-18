---
title: week6 workbook
author: JUNG YoungKyun
date: 2022-07-13
category: 19 study
layout: post
---

# 6주차 : Data Splitting & Model Loading
1. Data splitting: Split the data into training and test dataset
    1. Please [read](https://towardsdatascience.com/understanding-train-test-split-scikit-learn-python-ea676d5e3d1) on what is the training set and testing set in advance (e.g., what is feature, what is target label)
    1. Split the preprocessed dataset into training set (80%) and testing set (20%) (hint: use train_test_split)
        1. output: X_train, X_test, y_train, y_test
1. ML model: Create a classifier (machine learning model)
    1. Let’s try to make a simple Decision Tree classifier for our problem (hint: use DecisionTreeClassifier)
    1. Define your Decision Tree Classifier ([read](https://towardsdatascience.com/understanding-train-test-split-scikit-learn-python-ea676d5e3d1) here)
1. ML model: Train and test the classifier
    1. Train the classifier using the training data ! (hint: use “fit”)
    1. Test the classifier by creating predictions using the testing data (hint: use “predict”)  output: a list of prediction (e.g., y_pred)
    1. Show the accuracy score between y_test and y_pred
1. ML model: Load pre-trained model
    1. Find the pre-trained model (i.e., [dt_model_220707.pkl](./dt_model_220707.pkl)) on Teams folder
    1. Upload that model into your Jupyter Hub directory, place it in folder “model” (please make it first !)
    1. Load that model and create predictions using that model 
    1. Show the accuracy score ! (hint: use accuracy_score)
1. Watch and get insights from online lecture video 
    1. Please watch the lecture video until next Tuesday (2022.07.12)
    1. Get some idea or insights from the video
    1. Share with others on the next seminar session if you found some interesting parts from the video 
    1. Link: 
        1. [YouTube : 93. 머신러닝 파이프라인의 이해 (Annotation AI 이광희 CTO)](https://www.youtube.com/watch?v=hRqmBFd0juw&ab_channel=AI%ED%94%84%EB%A0%8C%EC%A6%88)
        1. [머신러닝 파이프라인의 이해.pdf](../images\15.02 ai traning\05\머신러닝 파이프라인의 이해_2021215.pdf){:target="_blank"}
1. Share any cool tips 꿀팁 to others !
    1. Found one or more cool tips to make other members can enjoy when study, or to finish their work/job, etc.
    1. You can share any cool tips ! 
    1. Only cool tips related to study or work-life are allowed, not for holiday or SNS 

import

 ```python
 #! pip install pandas
 #! pip install numpy
 #! pip install matplotlib
 #! pip install sklearn
 #!pip install category_encoders
 ```
 
 ```python
 import pandas as pd
 from sklearn.model_selection import train_test_split
 ```
 
 1. 데이터 분할: 데이터를 학습 데이터 세트와 테스트 데이터 세트로 분할
     1. 훈련 세트와 테스트 세트가 무엇인지 사전에 읽으십시오(예: 기능이 무엇인지, 대상 레이블이 무엇인지)
     1. 사전 처리된 데이터 세트를 훈련 세트(80%)와 테스트 세트(20%)로 분할합니다(힌트: train_test_split 사용).
         1. 출력: X_train, X_test, y_train, y_test
 
 
 ```python
 # 데이터 로더 함수 선언
 def data_loader():
     # a. 데이터 세트 로드
     pd_read_csv = pd.read_csv('./titanic-openml_01.csv')
     # b. 데이터 저장
     return pd_read_csv
     
 # 데이터 로더 함수 호출
 dfs = data_loader()
 
 import numpy as np
 
 dfs = dfs.replace('?', np.NaN)
 dfs = dfs.fillna(0)
 dfs
 
 dfs['age'] = dfs['age'].astype(float)
 
 from category_encoders import OneHotEncoder
 
 enc = OneHotEncoder(cols = ['sex', 'pclass', 'embarked'], use_cat_names = True)
 dfs = enc.fit_transform(dfs)
 
 df_x_data = dfs.drop(['survived', 'name', 'homedest', 'ticket', 'cabin', 'boat', 'body'],axis=1)
 df_y_data = dfs['survived']
 
 # 데이터 로드
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
 ```
 
     X_train
          pclass_1.0  pclass_2.0  pclass_3.0  sex_female  sex_male   age  sibsp  \
     832           0           0           1           1         0  43.0      1   
     797           0           0           1           0         1  40.5      0   
     49            1           0           0           0         1  36.0      0   
     867           0           0           1           1         0  22.0      1   
     514           0           1           0           0         1   2.0      1   
     ..          ...         ...         ...         ...       ...   ...    ...   
     337           0           1           0           1         0  19.0      1   
     91            1           0           0           0         1  31.0      1   
     80            1           0           0           0         1   0.0      0   
     703           0           0           1           0         1  21.0      0   
     921           0           0           1           0         1   0.0      0   
     
          parch      fare  embarked_S  embarked_C  embarked_0  embarked_Q  
     832      6   46.9000           1           0           0           0  
     797      0    7.7500           0           0           0           1  
     49       1  512.3292           0           1           0           0  
     867      1   12.2875           1           0           0           0  
     514      1   26.0000           1           0           0           0  
     ..     ...       ...         ...         ...         ...         ...  
     337      0   26.0000           1           0           0           0  
     91       0   57.0000           1           0           0           0  
     80       0   26.5500           1           0           0           0  
     703      0    7.7500           0           0           0           1  
     921      0    7.2500           1           0           0           0  
     
     [800 rows x 13 columns]
     ----------------------------------------------------------
     X_test
          pclass_1.0  pclass_2.0  pclass_3.0  sex_female  sex_male   age  sibsp  \
     25            1           0           0           0         1  25.0      0   
     464           0           1           0           0         1  32.0      0   
     372           0           1           0           0         1  29.0      1   
     730           0           0           1           0         1  27.0      0   
     757           0           0           1           1         0   0.0      1   
     ..          ...         ...         ...         ...       ...   ...    ...   
     278           1           0           0           0         1  32.0      0   
     449           0           1           0           1         0  54.0      1   
     221           1           0           0           0         1  65.0      0   
     741           0           0           1           0         1  22.5      0   
     572           0           1           0           1         0  28.0      0   
     
          parch     fare  embarked_S  embarked_C  embarked_0  embarked_Q  
     25       0  26.0000           0           1           0           0  
     464      0  10.5000           1           0           0           0  
     372      0  26.0000           1           0           0           0  
     730      0   7.8958           1           0           0           0  
     757      0  16.1000           1           0           0           0  
     ..     ...      ...         ...         ...         ...         ...  
     278      0  30.5000           0           1           0           0  
     449      3  23.0000           1           0           0           0  
     221      1  61.9792           0           1           0           0  
     741      0   7.2250           0           1           0           0  
     572      0  12.6500           1           0           0           0  
     
     [200 rows x 13 columns]
     ----------------------------------------------------------
     y_train
     832    0
     797    0
     49     1
     867    1
     514    1
           ..
     337    1
     91     1
     80     0
     703    0
     921    0
     Name: survived, Length: 800, dtype: int64
     ----------------------------------------------------------
     y_test
     25     0
     464    0
     372    0
     730    0
     757    1
           ..
     278    1
     449    1
     221    0
     741    0
     572    1
     Name: survived, Length: 200, dtype: int64
 
 
 2. ML 모델: 분류기 만들기(머신 러닝 모델)
     1. 우리 문제에 대한 간단한 의사 결정 트리 분류기를 만들어 봅시다(힌트: DecisionTreeClassifier 사용)
     1. 의사 결정 트리 분류자 정의(여기 읽기)
 
 
 ```python
 # 모델 학습
 from sklearn.model_selection import train_test_split
 from sklearn.tree import DecisionTreeClassifier
 
 model = DecisionTreeClassifier(random_state=42)
 ```
 
 3. ML 모델: 분류기 학습 및 테스트
     1. 훈련 데이터를 사용하여 분류기를 훈련시키십시오! (힌트: "fit"를 사용)
     1. 테스트 데이터를 사용하여 예측을 생성하여 분류기를 테스트합니다(힌트: "predict" 사용)  출력: 예측 목록(예: y_pred)
     1. y_test와 y_pred 사이의 정확도 점수 표시
 
 
 ```python
 # Train : fit
 model.fit(X_train, y_train)
 
 # Test : predict
 pred = model.predict(X_test)
 
 # accuracy
 from sklearn.metrics import accuracy_score
 print('예측 정확도: {0:.4f}'.format(accuracy_score(y_test,pred)))
 ```
 
     예측 정확도: 0.7400
 
 
 4. ML 모델: 사전 학습된 모델 로드
     1. Teams 폴더에서 사전 훈련된 모델(예: dt_model_220707.pkl)을 찾습니다.
     1. 해당 모델을 Jupyter Hub 디렉터리에 업로드하고 "model" 폴더에 넣습니다(먼저 만드세요!)
     1. 해당 모델을 로드하고 해당 모델을 사용하여 예측 생성
     1. 정확도 점수를 보여주세요! (힌트: Accuracy_score 사용)
 
 
 ```python
 import pickle
 
 # 데이터 로드
 with open('./dt_model_220707.pkl', 'rb') as f:
     data = pickle.load(f)
 
 dt_model_220707_pred = data.predict(X_test)
 
 print('예측 정확도: {0:.4f}'.format(accuracy_score(y_test,dt_model_220707_pred)))
 ```
 
     /opt/conda/lib/python3.9/site-packages/sklearn/base.py:493: FutureWarning: The feature names should match those that were passed during fit. Starting version 1.2, an error will be raised.
     Feature names unseen at fit time:
     - embarked_0
     - embarked_C
     - embarked_Q
     - embarked_S
     - pclass_1.0
     - ...
     Feature names seen at fit time, yet now missing:
     - embarked_enc
     - fare_type
     - pclass
     - status
     - title
     
       warnings.warn(message, FutureWarning)
 
 
 
     ---------------------------------------------------------------------------
 
     ValueError                                Traceback (most recent call last)
 
     /tmp/ipykernel_23/3499993152.py in <module>
           5     data = pickle.load(f)
           6 
     ----> 7 dt_model_220707_pred = data.predict(X_test)
           8 
           9 print('예측 정확도: {0:.4f}'.format(accuracy_score(y_test,dt_model_220707_pred)))
 
 
     /opt/conda/lib/python3.9/site-packages/sklearn/tree/_classes.py in predict(self, X, check_input)
         503         """
         504         check_is_fitted(self)
     --> 505         X = self._validate_X_predict(X, check_input)
         506         proba = self.tree_.predict(X)
         507         n_samples = X.shape[0]
 
 
     /opt/conda/lib/python3.9/site-packages/sklearn/tree/_classes.py in _validate_X_predict(self, X, check_input)
         469         """Validate the training data on predict (probabilities)."""
         470         if check_input:
     --> 471             X = self._validate_data(X, dtype=DTYPE, accept_sparse="csr", reset=False)
         472             if issparse(X) and (
         473                 X.indices.dtype != np.intc or X.indptr.dtype != np.intc
 
 
     /opt/conda/lib/python3.9/site-packages/sklearn/base.py in _validate_data(self, X, y, reset, validate_separately, **check_params)
         598 
         599         if not no_val_X and check_params.get("ensure_2d", True):
     --> 600             self._check_n_features(X, reset=reset)
         601 
         602         return out
 
 
     /opt/conda/lib/python3.9/site-packages/sklearn/base.py in _check_n_features(self, X, reset)
         398 
         399         if n_features != self.n_features_in_:
     --> 400             raise ValueError(
         401                 f"X has {n_features} features, but {self.__class__.__name__} "
         402                 f"is expecting {self.n_features_in_} features as input."
 
 
     ValueError: X has 13 features, but DecisionTreeClassifier is expecting 11 features as input.
 5. 온라인 강의 비디오 시청 및 통찰력 얻기
     1. 강의영상은 다음주 화요일(2022.07.12)까지 시청해주세요
     1. 비디오에서 아이디어나 통찰력 얻기
     1. 비디오에서 흥미로운 부분을 발견했다면 다음 세미나 세션에서 다른 사람들과 공유하십시오.
     1. 링크:
         1. YouTube : 93. 머신러닝 파이프라인의 이해 (Annotation AI 이광희 CTO)
         1. 머신러닝 파이프라인의 이해.pdf
 
 - 주제 : 머신러인 파이프라인의 이해
 - 연사 : Annotation AI 이광희 CTO
 - 주체 : AI프렌즈
 - 내용 : 머신러닝 파워드 애플리케이션 이라는 책과, fullstackdeeplearning.com/spring2021/ 를 정리했다고 함
 
 
 1. 머신러닝 파이프라인
     - 데이터 수집 - 전처리 - 학습 - 예측 까지의 아키텍처
     - 필요성
         - 머신러닝 자동화 : 불필요한 시간 소모 줄이기 위해
         - 예측 정확도 향상
 1. 드림
     - 잘 서비스 하면 되겠지?
 1. 실제
     - 수집 - 전처리 - 클랭징 - 레이블링
     - 디버깅 리소스 등 고민, 실험, 리뷰를 통해 모델 디플로이
     - 문제가 생기는 지 모니터링
     - 개발중에도 문제가 생기기도 함
 1. ML 리서치 개발하는거는 굉장히 작은 비율을 차지하고
     - 나머지 엔지니어링 하는데 더 많은 비용이 들어간다.
 1. 난관
     - 파이프라인이 주먹구구라면 진척도가 느림
     - 지속적 데이터 분포, 퀄리티가 변하기 때문에 업데이트 필요
     - 불필요한 리소스 활용이 증가할 수도 있음
     - 데이터 사이언티스트와 소프트웨어 개발자 간에 업무 공유와 협업이 어려움
 1. MLOps
     - 머신러닝 + 오퍼레이션
     - 모델 개발 + 운영 시스템 효율적으로 하는 것을 목표
     - 지속적 통합, 지속적 배포, 지속적 학습의 요소를 갖추어야 함
 1. 생애주기
     - 프레닝 -> 디플로이 까지의 이야기
     1. 플레닝, 프로젝트 셋업 : 요구사항 및 리소스 판단
     2. 데이터 컬렉션 레이블링 : 학습 데이터 모우고, 어노테이션 하는 과정
     3. 테스팅 & 디버깅 : 소타 등을 참고해서 모델을 만듬, 디버깅, 성능 향상
         - 난이도, 요구사항 조정이 필요하면 과거로 돌아감
     4. 디플로이 : 환경 poliot, 수행, 배포
         - 성능 동작 문제 있으면 3번으로
         - 데이터의 분포차이가 있으면 2번으로
         - user behavior, 성능 등에 문제가 있으면 1번으로
 1. 플레닝, 프로젝트 셋업
     - 우선순위 필요
     - 비즈니스 하이 impact : 가치가 높음
     - High Feasibilty : 데이터 가용성 고려
         - 데이터 가용성 가장 중요 ☆☆☆☆☆
             - 원하는 데이터 셋은 잘 없음
             - 유사한 레이블이 있는게 좋으나, 없으면 레이블링을 하던지, 안하고 하는 방법은 없는지?
             - 데이터 조차 없는 경우도 있음 : 새로 수집
         - 정확도 요구사항
             - 50 ~ 90 까지는 잘 오르는데, 90 ~ 99 까지는 잘 안오름
 1. 초기 모델 설계
     - 머신러닝 사용하지 않고 가능지 고민 << 이게 가장 빠름
     - 여러단계로 나누어 머신러닝
     - end to end 방식으로 모델링
 1. 기계 학습 로스 기반으로 학습을 함
     - 매트릭은 하나로 선택하는게 좋음
     - 매트릭 조합 방법이 여러가지가 있음
 1. 베이스 라인
     - 최소 하한선 이 염격할수록 유용하다
     - 갭이 크면 다른 모델을 선택하던지 해야 됨
     - 일반 사람보다 전문가가 할수록 좋아지나,
     - 전문가 집단이 레이블링 하면 데이터 수집이 어려워짐
 1. 데이터 수집 및 레이블링 옵션
     - 자체 적으로 어노테이터 채용 : 제조업, 데이터가 외부로 나갈 수 없는 상황, 데이터 날리지가 많이 필요한 경우
     - 크라우드 소싱 : 빠르고 싸나, 일관성 보장이 어려움
     - 데이터 구축 서비스 이용
     - 레이블링 소프트웨어 이용
 1. 데이터 버저닝
     - 소스코드만 관리, 데이터 관리 x 한다면 제대로 관리하고 있지 않음.
     - 데이터 버저닝 하는 오픈소스도 존재함
 1. 개발시 만나는 문제, 어떻게 하면 오류를 줄일수 있을지?
     - 수학공식 유도, 테스트, 디버깅, 튜닝하는데 90% 정도 시간을 씀
     - 실제 개발은 10% 정도만 사용
     - 성능 떨어지는 요인
         - 구현 버그
         - 하이퍼 파라미터의 선택이 너무 중요
             - 로우 rate는 너무 오래 걸림
             - 너무 크면 발산하는지 오래걸리는지
             - 언더피팅 되기도 함
         - 데이터와 모델이 잘 맞아야 함
             - 핏이 잘 맞는거도 중요해서, 잘 안맞으면 튜닝이나, 트렌스폼러닝을 해서 개션해야 됨
     - 데이터 셋 이슈
         - 데이터가 확보되지 않음
         - 레이블링이 잘못하는 경우가 많음
         - 정상 데이터가 훨씬 많을수 밖에 없음. 디섹 데이터는 잘 없음 :
             - 수퍼바이저로 풀기 어려움
             - 어너멀라이제이션? 으로 디섹을 찾는다던가 해야 함
         - 트레인 데이터와 테스트 데이터가 다를 경우
     - 문제 해결이 어려운 이유?
         - 디버거가 잘 안되어 있음
         - 제대로 나오고 있는건지 아닌지도 알기 어려움
         - 성능 저하의 원인도 너무 많음
         - 하이퍼파라미터와 데이터 구성에 따라서 학습결과가 다르게 나옴
     - 마인드셋
         - 비관적으로 봐야함 (잘 될거야라고 보기 보다 리스크를 잘 줄여보자로 가야 됨)
         - 아주 간단하게 시작해서 복잡도를 올려가야 함
     - 간단한 모델을 선택해라
     - 검증된 초기 세팅
         - 옵티마이즈 : 아담
         - 러닝 레잇 : 작게
         - 액티베이션 펑션 : 렐루 해보고 안되면, 바꿔보기
         - 초기화 : 히 노말
         - 레규레이제이션, 데이터 노말리제이션 : 처음에는 쓰지 말자
     - 문제를 단순화해야 함
         - 문제를 단순화 해서 모델이 동작이 되도록 하는게 좋음
     - 가장 많이 발생하는 버그
         - Tensor shape 불일치
         - 전처리 관련
         - Loss 평선을 변형할 때 실수
         - 학습 & 평가가 잘못해서 생김
         - 수치적 불안정
     - 조언
         - 간단하게 구현
         - 텐서플로 보다 케라스
         - 병렬처리는 나중에
     - 모델 런 이슈
         - shape 미스 매치
         - casting 이슈
         - 아웃오브 메모리 : 데이터 사이즈 줄여봄
         - 기타 : 스택오버 플로 찾아봄
     - 오버피팅?
         - 오래 걸림 : 러닝 레잇이 너무 큼
         - 발산
         - 언더피팅, 로스펑선, 데이터 오염
     - 모델이 언더피팅, 오버피팅, 최적인지 판단을 해서 개선해야함
     - 오버피팅을 막으려면 데이터가 충분해야 함
     - 모델 개선 방법
         - 언더피팅 없애야함
             1. 모델을 더 크게 만듬
             1. Regulatization을 줄임
             1. 에러 분석 (57:17)
 