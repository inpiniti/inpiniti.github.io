---
title: 030104 Build a Knowledge Mode
author: JUNG YoungKyun
date: 2023-04-19
category: 37 celonis
layout: post
---

위 벳지는 수강을 완료하고 받은 뱃지입니다.

수강 전 [연습 툴](https://ygjung-iochord-com-2023-03-24.training.celonis.cloud/) 에 로그인하세요.

# Build Knowledge Models and Views

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/q_100,a_exif,c_crop,x_0,y_0,w_800,h_385/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/63plq1vjehen-course_Build-Views-and-Knowledge-Models_catalogue.jpg)

# Build a Knowledge Mode

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_600/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/d0z30oujzdeh-course_Formalize_catalog800x385.png)

# 1 새로운 지식 모델 만들기
## 11 Knowledge Models의 정의에 대한 복습[2:00]

- Knowledge Models의 주요 이점
    - 재사용 성
    - 확장성
    - 일관성
    
- Knowledge Models에는 무엇이 필요합니까? 
    - Knowledge Models을 만들기 전에 Knowledge Models에 연결할 데이터 모델이 이미 있다고 가정합니다.

## 12 새로운 Knowledge Models 만들기 [4:00]

- Celonis Studio 내부에 있는 경우 새로운 지식 모델을 생성하려면 (기술적으로) 무엇이 필요합니까?
    - a Space
    - a Package

[트레이닝 링크](https://dam.celonis.com/download/en/3fxjBOrZkDrlGbDRxIOrom)

- space 생성
- package 생성
- Knowledge Models 생성
- Data Model variable 추가 후 데이터 모델 "ap-celonis-studio-app-creator-training"을 선택

아래 이미지와 같게 나와야 함

![](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/16ad115c-ab0a-4728-a2a0-4a4a56d8c6c9/9/scormcontent/assets/CfWwqHxylL1xqYgf_65uOKxEx4AOVUU98.png)

## 13 새로 만든 Knowledge Models 검토[4:30]

- KPI  정의 의 필수 필드는 id, pql 및 ___________입니다.
    - display name

# 2 시각적 편집기를 사용하여 KPI 추가
## 21 KPI란 무엇입니까? [2:30]

파란색 테두리 안에 KPI 목록이 있음

![](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/16ad115c-ab0a-4728-a2a0-4a4a56d8c6c9/9/scormcontent/assets/tcUVZNktACL63YJ5_hwg6KhSGS-P70K9E.jpg)

KPI 목록을 YAML 으로 표현하면 아래와 같음

![](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/16ad115c-ab0a-4728-a2a0-4a4a56d8c6c9/9/scormcontent/assets/DhizY8iWX5x8A5ql_ErvSGMNN9DtwN7Dl.png)

## 22 KPI 매개변수 검토[2:00]

- Knowledge Models에서 새로운 KPI를 생성하려면 무엇이 필요하다고 생각하십니까? ( 문서를 자유롭게 들여다보십시오.(새 탭에서 열림)!) 
    - ID
    - Display Name
    - PQL formula to calculate the value

생성은 YAML을 사용하든 Visual Editor를 사용하든 상관 없습니다.

- Display Name: Days Payable Outstanding
- Id: days_payable_outstanding
- PQL

```
AVG(DAYS_BETWEEN(PU_FIRST("BSEG", "_CEL_AP_ACTIVITIES"."EVENTTIME",
      "_CEL_AP_ACTIVITIES"."ACTIVITY_EN" = 'Record Invoice Receipt')
      ,PU_FIRST("BSEG", "_CEL_AP_ACTIVITIES"."EVENTTIME",
          "_CEL_AP_ACTIVITIES"."ACTIVITY_EN" = 'Clear Invoice')))
```

위에 3개만 입력하면 아래와 같이 KPI 가 만들어 집니다.

![](../images/37 celonis/230419/20230419105326.png)

## 23 Knowledge Models에 "미지급 일수" 추가 [10:30]

- Format : Rounded (,.Of)
- Unit : Days
- KPI Desired Direction : Down Trend

위 3개를 추가적으로 입력하면 아래와 같이 KPI 가 만들어 집니다.

![](../images/37 celonis/230419/20230419110029.png)

- 지금 몇시인지 아시죠?
    - Display Name: Days Payable Outstanding
    - Description: Financial ratio indicating avg. time (in days) to pay bills and invoices
    - PQL: AVG(DAYS_BETWEEN(PU_FIRST("BSEG", "_CEL_AP_ACTIVITIES"."EVENTTIME",    "_CEL_AP_ACTIVITIES"."ACTIVITY_EN" = 'Record Invoice Receipt')   ,PU_FIRST("BSEG", "_CEL_AP_ACTIVITIES"."EVENTTIME",   "_CEL_AP_ACTIVITIES"."ACTIVITY_EN" = 'Clear Invoice')))
    - Format: ,.0f
    - Unit: Days
    - Desired Direction: Down Trend   

# 3 YAML 편집기를 사용하여 레코드 추가
## 31 기록이란 무엇입니까? [2:30]
## 32 레코드 매개변수 검토[4:00]
## 33 Knowledge Models에 "송장" 추가 [12:00]

아래 그림은 YAML으로 레코드 편집 한 것 입니다. 

![](../images/37 celonis/230419/20230419151424.png)

Preview 에 아무 것도 안보이긴 한데, Attributes 에 3개가 추가 되어 있는것을 확인 할 수 있고,

![](../images/37 celonis/230419/20230419151603.png)

Attributes 를 열람해보면 Preview 가 나오는 것을 확인 가능합니다.

![](../images/37 celonis/230419/20230419151716.png)

Record Preview에 아무것도 표시 되지 않는 것은,
예제의 Records 에는 pql 이 안들어가 있어서 그럴수도 있을것 같습니다.

# 4 팁과 요령
## 41 PQL 편집기 사용 [2:30]

YAML 에서는 pql 구문에서 우클릭을 하면 되고,
비쥬얼 모드에서는 PQL 옆의 연필모양 아이콘을 클릭하면 됩니다.

## 42 CTRL + 스페이스바 [1:00]

일반 에디터와 마찬가지로 ctrl + 스페이스 바로 도움 같은걸 받을수 있습니다.

## 43 데이터 모델 자세히 알아보기 [0:40]

지식 모델의 기반인 실제 데이터를 데이터 모델에서 조금 더 자세히 볼수 있는데,  
오른쪽 상단의 버튼을 클릭하면 Data Model을 미리 볼 수 있습니다.

또한 데이터 탐색기로 조금 더 심층 분석이 가능한데,

[데이터 탐색기 소개](https://academy.celonis.com/learn/course/introduction-to-data-explorer) 에서 자세히 확인 할 수 있습니다.
