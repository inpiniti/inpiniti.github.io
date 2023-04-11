---
title: 02 Celonis Foundations - Transform Data
author: JUNG YoungKyun
date: 2023-03-28
category: 37 celonis
layout: post
---

<div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="dc47834b-9c58-4dbc-8c5b-d4042d7269a9" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# Transform Data

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yea1q1n7f0p3-skill-area_Conceptualize_catalogue.jpg)

Course | 1h 30min

Create transformations using Data Jobs and the Replication Cockpit.

After completing this course, you will be able to:

- Choose the appropriate tool for transformations
- Set up transformations with Data Jobs and the Replication Cockpit
- Build your Activity table and other important tables using transformations
- Accelerate your work with templates
- Troubleshoot your transformations

WHAT'S INCLUDED
- Self-paced learning. Take courses at your own speed.
- Learn when it suits you with round-the-clock access.
- Get enabled fast with laser-focused, goal-based training.

## 1 소개

### 11 학습 목표

데이터 통합의 중심 작업은 프로세스 데이터 모델을 구축하는 것입니다. 이렇게 하려면 먼저 시스템에 연결하고 원시 데이터를 추출한 다음 추출된 데이터를 " 변환 "합니다.

변형이란 다음을 의미합니다.

1. 모든 관련 프로세스 활동으로 하나 이상의 활동 테이블 작성
2. 필요에 따라 사례 테이블 및 기타 관련 마스터 데이터 테이블을 재작업하십시오.

비밀스럽게 들리나요? 걱정하지 마세요. 이 과정을 마치면 기본 사항을 마스터하고 다음을 수행할 수 있습니다.

- 데이터 변환의 의미 설명
- 변환에 적합한 도구 선택
- 데이터 작업 및 Replication Cockpit으로 변환 설정
- 변환을 사용하여 활동 테이블 및 기타 중요한 테이블 작성
- 템플릿으로 작업 가속화
- 변환 문제 해결

시작하자!

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/tfygvkk3e21f-braden-collum-9HI8UJMSdZA-unsplash.jpg)

> Personal Training Environment Required
>
> This course contains hands-on exercises that require a personal EMS Training Environment, also called an "EMS Team".
>  
> Not sure if you have one? Click below and we'll either create one for you or show you how to access your existing Team if you have one. Please make sure to disable adblockers on this page if the button is not working for you.

## 2 변환 개요

### 21 올바른 도구 선택

연결을 설정하고 추출을 설정한 후 다음 단계는 다음 도구 중 하나 이상을 사용하여 데이터를 변환하는 것입니다.

1. 데이터 작업
2. 복제 조종석

`데이터 작업`과 `Replication Cockpit 변환`은 모두 데이터 풀의 데이터 통합 ​​데이터 흐름 다이어그램에 나타납니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cceknn0hm06k-image.png)

추출과 마찬가지로 두 가지 주요 질문에 따라 변환에 사용해야 하는 도구가 결정됩니다.

- 실시간 연결이 가능한가요 ?
- 운영 사용 사례(일상 작업) 에 필요한 데이터입니까 ?

실시간?

연결이 실시간인지 여부는 설정과 특정 시스템에서 가능한지 여부에 따라 다릅니다.

현재 Replication Cockpit은 SAP 시스템, ServiceNow 및 Oracle DB, HANA DB, MSSQL DB와 같은 데이터베이스로 실시간 변환을 처리할 수 있습니다.

도구로 가능한 것은 무엇입니까?

다음은 `데이터 작업(DJ)` 및 `Replication Cockpit(RC)`으로 수행할 수 있는 작업에 대한 개요입니다. 녹색 강조 표시는 운영 사용 사례가 있는 경우 우선 순위를 지정해야 하는 방법을 나타냅니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/1o3betuc74cv-image.png)

이 표의 세 가지 주요 내용은 다음과 같습니다.

- `Replication Cockpit은 `현재 추출 및 변환을 위한 전체 및 `델타 로드를 처리`할 수 있습니다. 운영 사용 사례를 지원하므로 실시간 연결이 가능한 경우 우선 순위를 지정합니다. 즉, 데이터에 거의 실시간으로 작동합니다.
- *데이터 작업 델타 변환은 현재 베타 기능으로만 가능하므로 지금은 이 과정에서 다루지 않습니다. 관심이 있는 경우 이 [도움말 페이지](https://docs.celonis.com/en/delta-transformations-in-data-jobs.html) 를 살펴보십시오.
- 데이터 모델 로드는 데이터 작업에서만 가능합니다(자세한 내용은 "데이터 모델 로드" 과정 참조).

이 과정의 나머지 부분에서는 `데이터 작업` 및 `Replication Cockpit`을 ​​사용하여 변환을 설정하는 방법을 배웁니다. 데이터 작업부터 시작하겠습니다!

## 3 데이터 작업 - 변환 설정

### 31 데이터 모델용 테이블

#### 311 활동 테이블에 대한 검토

활동 테이블이 무엇인지 아십니까? 그렇다면 이 페이지를 건너뛰세요!

데이터 작업으로 원시 데이터를 추출한 후에는 프로세스 마이닝에 사용할 수 있도록 변환해야 합니다. 목표는 프로세스 데이터 모델이 될 수 있도록 데이터를 변환하는 것입니다 . 가장 중요한 작업은 이벤트 로그 라고도 하는 활동 테이블을 만드는 것입니다 . 이 테이블은 프로세스 흐름을 시각화하기 위해 구축하는 데이터 모델의 기초입니다. 그것 없이는 프로세스 마이닝 또는 기타 활동이 불가능합니다. 활동 테이블 구축은 종종 디지털 풋프린트 통합이라고도 합니다.

구체적으로 Transformations에서 수행해야 하는 작업은 다음과 같습니다.

1. 필요한 모든 열이 있는 빈 활동 테이블을 만듭니다 .
2. 소스 시스템에서 추출한 활동 및 활동 시간으로 채우십시오 .

활동 테이블은 프로세스를 나타내며 항상 프로세스를 매핑하는 다음 세 개 이상의 열을 포함합니다 .

- 객체 ID 또는 케이스 키
- 다른 케이스 키에 대해 발생한 프로세스 단계 또는 활동
- 각 활동의 타임스탬프 또는 이벤트 시간

구매-지불 프로세스에서 구매 주문 항목 번호는 우리가 따르는 핵심 케이스 키입니다 .

모든 구매 주문 항목은 요청 생성, 항목 생성, 상품 수령 및 송장 지불과 같은 다양한 활동을 거칩니다 . 그리고 모든 활동에는 해당 이벤트 시간이 있습니다 .

즉, 모든 구매 주문 항목에는 서로 다른 시점 에서 다양한 활동을 수행하는 고유한 케이스 키가 있습니다 . 이 세 열이 함께 프로세스 흐름의 핵심을 구축합니다.

다양한 활동을 진행하는 단순화된 P2P 구매 주문 항목(케이스):

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/guct86ws9jj0-image.png)

중간에 다른 활동이 있는 활동 테이블에 캡처된 동일한 사례:

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yg5jq5qsboix-image.png)

활동 테이블의 또 다른 예: O2C

다음은 활동 테이블이 다양한 테이블의 정보와 함께 제공되는 방법에 대한 또 다른 예를 보여주는 또 다른 그래픽입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/1loqojo152h3-transform.PNG)

#### 312 활동 테이블 확장

일반적으로 활동 표를 다른 열로 확장합니다 . 여기 몇 가지 예가 있어요.

- 사용자 유형

    예를 들어 SAP로 작업하는 경우 '사용자 유형 ' 이라는 열을 추가하여 수동 또는 자동 사용자가 활동을 수행했는지 여부를 나타낼 수 있습니다. 이 정보를 사용하여 자동화 속도를 분석할 수 있습니다.
    
    {SAP에서 수동 사용자는 A로 약칭되며 "대화 사용자"를 나타냅니다. 자동 사용자는 B로 표시되며 '배치' 사용자를 나타냅니다.}

- 정렬

    " 정렬 " 열을 추가할 수도 있습니다 . 활동에 대한 이벤트 시간이 겹치거나 정확하지 않은 경우 추가 정렬이 유용합니다. 예를 들어, 타임스탬프가 정확한 시간이 아닌 각 날짜만 표시하는 경우입니다. 활동의 타임스탬프가 동일한 경우 Celonis는 정렬 열을 사용하여 어떤 활동이 먼저 오는지 결정합니다.

- 활동 키
    
    발생할 수 있는 또 다른 중요한 열은 활동 키 열입니다. 많은 프로세스에서 항목 및 헤더 수준의 프로세스에서 개체를 추적합니다. 예를 들어 주문 현금화 프로세스의 판매 주문 항목 및 판매 주문 또는 구매 결제 프로세스의 구매 주문 항목 및 구매 주문 . 프로세스가 항목 수준을 추적하는 경우 헤드 수준에서 발생하는 활동을 식별하고 계산하는 방법이 필요합니다.
    
    활동 키를 사용하면 헤더 수준 활동에 고유한 키를 부여하고 헤더 개체 내의 모든 항목에 대해 동일한 활동이 발생했음을 알 수 있습니다. 간단히 말해서 판매 주문(헤더)에 배달 블록이 있는 경우 모든 판매 주문 항목에 동일한 활동 및 활동 키가 할당됩니다. 이를 통해 이 활동이 판매 주문(헤더) 수준에서 한 번 발생했음을 알 수 있습니다.

- 다른 예

    루프 활동을 식별 하고 이를 추적하기 위해 루프에 추가 열을 추가할 수도 있습니다 . 또는 변경 활동 중에 발생하는 정확한 값 변경을 추적할 수 있습니다 . 이렇게 하려면 " change from " 및 " change to " 열을 추가합니다 .
    
요약하면 `활동 테이블에는 항상 케이스 키, 활동 및 이벤트 시간 열이 포함`됩니다 . 거기에서 일반적으로 나중에 프로세스 분석을 지원하고 강화할 특정 활동 정보가 있는 추가 열을 추가합니다. 활동 테이블의 최종 열 목록은 현재 진행 중인 프로세스 와 다운스트림 분석 및 실행에 필요한 정보에 따라 달라집니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dtijslxfe955-image.png)

#### 313 관련된 다른 테이블은 무엇입니까?

`활동 테이블을 사용`하여 `프로세스를 분석`한다고 상상해 보십시오. 문제의 근본 원인을 발견하고 통찰력을 얻는 데 충분합니까? 아마 아닐 겁니다. 다음은 일반적으로 맨 위에 필요한 것입니다.

|||
|---|---|
|케이스 테이블|활동 테이블 외에 또 다른 중요한 테이블은 CASE 테이블입니다.|
| |일반적으로 IT 소스 시스템에서 프로세스를 통해 수행하는 CASE에 대한 보다 구체적인 정보가 포함된 하나의 테이블을 찾을 수 있습니다. 이것은 Case 테이블입니다.|
| |P2P 예에서 이것은 단일 구매 주문 항목 에 대한 자세한 정보를 포함하는 "EKPO" 테이블입니다 . 예를 들어 O2C(Order-to-Cash) 프로세스에서는 `판매 주문 항목`이 됩니다 .|
|마스터 데이터 테이블|활동 및 사례 테이블 위에 프로세스 데이터 모델에 마스터 데이터 정보도 추가합니다.|
| |P2P의 좋은 예는 공급업체에 대한 자세한 정보가 포함된 LFA1 테이블입니다 . 데이터 모델에 연결된 이 테이블을 사용하면 나중에 분석에서 공급업체를 쉽게 필터링할 수 있습니다.|

즉, 일반적으로 다음을 사용하여 활동 테이블을 보강합니다.

- 케이스 테이블 및
- 나중에 프로세스 분석 및 실행을 지원할 마스터 또는 트랜잭션 데이터 테이블.

데이터 모델에서 이러한 모든 테이블은 `외래 키를 사용하여 서로 연결`됩니다 .

P2P(Purchase-to-Pay) 프로세스를 상기하면서 공급업체(LFA1), 구매 주문(EKKO) 및 구매 주문 항목(EKPO: 사례 테이블)에 대한 정보를 추가하여 적절한 기반을 마련할 것입니다. 프런트엔드에서 분석. 미래를 내다보면 다음과 같은 아름다운 데이터 모델을 구축하게 됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8ygnstw9879e-image.png)

#### 314 데이터 모델에 대한 테이블 요약

요약하자면 데이터 통합의 `중심 작업`은 `프로세스 데이터 모델을 구축`하는 것입니다. 이렇게 하려면 `추출된 데이터를 "변환"합`니다. 변형이란 다음을 의미합니다.

1. 모든 관련 프로세스 활동으로 `하나 이상의 활동 테이블 작성`
2. 필요에 따라 사례 테이블 및 기타 관련 `마스터 데이터 테이블을 재작업`하십시오.

분석 또는 보기로 빨리 감기

변환을 통해 구축한 내용은 데이터 모델을 로드한 후 나중에 분석 및 기타 Celonis 서비스에 반영됩니다.

예: 프로세스 탐색기는 활동 테이블의 활동을 보여줍니다. 활동의 순서와 번호는 사례 ID, 타임스탬프 및 정렬 열을 사용하여 계산됩니다

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/c1o20sdq6zfb-image.png)

예: 변환에서 만들고 데이터 모델에 추가하는 사례 테이블 및 기타 테이블은 분석에서 필터링 옵션 및 KPI 작업을 지원하는 데 사용할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/fbncgihs4ofc-image.png)

흥분한? 다음으로 데이터 작업 변환부터 시작하여 활동 테이블을 생성해 보겠습니다.

### 32 활동 테이블 작성 및 확장

#### 321 Vertica SQL에 대한 참고 사항

여기서 변환 작업을 수행하기 전에 알아야 할 사항이 있습니다.

Celonis 변환 편집기(SQL Workbench)는 `PostgreSQL과 매우 유사한` Vertica SQL 구문을 사용합니다.

계속해서 무슨 일이 일어나고 있는지 완전히 이해하려면 SQL에 대한 기본 지식이 있는지 확인하십시오. 보다 정확하게는 최소한 다음 SQL 문/함수 의 기본 범주에 익숙해지는 것이 좋습니다 .

- 기초
    - 테이블 생성 / 뷰 생성
    - 드롭 테이블 / 드롭 보기
    - 선택하다
    - 에서
    - 어디
    - 존재하는 곳
    - 그룹화 기준
    - 주문
    - 가입하다
    - 에 집어 넣다
    - 세다
    - 경우
    - 깁스
    - ||
- 중급	
    - UNION ALL
    - LTRIM
    - ISNULL
    - DELETE
    - ROW NUMBER () OVER
    - PARTITION BY
    - COALESCE

길을 따라 배울 수 있습니다! 자세한 내용이 필요하거나 수행 방법을 확인하려면 언제든지 [Vertica SQL 참조 설명서](https://www.vertica.com/docs/10.1.x/HTML/Content/Authoring/SQLReferenceManual/SQLReferenceManual.htm?tocpath=SQL%20Reference%20Manual%7C_____0) 를 참조하거나 좀 더 사용자 친화적인 이 [PostgreSQL 설명서](https://www.postgresql.org/docs/14/queries.html) 를 참조 할 수 있습니다. PostgreSQL 구문은 Vertica와 최소한의 차이만 있으며 더 쉬운 시작점입니다.

참고로 Celonis SQL 편집기는 이러한 [Vertica](https://docs.celonis.com/en/supported-vertica-functions.html) 기능 만 지원합니다 .

#### 322 SQL 편집기 살펴보기
#### 323 활동 테이블 만들기
#### 324 사용해 보세요 - 활동 테이블 만들기

활동 테이블을 만들 차례입니다. 여기서는 "시스템에 연결" 및 "데이터 추출" 과정을 거쳐 연결 및 추출이 포함된 데이터 작업을 설정했다고 가정합니다.

평소와 같이 [개인 교육 환경](https://dam.celonis.com/download/en/3fxjBOrZkDrlGbDRxIOrom) 에서 작업을 계속하십시오

단계

1. `P2P 데이터 작업으로 이동`하여 "`테이블 만들기: 활동 테이블"이라는 새 변환`을 만듭니다. 템플릿을 사용하지 마십시오.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/aabsvb9z0tfk-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rcwbxpgpquas-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/zcvdn4xv4ccb-image.png)

2. 이 스크립트를 변환에 붙여넣고 실행합니다

    ```
    DROP TABLE IF EXISTS _CEL_P2P_ACTIVITIES;
    CREATE TABLE _CEL_P2P_ACTIVITIES (
          _CASE_KEY VARCHAR(100)
        , _ACTIVITY_EN VARCHAR(300)
        , _EVENTTIME TIMESTAMP
        , _SORTING INT
    );
    ```
   
   ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9rxekx92n9pm-image.png)
   
3. 출력에 "영향을 받는 행 0개"가 표시되더라도 걱정하지 마십시오. 방금 빈 테이블을 만들었으므로 이는 정상입니다. 실행되면 변환을 저장합니다.

결과

이제 스키마를 다시 로드한 후 스키마 탐색기에 새 활동 테이블과 해당 열이 표시되어야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8azglp9mehdz-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9zcwmtavy6c1-image.png)

#### 325 활동 테이블에 활동 추가 - 단계

다음은 활동 테이블에 활동을 추가하는 기본 사항을 보여주는 비디오입니다. "구매 요청 항목 만들기" 프로세스 활동을 예로 사용합니다.

즉, Activity Table에 활동을 추가하려면 스크립트를 작성합니다.

1. INSERT INTO () - 삽입할 테이블/열
2. SELECT - 삽입할 데이터
3. FROM / JOIN - 데이터를 가져오는 곳
4. WHERE - 어떤 필터로

이제 스크립트에 대해 가질 수 있는 질문에 대해 자세히 살펴보겠습니다.

#### 326 활동 테이블에 활동 추가 - 일반적인 질문

활동 테이블에 추가할 첫 번째 활동에 대한 전체 스크립트는 다음과 같습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/2xafc34ojy1o-image.png)

즉, Activity Table에 활동을 추가하려면 스크립트를 작성합니다.

1. 삽입할 테이블/열 (INSERT INTO)
2. 삽입하는 데이터 (SELECT)
2. 데이터를 가져오는 곳 (FROM/JOIN)
3. 어떤 필터로 (WHERE)

이 스크립트에서 가장 일반적으로 제기되는 질문을 살펴보겠습니다.

- 그게 왜 케이스 키인가요? (_CASE_KEY)

    여기서 Case Key는 EKPO의 기본 키(MANDT, EBELN, EBELP)를 연결한 것입니다. 여기에서 찾아볼 수 있습니다 . SQL에서는 "||"를 사용하여 값을 연결할 수 있습니다. `기본 키를 연결하면 모든 항목이 고유하고 제대로 추적`됩니다.

    EKPO는 `구매 주문 항목 테이블`이며 P2P 프로세스에서 추적하는 사례입니다.

    EBAN의 기본 키가 아닌 이유는 무엇입니까?
    
    구매 요청 항목이 아니라 P2P 프로세스 전체에서 구매 주문 항목을 추적하기 때문에 위의 변환에 EBAN의 기본 키(EBAN은 구매 요청 테이블임)를 사용하지 않습니다. P2P 프로세스의 첫 번째 활동은 구매 요청 생성입니다.

- EBAN.BADAT가 타임스탬프인 이유는 무엇입니까? (_EVENTTIME

    "구매 요청 주문 생성" 활동을 진행 중이므로 `생성 날짜를 정확하게 나타내는 열`이 필요합니다.
    
    열은 EBAN(구매 요청 항목 테이블)의 BADAT이며 테이블에 대한 자세한 내용은 여기 .

- 왜 10을 정렬해야 합니까?

    숫자 10은 임의의 숫자이며 현재 중요한 역할을 하지 않습니다. 나중에 더 많은 활동을 추가할 때 다른 활동에 대한 이벤트 시간이 동일한 경우 더 중요해지고 두 번째 정렬 기준을 제공합니다 . 예를 들어 정확한 `시간이 없고 날짜만 있는 경우 정렬 번호가 활동을 올바른 순서로 정렬`하는 데 도움이 됩니다.

- EKKO 조인이란 무엇입니까?

    이미 배운 것처럼 `두 개의 중앙 구매 테이블` "EKPO" 및 "EKKO":
    
    - "EKPO"에는 `구매 주문 항목 자체에 대한 정보`가 포함되어 있습니다.
    - "EKKO"는 해당 `구매 주문 헤더 에 대한 정보`를 포함합니다 .
    
    그렇다면 "EKPO" 외에 "EKKO"가 필요한 이유는 무엇입니까?
    
    결과적으로 두 테이블 모두 견적 및 일정 라인 계약과 같은 P2P 프로세스 범위 외부의 행을 포함합니다. 일반 구매 주문으로 정보를 제한하려면 EKKO에서 문서 범주 "F"를 필터링해야 합니다.
    
    구체적으로 말하자면 EKPO에서 가져와서 EKKO에 결합하여 실제 구매 주문 항목과 관련된 행만 필터링한다는 의미입니다.
    
    두 테이블은 클라이언트와 문서 번호라는 두 열을 통해 연결됩니다.
    
    이는 다음과 같이 작동하는 두 가지 "조인 조건"이 있음을 의미합니다.
    
    - 클라이언트 열은 서로 같아야 합니다. "EKPO.MANDT" = "EKKO.MANDT "
    - 문서 번호 열 = "EKPO.EBELN" "EKKO.EBELN"
    
    이 조인을 관심 있는 항목으로 제한하기 위해 구매 주문에 대한 문서 범주 열을 확인합니다. “EKKO.BSTYP” = 'F'.

- EBAN 조인이란 무엇입니까?

    "EBAN" 테이블에는 `구매 요청에 대한 정보가 포함되어 있으`며 여기에서 타임스탬프를 얻을 수 있습니다. 따라서 이 테이블을 기존 조인에 추가해야 합니다.
    
    [여기](https://www.leanx.eu/en/sap/table/ekpo.html) 에서 조인 조건을 조회할 수 있습니다 ("EKPO 외래 키 관계" 검색). 세 개의 열로 제공됩니다.
    
    클라이언트 "MANDT",
    구매 요청 번호 "BANFN"
    구매 요청 "BNFPO"의 항목 번호
    
- EKKO.BSTYP = 'F'가 끝에 있는 WHERE 문에 없는 이유는 무엇입니까?

    그것은 수. 그러나 조인에 포함하는 것이 `더 성능이 좋은 스크립트이므로` 가장 좋은 방법입니다.

- 조인에 1=1이 있는 이유는 무엇입니까?

    이것은 모든 조인 조건이 `정렬되도록 읽기 쉬운 스크립트`를 갖는 것입니다.

요약하자면 활동 테이블을 만든 후에는 `활동(프로세스 단계라고도 함)을 하나씩 추가합`니다. 활동을 추가하려면 사례 키, 활동 이름, 이벤트 시간 및 활동 테이블의 추가 열을 채울 정보가 필요합니다.

SQL 용어로 이것은 다음을 의미합니다.

1. 활동 테이블 및 해당 열을 가리키는 INSERT INTO
2. 활동 테이블 열을 채우기 위해 함께 모이는 열을 나타내는 SELECT
3. FROM / JOIN 및 WHERE 문을 사용하여 SELECT에 대한 모든 관련 테이블을 연결하고 필터링합니다.

상황이 이것보다 더 복잡해지지만 이것은 처음부터 변환을 생성할 때 따르는 기본 논리이며 미리 작성된 변환이 있는 기존 Process Connector로 작업할 때 볼 수 있습니다.

#### 327 사용해 보세요 - 활동 추가

이제 활동 테이블에 활동을 추가할 차례입니다.

단계

1. "활동 추가: `구매 요청 항목 생성"이라는 두 번째 변환`을 만듭니다.

2. 다음 스크립트를 붙여넣고 실행합니다.

    ```
    INSERT INTO _CEL_P2P_ACTIVITIES
    (
          _CASE_KEY
        , _ACTIVITY_EN
        , _EVENTTIME
        , _SORTING
    )
    SELECT
        EKPO.MANDT || EKPO.EBELN || EKPO.EBELP AS _CASE_KEY
        ,'Create Purchase Requisition Item' AS _ACTIVITY_EN
        ,EBAN.BADAT AS _EVENTTIME
        ,10 AS _SORTING
    FROM EKPO
    JOIN EKKO ON 1=1
        AND EKPO.MANDT = EKKO.MANDT
        AND EKPO.EBELN = EKKO.EBELN
        AND EKKO.BSTYP = 'F'
    JOIN EBAN ON 1=1
        AND EKPO.MANDT = EBAN.MANDT
        AND EKPO.BANFN = EBAN.BANFN
        AND EKPO.BNFPO = EBAN.BNFPO
    ;
    ```

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/y4s8reia9fg7-image.png)

3. 변환을 저장하십시오.

결과

출력 패널에는 영향을 받는 136개의 행이 표시되어야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/7bmwr8sondwb-image.png)

이는 데이터 세트에 이 특정 활동을 표시하는 136개의 타임스탬프가 있고 해당 활동에 대한 136개의 행이 활동 테이블에 추가되었음을 의미합니다.

### 33 템플릿 사용

#### 331 템플릿 사용 개요

작업 템플릿은 다`양한 데이터 작업 및 데이터 연결`에서 `추출 및 변환을 재사용`하는 데 사용됩니다. 이 교육의 뒷부분에서 여러 소스 `시스템을 연결하는 모범 사례에 대해 배우게 됩`니다.

지금 회사에 두 번째 소스 시스템이 있다고 상상해 보십시오. 이 시스템에는 이미 연결한 시스템과 동일한 테이블이 있지만 다른 회사 코드에 대한 것입니다. 즉, 시스템은 동일한 데이터 구조를 나타내지만 그 안에 다른 데이터를 저장합니다.

구조가 동일하기 때문에 첫 번째 시스템에 대해 생성된 모든 추출 및 변환 작업을 `잠재적으로 재사용할 수 있습니다`.

템플릿이 들어오는 곳입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/r5bxwbcd228m-image.png)

Marketplace에서 다운로드하는 모든 Process Connector와 함께 제공되는 작업은 템플릿입니다. 데이터 작업에 표시됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/hxmlrod5o6t0-image.png)

그리고 톱니바퀴 아이콘 아래 데이터 흐름 다이어그램의 오른쪽 상단에 있는 데이터 풀에 중앙 집중식으로 저장됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/mrg6oe61kdtc-image.png)

#### 332 템플릿 데모 사용
#### 333 사용해 보기 - 템플릿에서 활동 추가

샘플 P2P 프로세스의 다른 활동을 위해 처음에 Process Connector로 다운로드한 `기존 템플릿을 계속 사용할 수 있습`니다.

단계

1. 새 변환 작업을 생성하고 "`활동 추가: 구매 주문 항목 생성" 템플릿을 선택`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/zigdirqvy1kt-image.png)

2. 그것을 `열고 실행`하십시오

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/aayk149rqkko-image.png)

3. "활동 추가: 가격 변경" 및 "활동 추가: 수량 변경" 작업에 대해 `1단계와 2단계를 반복`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/t3xdmdnjqu4f-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/szef5s4ko1n3-image.png)

결과

이제 `4가지 활동이 있는 활동 테이블이 생겼`습니다. 이것을 데이터 모델에 로드하고(지금은 할 필요 없음) Process Explorer를 확인하면 다음과 같이 표시됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/xy4yhfdyzsp8-image.png)

네 가지 활동이 나타나고 타임스탬프와 정렬 열 덕분에 순서가 명확해졌습니다.

### 34 사례 테이블 및 기타 테이블 추가 및 확장

### 35 변환 문제 해결

### 36 고성능 변환 쓰기

### 37 데이터 작업 변환 요약

## 4 REPLICATION COCKPIT - 변환 설정

### 41 데이터 작업 변환과 실시간 변환

### 42 실시간 변환 작동 방식

### 43 델타 실시간 변환 설정

### 44 Replication Cockpit용 템플릿 및 매개변수

### 45 Replication Cockpit 변환 요약
