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

지금까지 우리는 점점 더 많은 활동을 프로세스에 통합했습니다. P2P 프로세스 흐름의 전체 프로세스 그림을 만들기 위해 계속 그렇게 할 수 있습니다.

그러나 지금은 추가 트랜잭션 및 마스터 데이터 정보로 데이터를 확장하려고 합니다. 즉, "EKPO", "EKKO" 및 "LFA1"과 같은 테이블을 데이터 모델에 추가해 보겠습니다.


원시 데이터 테이블을 직접 추가하지 않는 이유는 무엇입니까?

물론 추출한 원시 데이터 테이블을 데이터 모델에 직접 추가할 수 있습니다. 즉, `Celonis는 데이터 모델에 추가하는 모든 추가 테이블에 대해 새 변환을 생성할 것을 권장`합니다. 새 테이블을 생성하여 다음을 수행할 수 있습니다.

1. 필요한 경우 `원시 데이터 테이블에 추가 열(예: Case Key 열)을 추가`하고
2. `관련 데이터만 데이터 모델에 로드하도록 원시 데이터 테이블을 필터링`합니다 .

테이블을 추가하는 것은 활동 테이블에 활동을 추가하는 것과 비슷합니다.

스크립트 단계(설명, 따를 필요 없음)

1. CREATE TABLE

    "EKPO" 테이블부터 시작하겠습니다. CREATE TABLE 문과 새 테이블의 이름을 사용하여 EKPO에 대한 새 테이블을 생성해 보겠습니다.
    
    ```CREATE TABLE "P2P_EKPO" AS ()```

2. SELECT

    테이블 생성의 다음 단계는 관련 정보를 선택하는 것입니다. 우리의 경우 원시 데이터 테이블 "EKPO"에서 모든 항목을 선택하기만 하면 됩니다. 이를 위해 '별표'를 사용하여 모든 열을 나타낼 수 있습니다. 또한 활동 테이블과 관계를 가질 수 있도록 케이스 키 열을 제공합니다.
    
    ```
    CREATE TABLE "P2P_EKPO" AS (
    
    SELECT
    "EKPO".*,
    "EKPO". "MANDT" || "EKPO"."EBELN" || "EKPO"."EBELP" AS "_CASE_KEY"
    
    )
    ```

3. FROM / JOIN / WHERE

    다음으로 FROM / JOIN 문과 WHERE 문(필요한 경우)을 사용하여 가져올 테이블, 관계(조인) 및 필터를 지정합니다 . 항목을 문서 유형 F로 제한하려면 EKKO에 가입해야 합니다.
    
    ```
    CREATE TABLE "P2P_EKPO" AS (
    
    SELECT
    "EKPO".*,
    "EKPO". "MANDT" || "EKPO"."EBELN" || "EKPO"."EBELP" AS "_CASE_KEY"
    
    FROM EKPO
    JOIN EKKO ON 1=1
    AND EKPO.MANDT = EKKO.MANDT
    AND EKPO.EBELN = EKKO.EBELN
    AND EKKO.BSTYP = 'F'
    
    );
    ```

4. DROP TABLE IF EXISTS

    활동 테이블과 마찬가지로 앞에 DROP TABLE IF EXISTS 문을 추가하는 것이 가장 좋습니다. 이를 통해 변환을 반복적으로 실행할 수 있습니다. 항상 그렇듯이 각 문은 세미콜론으로 끝납니다.
    
    ```
    DROP TABLE IF EXISTS P2P_EKPO;
    
    CREATE TABLE "P2P_EKPO" AS (
    
    SELECT
    "EKPO".*,
    "EKPO". "MANDT" || "EKPO"."EBELN" || "EKPO"."EBELP" AS "_CASE_KEY"
    
    FROM EKPO
    JOIN EKKO ON 1=1
    AND EKPO.MANDT = EKKO.MANDT
    AND EKPO.EBELN = EKKO.EBELN
    AND EKKO.BSTYP = 'F'
    
    );
    ```

이것이 테이블을 구성하는 방법입니다.

1. DROP TABLE IF EXISTS - 상단에 drop table 문을 사용하여 스크립트를 반복 가능하게 만듭니다.
2. CREATE TABLE - 테이블 이름 지정
3. SELECT - 필요한 데이터를 선택합니다.
4. FROM / JOIN / WHERE - 조인 및 필터가 있는 기본 테이블을 나타냅니다.
`전체 변환 스크립트를 사용하여 새 변환을 만들고 그에 따라 이름을 지정`합니다.

그리고 방금 도출한 명령문을 삽입합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8ycn8sbkxgre-image.png)

변환을 실행한 후 스키마를 새로 고치고 `테이블이 올바르게 추가되었는지 확인`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/z2fzo61fxsvg-image.png)

#### 341 사용해 보기 - 사례 테이블 및 기타 테이블 추가

새 "테이블 만들기" 변환을 만들어야 합니다.

- 단계

1. 여기서 템플릿을 계속 사용하겠습니다. EKPO의 경우 새 변환 작업을 생성하고 "테이블 생성: P2P_EKPO" 템플릿을 선택합니다 .

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/nrr5dqr01w6z-image.png)

2. 쿼리를 실행하고 스키마를 다시 로드하여 테이블이 생성되었는지 확인합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sgqsics2zxd9-image.png)

3. 이제 행 수가 정확한지 확인해 보겠습니다. SELECT COUNT(*) FROM P2P_EKPO 문을 사용하여 카운트가 27937인지 확인합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/xzsy7idhkuhq-image.png)

4. 쿼리에서 SELECT COUNT 문을 지우고 돌아가십시오. 템플릿을 변경한 경우 이러한 변경 사항을 저장할지 묻는 메시지가 표시됩니다. 템플릿을 그대로 유지하려면 "삭제하고 그대로 두기"를 선택할 수 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9f0jx418a66g-image.png)

5. 적절한 템플릿을 사용하여 EKKO 테이블 과 LFA1 테이블에 대해 1~4단계를 반복 합니다.
매번 SELECT COUNT(*)를 사용하여 계산하여 확인하십시오.
   
   도움이 되는 몇 가지 추가 힌트:
    a. 변환을 만들 때 템플릿을 선택할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/c14lixbnknq4-image.png)

    b. 이러한 작업 템플릿은 "시스템에 연결" 과정에서 다운로드한 Process Connector에서 가져왔습니다.
    c. 템플릿이 없습니까? 스크립트는 다음과 같습니다.
    
    - P2P_엑코
            
        ```
        DROP TABLE IF EXISTS P2P_EKKO;
        CREATE TABLE P2P_EKKO AS (
        SELECT EKKO.*
        FROM EKKO
        WHERE EKKO.BSTYP = 'F'
        AND EXISTS (
                SELECT * FROM EKPO
                WHERE 1=1
                    AND EKPO.MANDT = EKKO.MANDT
                    AND EKPO.EBELN = EKKO.EBELN
        ));
        ```
        
    - P2P_LFA1
        ```
        DROP TABLE IF EXISTS P2P_LFA1;
        CREATE TABLE P2P_LFA1 AS (
        SELECT LFA1.*
        FROM LFA1
        WHERE EXISTS (
            SELECT * FROM EKKO
            WHERE 1=1
            AND EKKO.BSTYP = 'F'
            AND EKKO.MANDT = LFA1.MANDT
            AND EKKO.LIFNR = LFA1.LIFNR 
            AND EXISTS (
                SELECT * FROM EKPO
                    WHERE 1=1
                    AND EKPO.MANDT = EKKO.MANDT
                    AND EKPO.EBELN = EKKO.EBELN
        )));
        ```

결과

다음은 데이터 작업 및 작업의 모습입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rfj9uhrylsut-image.png)

당신이 본 SQL 스크립트는 압도적일 수 있지만 기본 사항은 항상 동일하게 유지되므로 걱정하지 마십시오.

1. DROP TABLE IF EXISTS - 상단에 drop table 문을 사용하여 스크립트를 반복 가능하게 만듭니다.
2. CREATE TABLE - 테이블 이름 지정
3. SELECT - 필요한 데이터를 선택합니다.
4. FROM / JOIN / WHERE - 조인 및 필터가 있는 기본 테이블을 나타냅니다.

요약하자면 지금까지:

1. 추출된 P2P 원시 데이터
2. 활동 테이블 생성
3. 활동 표에 추가된 활동
4. 케이스 테이블(EKPO) 및 기타 마스터 데이터 테이블 추가

이러한 기본 단계를 통해 이제 데이터 모델의 기반이 마련되었습니다. "데이터 모델 로드" 과정에서는 이 데이터를 선택하여 데이터 모델에 로드합니다.

### 35 변환 문제 해결

새 변환을 생성할 때 항상 수동으로 실행하여 제대로 작동하는지 확인해야 합니다. 이렇게 하면 구문 오류가 있거나 결과에 문제가 있는지 미리 알 수 있습니다. 추출과 마찬가지로 SQL을 스크립팅한 직후에 테스트하면 나중에 전체 데이터 작업을 실행할 때 오류를 방지하는 데 도움이 됩니다. 다음은 주의해야 할 몇 가지 간단한 일반적인 오류입니다.

- 세미콜론이 추가되었습니까? : DROP TABLE 또는 독립 쿼리 뒤에 세미콜론이 없으면 스크립트가 실행되지 않습니다.
- 올바른 따옴표를 사용하고 있습니까? : 때때로 언어나 키보드에서 "A" 곧은 문자 대신 "A" 또는 «A»와 같은 다른 유형의 인용 부호를 입력할 수 있습니다. 이로 인해 오류가 발생합니다.
- 밑줄 누락 또는 추가?: 특히 템플릿 없이 스크립팅할 때 활동 테이블 열 중 하나에 밑줄을 추가하는 것을 잊을 수 있습니다.
- 여분의 라인(반환) 공간?: 믿거나 말거나, 여분의 빈 라인으로 인해 실행 시 오류가 발생할 수 있습니다. 오류가 명확하지 않거나 단순히 빈 따옴표 ""를 나타내는 경우 어딘가에 빈 줄이 있을 수 있습니다.
- 테이블/열의 철자가 틀렸습니까?: 스크립트가 실행 중이 아닐 때 포착하기 어려운 경우가 있습니다. 즉, 로그의 오류 또는 스크립트를 수동으로 실행할 때 일반적으로 오류가 발생한 행이나 테이블 또는 열이 존재하지 않음을 알려줍니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/zcxxtdikwxv2-image.png)

### 36 고성능 변환 쓰기

#### 361 성능 변환 기본사항

간단히 말해 스크립트를 `작성하는 방식이 성능에 영향을 미칩`니다. 변환 작업의 성능 향상은 EMS SQL 변환 향상 과정에서 다루는 중요하고 큰 주제입니다. 지금은 다음 기본 사항을 고려하십시오.

- 가능한 경우 SELECT *를 피하고 시스템 부하를 줄이는 데 `필요한 열만 선택`합니다.
- SELECT DISTINCT는 과세 문이므로 가능하면 피하십시오. DISTINCT가 필요하다는 것은 일반적으로 쿼리 또는 소스 시스템 `데이터에서 중복이 발생하고 있음을 의미`합니다. 대안에 대한 자세한 내용은 SQL 모범 사례 과정에서 확인하세요.
- 가능한 경우 `조건을 추출로 이동`합니다 . 예를 들어 간단한 사용 사례에서 EKKO.BSTYP = "F"는 EKKO 테이블 추출로 이동할 수 있습니다.
- WHERE 조건을 `JOINS로 직접 이동`합니다. 이것은 EKKO.BSTYP = 'F'로 한 것입니다. 스크립트 끝에 WHERE 문을 사용하여 적용할 수 있었지만 JOIN에 직접 추가했습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/xuk0166yo4ew-image.png)

- 가능한 경우 JOIN 대신 `WHERE EXISTS를 사용`하십시오 . 다른 테이블에서만 필터링해야 하는 경우에는 JOIN을 사용하지 마십시오. 이것은 P2P_EKPO 테이블을 생성할 때 하지 않은 것입니다. 결과는 동일하지만 WHERE EXISTS가 더 효율적입니다. 다음은 측면 비교입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8804vowfgv7u-image.png)

이러한 사항 중 일부가 혼란스러워 보이더라도 걱정하지 마십시오. [EMS SQL 변환 향상 과정](https://academy.celonis.com/courses/sql-best-practices) 에서 이 주제에 대해 자세히 알아볼 수 있습니다 . 시간이 지남에 따라 변환을 읽고 올바른 선택을 할 수 있습니다.

#### 362 변환의 테이블 결과 보기

Marketplace에서 Process Connectors로 작업을 시작하면 변환에서 테이블과 보기를 모두 보게 됩니다. 차이점을 살펴보겠습니다.

||||
|---|---|---|
| |	테이블|	견해|
|정의|	Vertica에서 테이블은 관련 데이터 항목의 모음 이며 열과 행으로 구성됩니다.|	뷰는 하나 이상의 SELECT 문을 캡슐화하는 저장된 쿼리입니다. 뷰는 실행 시 데이터베이스의 데이터에 동적으로 액세스하고 데이터를 계산합니다.|
|사용 사례|	생성한 항목 에 변환에서 액세스해야 하는 경우 테이블을 사용하는 것이 더 빠릅니다. 테이블을 사용하면 계산이 한 번 완료되고 나중에 테이블에 액세스할 수 있기 때문입니다.|	보기를 사용하는 경우 액세스하려고 할 때마다 결과를 새로 계산합니다 . 변환에서 액세스할 수 없는 항목을 생성하려는 경우 참조일 뿐이므로 보기를 사용하는 것이 더 빠릅니다.|
|예|	P2P 예에서는 모든 활동 추가 변환에서 EKPO 및 EKKO 테이블을 조인합니다. 이 조인을 테이블로 저장하면 시스템에서 반복적인 계산을 많이 줄일 수 있습니다 . 대부분의 경우 이러한 종류의 재사용 테이블은 임시 테이블로 표시됩니다(예: CREATE TABLE TMP_P2P_EKPO_EKKO).|	P2P 예에서 P2P_EKPO, P2P_EKKO 및 P2P_LFA1 테이블은 다른 변환에서 사용되지 않고 데이터 모델에만 필요하므로 보기가 될 수 있습니다.|

### 37 데이터 작업 변환 요약

1. 3개의 기본 열 (케이스 키, 활동 및 타임스탬프)과 기타 선택적 열이 있는 `활동 테이블을 생성`하려면
2. 이 패턴을 사용하여 활동 테이블에 활동을 추가하려면 다음을 수행하십시오.
    - INSERT INTO () - 삽입할 테이블/열
    - SELECT - 삽입할 데이터
    - FROM / JOIN - 데이터를 가져오는 곳
    - WHERE - 어떤 필터로
3. Case Table 및 기타 마스터 데이터 테이블과 같은 `추가 테이블을 생성`하려면
    - DROP TABLE IF EXISTS - 상단에 drop table 문을 사용하여 스크립트를 반복 가능하게 만듭니다.
    - CREATE TABLE - 테이블 이름 지정
    - SELECT - 필요한 데이터를 선택합니다.
    - FROM / JOIN / WHERE - 조인 및 필터가 있는 기본 테이블을 나타냅니다.
    
위의 세 단계는 프로세스가 아무리 복잡하더라도 모든 데이터 파이프라인에 적용됩니다.

또한 다음을 배웠습니다.

- 필수 `Vertical SQL 문을 사용`하려면
- `템플릿을 사용`하여 작업을 가속화하고 확장하려면
- 가장 일반적인 구문 오류에 대한 `변환 문제를 해결`하려면
- 변환에서 깨끗하고 성능이 뛰어난 SQL 스크립트를 목표로 합니다 .

## 4 REPLICATION COCKPIT - 변환 설정

### 41 데이터 작업 변환과 실시간 변환

#### 411 데이터 작업 대 복제 조종석 변환

배치 변환이라고도 하는 `데이터 작업 변환을 사용하면 실행할 때마다 테이블이 삭제되고 처음부터 다시 생성`됩니다. 즉, `일괄 변환은` 델타 추출만 수행한 경우에도 Celonis에서 `사용 가능한 전체 데이터를 처리`합니다.*

반대로 `실시간 변환은 마지막 실행 이후 변경된 데이터만 고려`합니다 . 새롭거나 변경된 항목(델타)은 기존 테이블 레코드에 삽입되거나 병합됩니다. 차이점을 더 잘 이해하려면 그래픽을 살펴보십시오.

데이터 작업 변환:

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qggq5gmhqjst-image.png)

실시간 변환

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/f42j925irfmc-image.png)

#### 412 Replication Cockpit을 ​​사용해야 하는 경우

- 소스 시스템이 `실시간으로 활성화`되어 있습니까?
- 테이블이 트랜잭션 테이블입니까 아니면 메타데이터 테이블입니까?

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/5bi8oybw4trq-image.png)

### 42 실시간 변환 작동 방식

#### 421 개요

#### 422 트리거 테이블

새 레코드가 특정 테이블로 `추출될 때마다 실시간 변환이 발생`합니다. 
즉, 추출이 `변환을 트리거`해야 하는 테이블에 각 `변환 문을 매핑`해야 합니다. 
이 테이블을 트리거 테이블이라고 합니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/q5dauwe4keee-image.png)

CDHDR은 `강조 표시`된 변환의 트리거 테이블입니다. 복제 또는 초기화를 통한 CDHDR의 업데이트는 변환 문의 실행을 트리거합니다.

#### 423 스테이징 테이블

그렇다면 델타 레코드는 어떻게 식별되어 새 추출에 보관됩니까? 간단히 말해서 " 스테이징 테이블 "을 사용합니다.

스테이징 테이블은 실시간 변환을 실행할 수 있는 `중간 테이블`입니다. 
여기에는 마지막 추출 이후에 변경된 레코드의 `특정 하위 집합 만 포함`됩니다 . 
Replication Cockpit에서 추출된 모든 테이블에 대해 
"생성 및 업데이트된 테이블"과 "삭제된 테이블"이라는 두 개의 별도 스테이징 테이블이 있습니다. 
아이디어는 변환이 완전히 추출된 테이블 대신 스테이징 테이블에서 선택한다는 것입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/kyvym1yaph95-image.png)

전체적인 흐름은 다음과 같습니다.

1. `추출`이 시작되었습니다
2. 추출이 완료되었습니다.
3. 델타가 `스테이징 테이블에 삽입`됨
4. `변신`이 시작되다
5. 변신 완료
6. 스테이징 테이블이 `지워졌`습니다.

스테이징 테이블의 구문

스테이징 테이블에는 간단한 구문이 있습니다. 
예를 들어 변환이 트리거 테이블 EKPO를 가져오는 경우 스테이징 테이블의 이름은 `_CELONIS_TMP_`EKPO`_TRANSFORM_DATA` 입니다.

#### 424 종속성

그러나 변환이 `여러 테이블에 의존`하는 경우 어떻게 됩니까? 
상상할 수 있듯이 변환이 가져온 테이블이 서로 다른 시간에 업데이트된 경우 변환을 실행할 수 없습니다 .

따라서 변환이 실행될 때 최신 상태여야 하는 변환에서 참조되는 테이블인 종속 테이블을 고려해야 합니다 . 
`종속 테이블은` 일반적으로 `EXIST 문에서 내부 조인되거`나 사용되는 모든 테이블입니다.

"변환 구성" 아래의 "복제 종속성"에서 찾을 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/q9m1ty8zafsx-image.png)

`종속 테이블은` 변환이 트리거될 때 항상 최신 상태이므로 `트리거 테이블(위 그래픽의 CDHDR)이 아닙`니다. 간단한 예를 살펴보겠습니다.

예

- CDHDR(문서 헤더 변경) 테이블에 의해 변환이 트리거됩니다.
- 변환에서 CDPOS(문서 항목 변경) 테이블도 참조합니다.
- CDHDR과 CDPOS가 "`동기화"되었는지 확인해야 합니`다.

    => CDHDR 테이블에 대한 CDPOS에 대한 종속성을 정의합니다. Replication Cockpit은 백그라운드에서 이 동기화를 자동으로 처리합니다.

더 자세히 작동하는 방법

- CDPOS의 마지막 추출 날짜: 00:00:20
- CDHDR의 마지막 추출 날짜: 00:00:30

    => 최소 마지막 추출 날짜: 00:00:20
    => `스테이징 테이블에서 최소 추출 날짜(00:00:20) 이전 레코드만 처리`
    => 이후 레코드(00:00:20에서 00:00:30 사이)는 종속 테이블(CDPOS)이 다시 추출되는 즉시 처리됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0leah52b7e9z-image.png)

#### 425 변환 초기화

Replication Cockpit에서 초기화 스크립트를 사용하여 데이터 모델 테이블과 활동 테이블을 생성합니다. 
생성된 테이블은 전체 변환 및 진행 중인 델타 변환의 기초 역할을 합니다.
 범위 설정 -> 초기화 스크립트 아래에서 스크립트를 찾을 수 있습니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/49t4hoi04wy2-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ad40loq70245-image.png)

`초기화 스크립트는 자동 전체 로드가 아닙`니다.

초기화를 실행할 때 세 가지 옵션이 있습니다.

1. 전체 추출을 실행할 `원시 테이블`
2. 전체 변환을 실행할 `트리거 테이블`(추출된 테이블)
3. 필요한 관련 테이블을 생성하기 위해 `실행할 초기화 스크립트`

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dzluwe2yn9ou-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/taajgt1egoxl-image.png)

이해해야 할 중요한 점은 `초기화 스크립트가 빈 테이블을 생성해야 한다는 것`입니다. 초기화 스크립트에 "`LIMIT 0`"을 추가하면 생성된 테이블이 비어 있는지 확인할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/vz0ysi42cqwp-image.png)

`전체 변환 로드의 경우 트리거 테이블에 연결된 변환에 의존`합니다. 델타 레코드에 의존하는 대신 추출된 모든 레코드를 사용하여 실행됩니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/kw5x5qx6l0aa-image.png)

변환 초기화 예약

변환 테이블에서 시간이 지남에 따라 `발생할 수 있는 문제`(예: 메타데이터 변경, 삭제)를 수정하고 백업하려면 범위 설정 -> 초기화 변환 예약에서 `변환 초기화 의 정기적인 실행을 예약할 수 있`습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9rbancz7upyo-image.png)

### 43 델타 실시간 변환 설정

#### 431 실시간 변환 설정

높은 수준에서 각각의 실시간 변환을 설정하는 세 가지 간단한 단계가 있습니다.

1. `트리거 테이블 식별`
2. 이 트리거 테이블에서 `변환 정의`
3. `종속 테이블 정의`

#### 432 실시간 변환 스크립트 - 데이터 모델 테이블

#### 433 실시간 변환 스크립트 - 데이터 모델 테이블

데이터 모델 테이블(즉, 활동 테이블과 별개로 데이터 모델의 일부인 모든 테이블)에 대한 `실시간 변환을 정의하는 단계의 개요`입니다. 
이러한 단계는 데이터 작업 변환 스크립트를 실시간 `델타 변환 스크립트에 적용하는 방법`입니다.

여기서 키워드는 `델타`입니다. 델타는 `실시간 변환`이 `데이터 작업 변환`과 다른 이유입니다. O2C 프로세스의 테이블 KNA1을 사용하여 이러한 단계를 살펴보겠습니다.


1. 스테이징 테이블 선택

    일반 데이터 작업 변환과의 첫 번째 차이점은 `준비 테이블에만 변환을 적용`한다는 것입니다.
     Replication Cockpit을 ​​사용하여 델타 추출 후 델타 레코드가 저장되는 곳입니다.
    준비 테이블의 구문은 _CELONIS_TMP_{TABLE}_TRANSFORM_DATA 입니다 . → KNA1 의 경우 
    _CELONIS_TMP_KNA1_TRANSFORM_DATA 입니다.
    
    시각적으로 여기에 스크립트의 첫 번째 변경 사항이 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/165hj5wrdga3-image.png)
    
2. 뷰 대신 테이블 사용

    어떤 견해인지 기억하십니까? 액세스할 때마다 실행되는 저장된 쿼리입니다.
    델타 변환으로 레코드를 추가/업데이트/삭제해야 하고 뷰는 레코드를 저장하지 않으므로 `뷰에서는 이러한 변경이 불가능`합니다. 
    따라서 뷰를 `테이블로 변경`해야 합니다. 
    다음은 스크립트의 변경 사항입니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/wgb06soolv97-image.png)
    
    참고 - 이는 실시간 변환이 아니라 데이터 작업 또는 Replication Cockpit 초기화에서 발생합니다. 
    `실시간 변환에서는 테이블이 생성되지 않`습니다. 
    3단계(DELETE & INSERT)를 읽으면 이해가 될 것입니다.
    
    이 코드를 사용하면 기존 뷰를 기반으로 직접 테이블을 만들 수 있습니다.
    
    ```
    CREATE TABLE O2C_KNA1 AS SELECT * from O2C_KNA1
   ```

3. 삭제 + 삽입 방식으로 변경

   데이터 작업 변환을 사용하면 실행될 때마다 모든 것이 잘리고 다시 생성됩니다. 
   델타 변환을 사용하여 기존 세트에 새 레코드를 점진적으로 추가 하려고 합니다 .
   따라서 중복을 피하기 위해 `기본 키가 동일한 항목을 삭제`한 후 스테이징 테이블에서 `새 값을 삽입`합니다 . 
   삭제를 위해 DROP TABLE 문을 `DELETE FROM 및 WHERE EXISTS` 문으로 바꿉니다. 
   삽입의 경우 CREATE TABLE 문을 `INSERT INTO`로 바꿉니다.
   
   ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/oyi6rwike5ru-image.png)

4. 임시 테이블을 쿼리로 이동하거나 트리거된 임시 테이블 사용

    델타 변환을 사용하면 여러 다른 변환(다른 트리거 테이블 포함)에 사용되는 임시 테이블을 더 이상 사용할 수 없습니다. 
    대신 `임시 테이블은` 변환에 직접 `하위 쿼리로 구현되거나` 트리거 테이블에만 연결된 "`트리거된 임시 테이블"을 생성`합니다.
    
    트리거된 임시 테이블
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rw9iv54dkcua-image.png)
    
    여기서 임시 테이블은 `다른 실시간 변환이 실행되기 전에 생성`됩니다. VBAP 테이블의 복제(델타 추출)에 의해 트리거됩니다.
    
    변환 중인 직접 하위 쿼리
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sycp5yp65waj-image.png)
    
5. 모든 열을 구체적으로 선택하십시오.

    모든 열이 참조되는 경우(예: KNA.* ) 원본 테이블의 메타데이터 변경으로 인해 `변환이 중단될 수 있습`니다 .
    
    소스 시스템에 메타데이터가 변경되는 즉시 오류를 방지하려면 
    현재 데이터 모델 테이블 (이 경우 O2C_KNA1)의 `모든 열을 구체적으로 참조하는 것이 좋습`니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sekd3x0yv0fu-image.png)
    
이러한 단계는 처음에는 약간 압도적일 수 있습니다. 
여기서 중요한 것은 `이러한 차이의 이유`와 `실시간 변환의 논리를 이해`하는 것입니다.

#### 434 실시간 변환 스크립트 - 활동 추가
#### 435 실시간 변환 스크립트 - 활동 추가

`활동에 대한 실시간 변환`을 설정하는 방법(예: "활동 추가: {name_of_activity}" 변환)은 약간 다릅니다. 
이는 이러한 변환이 여러 소스의 데이터를 결합 및 변환 하고 기본 SQL 스크립트가 데이터 모델 테이블과 상당히 다르기 때문입니다.
다시 키워드는 Delta 입니다 . 델타 레코드로 작업하기 때문에 데이터 작업 변환과의 차이점이 있습니다.

다음은 이 경우 변환을 준비하고 스크립팅하는 단계의 개요입니다.

#### 436 실시간 변환 설정에 대한 요약

1. 트리거 테이블 식별

    각 활동은 추출이 해당 변환 문을 트리거하는 `트리거 테이블에 매핑`되어야 합니다.
    
    대부분의 경우 트리거 테이블은 `이벤트 타임스탬프 또는 해당 헤더/항목 테이블을 포함하는 테이블`입니다 .
    
    `활동을 생성`하려면 각 트리거 테이블의 `스테이징 테이블에서 선택 해야 합`니다 .
    
    예를 들어 트리거가 VBFA 인 경우 _CELONIS_TMP_VBFA_TRANSFORM_DATA를 사용합니다.

2. 트리거 테이블을 기반으로 `활동 테이블을 여러 개로 분할`

    델타 변환을 사용하면 더 이상 하나의 큰 활동 테이블을 가질 수 없습니다. 
    여러 트리거 테이블이 동시에 활동 테이블에 쓰기를 시도하면 테이블 잠금 및 변환 실패로 이어질 수 있기 때문입니다.
    
    이를 방지하려면 각 트리거 테이블에 자체 전용 활동 테이블이 있어야 합니다. 
    예를 들어 트리거가 CDHDR 인 경우 해당 활동 테이블은 `_CEL_O2C_`CDHDR`_ACTIVITIES`일 수 있습니다.
    
    별도의 활동 테이블은 데이터 작업을 사용하여 다음을 수행해야 함을 의미합니다.
    
    1. 각 활동 테이블 생성
    
        ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/gcounl6na3qv-image.png)
        
    2. UNION ALL 문을 사용하여 뷰에서 테이블을 함께 가져옵니다. 
    이 뷰는 데이터 모델에서 참조될 때마다 계산되므로 한 번만 생성하면 됩니다
    
        ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6zlkkqzq62db-image.png)

3. 대부분의 경우 INSERT + WHERE NOT EXISTS 사용

    활동의 경우 델타 변환을 수행하는 3가지 접근 방식이 있습니다. 
    접근 방식은 활동 자체의 논리에 따라 다릅니다. 
    두 가지 질문에 답해야 합니다.
    
    1. 생성 후 활동을 업데이트해야 합니까?
    2. 트리거 테이블에서 업데이트가 가능합니까?
    
    다음은 세 가지 접근 방식에 대한 개요이며 가운데 접근 방식이 가장 일반적입니다.
        
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yn00ime7ptji-image.png)
    
    상상할 수 있듯이 여기서 스크립트는 조금 더 복잡해질 수 있습니다. 이 도움말 페이지 에서 샘플 스크립트를 볼 수 있습니다 .
    
    고맙게도 `Process Connector 템플릿을 사용하`여 필요한 스크립트의 핵심과 선택할 접근 방식을 제공할 수 있습니다. 
    즉, 누군가 `변경을 요청하는 경우 이를 조정하기 위해 스크립트 이면의 논리를 잘 이해`해야 합니다.

4. 임시 테이블을 쿼리로 이동하거나 트리거된 임시 테이블 사용

    데이터 모델 테이블에 대한 실시간 변환과 마찬가지로 모든 임시 테이블을 변환으로 직접 이동하거나 
    "트리거된 임시 테이블"을 사용해야 합니다. 
    이러한 방식으로 결과는 사전(변환 실행 전)이 아니라 런타임 중에 동적으로 생성됩니다.

### 44 Replication Cockpit용 템플릿 및 매개변수

템플릿

시간을 절약하고 모범 사례를 공유하려면 핵심 프로세스(O2C, P2P, AP, AR)의 경우 
Replication Cockpit에서 `델타 추출` 및 `델타 변환` 모두에 대한 `템플릿을 가져올 수 있음`을 알아야 합니다. 
이러한 템플릿은 Data Job 템플릿인 Celonis Marketplace의 템플릿과 동일하지 않습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/hdpz1795qq2i-image.png)

매개변수

Replication Cockpit의 모든 매개변수는 데이터 `풀 매개변수이며` 필요에 따라 데이터 작업에서도 재사용할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/mana63wie8gn-image.png)

복제를 구성할 때 동일한 매개변수가 나타납니다

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/vy51hccq48rx-image.png)

### 45 Replication Cockpit 변환 요약

Replication Cockpit 변환에 대한 이 섹션을 요약하면 다음을 배웠습니다.

- `변환`을 위해 Replication Cockpit을 ​​선호하는 경우 - 운영 사용 사례에 사용되는 `트랜잭션 테이블`
- `트리거 테이블`, `스테이징 테이블` 및 종속성의 개념을 사용하여 `Replication Cockpit 변환`을 설정하는 방법
- `초기화 스크립트`의 목적 및 변환 초기화 일정
- 데이터 모델 테이블과 활동 모두에 대한 `실시간 변환을 스크립팅하는 방법`
- Replication Cockpit에서 `템플릿` 및 `매개변수` 사용 정보

이 과정을 마친 것을 축하합니다!

우리는 이것이 이 트랙에서 가장 어려운 섹션 중 하나라는 것을 알고 있습니다. 
`한 번에 모든 것을 기억하고 마스터할 것으로 기대하지 마십`시오. 
고맙게도 `프로세스 커넥터`와 `템플릿`은 프로젝트를 시작할 수 있는 견고한 기반 역할을 합니다. 
또한 우리의 도움말 문서는 재교육이 필요할 때마다 도움을 주거나 특정 개념을 더 깊이 파고들 수 있도록 도와줍니다.
