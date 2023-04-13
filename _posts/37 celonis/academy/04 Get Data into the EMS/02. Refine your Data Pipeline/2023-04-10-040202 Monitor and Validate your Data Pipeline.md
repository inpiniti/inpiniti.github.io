---
title: 040202 Monitor and Validate your Data Pipeline
author: JUNG YoungKyun
date: 2023-04-10
category: 37 celonis
layout: post
---

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# Get Data into the EMS

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/q_100,a_exif,c_crop,x_0,y_0,w_800,h_450/a_exif,c_fill,w_800,h_450/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/e2jaa6l2jb4l-course_Get-Data-into-EMS_detail.jpg)

# 02. Refine your Data Pipeline

# Monitor and Validate your Data Pipeline

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fit,w_440,h_200/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/7ukj66bv01oz-skill-area_Management-Monitoring_catalogue.jpg)

## 1 소개

### 11 학습 목표

- 데이터 작업, 복제 및 데이터 모델 로드를 포함한 전체 데이터 `파이프라인 모니터링`
- 올바른 `필터와 로그를 사용`하여 모든 문제 해결
- 데이터 `파이프라인에 기본 검증` 적용

## 2 데이터 작업 모니터링

### 21 문제 해결 및 모니터링

#### 211 문제 해결

Replication Cockpit을 ​​사용하여 `데이터 작업 일정` 또는 `복제를 설정`할 때 소스 시스템에 연결하는 순간부터 
`데이터 파이프라인 문제` 해결의 모든 것을 아는 것이 중요합니다. 
다음은 데이터 통합에서 유의해야 할 사항 목록입니다.

1. 데이터 풀 목록 보기 및 필터링

    데이터 통합에 들어가면 상태 아이콘 덕분에 파이프라인에 `문제가 있는 데이터 풀을 즉시 확인할 수 있`습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/1e9h2qyb9s2l-image.png)

    여기에서 문제 및 필터가 있는 데이터 풀을 입력하여 `근본 원인을 찾을 수 있`습니다. 
    파이프라인의 모든 부분에서 필터링할 수 있으며 이 필터는 전체 데이터 흐름 다이어그램에 적용됩니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dl7mlfezv3wq-image.png)
    
    필터와 관련된 모든 `영향을 받거나 원인이 되는 개체가 다이어그램에 표시`됩니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qp74tf06x6nj-image.png)
    
2. 시스템에 연결

    연결할 때 연결을 테스트 하고 필요한 시스템별 사전 작업에 대한 도움말 문서를 확인 하십시오.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/shjecax1u4fy-image.png)
    
3. 데이터 작업으로 데이터 추출

    구문 오류
    
    추출을 설정할 때 추출을 저장하기 전에 "`잠재적인 문제를 찾을 수 없습니다"라는 메시지가 화면에 나타나는지 
    확인해야 합`니다. 이것은 필터의 구문 문제를 확인하고 수정되지 않는 한 나타나지 않습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/k547yennt16r-image.png)
    
    문제가 있는 경우 클릭하여 목록을 가져오고 하나씩 살펴볼 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/2hj2fbyv7s11-image.png)
    
    델타 필터 문제는 기본적으로 자주 나타나지만 델타 실행을 계획하지 않는 경우 수정할 필요가 없습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/g8ub5bherun7-image.png)
    
    `명백한 오류의 경우 필터 상자 바로 아래에 경고가 표시`됩니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/b2rx7bpcqa0v-image.png)
    
    추출 미리보기
    
    사용하는 추출 방법에 따라 로그 액세스 수준이 달라집니다. 
    가능한 경우 새 추출 또는 조정된 테이블 `추출을 실행하기 전`에 `추출 미리 보기를 사용 하고 `
    `로그를 살펴보고` `모든 것이 원활하게 실행되는지 확인하는 것이 좋습`니다 .
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0poshgrpkuxu-image.png)
    
    로그 확인
    
    추출 실행 중이나 후에는 물론 데이터 작업 수준에서 해당 `로그를 확인`할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ah4vs2blja1g-image.png)
    
    `자세한 내용`을 보려면 `디버그 모드`를 활성화하십시오.
    
    마지막으로 로그에 대한 자세한 정보가 필요한 경우 추출 설정에서 디버그 모드를 활성화하십시오.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ab6zqgmotxeq-image.png)
    
3. 데이터 작업으로 데이터 변환

    SQL 워크벤치에서 변환 확인
    
    `변환 작업을 할 때` 데이터 작업 수준에서 실행하기 전에 
    `SQL 워크벤치에서 변환을 실행해야 합`니다. 
    이는 간단한 구문 오류를 사전에 제외하는 데 도움이 됩니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ysz00frqpsz3-image.png)
    
    스크립트의 일부 실행
    
    `스크립트의 일부를 강조 표시`하고 `실행을 선택`하여 `실행할 수 있음`을 기억하십시오.
    
    추출과 마찬가지로 데이터 작업 수준에서 변환에 대한 `로그를 볼 수 있으며 `
    클릭하여 특정 변환으로 드릴다운할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/l46srhgiey9r-image.png)
    
4. Replication Cockpit으로 추출 및 변환

    테이블 상태 확인
    
    Replication Cockpit을 ​​사용하면 각 테이블의 모니터링 탭에서 
    `복제 및 초기화에 대한 기본 로그를 볼 수 있`습니다. 
    연결(범위) 아래의 각 테이블에 대한 각 복제의 상태를 직접 볼 수도 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/x47kn848pcu3-image.png)
    
    `자세한 로그`는 엄청난 양의 저장 공간을 소비하므로 기본적으로 `비활성화되어 있`습니다. 
    즉, 복제 구성에서 특정 테이블에 대해 `임시로 활성화할 수 있`습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/5mafcwvywzar-image.png)
    
5. 데이터 모델 로드

    데이터 모델 로드의 경우 데이터 모델의 데이터 로드 `탭 바로 아래에 경고 및 오류가 나타`납니다. 
    이는 로드를 수동으로 실행하든 데이터 작업의 일부로 실행하든 관계없이 적용됩니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8ie821l8b9nq-image.png)
    
    대부분의 문제는 테이블이 연결된 방식과 `타임스탬프 및 케이스 키가 얼마나 정확한지`에 연결됩니다.
    
    로드 도중 또는 이후에 세부 정보를 클릭하여 테이블당 로드된 행 수를 확인할 수도 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dobkevsk9r1o-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/d8um072c5f5r-image.png)
    
6. 데이터 작업 예약

    일정에 대한 로그는 데이터 작업 로그와 동일합니다. 
    스케줄이 데이터 작업을 실행하기 때문입니다 . 
    `일정 로그를 보려면` `실행 기록으로 이동`하십시오.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/td1oorrjh9b0-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/w4ay5met3g19-image.png)

#### 212 감시 장치

모니터링

데이터 파이프라인이 엔드 투 엔드로 설정되어 있으면 이론적으로 편안히 앉아서 작업의 아름다움을 즐길 수 있습니다. 
즉, 모든 것이 순조롭게 진행되도록 계속 주시해야 합니다. 
모니터링에 대한 몇 가지 중요한 사항은 다음과 같습니다.

1. 데이터 작업 알림

    각 데이터 작업에 대해 `경고를 구성하고 이메일 알림을 받을 시기`
    (실패 시, 성공 시, 데이터 작업을 건너뛰는 경우 또는 특정 기간 초과 시)를 표시할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/69gh1nbv6kvr-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/uw7gu6xqr4pl-image.png)
    
2. 복제 경고

   추출 또는 변환에서 `복제 실패가 있을 때마다 알림을 받으려면 `
   "설정" 아래의 연결 수준에서 경고를 `활성화할 수 있습`니다.
   
   ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/03xjcjhuxaxv-image.png)
   
   ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/e3el1e71h0bo-image.png)
   
3. 데이터 모델 가입

    데이터 모델이 `실패하면` `데이터 모델을 구독하여 이메일을 받을 수 있습`니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/4zi54k9i9gh1-image.png)
    
4. 일정 모니터링

    일정 설정 내에서 모니터링을 `활성화할 수도 있습`니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/2dp2k9u7e1an-image.png)
    
    이 경우 모니터링은 Celonis에서 수행되며 중요한 생산 사례에 대해서만 활성화해야 합니다. 
    `심각한 오류가 발생하면` Celonis에 알림이 전송되어 `잠재적으로 조치를 취할 수 있`습니다. 
    오류가 인프라 문제 또는 잘못된 구성으로 인한 경우 일정이 모니터링에서 제외될 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/j1jdkyiiw6sz-image.png)

5. 커스텀 모니터링

    Data Pool List 뷰에서 오른쪽 상단의 Monitoring 아이콘을 클릭하여 Monitoring으로 이동합니다. 
    (예, 이것은 데이터 풀 내의 실행 기록과 동일한 아이콘입니다)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8x2nofsdt3gs-image.png)
    
    여기에서 "`사용자 지정 모니터링"을 활성화하`여 Data `Pipeline 상태를 모니터링할 수 있`습니다. 
    이 옵션은 세 가지 데이터 모델(데이터 소비 모니터링, 데이터 파이프라인 모니터링 및 복제 조종석 모니터링)이 
    포함된 독립적인 데이터 풀을 생성하여 분석에 사용하고 원하는 대로 사용자 지정할 수 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/m2uva5bg52af-image.png)
    
    Studio에서 데이터 모델로 작업하려면 Marketplace에서 
    Data Pipeline & Consumption Monitor 라는 바로 사용할 수 있는 패키지를 다운로드할 수 있습니다 .
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ajtgxto7m9ru-image.png)
    
    여기에서 생성된 데이터 모델은 라이선스 제한에 포함되지 않습니다.
    
    `이 기능은` 특히 여러 프로세스 및 데이터 풀로 작업할 때 `데이터 파이프라인의 
    전체 개요를 얻는 가장 좋은 방법` 중 하나입니다.
    
    자세한 내용은 이 기능에 대한 [도움말 페이지](https://docs.celonis.com/en/custom-data-pipeline-monitoring.html) 를 확인하십시오 .
    
6. 데이터 소비

    생산적인 모든 Celonis 라이센스에는 `소비할 수 있는 데이터 양이 제한`되어 있습니다. 
    데이터 풀 목록 보기의 왼쪽 상단에서 직접 `총 소비량을 확인`할 수 있습니다. 
    또한 모든 데이터 풀 아래에서 `얼마나 많은 데이터가 소비되는지 확인`할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/t0kme4ehjb2x-image.png)
    
    데이터 풀 내에서 가장 많이 소비하는 테이블을 확인해야 합니까? 
    오른쪽 상단의 데이터 소비로 이동한 다음 데이터 풀을 검색하고 크기별로 정렬합니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sbkyesrpcqk7-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/it656l9cbm2d-image.png)

#### 213 요약 - 문제 해결 및 모니터링

- 파이프라인의 각 부분에 대한 `로그를 찾을 위치를 파악` 하고 해당되는 경우 부분/수동 테스트를 실행합니다.
- `어떤 데이터 풀에 문제가 있는지 확인하는 방법` 과 필터를 사용하여 드릴다운하는 방법을 알고 있습니다.
- 데이터 작업, 데이터 모델, 복제에 대한 `알림을 설정하는 방법`을 알고 있습니다.
- 데이터 소비를 확인 하고 더 깊은 통찰력을 위해 `사용자 지정 모니터링을 활성화하는 방법`을 알고 있습니다.

## 3 공정 흐름 검증

### 31 프로세스 검증

#### 311 확인을 요청하는 질문

프로젝트의 유효성 검사 단계에 들어가거나 데이터 통합에서 
데이터 작업에 대한 업데이트를 수행할 때 팀은 다음 유효성 검사 질문에 답해야 합니다.

- 프로세스 흐름이 일반적으로 `타당해 보 입니까` ?
- `경우의 수가 정확 합`니까 ?
- `활동`이 `올바르게 정의`되어 있고 `올바른 양`과 `순서` 로 나타나고 있습니까 ?
- 개별 사례가 Celonis에서 소스 시스템과 정확히 동일한 방식으로 표현됩니까 ?
- Total Net Value와 같은 기본 KPI가 정확 합니까 ?

대부분의 경우 데이터를 확인하는 사람은 `프로세스 검증` 리드 또는 비즈니스 `도메인 전문가`입니다. 
이것이 귀하인지 여부에 관계없이 발견된 모든 문제를 해결하는 데 관여할 가능성이 큽니다. 
`대부분의` 경우 해결해야 할 `문제는 변환 작업에 있습`니다 .

분석 또는 데이터 탐색기를 사용하여 Studio에서 대부분의 유효성 검사를 수행할 수 있습니다 . 
일반적으로 대부분의 유효성 검사에 데이터 탐색기를 사용하는 것이 좋지만 
해당되는 경우 두 가지 유효성 검사 접근 방식의 예를 볼 수 있습니다.

데이터 탐색기에 대한 자세한 내용은 데이터 탐색기 교육 및 해당 문서를 확인하십시오 .

각 유효성 검사 질문에 대해 자세히 살펴보겠습니다.

#### 312 타당성 검사

Process Validation의 첫 번째 단계는 일반적인 타당성 검사 입니다 . 
비즈니스 도메인 전문가는 일반적인 타당성을 위해 
프로세스 `순서`, 타임스탬프, 사례 수 및 KPI와 같은 프로세스의 `다양한 측면을 확인`해야 합니다.

이 단계에서 다양한 필터를 적용하여 의미 있는 관점에서 프로세스를 볼 수 있도록 하여 
비즈니스 도메인 전문가가 표시된 그림과 관련될 수 있도록 할 수 있습니다.

일반적인 타당성 검사는 세 가지 주요 통찰력으로 이어질 수 있습니다.

1. Celonis의 표현은 사실적입니다 . 좋습니다. 다음 유효성 검사로 넘어갑시다!
2. Celonis의 표현 은 비현실적으로 보입니다. 문제를 자세히 조사해야 합니다. 
그렇게 하면 Celonis의 표현이 정확하다는 것을 알아낼 수 있습니다. 
이것은 이미 흥미로운 결과를 낳았습니다.
3. Celonis의 표현 이 잘못되었습니다. 그에 따라 데이터 모델을 조정해야 합니다.

#### 313 사례 수

다음 단계에서는 소스 시스템 항목에 대해 Celonis의 사례 수를 검증해야 합니다.

여기에서 다음 질문에 답해야 합니다.

- 경우의 수가 정확합니까(예: 구매 주문 품목)?

    예를 들어 고려된 기간 동안 x개의 구매 주문 항목이 현실적입니까?
    
- 다른 케이스 유형의 번호가 정확합니까(예: 구매 주문 항목 유형)?

    예: 문서 유형 "표준 구매 오더"가 실제로 대부분의 경우에 발생합니까?
    
- 시간 경과에 따른 분포가 정확합니까?

    예: 구매 주문 항목 생성이 2019년 10월에 최고조에 달했을 가능성이 있습니까?

데이터 탐색기에서

빌드된 분석 또는 보기가 없는지 `확인하는 빠른 방법`은 `데이터 탐색기를 사용하는 것`입니다. 
다음은 케이스 테이블(EKPO)을 선택하는 샘플 데이터 세트의 예입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/jwzlc7044zlo-image.png)

분석에서

Studio에서 분석을 사용하여 다음 질문에 답할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/h70nyy922l2m-Analysispic.jpg)

정보가 잘못된 경우 어떻게 합니까?

Celonis의 사례 수가 소스 시스템의 사례 수를 나타내지 않는 경우 다음 확인을 수행해야 합니다. 

- 데이터베이스의 사례 수를 계산합니다. 일치하지 않으면 추출이 `올바르게 구성되었는지 확인`해야 합니다. 
- 필터링 조건으로 인해 `손실된 사례가 있는지 확인`합니다. 
- 조인 조건(예: 텍스트 테이블에 대한 사례 테이블의 내부 조인)으로 인해 `사례 손실이 발생하는지 확인`합니다.

#### 314 활동

이 단계에서 프로세스는 일반적으로 그럴듯해 보이고 사례 수가 일치합니다. 
프로세스 표현의 `모든 세부 사항이 올바른지 확인하기 위해` `활동의 유효성 검사`에 대해 자세히 살펴보겠습니다.

1. 활동 정의

    활동 정의 검증
    
    이 단계에서는 기본 테이블 구조에 대한 `지식이 있는 소스 시스템 전문가가 활동의 정의를 확인`합니다. 
    여기에는 다음에 대한 검증이 포함됩니다.
    
    - 활동 이름
    - 사용된 타임스탬프
    - 적용된 모든 필터/조건
    - 변경 활동에 대해 고려되는 변경 필드입니다.
    
    "템플릿 가져오기" 버튼(Marketplace)을 통해 데이터 통합에서 사용할 수 있는 
    표준 프로세스에 대한 활동 정의가 있습니다. 
    사용자 지정 프로세스를 배포하는 경우 이러한 활동을 직접 정의해야 합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/151z60d12ief-activityvalidation.jpg)
    
    활동의 정의를 확인했으므로 이제 모든 활동이 올바르게 표시되는지 확인하여 누락된 것이 없는지 확인할 차례입니다.

2. 활동 수

    데이터 탐색기에서
    
    활동 수를 확인하려면 활동 테이블을 선택하고 "그룹 및 집계" 토글을 켜고 활동 이름 열의 `항목을 계산하여` 
    데이터 탐색기를 사용할 수 있습니다. 이 보기를 사용하면 활동의 가시성 과 빈도를 빠르게 확인할 수 있습니다 .

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/tvqmf6v3jaxp-image.png)
    
3. 분석에서

    또는 Studio에서 Celonis Analysis로 이동하여 `Process Explorer를 사용`하여 
    프로세스 흐름 자체를 `검사할 수 있`습니다. 단계는 다음과 같습니다.
    
    1. 가시성 확인: 먼저 정의된 모든 활동이 분석에 표시되는지 확인합니다. 
    이 경우 활동 변환이 모두 작동하고 있음을 알 수 있습니다.
    
        ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qdru6hee27si-image.png)
        
    2. 빈도 확인: 활동이 올바른 빈도로 나타나는지 확인합니다. 
    프로세스 탐색기의 "목록" 보기는 존재하는 모든 활동 목록과 활동이 나타나는 사례 수를 제공합니다.
    예를 들어 비현실적일 수 있는 주문 이전에 구매 요청이 나타나는 경우의 50%에서만 발견할 수 있습니다.
    
        ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rrh2dsxi8l4b-image.png)

    문제 해결
    
    개별 사례 확인: 숫자가 너무 높거나 너무 낮은 활동을 식별하는 경우 해당 
    `활동 정의를 확인해야 하며` 개별 사례를 확인하여 
    Celonis에서 볼 수 없는 활동을 소스 시스템에서 볼 수 있는지 확인할 수 있습니다.
    
    필터 적용: 이 조사에 필터를 적용하면 도움이 될 수 있습니다. 
    예를 들어 특정 구매 주문 유형의 경우 모든 경우에 대한 구매 요청이 있어야 한다는 것을 알 수 있습니다. 
    이 경우 해당 `필터를 적용`하고 Celonis에 대해 소스 시스템을 확인할 수 있습니다. 
    이렇게 하면 이 활동이 `누락된 사례의 범위를 좁힐 수 있으`므로 그 이유를 평가할 수 있습니다.
    
4. 활동 순서

    지금까지 훌륭했습니다! 모든 활동은 Celonis에서 올바른 번호로 표시되지만 나타나는 순서는 어떻습니까?
    
    데이터 탐색기에서
    
    `데이터 탐색기를 사용`하면 개별 사례를 자세히 확인할 수 있습니다. 
    이렇게 하려면 활동 테이블을 선택하고 특정 사례에 대해 필터링합니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qevkr3e7rcpc-image.png)
    
    분석에서
    
    프로세스 탐색기를 사용하면 활동 순서에 대한 `집계 개요`를 볼 수 있습니다. 
    여기에서 가장 일반적인 변형을 살펴보는 것으로 시작하여 새로운 활동과 연결을 지속적으로 추가합니다. 
    당신이 보는 것이 정확하게 묘사되어 있는지 항상 스스로에게 물어보십시오.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/lkz0no74chhl-image.png)
    
    특정 프로세스 순서를 찾을 때 "선택 UI"에서 "프로세스 흐름 선택"을 활용할 수 있습니다. 
    이런 식으로 `절대로 발생해서는 안 되는 프로세스 패턴을 찾을 수 있습`니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yqb7t9uabqfg-image.png)
    
    사례의 초기 활동
    
    또한 사례의 초기 활동을 확인하는 것이 좋습니다. 
    이를 조사하려면 프로세스 탐색기에서 "프로세스 시작"과 "케이스 이동"을 클릭하기만 하면 됩니다. 
    프로세스 종료에 대해서도 동일한 작업을 수행할 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0vgukmvdq4mi-image.png)
    
    프로젝트 구성원이 전체 프로세스 흐름이 정확하다는 데 동의하면 마지막 확인을 수행해야 합니다.
    
#### 315 개별 사례 심사

개별 사례 조사는 Celonis에서 `선택한 사례를` 소스 시스템 항목과 `비교하는 데 사용`됩니다. 
`대표적인 사례를 선택`하려면 Celonis에서 소스 시스템에 대해 확인된 `사례의 계층화된 무작위 샘플을 선택해야 합`니다. 
일반적인 단계는 다음과 같습니다.

1. 계층화 기준 (예: 회사 코드, 문서 유형, 공급업체, 자재 그룹)을 정의합니다.
2. 선택한 계층화 기준에 따라 필터링한 후 무작위 사례를 선택합니다 . 
또한 활동이 많거나 매우 적은 경우, 빠른 사례, 장기 실행자, 반복적이거나 미결 사례와 같은 일부 `이상값을 찾고자 합`니다.
3. 사례에 표시된 모든 활동이 소스 시스템 항목과 일치하는지 확인하십시오 .
4. 모든 불일치를 기록 하고 활동이 Celonis에서 다른 타임스탬프를 가질 수 있는 이유 
또는 활동이 전혀 나타나지 않는 이유를 자세히 분석하십시오. 
이렇게 하면 이유를 역추적하여 불일치가 발생하는 위치를 이해하고 이에 따라 변환을 조정할 수 있습니다.

데이터 탐색기에서

활동 표를 선택하고 필요한 `필터를 적용하기만 하면 됩`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/17f38e404h7f-image.png)

분석에서

`사례 탐색기를 사용하여 사례 활동을 분석`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qtylbmxsyxno-image.png)

#### 316 순 가치

표준 프로세스로 작업하는 경우 `총 순 주문 금액도 검증해야 할 가능성이 있습`니다. 
순 주문 총 금액은 비즈니스 사용자가 볼 수 있는 중앙 KPI인 경우가 많습니다. 
순 가치는 모든 경우의 가치를 합한 것입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/oif835d4nfvx-image.png)

데이터 탐색기에서

순 가치를 확인하려면 `사례 테이블을 선택하고` 선택한 필터를 사용하거나 사용하지 않고 순 가치 열을 `합산`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/p41jkrkrvi7s-image.png)

분석에서 더 깊이 파고들기

데이터 엔지니어로서 귀하는 총 가치를 살펴보고 그것이 `정확한지 확인하는 것 
이상으로 나아가지 않을 것입`니다. 대조적으로, 사용 사례에 대해 작업하는 데이터 분석가는 
더 깊이 파고들어 환율의 오류를 찾을 수 있습니다.

다음은 문서 통화의 금액을 변환된 통화로 나누어 변환율을 계산하는 샘플 분석입니다. 
영역 차트는 시간 경과에 따른 추세를 표시할 수 있습니다. 
분석가는 다양한 통화를 선택하여 모든 전환이 정확한 값을 가져오는지 확인합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/q4q0ktvds766-image.png)

### 32검증 문서화

유효성 검사는 프로세스를 살펴보는 것 이상이며 분석 및 작업 흐름과 같은 다른 Celonis 영역에 적용됩니다. 
검증 문서화 의 중요성은 아무리 강조해도 지나치지 않습니다 . 
다음은 유효성 검사 실행, 추적 및 후속 작업에 대한 명확한 책임 할당을 지원하는

[샘플 Excel 시트](https://academy.celonis.com/learn/courseFileLists/03c5952f-3e87-42d0-ad03-3aad0711be9d?fileListId=d7a3bb4c-74fc-4e5c-917d-f968aa39188b&fileIndex=0&download=1) 입니다. 필요에 따라 시트를 자유롭게 조정하십시오.

유효성 검사 주제에 대한 자세한 내용은 [프로세스 및 데이터 유효성 검사 과정](https://academy.celonis.com/learn/course/process-data-validation) 을 확인하십시오 .

## 4 과정 요약

### 41 과정 요약

- 데이터 연결, 데이터 작업, 일정, 데이터 모델 로드, Replication Cockpit 및 데이터 소비 문제 `해결 및 모니터링`
- 타당성, 사례, 활동 및 순 가치를 살펴보고 프로세스 흐름을 `검증하는 기본 사항`
- `검증 문서화`의 중요성에 대해
