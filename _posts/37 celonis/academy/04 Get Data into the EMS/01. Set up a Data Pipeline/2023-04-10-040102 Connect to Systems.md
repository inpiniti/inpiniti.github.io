---
title: 040102 Connect to Systems
author: JUNG YoungKyun
date: 2023-04-10
category: 37 celonis
layout: post
---

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# Get Data into the EMS

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/q_100,a_exif,c_crop,x_0,y_0,w_800,h_450/a_exif,c_fill,w_800,h_450/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/e2jaa6l2jb4l-course_Get-Data-into-EMS_detail.jpg)

# 01 Set up a Data Pipeline

# Connect to Systems

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fit,w_440,h_200/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/029wel1b7lio-skill-area_Configure_catalogue.jpg)

## 01 . 소개

### 11 학습 목표


환영! 이 과정을 완료하면 다음을 수행할 수 있습니다.

- 적절한 연결 방식 선택 및 설정
- 연결을 위해 다양한 시스템 유형을 준비하는 방법 이해
- 데이터 파이프라인을 데이터 풀로 구조화

이 과정은 `시스템 연결에 중점`을 둡니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/j909grql93cl-image.png)

## 02 . 올바른 연결 방법 선택 및 설정

### 21 주요 연결 방법

EMS가 데이터를 가져오는 방법

소스 시스템에 연결하는 것은 프로세스 데이터를 Celonis EMS로 가져오는 첫 번째 단계입니다. EMS는 `메시지 대기열, Restful API, Soap API, 직접 데이터베이스` 액세스 또는 연결을 위한 시스템별 솔루션과 같은 광범위한 기술을 활용합니다.

EMS의 데이터 통합

데이터 통합은 연결 및 데이터 파이프라인을 설정하는 곳입니다. 데이터를 EMS로 가져올 수 있는 주요 방법은 다음과 같습니다.

1. 프로세스 커넥터
2. 추출기(데이터 연결)
3. 추출기 빌더
4. 파일 업로드
5. 데이터 푸시 API
6. 셀록스트랙터

데이터 통합 ​​UI로 이동하여 연결 방법에 대한 첫인상을 얻을 수 있습니다.

Process Connectors: 데이터 풀을 생성할 때 Process Connector 템플릿을 다운로드할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0blrdsyomxd9-image.png)

기타 방법: 처음부터 데이터 풀을 생성하는 경우 다른 연결 방법을 마음대로 사용할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/m4wx7hp21xcw-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/x50atoiz352k-image.png)

참고: 이 페이지의 방법은 프로세스 마이닝을 위해 트랜잭션 시스템에 `연결하는 데 중점`을 둡니다. 작업 마이닝 에 대한 정보를 찾고 있다면 이 과정을 살펴보십시오 .

### 22 프로세스 커넥터

#### 프로세스 커넥터 개요

`데이터 파이프라인을 구축`하려면 대부분의 경우 `프로세스 커넥터를 사용`합니다 .

프로세스 커넥터는 가장 확립된 프로세스 사용 사례를 연결하고 처리할 수 있는 가장 빠르고 일반적인 방법입니다 . Celonis Marketplace 에서 또는 데이터 풀을 생성할 때 다운로드할 수 있습니다 .

바로 사용할 수 있는 커넥터는 선택한 시스템 및 프로세스를 기반으로 표준 데이터 모델을 만드는 데 필요한 모든 것을 제공합니다 . 연결에 성공하면 커넥터는 ETL(Extract, Transform, Load) 프로세스 전반에 걸쳐 템플릿을 지원합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rbhueizwq0ij-image.png)

예를 들어 구매-지불 프로세스용 SAP 커넥터 또는 주문-현금 프로세스용 Oracle 커넥터 등이 필요할 수 있습니다.

데이터 통합에서 데이터 풀을 생성하면 프로세스 커넥터를 다운로드하는 옵션을 즉시 사용할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/k02cfehzmwyb-image.png)

다운로드 후 커넥터가 제공하는 자산을 즉시 시각화할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8rp76a57azvu-image.png)

여기에서 프로세스 흐름의 새롭거나 고유한 활동과 같이 소스 시스템에 존재할 수 있는 모든 사용자 정의에 커넥터를 적용하는 것은 귀하에게 달려 있습니다.

참고: 각 커넥터에는 특정 테이블에 대한 권한이 있는 소스 시스템 사용자가 필요합니다. Celonis 도움말 또는 커넥터 자체 추출에서 커넥터에 필요한 테이블 목록을 찾을 수 있습니다.

#### 마켓플레이스에서 커넥터 설치

이 비디오는 Process Connector를 설치하는 기본 단계를 보여줍니다.

![](../images/37 celonis/230410/040102/20230410100059.png)

![](../images/37 celonis/230410/040102/20230410100128.png)

![](../images/37 celonis/230410/040102/20230410100132.png)

![](../images/37 celonis/230410/040102/20230410100152.png)

![](../images/37 celonis/230410/040102/20230410100156.png)

![](../images/37 celonis/230410/040102/20230410102459.png)

![](../images/37 celonis/230410/040102/20230410102501.png)

![](../images/37 celonis/230410/040102/20230410102505.png)

![](../images/37 celonis/230410/040102/20230410102514.png)

![](../images/37 celonis/230410/040102/20230410102523.png)

![](../images/37 celonis/230410/040102/20230410102526.png)

![](../images/37 celonis/230410/040102/20230410102557.png)

![](../images/37 celonis/230410/040102/20230410102604.png)

![](../images/37 celonis/230410/040102/20230410102608.png)

![](../images/37 celonis/230410/040102/20230410102613.png)

![](../images/37 celonis/230410/040102/20230410102627.png)

![](../images/37 celonis/230410/040102/20230410102634.png)

![](../images/37 celonis/230410/040102/20230410102640.png)

![](../images/37 celonis/230410/040102/20230410102644.png)

![](../images/37 celonis/230410/040102/20230410102647.png)

![](../images/37 celonis/230410/040102/20230410102653.png)

![](../images/37 celonis/230410/040102/20230410102715.png)

#### 사용해 보기 - Process Connector 설치

개인 교육 환경에 기본 Process Connector를 설치하려면 아래의 간단한 3단계를 따르십시오. "확장"을 클릭하여 단계를 시작합니다.

환경에 액세스하려면 [이 지침을 확인하십시오](https://dam.celonis.com/download/en/3fxjBOrZkDrlGbDRxIOrom).

1. 데이터 -> 데이터 통합 ​​-> 오른쪽 상단의 "+ `새 데이터 풀`"을 클릭합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dguh6mvzv2p1-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ed26a89wm4aq-image.png)

2. "Process Connector `템플릿으로 시작`"을 클릭합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/jvogmtgi63ha-image.png)

3. "Get Data"를 검색하고 "Get Data into EMS - P2P" 커넥터를 선택하고 "`Install Process Connector`"로 설치합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/g1ki48vs7hho-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/j3dfo7wnnu5h-image.png)

이제 빈 연결 자리 표시자, 데이터 작업 및 작업 템플릿이 있는 "EMS로 데이터 가져오기 - P2P"라는 `새 데이터 풀`이 있어야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/mjvvjb7bhjca-image.png)

그래픽에서 데이터 작업을 클릭하면 작업 템플릿이 표시됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/03co7fqjltks-image.png)

이것은 제거된 프로세스 커넥터임을 명심하십시오. 일반적으로 데이터 작업, 일정 및 데이터 모델의 구조가 더 복잡합니다.

이것이 압도적이라면 걱정하지 마십시오! 데이터를 EMS로 가져오기 트랙을 진행하면서 이러한 개체에 대해 자세히 알아볼 것입니다.

### 23 추출기

#### 추출기 개요

추출기는 프로세스에 대한 참조가 없는 `빈 데이터 연결`입니다. 추출기를 사용하면 소스 시스템에 연결한 다음 처음부터 데이터 파이프라인(예: 추출, 변환 및 데이터 모델)을 구축해야 합니다. 추출기는 Marketplace에서 `프로세스 커넥터의 "연결 부분"`으로 생각할 수 있습니다 .

데이터 풀에서 "데이터 연결 추가"를 클릭한 다음 "데이터 원본에 연결"을 클릭한 경우 :

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sxtazfj6aa3i-image.png)

환경의 액세스 권한을 기반으로 몇 가지 추출기 예제가 표시됩니다 (아래 스크린샷과 다름) .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cprlx1vxbcdh-image.png)

데이터베이스 액세스

모든 소프트웨어 시스템은 `데이터를 중앙 위치에 저장`해야 합니다. 대부분의 경우 데이터는 솔루션 공급자가 개발하지 않은 기본 데이터베이스(예: PostgreSQL 또는 MSSQL)에 저장됩니다 . 이는 `JDBC 추출기`라고도 하는 데이터베이스 추출기의 완벽한 사용입니다 . 이 추출기는 20개 이상의 [데이터베이스 유형](https://docs.celonis.com/en/general-overview.html)을 지원하며 사용자 지정 데이터베이스 드라이버로 확장할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/1f9v42ymigjx-image.png)

#### 추출기로 새 연결 만들기

![](../images/37 celonis/230410/040102/20230410103535.png)

![](../images/37 celonis/230410/040102/20230410103644.png)

![](../images/37 celonis/230410/040102/20230410103716.png)

![](../images/37 celonis/230410/040102/20230410103720.png)

![](../images/37 celonis/230410/040102/20230410103726.png)

![](../images/37 celonis/230410/040102/20230410103735.png)

![](../images/37 celonis/230410/040102/20230410103739.png)

![](../images/37 celonis/230410/040102/20230410103758.png)

![](../images/37 celonis/230410/040102/20230410103816.png)

![](../images/37 celonis/230410/040102/20230410103835.png)

![](../images/37 celonis/230410/040102/20230410103846.png)

![](../images/37 celonis/230410/040102/20230410103908.png)

![](../images/37 celonis/230410/040102/20230410103919.png)

#### 사용해 보세요 - 새 연결 만들기

개인 환경에서 MSSQL 데이터베이스에 대한 새 연결을 생성하려면 아래 단계를 따르십시오.

1. 데이터 풀 "EMS 교육에 데이터 가져오기 - P2P"로 이동하고 "데이터 연결"을 클릭합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/3ws9hzqigwrq-image.png)

2. 기존 데이터 연결을 삭제합니다. 연결 이름을 입력해야 삭제할 수 있습니다. 팝업 내에서 자유롭게 복사하여 붙여넣으세요.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/hs96nnu7sro9-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/pmz69wwqrbib-image.png)

3. 기본 그래픽에서 해당 연결과 관련된 추출 및 변환이 지워진 것을 볼 수 있습니다. 걱정하지 마세요. 여전히 백업으로 템플릿이 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/gi3trzldblw7-image.png)
    
    템플릿은 나중에 필요한 경우 사용할 수 있도록 오른쪽 상단 모서리에 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/57zjp2tigjnz-image.png)

4. 이제 "데이터 소스에 연결"(2회)을 클릭하여 새 데이터베이스 연결을 만든 다음 "클라우드"를 필터링하고 "데이터베이스"를 클릭합니다. 구분선 아래에서 두 번째 데이터베이스 추출기를 선택

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/fsir47xaij35-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qhbha5pl85i3-image.png)
    
    해야 합니다 . 이것은 클라우드 추출기입니다 
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/3azlybfrswdt-image.png)

5. 다음 연결 세부 정보를 삽입합니다.

    이름: P2P 데이터 연결
    
    유형: PostgreSQL
    
    호스트: celonis-academy-instance-1.ckynnbglhixw.eu-central-1.rds.amazonaws.com
    
    포트: 5432
    
    데이터베이스 이름: celonis
    
    스키마 이름:  p2p
    
    사용자 이름: p2p_user
    
    암호: Celonis123!
    
    최대 병렬 테이블 추출(고급 설정) :  8
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/v7w1r5pkm299-image.png)

6. 연결을 테스트하십시오. 문제가 있는 경우 연결이 작동할 때까지 항목을 다시 확인하십시오.
7. "저장"을 클릭합니다.

이제 데이터 풀의 데이터베이스에 대한 기능 연결이 있고 Process Connector에서 작업 템플릿을 유지해야 합니다. 데이터 작업 추출 작업을 시작하면 템플릿이 유용합니다.

### 24 추출기 빌더

#### 추출기 빌더 소개

경우에 따라 즉시 사용 가능한 `Process Connectors 또는 Extractor가 없는 시스템`이나 프로세스를 보게 될 것입니다 . 이러한 경우 `Extractor Builder를 사용`할 수 있습니다 . 새 데이터 원본을 연결할 때 "사용자 지정 연결"에서 찾을 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8ifi69rp3wnh-image.png)

이 도구는 `REST API를 사용하여 추출기를 신속하게 구축`하는 데 도움이 되며 OData V2 및 V4 표준도 지원합니다. 소스 시스템에 빠르게 연결하고 필요한 데이터를 추출할 수 있습니다. 이렇게 하면 작업을 중단하거나 Celonis가 데이터를 EMS로 가져오기 위해 커넥터 또는 추출기를 구축할 때까지 기다릴 필요가 없습니다.

대부분의 경우 Extractor Builder를 사용하여 빌드된 기존 Celonis Extractor를 사용자 정의할 수도 있습니다 .

다른 추출기와 마찬가지로 소스 시스템에 연결한 후에도 여전히 추출, 변환 및 데이터 모델을 정의해야 합니다.

#### 나만의 추출기 만들기

#### 사용해 보세요(선택 사항) - 추출기 구축

#### 자세히 알아보고 싶으신가요?


### 25 파일 업로드

### 26 데이터 푸시 API

### 27 셀록스트랙터

### 28 시스템의 주요 유형

### 29 요약

## 3 연결을 위한 시스템 준비

### 31 연결을 위한 시스템 준비

### 32 폐쇄형 호스팅 환경

### 33 개방형 호스팅 환경

### 34 실시간 연결을 위한 준비

### 35 문제 해결

### 36 요약

## 4 데이터 풀 구성

### 41 필요에 따라 데이터 구조화

## 5 요약

### 51 배운 내용 확인 및 요약

