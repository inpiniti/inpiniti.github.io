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

![](../images/37 celonis/230410/040102/20230410104755.png)

![](../images/37 celonis/230410/040102/20230410104816.png)

![](../images/37 celonis/230410/040102/20230410104826.png)

![](../images/37 celonis/230410/040102/20230410104835.png)

![](../images/37 celonis/230410/040102/20230410104857.png)

![](../images/37 celonis/230410/040102/20230410104913.png)

![](../images/37 celonis/230410/040102/20230410104933.png)

![](../images/37 celonis/230410/040102/20230410104944.png)

![](../images/37 celonis/230410/040102/20230410104955.png)

![](../images/37 celonis/230410/040102/20230410105016.png)

![](../images/37 celonis/230410/040102/20230410105030.png)

![](../images/37 celonis/230410/040102/20230410105049.png)

![](../images/37 celonis/230410/040102/20230410105105.png)

![](../images/37 celonis/230410/040102/20230410105112.png)

![](../images/37 celonis/230410/040102/20230410105130.png)

![](../images/37 celonis/230410/040102/20230410105137.png)

![](../images/37 celonis/230410/040102/20230410105144.png)

![](../images/37 celonis/230410/040102/20230410105157.png)

![](../images/37 celonis/230410/040102/20230410105210.png)

![](../images/37 celonis/230410/040102/20230410105220.png)

#### 사용해 보세요(선택 사항) - 추출기 구축

많은 공급업체가 COVID19의 영향을 많이 받습니다. 이는 공급망 위험을 초래하므로 COVID 사례 데이터를 데이터 파이프라인에 추가해야 합니다. 이렇게 하려면 추출기 빌더를 사용하여 추출기를 만듭니다. 귀하의 목표는 `세계 및 국가 수준에서 사례 번호를 추출하는 것`입니다.

[이 API](https://documenter.getpostman.com/view/10808728/SzS8rjbc#00030720-fae3-4c72-8aea-ad01ba17adf8) 의 요약 `엔드포인트를 사용`합니다 . 기술에 자신이 있다면 기본 지침을 따르십시오. 약간의 지원이 필요한 경우 단계 섹션을 사용하십시오.

다음 자격 증명을 사용하여 추출기 빌더에서 [이 API](https://documenter.getpostman.com/view/10808728/SzS8rjbc#00030720-fae3-4c72-8aea-ad01ba17adf8) 의 요약 엔드포인트를 빌드합니다 .

사용자 이름: go-corona-admin

PW: 5577YvzU4bK63a1WIQ3Z043H

도움이 필요하면 아래 단계를 따르십시오.

1. 데이터 풀로 이동하여 데이터 연결을 추가하고 데이터 원본에 연결 -> 사용자 정의 -> 사용자 정의 연결 빌드 -> 새 추출기 빌드를 클릭합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/htzrlkwx4uda-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/fd5lkm3zyczq-image.png)
    
2. 추출기에 적절한 이름을 지정하고 저장 및 계속을 클릭합니다.

3. URL 매개변수를 편집하고 " https://api.covid19api.com/ "을 기본값으로 입력합니다. URL 뒤에 추가 공백이 없는지 확인하세요!
저장을 클릭하고 다시 저장하고 계속하기를 클릭합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/8vpup404xmlj-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/d9d7170tf5qi-image.png)
    
4. 기본 인증을 선택하고 저장 및 계속을 클릭합니다.
5. 새 엔드포인트 추가
6. 그것을 요약이라고 부르십시오

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/n2y2nsag1mla-image.png)
    
7. Configure Request -> URL 아래에 "{Connection.API_URL}summary"를 입력합니다
. 참고: 슬래시가 연결 URL 내에 있는지 아니면 끝점에 있는지는 사용자가 결정합니다. 여기서도 공백을 피하십시오.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/out4y9g7v9yj-image.png)
    
8. 응답 구성에서 대상 테이블 이름으로 "CovidSummary"를 입력합니다. 이것은 단순히 테이블이 추출된 후에 갖게 될 이름입니다.
9. "샘플을 사용하여 응답 구성..."을 클릭합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/zkxrkpdhpm16-image.png)
    
10. "새 데이터 소스 만들기"를 선택하고 "새 데이터 소스 만들기"를 클릭합니다 (Extractor Builder 외부의 데이터 연결로 이동하지 마십시오) .

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/b0sp2wf2ry3j-image.png)
    
11. 팝업에서 다음 사용자 및 PW를 입력하고 저장을 클릭합니다.

    - 이름: Sample Connection(또는 원하는 항목)
    - 사용자 이름: go-corona-admin
    - pw: 5577YvzU4bK63a1WIQ3Z043H
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6eznjyaso12z-image.png)
    
12. 연결이 작동하지 않는 경우 일반적으로 API URL(4단계) 또는 엔드포인트에 추가 공백이나 슬래시가 있기 때문입니다. 제거하면 연결이 작동합니다.
13. 연결이 설정되면 "응답 작성"을 클릭할 수 있어야 합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sgy0nyvliwba-image.png)
    
14. 다른 이유로 샘플 연결이 작동하지 않는 경우 API 문서 에서 샘플 응답을 복사하여 응답 상자에 직접 붙여넣을 수 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/wf08t7ld6zgg-image.png)
    
15. 샘플 응답이 나타나면 특정 국가에 대한 데이터만 원하는 경우 응답 루트를 국가로 조정할 수 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/q7ie91yhv5ui-image.png)
    
16. 완료를 두 번 클릭하면 완료됩니다!

생성한 추출기와 "데이터 원본"이 이제 데이터 연결 아래에 옵션으로 나타납니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/12o345zt4ngl-image.png)

추출기는 새 연결을 클릭할 때도 나타나며 이를 사용하여 데이터 파이프라인을 구축할 수 있습니다. 

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/hfqru78ns4eq-image.png)

물론 API와 Extractor Builder는 더 복잡합니다. 여기서 작업의 기초는 REST API가 작동하는 방식과 소스 시스템의 API 문서에 대한 확실한 이해입니다. REST API에 익숙하지 않은 경우 몇 분 동안 웹에서 "REST API 사용 방법" 또는 "REST API 이해"를 검색하면 지식을 매우 빠르게 향상시킬 수 있습니다. 

#### 자세히 알아보고 싶으신가요?

### 25 파일 업로드

#### 파일 업로드

새 데이터 원본에 연결할 때 파일 업로드를 사용하여 데이터를 EMS에 직접 업로드할 수 있습니다. 파일은 다음 형식 중 하나여야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/h01xotu4prpl-image.png)

언제 파일 업로드를 사용하시겠습니까?
다음은 몇 가지 샘플 사용 사례입니다.

- 추가 정적 데이터
- 번역 용어 목록
- 소스 시스템 외부의 권한 목록
- 절대 변경되지 않는 과거 데이터의 경우
- 일회성 업로드

가능하면 정기적으로 새로 고쳐야 하는 동적 데이터에 파일 업로드를 사용하지 마십시오. 이를 위해 즉시 사용 가능한 추출기 또는 Data Push API를 대신 고려해야 합니다.

SAP ABAP 보고서 생성을 위해 SAP ABAP Generator를 사용 하고 나중에 파일 업로드에서 ABAP 파일을 업로드할 수도 있습니다. 자세한 내용은 [이 Microlearning](https://academy.celonis.com/learn/video/one-time-sap-upload-with-abap-generator-uploader) 및 [도움말 설명서](https://docs.celonis.com/en/one-time-extraction-from-sap-ecc-and-s-4.html)를 참조하십시오 .

#### 파일 업로드하다

![](../images/37 celonis/230410/040102/20230410110406.png)

![](../images/37 celonis/230410/040102/20230410110415.png)

![](../images/37 celonis/230410/040102/20230410110424.png)

![](../images/37 celonis/230410/040102/20230410110434.png)

![](../images/37 celonis/230410/040102/20230410110442.png)

![](../images/37 celonis/230410/040102/20230410110452.png)

![](../images/37 celonis/230410/040102/20230410110458.png)

![](../images/37 celonis/230410/040102/20230410110512.png)

![](../images/37 celonis/230410/040102/20230410110520.png)

![](../images/37 celonis/230410/040102/20230410110530.png)

![](../images/37 celonis/230410/040102/20230410110548.png)

#### 사용해 보세요(선택 사항) - 파일 업로드

파일 업로드는 정말로 로켓 과학이 되어서는 안됩니다. 즉, 직접 경험해 보는 것이 좋으며 어떤 옵션을 마음대로 사용할 수 있는지 알 수 있습니다.

1. 이 과정의 리소스 섹션에서 "파일 업로드 수행" 파일을 다운로드합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dx20zndbivzh-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6xaqeshyv7j2-image.png)

2. 데이터 연결로 이동하여 "데이터 연결 추가"를 클릭한 다음 "파일 업로드"를 클릭합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/2tuzajjibm18-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/7nw43yxvqill-image.png)

3. 다운로드한 파일을 선택합니다(또는 해당 영역으로 끌어다 놓습니다). 아래와 같이 나타나야 합니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/v7l0gnexn9p3-image.png)

4. 파일 옆에 있는 세 개의 점을 클릭한 다음 "업로드 구성"을 클릭합니다. 여기에서 데이터를 업로드할 연결(데이터베이스 스키마)을 결정합니다. 기본적으로 "글로벌"로 이동합니다. 필요한 경우 여기에서 대상 테이블 이름을 바꿀 수도 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/fyfwhpbfg5zq-image.png)
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/xnowsnd44sx6-image.png)

5. 이제 세 개의 점을 다시 클릭하고 두 번째 옵션인 "데이터 스키마 구성:

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/56vizzk55bud-image.png)
    
    필요한 경우 헤더, 데이터 유형 등을 조정할 수 있습니다. 반복되는 오류가 발생하는 경우 모든 것을 문자열로 가져오는 것이 좋습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/uu3rn6a9isz7-image.png)

6. 재생 버튼 동작을 클릭하고 업로드가 완료될 때까지 기다립니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/188v4ef92wju-image.png)
    
    완료되지 않은 경우 세 개의 점 또는 상태 아이콘 아래의 실행 기록을 보고 오류를 확인하십시오.

쉽죠? 이제 시트가 데이터 풀에 테이블로 업로드되었으며 변환을 수행하고 데이터 모델에 포함할 수 있습니다. (이후 과정에서 변환에 대해 자세히 설명)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/bt5fj0wv17x1-image.png)

### 26 데이터 푸시 API

#### 데이터 푸시 API

드문 경우지만 소스 시스템에서 데이터를 "풀"할 수 없거나 가져오면 안 되지만 소스 시스템은 데이터를 Celonis로 푸시할 수 있습니다 . 이를 위해 Celonis는 `Data Push API를 제공`합니다 . Data Push API는 기본 제공 기본 추출기에도 사용되는 기본 기술입니다.

확장 가능하고 신뢰할 수 있음

Data Push API는 마이크로 배치(데이터 청크)를 사용하여 확장 가능하고 안정적인 통합 지점을 제공하고 Parquet 및 CSV 파일 구성을 허용합니다. 데이터 푸시 API는 "푸시 작업"을 생성, 실행 및 모니터링하기 위한 일련의 순차적 API 호출입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/9aos234i7wdq-image.png)

시스템에서 데이터를 사용할 수 있게 되면 Celonis에서 제공하는 추출기와 동일한 방식으로 데이터를 변환, 분석 및 작업할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/a7jbi0mmlrd6-image.png)

사용 사례

Data Push API의 매우 일반적인 사용 사례는 사용 중인 `기존 데이터 파이프라인 도구(ETL 도구)가 있고 EMS를 이 도구와 통합`하는 것이 선호되는 경우입니다.

경우에 따라 IT 또는 공급업체가 시스템에 직접 액세스하는 것을 차단할 수 있습니다 . 시스템에서 예약된 보고서 또는 내보내기 에 대한 옵션을 제공하는 경우 Data Push API를 사용하여 내보내기 또는 보고서를 선택하고 데이터를 EMS에 삽입할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/fkeke7pjqp94-image.png)

#### 데이터 푸시 API 연결 만들기

지금쯤이면 데이터 풀의 각 연결이 데이터를 구성하는 별도의 컨테이너 역할을 한다는 사실을 이해하셨을 것입니다. 용어에 익숙하다면 데이터베이스 스키마와 비교할 수 있습니다.

Data Push API의 경우 데이터를 푸시하려는 별도의 연결을 선택적으로 만들 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/sciugfltfy93-image.png)

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/wkaw8n4n9gim-image.png)

데이터 푸시 API 작업

대부분의 경우 Data Push API를 사용하여 Data Pipeline을 설정하려면 `기본 프로그래밍 기술(Python 또는 Java)이 필요`합니다. 즉, `Postman과 같은 도구를 사용하여 테스트`를 실행할 수 있습니다. 또는 Celonis 작업 흐름을 사용하여 영구 흐름을 테스트하고 설정할 수도 있습니다.

API에 대한 자세한 내용은 이 [도움말 페이지](https://docs.celonis.com/en/data-push-api.html) 와 [Data Push API 기본 과정](https://academy.celonis.com/courses/data-push-api-basics) 을 참조하십시오.

### 27 셀록스트랙터

완전한 제어를 위한 Celoxtractor

`Python 프로그래밍 경험이 있고 특정 사용 사례에 맞는 다른 연결 방법이 없는 경우` Celoxtractor 사용을 고려할 수 있습니다.

Celoxtractor는 자신만의 EMS Extractor를 쉽게 개발할 수 있도록 설계된 `Python 패키지`입니다. 다음을 제공합니다.

- 데이터에 대한 완벽한 제어,
- 기본 Celonis 추출기에 대한 기능 패리티,
- 추출의 모든 측면을 조정할 수 있는 완전한 유연성을 제공합니다.

이 도구에 대한 자세한 내용은 [도움말](https://docs.celonis.com/en/custom-connection,-python-extractor--celoxtractor-.html) 및 [github 설명서](https://celonis.github.io/celoxtractor/) 를 참조하십시오 .

### 28 시스템의 주요 유형

그래서 몇 가지 연결 방법을 살펴보았지만 Celonis `EMS는 일반적으로 어떤 시스템에 연결`됩니까?

다음은 EMS를 사용하여 연결하는 방법에 대한 간단한 설명과 함께 가장 일반적인 시스템 및 데이터 소스 목록입니다.

Celonis를 사용하면 사용 가능한 연결 방법을 사용하여 여러 소스에서 데이터를 가져와 이 데이터를 하나의 큰 데이터 모델로 통합 할 수 있습니다 .

이미 이러한 시스템에 익숙하다면 이 페이지를 건너뛰십시오 .

- 서비스로서의 소프트웨어

    Salesforce Lightning Platform, Workday, ServiceNow, Zendesk, SAP Ariba 등과 같은 SaaS(Software-as-a-Service) 제품의 데이터에 액세스하려면 일반적으로 Marketplace 또는 추출기(데이터 연결)의 `프로세스 커넥터를 사용`합니다. 이 두 가지 방법을 모두 사용하여 EMS와 소스 시스템 간에 직접 클라우드 간 연결을 설정합니다.
    
    일반적으로 추출은 소스 시스템에서 제공하는 세 가지 API 아키텍처인 REST-API(예: [Zendesk](https://developer.zendesk.com/rest_api) ), SOAP 웹 서비스(예: [Workday](https://community.workday.com/sites/default/files/file-hosting/productionapi/index.html) ) 또는 메시지 큐(예: [Salesforce Platform Events](https://developer.salesforce.com/docs/atlas.en-us.platform_events.meta/platform_events/platform_events_intro.htm) ) 중 하나를 사용합니다. 각 시나리오에서 시스템 API 끝점은 데이터를 JSON 파일, .csv 파일 형식 또는 이와 유사한 형식으로 제공하고 Celonis 추출기는 파일 형식을 .parquet로 변환하고 데이터를 EMS 데이터 저장소에 삽입합니다.
    
- ERP 시스템

    ERP(Enterprise Resource Planning System) 시스템은 비즈니스 백오피스 기능, 서비스 및 인적 자원을 통합하고 자동화하는 소프트웨어 제품군입니다. 대부분의 ERP는 고객 인프라 내의 "온프레미스" 또는 폐쇄형 호스팅 환경에서 실행됩니다.
    
    SaaS 제품과 마찬가지로 `기본 커넥터 또는 추출기를 사용`하여 ERP 시스템에 대한 연결을 설정합니다. 주요 차이점은 폐쇄된 환경에서는 연결을 설정하기 전에 `추가 구성 요소를 설치`해야 한다는 것입니다. 예를 들어 `SAP 시스템에 연결하려면 RFC 모듈과 Celonis Extractor를 설치`해야 합니다.
    
    Celonis EMS는 온프레미스 추출기를 통해 온프레미스 ERP 시스템에 대한 연결을 설정합니다.

- 데이터 웨어하우스

    데이터 웨어하우스는 보고 및 데이터 분석에 사용되는 시스템입니다. 대부분의 조직에는 비즈니스 인텔리전스 설정의 일부로 데이터 웨어하우스가 있습니다. 데이터 웨어하우스는 여전히 주로 MSSQL 또는 SAP HANA와 같은 전통적인 온프레미스 시스템이지만 `Google BigQuery`, `Snowflake` 또는 `AWS Redshift`와 같은 최신 클라우드 애플리케이션을 보게 될 것입니다.
    
    대부분의 경우 `JDBC(Java Database Connectivity) 인터페이스`를 통해 데이터 웨어하우스에 액세스합니다. 이것은 데이터베이스 기본 추출기입니다. 이를 통해 20개 이상의 서로 다른 데이터베이스 유형에 연결할 수 있습니다. 필요한 경우 JDBC 드라이버로 EMS JDBC 추출기를 확장하고 JDBC 인터페이스가 있는 모든 시스템에 대한 연결을 설정할 수 있습니다.

- 생산성 도구

    또 다른 유용한 정보 소스는 생산성 도구 입니다 . `Microsoft Teams`, `Google 드라이브`, `MS365`와 같은 시스템은 모든 조직에서 일상적으로 사용되는 시스템입니다. 대부분의 최신 생산성 도구는 SaaS 애플리케이션이며 데이터 추출을 위한 `API를 제공`합니다. 기본 추출기를 사용하면 이러한 시스템에 대한 클라우드 간 연결을 설정하고 우선 순위 시트, 작업 문서 등과 같은 지원 문서를 추가할 수 있습니다.
    
    또는 파일 업로드를 사용하거나 예를 들어 Google 시트를 지속적으로 동기화하는 기본 추출기와 플랫 파일의 지속적인 통합을 설정할 수도 있습니다.

- 작업 마이닝

    일부 사용 사례의 경우 데스크톱 데이터라고도 하는 `사용자 상호 작용 데이터를 캡처`해야 합니다. 이 데이터 캡처 및 분석을 " `태스크 마이닝` "이라고 합니다. 데이터는 IT 소스 시스템에서 캡처할 수 없는 컴퓨터에서 사용자가 수행하는 모든 작업입니다. 캡처를 위해 Celonis는 `Task Mining Desktop Client를 제공`합니다. 클라이언트는 브라우저 또는 SAP GUI와 같은 소스 시스템에서 시스템 이벤트, 화면 데이터 및 소프트웨어 이벤트를 캡처할 수 있습니다. 그런 다음 데이터는 구조화 및 분석을 위해 EMS로 전송됩니다.
    
    작업 마이닝을 사용하면 데스크톱 데이터로 기존 IT 기반 비즈니스 프로세스를 강화하고 IT 시스템이 관련되지 않거나 기본 IT 시스템이 데이터에 대한 액세스를 제공하지 않는 프로세스를 캡처할 수 있습니다. [태스크 마이닝 기본 과정](https://academy.celonis.com/courses/task-mining-basics) 에서 이 주제에 대해 자세히 알아볼 수 있습니다 .

- 종이 문서 / OCR

    많은 프로세스가 여전히 종이 문서에서 실행됩니다. `EMS는 터치리스 송장 수집 앱 내에서 광학 문자 인식(OCR)을 통해 종이 송장을 처리`할 수 있습니다. 종이 청구서의 정보는 SAP 또는 Oracle과 같은 기본 IT 시스템에 기록될 수 있습니다. 필요한 경우 최종 사용자가 추출된 정보를 확인할 수 있는 앱을 통해 정보를 라우팅할 수도 있습니다.

- 맞춤형 데이터 통합

    많은 경우 조직에서는 맞춤형 솔루션을 사용합니다. 고맙게도 EMS는 사용자 지정 데이터 소스로 쉽게 확장할 수 있도록 구축되었습니다. 다음 방법으로 사용자 지정 통합을 구축할 수 있습니다.
    
    - 데이터베이스 추출기를 사용한 데이터베이스 액세스
    - 추출기 빌더
    - 파일 업로드(비연속)
    - 데이터 푸시 API
    - Python 추출기(Celoxtractor)
    
그것이 요점입니다!

`이것이 가장` 일반적인 시스템 유형의 기본 사항이며 가장 `많이 연결되는 방법`입니다.

### 29 요약

요컨대 연결하는 방법을 배웠습니다. 다음은 다루는 연결 방법에 대한 몇 가지 정보입니다.

- 프로세스 커넥터 - 가능할 때마다 마켓플레이스에서 프로세스 커넥터를 찾으십시오. 새 데이터 풀을 생성할 때 프로세스 커넥터를 직접 가져올 수 있습니다.
- 기본 추출기 - 다음으로 시스템에 중립적으로 연결하고 추출기(중립 연결)를 사용하여 데이터를 추출할 수 있습니다 .
- Extractor Builder - 커넥터/추출기를 사용할 수 없는 경우 Celonis에 요청하여 하나를 만들 수 있지만(servicedesk@celonis.com에 문의) 기다리지 마십시오. Extractor Builder를 사용하여 자신만의 연결 및 추출을 구축하십시오 .
- 파일 업로드 - 일회성 또는 정적 사례의 경우 파일 업로드 옵션을 사용하십시오 .
- 데이터 푸시 API - 사용 사례에서 기존 ETL 도구 또는 예약된 보고서와 같은 데이터를 푸시해야 하는 경우 데이터 푸시 API를 사용합니다.
- Celoxtractor - 마지막으로 Python에 익숙하고 추출기의 모든 측면을 제어하려는 경우 Celoxtractor를 고려할 수 있습니다.

연결하는 소스 시스템에 따라 이러한 방법 중 하나 이상이 적합하며 사용할 방법을 결정하는 것은 사용자의 몫입니다. 잊어버린 것이 있으면 UI로 이동하여 살펴보세요!

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/z09yaboa4tlz-image.png)

## 3 연결을 위한 시스템 준비

### 31 연결을 위한 시스템 준비

모든 연결은 다릅니다

시중에 나와 있는 시스템 및 호스팅 접근 방식의 종류가 너무 많기 때문에 데이터 연결을 설정하기 위해 추가 단계를 거쳐야 하는 경우가 많습니다. 걱정하지 마십시오. 각 연결에 대해 Celonis 도움말 문서에서 수행할 작업에 대한 체크리스트를 안내합니다.

지금은 세 가지 기본 연결 시나리오와 관련 설정 및 추출 흐름을 살펴보겠습니다.

- 폐쇄형 호스팅 환경(온프레미스 또는 클라우드)
- 개방형 클라우드 환경
- 실시간 연결

### 32 폐쇄형 호스팅 환경

#### 폐쇄 시스템에 연결

"폐쇄형"이란 온프레미스 시스템을 가장 자주 지칭하지만 직접 연결을 통해 액세스할 수 없는 클라우드에서 호스팅되는 시스템을 가리키기도 합니다. 폐쇄형 호스팅 환경의 좋은 예는 SAP ECC 및 SAP S/4HANA입니다. 이 두 시스템 모두 연결을 설정하기 전에 다음 단계를 거쳐야 합니다.

|무엇|	어디|	WHO|
|---|---|---|
|1. Celonis SAP RFC 모듈 설치|	SAP ECC 또는 S/4HANA 시스템|	SAP 기초 팀|
|2. 구내 추출기 설치 _|	고객 네트워크|	서버 및 인프라 관리자|
|3. 데이터 연결 만들기|	셀로니스 EMS|	데이터 엔지니어|

즉, Celonis는 SAP에 직접 연결할 수 없으며 추가 Extractor Server(모든 폐쇄 시스템용) 와 함께 호스팅 서버에 설치된 `RFC 모듈(SAP 전용)이 필요`합니다 . 각 단계에는 서로 다른 내부 팀 구성원과의 협업이 필요하며 `소스 시스템(예: 수신 허용 목록 IP 및 포트)`과 EMS 측 모두에 대한 분 하위 단계가 포함됩니다. 이 [도움말 페이지](https://docs.celonis.com/en/how-do-i-set-up-my-sap-data-connection-.html) 에서 단계에 대한 자세한 개요를 확인할 수 있습니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/revg4xrmshkp-image.png)

온프레미스 추출기가 필요한 이유는 무엇입니까?

두 가지 간단한 이유가 있습니다.

1. 온프레미스 시스템은 일반적으로 외부 애플리케이션과 통신할 수 없습니다.
2. 네트워크 내부 연결은 훨씬 더 안정적이고 성능이 뛰어나므로 소스 시스템에 대한 부하가 최소화됩니다.

여기서 모든 단계를 기억할 필요는 없습니다. 설치하는 각 커넥터에 대한 해당 문서를 확인하고 Celonis 프로젝트에서 이러한 단계를 진행할 책임이 있음을 확인하십시오.

참고: 추출기가 닫힌 시스템의 소스 시스템 측에 있는 경우 EMS에서 연결 유형을 "업링크됨"으로 설정합니다. 데이터 통합에서 온프레미스 연결 유형을 선택하면 자동으로 선택됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/q3athj6umb5x-image.png)

#### 폐쇄 시스템의 추출 흐름

연결 및 추출 흐름

다음은 폐쇄형 소스 시스템을 사용한 일반 연결 및 데이터 추출 흐름입니다. 더 잘 이해하려면 오른쪽의 단계를 읽으십시오. 이 흐름을 암기할 필요는 없습니다. 이것은 단순히 백그라운드에서 일어나는 일에 대한 이해를 제공하기 위한 것입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ncwhth4ad9lv-image.png)

보시다시피` 추출기 서버는 소스 시스템 측에 있으며 TLS 1.2를 통해 암호화된 https`를 사용하는 모든 교차 시스템 연결과 함께 폐쇄형 시스템과 EMS 간의 중개자 역할을 합니다.

### 33 개방형 호스팅 환경

#### 개방형 호스팅 환경에 연결

개방형 호스팅 환경에 연결하면 삶이 조금 더 쉬워진다고 말할 수 있습니다. 대부분의 경우 이들은 클라우드 시스템입니다. 잠재적으로 IP를 허용 목록에 추가하고 사용자에게 적절한 액세스 권한을 부여하는 것 외에는 일반적으로 몇 가지 추가 단계가 필요합니다. 이 경우 추출기는 EMS 측에 있으며 클라우드 시스템과 직접 연결 (업링크되지 않음)이 설정됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/tywgao6o8wbv-image.png)

#### 개방형 시스템의 추출 흐름

다음은 EMS와 개방형 클라우드 시스템 간의 연결 및 추출 흐름에 대한 개요입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/7oryg4s54cy4-image.png)

### 34 실시간 연결을 위한 준비

이제 실시간 연결 준비에 대해 자세히 살펴보겠습니다. 폐쇄형 호스팅 환경에서 작업하든 개방형 호스팅 환경에서 작업하든 상관없이 이것들이 가장 중요합니다.

다시 SAP 예제를 사용할 수 있습니다. 실시간이란 소스 시스템 테이블의 변경 사항을 빠르게 추적하고 데이터를 Celonis로 신속하게 푸시할 수 있음을 의미합니다. 그렇다면 소스 시스템 측에서 어떻게 동적으로 변경 사항을 추적할 수 있습니까? 세 가지 일반적인 단계가 있습니다.

1. 변경 사항을 저장할 변경 로그 테이블 생성
2. 트리거를 설치하여 변경 사항을 모니터링 및 캡처
3. 정리 백그라운드 작업을 활성화하여 로그 테이블 정리(SAP 관련)

SAP와 같은 폐쇄형 시스템 사용 사례에서 귀하의 임무는 SAP 팀에 조언하고 `때가 되면 정보를 전달하는 것`입니다. 설정에 대한 모든 정보를 얻으려면 이 [도움말 페이지](https://docs.celonis.com/en/setup-checklist---real-time-connectivity-to-sap.html) 를 검색하고 즐겨찾기에 추가하십시오 .

트리거 및 변경 로그 테이블은 무엇을 위한 것입니까?

다음은 이 두 가지 중요한 구성 요소를 이해하기 위한 간단한 그래픽입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/79ast42zwlzj-image.png)

여기서 키워드는 `"트리거"와 "변경"`입니다. 원본 테이블에서 레코드가 `추가, 업데이트 또는 삭제될 때마다` 트리거가 꺼지고 변경된 `레코드의 기본 키, 업데이트 유형 및 타임스탬프가 변경 로그 테이블에 저장`됩니다.

`빈번한 간격으로 EMS는 이러한 레코드를 요청`하고 Extractor Server는 레코드를 준비하고 EMS로 푸시하는 중개자 역할을 합니다. 다음은 일반 SAP EKKO 테이블에 대한 샘플 변경 로그 테이블입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/g63qzi2fsl1p-rcchangelog.png)

이 실시간 설정은 [SAP](https://docs.celonis.com/en/setup-checklist---real-time-connectivity-to-sap.html) 및 [JDBC 실시간](https://docs.celonis.com/en/real-time-extension--overview.html) 시나리오에 적용됩니다. [Salesforce](https://academy.celonis.com/learn/video/real-time-extractions-with-the-streaming-cockpit) 또는 Azure Event Hub 와 같은 다른 시스템의 경우 설정이 다릅니다.

실시간 연결은 데이터 추출 및 데이터 변환 과정에서 자세히 다루는 더 큰 주제입니다.

### 35 문제 해결

소스 시스템과의 연결 문제를 해결할 때 따라야 할 기본 단계는 다음과 같습니다.

- Help Doc First - 항상 특정 커넥터 또는 연결 방법에 대한 도움말 전제 조건을 따르십시오. 대부분의 커넥터에는 FAQ 목록과 잠재적인 오류가 있습니다. 도움말에서 검색하거나 도움말에서 [이 페이지](https://docs.celonis.com/en/data-connections.html) 를 좋은 출발점으로 책갈피에 추가할 수 있습니다.
- 로그 - 가능한 경우 `연결 로그를 확인`하십시오. 업링크 연결인 경우(온프레미스 또는 폐쇄형 호스팅의 경우) 로컬 추출기 로그를 확인 하고 Celonis 지원의 도움이 필요한 경우 오류 메시지를 캡처해야 합니다.

도움말이나 로그로 문제가 해결되지 않으면 Celopeers 커뮤니티를 통해 또는 servicedesk@celonis.com 으로 지원팀에 문의하십시오 . 데이터 풀 및 연결 ID가 포함되어 있으므로 연결 페이지 URL을 포함해야 합니다.

### 36 요약

시스템 연결을 준비할 때 다음 사항을 고려해야 합니다.

- 호스팅 환경이 닫혀 있습니다 (대부분의 경우 온프레미스). 그러면 `Celonis Extractor를 온프레미스에 설치`하고 EMS에 대한 업링크 연결을 사용합니다.
- 호스팅 환경이 열려 있습니다 (대부분의 경우 클라우드). 그런 다음 EMS에 직접 연결된 `기본 Celonis Cloud Extractor를 사용`합니다.
- 연결이 실시간이므로 소스 시스템 환경에서 `로그 테이블과 트리거를 설정`해야 합니다 .

다음은 폐쇄형 소스 시스템 환경과 오픈 소스 시스템 환경 의 연결 차이를 명확하게 보여주는 그래픽입니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/uyanaaqhzegw-image.png)

마지막으로 연결 문제를 해결하려면 사용 가능한 로그를 사용하고 도움말 문서를 참조하고 필요한 경우 지원에 문의하십시오.

## 4 데이터 풀 구성

### 41 필요에 따라 데이터 구조화

#### 데이터 풀 소개

데이터 통합에서 소스 시스템에 연결하면 새 연결이 새 데이터 풀 또는 기존 데이터 풀에 도달합니다.

데이터 풀이란 무엇이며 왜 중요한가요?

데이터 풀은 `데이터 연결, 데이터 작업 및 데이터 모델`과 같은 `데이터 통합의 다른 모든 요소에 대한 컨테이너`입니다. 그들은 당신의 데이터를 모읍니다 . EMS에서 여러 시스템과 프로세스를 통합하려는 경우 계획을 데이터 통합의 구조적 요소에 맞추는 것이 매우 중요하며 나중에 구조 조정 작업을 줄일 수 있습니다.

#### 데이터 통합 ​​구조

이제 데이터 통합의 기본 데이터 구조와 이것이 의미하는 바를 파헤쳐 보겠습니다. 당신은 이러한 점들을 간접적으로 다루었지만 다음은 몇 가지 확실한 사실입니다.

- Marketplace에서 `Process Connector를 다운로드하면 EMS가 데이터 풀을 생성`합니다.
- 데이터 풀 - `하나의 데이터 풀은 여러 데이터 연결`을 호스트할 수 있습니다.
    - 데이터 연결 - 데이터 연결은 단순히 `소스 시스템에 대한 연결`이며 데이터 풀 내에서 데이터 조직자 역할도 합니다.
    - 하나 이상의 데이터 연결을 생성할 수 있으며 각각에 대해 하나 이상의 데이터 작업에 대해 작업합니다.
        - `데이터 작업`은 추출, 변환 및 데이터 모델 로드 "작업"을 `결합`하고 이를 `순서대로 실행`할 수 있도록 합니다.
        - 데이터 작업이 여러 개 있을 때의 이점은 서로 다른 실행 일정을 할당 할 수 있다는 것입니다 . 이는 특정 테이블을 다른 테이블보다 더 자주 추출하고 변환하고 로드해야 하는 경우 관련이 있습니다.
            - 데이터 모델 - 마지막으로 다양한 작업이 준비되면 데이터를 하나 이상의 데이터 모델 로 가져옵니다 .
            - 논리적으로 말하면 데이터 모델을 생성한 후에만 데이터 모델 로드 작업을 생성할 수 있습니다.
            - 데이터 모델은 EMS의 모든 다운스트림 작업의 기초 역할을 합니다. 데이터 모델은 하나의 데이터 풀 내의 여러 연결 및 데이터 작업에서 테이블을 가져올 수 있습니다 . (참고: 필요한 경우 데이터 풀 간에 데이터를 공유할 수 있습니다. 이에 대해서는 나중에 자세히 설명합니다.)
            
다음은 계층 구조를 더 잘 캡처하는 시각적 개체입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/f4nylcrrz3i5-image.png)

데이터 통합 ​​UI로 작업할수록 구조와 데이터 흐름에 미치는 영향이 더 명확해지기를 바랍니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6ri94y6tw0r5-image.png)

마지막으로 각 요소에 포함된 내용을 요약한 작은 표가 있습니다.

|||
|---|---|
|데이터 풀|	하나 이상의 데이터 연결 호스팅|
|데이터 연결|	하나 이상의 데이터 작업 포함|
|데이터 작업|	추출, 변환 및 데이터 모델 로드를 위한 " 작업 " 포함|
|데이터 모델|	하나의 데이터 풀에 있는 모든 연결에서 데이터 가져오기|

#### 데이터 통합에서 데이터 구조화

이 구조를 보면 관련된 `모든 프로세스와 시스템이 하나의 Data Pool 안에 있도록 최선`을 다해야 합니다. 마찬가지로 관련 없는 프로세스를 별도의 데이터 풀에 보관해야 합니다. 예를 들어 모든 SAP ERP 프로세스에 대해 하나의 데이터 풀을 생성하고 IT 서비스 관리 프로세스에 대해 또 다른 데이터 풀을 생성할 수 있습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0xlz0mfxss7e-image.png)

경우에 따라 특정 사용자 또는 사용자 그룹의 데이터에 대한 액세스를 제한하기 위해 서로 다른 지역 또는 법인에 대해 별도의 데이터 풀을 만드는 것이 좋습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cec96h3taj5y-image.png)

## 5 요약

### 51 배운 내용 확인 및 요약

이 과정은 모두 연결에 관한 것입니다 . 다음은 우리가 다룬 내용을 요약한 것입니다.

- 연결 방법 —Celonis는 다양한 사용 사례를 위한 다양한 연결 방법을 제공합니다.
    - 프로세스 커넥터
    - 추출기(데이터 연결)
    - 추출기 빌더
    - 파일 업로드
    - 데이터 푸시 API
    - 셀록스트랙터
- 연결 준비 - 연결을 위해 시스템을 준비하는 방법은 연결 유형에 따라 다릅니다.
    - 폐쇄형 환경 의 경우 일반적으로 다른 준비 단계와 함께 온프레미스 추출기 서버가 필요합니다.
    - 실시간 연결 의 경우 시스템에 따라 변경 로그, 트리거 및 기타 단계가 필요합니다.
- 데이터 통합 ​​구조 - 데이터 풀은 데이터 통합의 최상위 구조 요소이며 기본적인 모범 사례는 관련 프로세스를 동일한 데이터 풀에 유지하는 것입니다. 데이터 풀 내에서 다음 작업을 수행합니다.
    - 데이터 연결,
    - 데이터 작업,
    - 작업 - 추출, 변환, 데이터 모델 로드,
    - 및 데이터 모델.
    
피드백 페이지를 방문하는 것을 잊지 마십시오 . 귀하의 피드백은 선택 사항 이지만 대단히 감사합니다. 
