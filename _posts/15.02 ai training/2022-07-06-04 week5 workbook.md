---
title: 03 week4 workbook
author: JUNG YoungKyun
date: 2022-06-22
category: 15.02 ai training
layout: post
---

# 5주차 : Python Function
1. 파이썬 함수를 만드는 방법에 대해 알아보십시오.
    1. 함수를 만드는 방법과 사용하는 방법에 대한 기사를 읽으십시오 (출처)
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