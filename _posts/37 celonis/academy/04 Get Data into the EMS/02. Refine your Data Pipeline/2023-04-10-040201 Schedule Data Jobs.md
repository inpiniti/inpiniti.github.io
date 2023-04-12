---
title: 040201 Schedule Data Jobs
author: JUNG YoungKyun
date: 2023-04-10
category: 37 celonis
layout: post
---

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# Get Data into the EMS

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/q_100,a_exif,c_crop,x_0,y_0,w_800,h_450/a_exif,c_fill,w_800,h_450/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/e2jaa6l2jb4l-course_Get-Data-into-EMS_detail.jpg)

# 02. Refine your Data Pipeline

# Schedule Data Jobs

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fit,w_440,h_200/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/pkvfwbmthrmj-skill-area_Configure_catalogue.jpg)

## 1 소개

## 11 학습 목표

환영!

이 과정은 모두 일정에 관한 것이며 귀하가 데이터 작업 및 해당 작업(추출, 변환 및 데이터 모델 로드)을 이해하고 있다고 가정합니다. 데이터 흐름 다이어그램에서 일정 만들기는 `데이터 모델을 만든 후의 다음 단계`입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/mlva101nslw4-image.png)

이 과정을 완료하면 다음을 수행할 수 있습니다.

- 데이터 작업 `일정 설정`
- `델타` 대 전체 부하를 사용해야 하는 경우 `이해`
- 다양한 유형의 데이터에 `적합한 일정 빈도 적용` 및 혼합
- 예약된 데이터 작업과 `Replication Cockpit 모두 사용`

이 과정이 끝나면 "귀하의 피드백" 페이지를 통해 피드백을 자유롭게 공유하십시오.

## 2 데이터 작업을 적절하게 예약

### 21 스케줄링 기본 사항

#### 211 일회성과 연속 실행

생산적인 환경에서 Celonis를 설정하면 소스 시스템이 `지속적으로 새로운 데이터를 생성`합니다.

항상 `최신 상태를 유지`하려면 추출, 변환 및 데이터 `모델 로드를 지속적으로 실행`해야 합니다 . 그렇게 하기 위해 때때로 각 데이터 작업을 수동으로 실행할 수 있지만 자연스럽게 그 프로세스를 `자동화하려고 합`니다.

연속적이고 자동화된 데이터 로드의 경우 `예약 기능을 사용할 수 있습`니다. 일정을 사용하면 `정기적으로 데이터 작업을 순차적으로 실행할 수 있습`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/924lkehlwe2r-image.png)

#### 212 일정은 전체 데이터 작업을 실행합니다.

추출, 변환 또는 데이터 모델 로드와 같은 단일 작업에는 일정을 적용할 수 없으며 `전체 데이터 작업에만 적`용됩니다 . 즉, 특정 작업을 다른 일정으로 실행하려면 다른 데이터 작업에서 설정해야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ncz2wir6ny1f-image.png)

#### 213 데이터 모델 로드 작업 추가

간단한 알림 - 데이터 작업이 추출 및 변환을 실행하는 경우 `동일한 데이터 작업 내에서 해당 데이터 모델 로드 작업을 추가하는 것이 좋습`니다. 데이터 모델이 `다시 로드되는 즉시 데이터 모델을 기반으로 하는 분석, 앱 및 기타 개체가 새 데이터로 자동으로 새로 고쳐집`니다. 데이터 모델 로드가 없으면 데이터 작업이 데이터 모델에 영향을 미치지 않습니다.

별도의 데이터 모델 로드를 사용하는 데이터 작업을 사용하면 어떤 데이터 모델이 어떤 데이터 작업에 로드되는지 정의하여 하나의 데이터 풀에서 여러 프로세스를 쉽게 관리할 수 있습니다.

또한 설정한 데이터 모델 작업은 부분적일 수 있습니다 . 즉, 일정이 특정 테이블만 추출하고 변환하는 경우 데이터 `모델 로드 작업에서 영향을 받는 테이블만 업데이트하도록 선택할 수 있습`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6qws9cg9vd9x-image.png)

#### 214 일정은 Replication Cockpit용이 아닙니다.

실시간 연결을 설정한 경우 일정 외에 Replication Cockpit을 ​​사용하여 델타 로드를 구성할 수 있습니다. `Replication Cockpit`을 ​​사용하면 로드가 일정 기반이 아닌 `트리거 기반`입니다. Replication Cockpit을 ​​사용하는 경우 두 접근 방식의 혼합이 필요합니다.

예를 들어 특정 트랜잭션 테이블(전체 및 델타 추출 및 변환 모두)에 대해 Replication Cockpit을 ​​사용하는 경우 다음에 대해 예약된 데이터 작업이 계속 필요합니다.

- 데이터 모델 로드,
- 복제 설정에 포함하지 않기로 선택한 테이블의 델타 및 전체 로드.

Celonis Marketplace에서 다운로드하는 실시간 프로세스 `커넥터는 Replication Cockpit과 데이터 작업의 사전 설정 조합을 사용합`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/2lkvy661nghy-image.png)

Replication Cockpit 설정을 검토하려면 Get Data into the EMS 트랙에서 시스템에 연결, 데이터 추출 및 데이터 변환 과정을 검토하십시오.

이 섹션의 나머지 부분에서는 데이터 작업 예약 기능을 확대합니다.

### 22 일정 설정

#### 221 일정 설정

#### 222 트리거 기반 일정

`일정을 최적화하기 위해 트리거 기반 일정을 사용`할 수 있습니다. 여기에서 "트리거 기반 일정"을 선택하고 트리거 역할을 하는 일정을 결정하기만 하면 됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9ni054u56kse-image.png)

트리거 기반 일정을 사용하면 일정이 더 이상 미리 정의된 빈도에 따라 실행되지 않고 `트리거 일정이 성공적으로 완료되면 시작`됩니다. 즉, 중간에 `시간 손실 없이 일정을 차례로 실행할 수 있습`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/m7fkm9gtwwt1-image.png)

일정은 또한 `무한 루프에서 자체적으로 트리거될 수 있습`니다. 예를 들어 Replication Cockpit을 ​​사용하여 데이터 모델을 지속적으로 다시 로드해야 하는 경우에 잘 작동합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9u098zmqjebz-image.png)

#### 223 병렬 실행

기본적으로 일정은 데이터 작업을 순차적으로, 즉 차례로 실행합니다. 일정의 데이터 작업이 `겹치지 않고 동일한 데이터에 액세스하지 않는 경우 병렬 실행 사용을 고려하십`시오 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cu93ftyh4fh3-image.png)

이 경우 이 일정의 두 데이터 작업은 일정이 시작되는 즉시 병렬로 실행됩니다. `트리거 기반 일정과 함께 서로를 트리거하고 여러 데이터 작업을 병렬로 실행하는 일정의 종속성 트리를 설정할 수 있`습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/en6idrxihrkn-image.png)

병렬 데이터 작업을 설정할 때 동일한 테이블에서 작동하지 않는지 확인하십시오. 이로 인해 " 경합 상태 "가 발생하여 데이터에 문제가 발생할 수 있습니다.

#### 224 Full일 때, Delta일 때, 그리고 얼마나 자주?

일정 및 데이터 작업을 설정하는 방법은 실제로 다음 세 가지 질문에 따라 다릅니다.

- 이 데이터를 얼마나 자주 새로 고쳐야 합니까?
- 이 데이터를 로드하면 소스 시스템에 어떤 영향이 있습니까?
- Replication Cockpit이 사용 중입니까?

이러한 질문에 답하면서 몇 가지 기본 원칙을 도출할 수 있습니다.

|||
|---|---|
|트랜잭션 데이터에 대한 `델타 로드 우선 순위 지정`|일반적으로 트랜잭션 데이터에 대해 `가능할 때마다 델타 로드를 사용하는 것이 좋습`니다 . 주로 로드 시간과 소스 시스템의 로드를 줄이고 싶기 때문입니다. 빈도 측면에서 트랜잭션 테이블의 델타 로드는 일반적으로 매시간 또는 매일 실행됩니다 . 트랜잭션이란 활동 및 사례 테이블에 직접 영향을 미치는 모든 데이터를 의미합니다. 경우에 따라 환율, 고객 또는 재료 데이터와 같이 자주 변경되는 마스터 데이터도 일일 델타 로드를 보장할 수 있습니다.|
|자주 사용하지 않고 `오프 타임에만 전체 로드를 사용`하십시오.| 전체 로드를 사용하여 모든 데이터를 새로 고치고 사용량이 적은 시간(예: 밤, 매일 또는 매주)에 실행하여 사용량이 가장 많은 시간 동안 소스 시스템의 부하를 줄입니다. 궁극적으로 전체 로드는 어느 시점에서 모든 테이블에 대해 실행되어야 하지만 가능한 델타 로드가 없거나 메타데이터 변경이 자주 발생하는 경우 일부는 더 높은 빈도로 실행될 수 있습니다.|
|Replication Cockpit의 경우 대부분 전체 로드 및 데이터 모델 로드를 사용합니다.| Replication Cockpit이 트랜잭션 데이터에 대한 추출 및 변환을 처리하는 경우 데이터 모델의 매시간 또는 자체 트리거 재로드를 예약 하고 정기적인 전체 로드(매일 또는 매주)에 의존하여 Replication Cockpit에서 다루지 않는 모든 테이블을 처리할 수 있습니다. 있는 것을 새로 고칩니다. 또한 RC와 DJ 추출 및 변환 사이의 충돌을 피하십시오. 데이터 모델의 경우 트리거 기반 일정도 고려할 수 있습니다. (자세한 내용은 다음 페이지에서)|
|작업이 다른 세분화된 데이터 작업 고려|모든 추출 및 변환이 포함된 대용량 데이터 작업은 전체 로드가 드문 경우에만 적합합니다. `추출, 변환 및 데이터 모델 로드를 여러 데이터 작업에 걸쳐 분할하여 일정에 더 많은 유연성을 갖도록 하십`시오.|

#### 225 프로세스 커넥터에서 배우기

모든 Marketplace Process Connector는 당면한 시스템 및 프로세스에 대한 모범 사례를 기반으로 예약된 데이터 작업의 제안된 조합과 함께 제공됩니다. 예약 모범 사례에 익숙해지는 가장 좋은 방법은 Process Connector를 다운로드할 때 제안된 일정, 데이터 작업 및 해당 태스크를 자세히 살펴보는 것입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/r1eaewflea9k-image.png)

#### 226 실행 확인

일정이 성공적으로 실행되었는지 확인하려면 언제든지 실행 기록(오른쪽 상단 모서리에 있음)으로 이동하여 일정 및 작업의 상태, 실행 시간 및 로그를 확인할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/khaapqe8eyio-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/eksfm66679x1-image.png)

일정 로그는 데이터 작업 로그입니다.

일정 로그를 클릭하면 데이터 작업 로그를 클릭할 때와 유사한 로그 화면으로 이동하는 것을 볼 수 있습니다. 유일한 차이점은 데이터 작업이라는 하나의 추가 수준이 로그에 추가된다는 것입니다.
일정 로그를 클릭할 때의 로그:

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/v3ispop02jud-image.png)

데이터 작업 로그를 볼 때의 로그:
![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/oitkedrwssdb-image.png)

### 23 스마트 ETL

#### 231 변형의 순서

일정 순서를 결정할 수 있지만 데이터 작업 내에서 작업 순서를 어떻게 결정합니까?

데이터 작업을 실행할 때 변환이 `데이터 작업에 나타나는 대로 순차적으로 실행된다고 가정합`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/io6r8kfl0kya-image.png)

변환이 많을수록 특히 이러한 변환이 서로 의존하지 않고 병렬로 실행될 수 있는 경우 효율성 손실로 이어질 가능성이 커집니다.

역사적으로 변환은 순차적으로 실행되었지만 2022년에 Celonis는 데이터 작업 로드 시간을 크게 단축하는 새로운 중요한 기능인 스마트 ETL을 도입했습니다.

#### 232 스마트 ETL 사용

Celonis는 수동으로 변환 순서를 다시 지정하지 않고 다음을 수행하여 `최적의 방식으로 변환을 지능적으로 실행`합니다.

1. 최적의 변환 순서 계산: 각 데이터 작업을 실행하기 전에 Celonis는 데이터 작업의 모든 항목에 대한 `종속성을 기반으로 최적의 변환 실행 순서를 계산`합니다.

    a. 병렬성을 최적화하기 위해 `가장 효율적인 실행 순서를 나타내는 DAG` (Directed Acyclic Graph)를 생성하여 백그라운드에서 자동 생성

2. DAG를 사용하여 `최적의 계산된 실행 순서에 따라 모든 변환 작업을 트리거`합니다.

이 그래픽은 순차적 변환 실행과 최적화된 변환 실행 간의 차이를 보여줍니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/d7slhqmez3sw-parallelorchestration.png)

Smart ETL은 사용자 환경에서 기본적으로 켜져 있으므로 `아무 것도 활성화할 필요가 없습`니다. 수동 및 일정 데이터 작업 실행 모두에 적용됩니다.

### 24 일정 요약

이 과정은 일정 에 관한 것입니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/bdhck74g2ffb-image.png)

당신은 보았다:

- 일정이 `연속 실행`을 허용하는 방법
- 일정이 `전체 데이터 작업을 실행`하는 방법
- 데이터 작업에서 `데이터 모델 로드 작업의 중요성`
- 예약된 데이터 작업이 `Replication Cockpit 추출 및 변환을 보완`하는 방법
- `빈도 기반 또는 트리거 기반 `일정 설정 방법
- `델타 부하, 전체 부하 및 빈도`에 대한 기본 원칙
- Marketplace Process `Connectors에서 볼 수 있는 예약`에 대한 모범 사례.
- 데이터 작업 내 변환의 최적 실행 순서를 계산하는 `스마트 ETL 기능`

이 과정을 수료하셨습니다!

피드백 페이지를 방문하는 것을 잊지 마십시오 . 귀하의 피드백은 선택 사항 이지만 대단히 감사합니다. 