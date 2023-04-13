---
title: 040204 Boost your EMS SQL Transformations
author: JUNG YoungKyun
date: 2023-04-10
category: 37 celonis
layout: post
---

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# Get Data into the EMS

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/q_100,a_exif,c_crop,x_0,y_0,w_800,h_450/a_exif,c_fill,w_800,h_450/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/e2jaa6l2jb4l-course_Get-Data-into-EMS_detail.jpg)

# 02. Refine your Data Pipeline

# Boost your EMS SQL Transformations

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fit,w_440,h_200/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/nrzz2n36izk3-skill-area_Configure_catalogue1.jpg)


## 1 변환 모범 사례

### 11 소개
#### 111 학습 목표

- 쿼리 성능 예측
- 읽기 쉽고 성능이 뛰어난 SQL 변환 작성
- 일반적인 반패턴을 식별하고 Celonis 플랫폼 내에서 기존 SQL 변환을 최적화합니다.
- 추가 모범 사례 리소스에 익숙해지기

#### 112 버티카 소개

Celonis EMS에 작성된 모든 SQL 코드는 분석 데이터베이스 관리 소프트웨어인 Vertica 에서 처리됩니다 . 
Vertica는 ANSI STANDARD SQL 구문을 완벽하게 지원하므로 
`표준 SQL을 사용하여 변환 스크립트를 생성`할 수 있습니다.

Vertica 데이터베이스 는 예를 들어 데이터 저장 및 검색 방식에서 
작업한 다른 DBMS(데이터베이스 관리 시스템)(MSSQL, Oracle DBMS)와 몇 가지 차이점이 있습니다 . 
이 과정의 끝에서 공유되는 리소스를 통해 이러한 차이점에 대해 자세히 알아볼 수 있습니다.

#### 113 이 과정의 테이블

이 과정에서 대부분의 쿼리 예제는 `SAP ECC 테이블을 기반`으로 합니다 . 
여기에서 특정 테이블 및 열에 대한 추가 정보를 찾을 수 있습니다 . 
걱정하지 마세요. 이 과정의 모범 사례는 Vertica 데이터 레이크를 사용하는 모든 프로세스 커넥터 에 적용됩니다 .

### 12 추출 모범 사례
#### 121 필요한 데이터만 추출

최적화된 데이터 파이프라인은 `필요한 데이터 만 추출하고 변환`합니다 . 
추출 최적화를 건너뛰면 데이터 파이프라인에 매우 해로운 영향을 미칠 수 있습니다. 이는 다음으로 이어집니다.

- 더 높은 스토리지 요구 사항(라이선스의 APC에 영향을 미침)
- 변환에서 잘못된 관행의 심각한 결과(예: SELECT *)
- 추출, 변환 및 데이터 모델 로드 시 로드 시간에 부정적인 성능 영향

다음은 필요한 데이터만 추출할 수 있는 몇 가지 방법입니다.

- 프로세스 커넥터 조정

    기본적으로 커넥터는 많은 프로세스 변형을 수용하기 위해 많은 열을 추출합니다. 커넥터에서 표준 구성을 검증 및 조정하고 프로세스에 필요한 테이블과 열만 추출하도록 합니다.

- 큰 테이블 자르기

    중요한 테이블에는 종종 많은 수의 열이 포함됩니다. SAP의 경우 LIPS, VBRP, VBAP, EKPO, BSEG, LIKP, EKKO, VBAK와 같은 테이블에는 150-380개의 열이 포함됩니다. 실제로는 열의 작은 부분만 필요할 수도 있습니다.

- 추출 필터 사용

    가능하면 시간 필터, 조인 필터 또는 추가 필터를 기반으로 제외할 수 있는 데이터를 결정하십시오. 이렇게 하면 추출 시 직접 데이터 양을 줄일 수 있습니다.

### 13 성능 추정
#### 131 쿼리 실행 계획(EXPLAIN)

Vertica에 제출된 각 쿼리에 대해 Vertica 쿼리 최적화 프로그램은 
일련의 단계와 데이터에 액세스하고 결과를 계산하는 데 필요한 작업인 쿼리 실행 계획을 구성합니다.

쿼리 실행 계획을 보려면 SELECT, UPDATE 또는 DELETE 문 앞에 `EXPLAIN을 삽입하기만 하면 됩`니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cqknviz9dhs9-image.png)

쿼리 실행 계획(EXPLAIN)을 사용하는 것은 쿼리를 `최적화하는 데 필수`적입니다 . 
쿼리의 비효율적인 부분을 식별하고 적용하는 영향 개선 사항을 검증하는 데 도움이 됩니다. 
전체 쿼리 실행 계획을 분석하는 것이 압도적으로 보일 수 있지만 대부분의 Celonis 변환 시나리오에서는 
다음 사항에 집중하면 충분합니다.

- 예상 쿼리 비용
- 조인 유형,
- 및 "NO STATISTICS" - 누락된 테이블 통계 표시기.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/cx4bo83h833s-image.png)

#### 132 예상 쿼리 비용

뭐야?

"경로"라고도 하는 각 `쿼리 단계에 대해` Vertica는 성능 `비용을 추정`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rwvgcnj50vz1-image.png)

이 추정치는 `근사치입니다` . 계산된 비용은 일반적으로 쿼리 실행 시간을 반영하지만 실제 실행 시간을 추정하지는 않습니다.

예를 들어 옵티마이저가 플랜 A 비용이 플랜 B보다 2배 많다고 판단하면 플랜 A를 실행하는 데 더 많은 시간이 필요할 수 있습니다. 그러나 이것은 계획 A가 계획 B보다 정확히 두 배 더 오래 실행된다는 것을 반드시 나타내지는 않습니다.


로그에서 실제 런타임 확인

정확도가 더 필요한 경우 쿼리를 실행한 후 이벤트 수집 로그에서 `직접 런타임을 확인할 수도 있`습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/n33gzk60rx4a-image.png)

#### 133 조인 유형

병합 조인

두 테이블이 모두 조인 열에서 미리 정렬된 경우 Vertica 최적화 프로그램은 `병합 조인을 선택`합니다. 
이 조인은 해시 조인보다 훨씬 빠르고 훨씬 적은 리소스를 사용합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/5hhe248j1kr0-MergeJoin.gif)

해시 조인

조인 열에서 테이블이 `정렬되지 않은 경우 옵티마이저는 해시 조인을 선택`합니다. 
이 조인은 조인을 용이하게 하기 위해 Vertica가 메모리에 정렬된 해시 테이블을 구축해야 하기 때문에 
병합 조인보다 더 많은 메모리를 소비합니다 . 
해시 조인 알고리즘을 사용하여 Vertica는 하나의 테이블(즉, 내부 테이블)을 선택하여 
조인 열에 인메모리 해시 테이블을 구축합니다. 
이해하기 어려운 것처럼 들리신다면 다음은 해시 조인을 위해 백엔드에서 어떤 일이 발생하는지에 
대한 아이디어를 제공하는 단순화된 그래픽입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/impvq917rdlz-HashJoin.gif)

그렇다면 어떤 조인 유형이 적절할까요?

일반적으로 `가능할 때마다 병합 조인을` 목표로 합니다 . 특히 매우 큰 테이블을 조인할 때는 더욱 그렇습니다.

실제로 변환 쿼리에는 여러 테이블 조인이 포함되는 경우가 많습니다. 
따라서 조인 열에서 테이블을 사전 정렬해야 하므로 모든 테이블을 병합 유형으로 조인하는 것은 거의 불가능합니다 .

병합 조인은 항상 더 효율적이며 해시 조인보다 훨씬 적은 메모리를 사용합니다 . 그러나 반드시 더 빠른 것은 아닙니다. 
데이터 세트가 매우 작은 경우 해시 조인이 더 빠르게 처리될 수 있지만 이는 매우 드뭅니다.

병합 조인을 얻기 위해 정렬하는 방법은 무엇입니까?

제대로 정렬하려면 다음 중 하나를 수행해야 합니다.

- CREATE TABLE 문의 시작 부분(예: MANDT, VBELN, POSNR)에 키 열을 배치합니다 .
- 또는 CREATE TABLE 문의 끝에 명시적 ORDER BY { key columns } 절을 추가합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rdozcr3fqvl1-image.png)

#### 134 배운 내용 확인 - 성능 추정

### 14 테이블 통계
#### 141 테이블 통계 개요
통계의 영향
테이블에 통계가 있는지 확인
배운 내용 확인 - 테이블 통계
