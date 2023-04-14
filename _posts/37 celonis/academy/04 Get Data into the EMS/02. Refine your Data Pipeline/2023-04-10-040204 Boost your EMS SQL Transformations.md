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

그들은 무엇인가?

테이블 통계는 쿼리 최적화 프로그램이 더 나은 결정을 내리는 데 도움이 되는 `테이블의 분석 요약`입니다 . 
테이블 통계는 `쿼리 성능을 크게 향상시켜` 쿼리 실행 시간을 50% 이상 줄입니다 .


언제 추가합니까?

Celonis `추출기`를 사용하여 소스 시스템에서 추출된 테이블(즉, VBAP, VBAK, EKKO, EKPO와 같은 "원시" 테이블)의 경우 
추출 후 각 테이블에 대한 `테이블 통계가 자동으로 수집됩`니다.

`변환 단계`에서 생성된 추가 테이블(예: 임시 조인 테이블 TMP_CDHDR_CDPOS 또는 사용자가 생성한 데이터 모델 테이블)의 경우 
명시적으로 `통계를 생성해야 합`니다 . 일반적으로 `변환에서 생성되고 사용되는 모든 테이블` 에 `통계를 추가하는 것이 좋`습니다 .

또한 INSERT, DELETE 또는 UPDATES로 `기존 테이블을 크게 변경하는 경우` `통계를 새로 고치는 것이 좋`습니다.

통계를 만들거나 새로 고치는 방법

테이블을 생성하고 채우는 각 CREATE TABLE 문 다음에 또는 `테이블의 내용을 크게 변경한 후에` `이 코드를 추가`하기만 하면 됩니다 .

```
SELECT ANALYZE_STATISTICS ('TABLE_NAME');
```

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/l8f6nqopvw45-image.png)

데이터베이스 는 `변환` 또는 `쿼리가 실행`될 때 `테이블 통계를 수집`합니다.

#### 142 통계의 영향

동일한 쿼리라도 관련된 테이블에 대한 `통계가 존재하는지 여부에 따라` 쿼리 `비용과 성능이 상당히 다를 수 있`습니다 . 
예제를 통해 테이블 ​​통계가 쿼리 실행 계획에 어떤 영향을 미치는지 살펴보겠습니다.

테이블 통계가 없는 쿼리 비용

이 예에서는 쿼리 실행 계획에서 "NO STATISTICS" 표시기로 볼 수 있듯이 
통계 없이 임시 조인 테이블 O2C_VBFA_V를 생성했습니다. 통계가 없으면 예상 쿼리 비용은 5K입니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/pmjf25bcx1n1-image.png)

테이블 통계의 쿼리 비용

이 두 번째 예에서는 O2C_VBFA_V 테이블에 대한 통계를 수집한 후 동일한 쿼리에 대한 쿼리 실행 계획 및 예상 비용을 확인합니다.
 "NO STATISTICS" 표시가 더 이상 나타나지 않습니다. 비용은 5K에서 137로 증가했습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/h5ij6s2jzcsr-image.png)

테이블 통계가 중요한 이유는 무엇입니까?

많은 이점 중에서 테이블 통계는 해시 조인이 있는 `쿼리 실행 계획에 특히 중요합`니다. 
쿼리 최적화 프로그램이 더 작은 테이블을 선택하여 해시 테이블을 만들 수 있습니다(더 큰 테이블 대신). 
대부분의 시나리오에서 이것은 " inner join did not fit into memory " 오류를 방지하고 성능을 향상시킵니다 .

#### 143 테이블에 통계가 있는지 확인

`통계가 없는 테이블을 확인`하는 두 가지 주요 방법이 있습니다.

1. EXPLAIN 사용

    쿼리에 대해 EXPLAIN 문을 실행하고 테이블 이름 옆에 " `NO STATISTICS " 가 있으면 해당 테이블에 통계가 없는 것`입니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/wxcgz1i8gin0-image.png)

2. "projections" 표 확인

    한 번에 모든 테이블을 확인하려면 `프로젝션 시스템 테이블을 확인`하십시오
    (이 Vertica 테이블에 대한 자세한 내용은 여기 참조 ).
    
    ```
    SELECT anchor_table_name AS TableName 
    FROM projections 
    WHERE has_statistics = FALSE ;
    ```
   
    이 쿼리는 데이터 풀에서 `통계가 누락된 모든 테이블 목록을 반환`합니다.

대부분의 경우 `활동 테이블은` 다른 변환의 조인에 사용되지 않으므로 `통계가 필요하지 않습니`다. 
즉, 확실하지 않은 경우 모든 테이블에 통계를 추가해도 문제가 되지 않습니다.

필요할 때 통계 추가

이미 배운 것처럼 `통계가 없는 테이블을 찾은 경우 다음을 추가해야 합니`다.

```
SELECT ANALYZE_STATISTICS ('TABLE_NAME');
```

해당 테이블을 생성하는 변환에. `그러면 데이터베이스가 백그라운드에서 테이블 통계를 수집합`니다.

#### 144 배운 내용 확인 - 테이블 통계

### 15 일반 모범 사례
#### 151 읽기 쉽고 유지 관리 가능한 SQL 코드 작성

전문적인 SQL 코드를 작성하려면 서식 지정 모범 사례를 따라야 합니다. 
적절한 형식을 사용하면 SQL 코드를 더 쉽게 읽고, 이해하고, 업데이트할 수 있습니다.

SQL 스크립트를 개발하고 유지 관리하는 팀으로 작업하는 경우 서식 표준을 따르면 오류를 방지하고 
시간을 절약하는 데 큰 도움이 됩니다. `좋은 SQL 에티켓은 다음과 같습`니다.

- SELECT 문
    - SELECT columns, `SELECT *` 쓰지마세요
    - `SELECT DISTINCT` 쓰지마세요. (more on this later)
    - SELECT 다음에 3개 이상의 열이 있는 경우 각각 별도의 줄에 배치하여 구분합니다.
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/at1fb4vg7ngu-image.png)
- JOIN 문
    - 연산자 `INNER JOIN`, `LEFT JOIN`등에 새 줄을 사용하십시오.
    - 모든 중요한 조건이 서로 아래에 있도록 JOIN 조건은 1=1로 시작해야 합니다.
    - 둘 이상의 조건이 있는 경우 또는 조건 연산자 앞에 새 들여쓰기 줄을 사용 `AND`합니다 `OR`.
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/36rfl8yt0ngn-image.png)
- 변환당 하나의 쿼리 (One Query per Transformation)
    
    변환의 쿼리 수를 제한합니다. 
    이상적으로는 하나의 변환(예: "전달 문서 생성")이 하나의 쿼리만 포함하거나 `하나의 목적만 제공해야 합`니다 . 
    모든 관련 보조 쿼리 또는 임시 테이블은 이전의 별도 변환의 일부여야 합니다.
    
    단일 변환 내에 여러 쿼리가 있으면 코드를 디버깅하고, 쿼리 성능을 측정하고, 잠재적으로 문제를 일으킬 수 있는 쿼리를 식별하기가 어렵습니다.
    
- 테이블 명명 규칙 (Table Naming Conventions)
    
    테이블과 뷰의 이름을 다음과 같이 지정하는 것이 좋습니다.
    
    |Object	Naming |Convention	|Example|
    |---|---|---|
    |Activity Table	|_CEL_ProcessShortName_ACTIVITIES	|_CEL_O2C_ACTIVITIES|
    |Temporary/ Auxiliary Table	|TMP_ProcessShortName_Table1_Table2	|TMP_O2C_CDHDR_CDPOS|
    |Data Model views/tables	|ProcessShortName_Table	|O2C_VBAP|
    
- 대문자 / 대문자 (Capital Letters / Uppercase)

    쿼리를 작성할 때 다음과 같은 경우 대문자를 사용하십시오.
    
    1. SELECT, FROM, WHERE 등과 같은 SQL 키워드,
    2. CAST, SUBSTRING, AVG 등과 같은 SQL 함수
    3. LIKE, OR, BETWEEN 등과 같은 SQL 연산자
    
    피하다
    ```
    select id, name from users where name like 'm%';
    ```
    사용해보기
    ```
    SELECT id, name FROM users WHERE name LIKE 'm%';
    ```
    
- 들여쓰기 및 새 줄 (Indentation & New Lines)
    
    다음을 권장합니다.
    
    - 키워드 뒤에 `들여쓰기`
    - `쉼표 뒤에` 있는 각각의 개별 열에 `새 줄`을 사용하십시오.
    
    피하다
    
    ```
    SELECT tableA.column1, tableA.column2 ,tableA.column3,tableA.column4,
    tableB.column1,tableB.column10 FROM tableA INNER JOIN tableB
    ON 1=1 and tableA.key_column=tableB.key_colum WHERE tableA.column30 < 10
    ```  
  
    사용해보기
    
    ```
    SELECT tableA.column1
         ,tableA.column2
         ,tableA.column3
         ,tableA.column4
         ,tableB.column1
         ,tableB.column10
    FROM tableA
    INNER JOIN tableB ON 1=1
         AND tableA.key_column=tableB.key_column
    WHERE
        tableA.column30 < 10
    ```
    
- 테이블 별칭 (Table Aliases)

    다음은 테이블 별칭을 사용할 때 권장되는 사항입니다.
    
    - 여러 테이블을 쿼리할 때 `select 문에서 별칭을 사용`합니다.
    - `AS`코드를 더 쉽게 읽을 수 있도록 별칭을 만드는 키워드를 포함합니다 .
    - select 문에 해당하는 각 열에 대한 `테이블 별칭을 포함합`니다. 
    이렇게 하면 판독기가 어떤 열이 어떤 테이블에 속하는지 구문 분석할 필요가 없습니다.
    
    여기에서 FROM 아래에 정의되고 SELECT 문에서 사용되는 테이블 별칭을 볼 수 있습니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/bunbe1qrvu5a-image.png)

- 코멘트(Comments)

    복잡하거나 비표준 쿼리를 생성하는 경우 코드의 다른 부분을 설명하는 `유용한 주석을 포함`합니다. 
    쿼리 주석은 쿼리를 유지 관리해야 하는 모든 `사람`(자신 포함)`에게 도움이 됩`니다.
    
    의견을 짧고 간결하게 유지하십시오.

#### 152 JOIN 대신 존재하는 곳

`WHERE EXISTS` instead of `JOIN`

차이점은 무엇입니까?

|JOIN|		WHERE EXISTS|
|---|---|
|테이블을 다른 테이블의 추가 필드와 `결합하는 데 사용`됩니다 .	|테이블 또는 하위 쿼리에 `관련 레코드가 있는지 테스트하는 데 사용`됩니다 .|

JOIN 대신 WHERE EXISTS를 사용하는 이유는 무엇입니까?

WHERE EXISTS는 대부분의 경우 JOIN보다 `성능이 좋`습니다. WHERE EXISTS를 사용하면 SQL 엔진이 조건이 충족되는 레코드를 찾는 즉시 `추가 레코드 처리를 중지`합니다.

JOIN 대신 WHERE EXISTS를 사용해야 하는 경우

경우에 따라 다른 테이블에 해당 레코드가 있는 레코드만 원할 수도 있습니다. 
따라서 관련 레코드를 필터링 해야 합니다 . 
관련 레코드의 `존재 여부 만 확인하고` 다른 곳(예: SELECT 또는 다른 JOIN)에서 두 번째 테이블의 `열이 필요하지 않은 경우 WHERE EXISTS를 사용해야 합`니다 .

예를 들어 `책과 저자`라는 두 개의 `간단한 테이블`을 상상해 보십시오. 
책을 쓴 `저자`만 선택하고 `책 자체에 대한 정보는 필요하지 않`습니다. 
이 경우 두 테이블을 조인할 필요가 없습니다. 
적절한 조건과 함께 WHERE EXISTS를 사용하여 레코드의 `존재를 확인하기만 하면 됩`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/orikpbcdkwpq-image.png)

#### 153 DISTINCT - 개요

SELECT DISTINCT는 무엇을 위한 것입니까?

SELECT DISTINCT는 결과 집합에서 고유한 값만 반환합니다. 
쿼리가 복잡한 경우 중복 레코드를 방지하기 위해 DISTINCT를 습관으로 추가할 수 있습니다. 
일반적으로 DISTINCT를 `피 하거나` 드문 경우에만 사용해야 합니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/dix467ge78sn-image.png)

SELECT DISTINCT를 피하는 이유는 무엇입니까?

DISTINCT는 데이터베이스가 `매우 비용이 많이 드는` 
중복 제거를 수행하도록 강제하므로 `쿼리 런타임, 메모리 소비가 크게 확장`되고 `쿼리 실패 위험이 증가`합니다. 
필요한 결과를 얻을 수 있지만 비용이 너무 높고 데이터 세트 또는 쿼리와 관련된 문제를 마스킹할 가능성이 높습니다 .

대안

기본적으로 DISTINCT를 사용하는 대신:

1. 중복 데이터 세트 확인
2. 불완전한 조인 또는 데카르트 곱과 같은 중복이 발생하지 않도록 `테이블 조인을 확인`하십시오 .

#### 154 DISTINCT 피하기 - 중복 확인

기본 키에 대한 명확성

중복을 확인하려면 생성하려는 테이블, 보기 또는 활동의 `기본 키를 알아야 합`니다 . 
특히 키가 종종 비즈니스 로직을 기반으로 하는 활동의 경우 이는 어려울 수 있습니다.

중복 확인 방법

먼저 `기본 키를 기반으로 고유한 행을 계산 하`고 `합계`를 `모든 행의 일반적인 수`와 `비교`하여 테이블, 보기 또는 활동에 중복 항목이 있는지 확인합니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rqwcadv0obnt-image.png)

결과가 일치하면 중복이 없으며 DISTINCT를 사용할 필요가 없습니다.

결과가 일치하지 않으면 다음을 수행할 수 있습니다.

- 기본 키를 기반으로 `올바른 추출을 보장하기 위해 추출 논리를 수정`하거나
- 테이블에서 중복을 제거하십시오.

참고: 대표 데이터 세트에 대해 중복 확인을 수행해야 합니다. 
작은 데이터 세트로 작업하는 경우 레코드가 증가함에 따라 발생할 수 있는 중복을 예상해야 합니다.

테이블에서 중복 제거

원시 데이터에 중복이 있는 이유를 조사하십시오. 패턴을 감지할 수 있으면 `DELETE 문을 직접 작성하여 이러한 사례를 정리`할 수 있습니다 .

그렇지 않으면 기본 키가 동일한 항목을 감지하기 위한 행 번호를 포함하여 원시 테이블을 기반으로 테이블을 만들 수 있습니다 . 
아래 예에서 "BSIK" 테이블의 중복은 `테이블의 기본 키를 기준으로 1보다 큰 행` 번호로 표시됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/ir49nudc2ll5-image.png)

```
CREATE TABLE BSIK_CLEAN AS(
SELECT
    ROW_NUMBER() OVER(
        PARTITION BY 
        BSIK.MANDT
        , BSIK.BUKRS
        , BSIK.BELNR
        , BSIK.GJAHR
        , BSIK.BUZEI 
        ORDER BY 
        BSIK.MANDT
        , BSIK.BUKRS 
        , BSIK.BELNR
        , BSIK.GJAHR
        , BSIK.BUZEI
        ,_CELONIS_CHANGE_DATE DESC
    ) AS NUM
    , BSIK.*
FROM BSIK AS BSIK
);

DELETE FROM BSIK_CLEAN WHERE NUM > 1;
```

위의 쿼리를 이해하는 데 잠시 시간을 내십시오. ROW_NUMBER()에 대한 자세한 내용은 이 Vertica 기사를 참조하십시오 .

중복 제거된 테이블(BSIK_CLEAN)에서 테이블 열의 하위 집합(이 경우 BSIK)만 필요한 경우 BSIK.* 대신 특정 열을 선택합니다.

생성된 테이블(예제에서는 BSIK_CLEAN)을 사용할 때 다음 중 하나에 WHERE 문을 추가해야 합니다.

- BSIK_CLEAN에서 행 번호가 1인 항목만 선택(NUM = 1)
- 또는 행 번호가 1보다 큰(NUM > 1) 테이블에서 모든 항목을 삭제합니다. 위의 예에서는 NUM이 1보다 큰 모든 항목이 중복되므로 삭제합니다.

#### 155 DISTINCT 방지 - 테이블 조인 확인

DISTINCT 및 Multiple Joins을 사용한 쿼리

이 예에서는 두 개 이상의 테이블을 조인한 후 쿼리에 DISTINCT가 필요한지 여부를 확인하려고 합니다 . 
"청구 문서 만들기"와 같은 활동을 만드는 변환에서 여러 조인을 자주 볼 수 있습니다. 
이 쿼리에는 `두 조인과 함께 SELECT DISTINCT가 있습`니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/c28gnihva58p-image.png)

DISTINCT가 필요한지 확인

쿼리를 약간 변경하여 레코드 수를 가져오겠습니다. 
아래 스크린샷과 같이 원본 쿼리를 하위 쿼리에 넣고 `SELECT COUNT(*)를 실행`합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/vv8zscwjokwg-image.png)

주어진 쿼리는 DISTINCT 명령이 사용된 125.001개의 레코드를 보여줍니다. 
이제 `DISTINCT 절을 주석 처리하고 동일한 쿼리`를 다시 실행한 후 결과를 비교해 보겠습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/0zvhi089txy1-image.png)

쿼리는 동일한 수의 레코드를 반환하므로 이 경우 DISTINCT가 필요하지 않습니다. 데이터 품질을 방해하지 않고 쿼리에서 제거할 수 있습니다.

두 개 이상의 테이블을 조인한 후 DISTINCT가 필요한 경우 어떻게 합니까?

우선, DISTINCT가 불가피해 보이는 이유를 확인하십시오. 그런 다음 그에 따라 접근할 수 있습니다.

1. 테이블 조인은 필터링 목적으로만 사용됩니다.

    이미 다뤘습니다. 
    때로는 다른 테이블에 해당 레코드가 있는 행만 원할 수도 있습니다. 
    그렇다면 이러한 관련 레코드에 대한 쿼리만 필터링하면 됩니다. 
    조인으로 인해 중복이 발생하지만 필터링 목적으로만 필요한 경우 WHERE EXISTS로 바꿀 수 있습니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/qw7jcsyu3zfx-image.png)
    
2. 불완전하거나 잘못된 JOIN

    불완전한 조인은 조인하려는 테이블 간에 원치 않는 1:n 또는 m:n 관계가 있음을 의미합니다.
    
    이상적으로는 만들려는 테이블, 보기 또는 활동의 `올바른 기본 키를 찾아야 합`니다. 
    둘째, 모든 테이블이 기본 키와 1:1 또는 1:n 관계를 갖도록 해야 합니다 . 
    `기본 키와 관계가 모두 올바른 경우 중복 항목이 없`습니다.
    
    전체 기본 키를 사용할 수 없거나 관계로 인해 중복이 발생하는 경우 다음 두 가지 방법으로 불완전한 조인을 처리할 수 있습니다.
    
    1. WHERE EXISTS: 당신은 이미 이것에 익숙합니다.
    2. SUBQUERY: 결과 테이블에서 중복을 방지하기 위해 조인에 `필요한 열과 결과 테이블에 추가하려는 열만 하위 선택`할 수 있습니다. 
    각 조인 키에 대해 여러 레코드가 있는 경우 집계 함수(예: MIN, MAX, AVG)를 사용하고 조인 열을 그룹화할 수 있습니다. 
    이것은 약간 복잡하므로 다음은 접근 방식을 설명하는 비디오입니다.

    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/6wxbux7987ka-image.png)

#### 156 테이블 조인 유효성 검사

`조인을 확인하는 것`은 `DISTINCT를 피하는 데 중요한 부분`입니다. 
동시에 조인의 유효성을 검사하여 성능을 최대화 하고 쿼리 속도를 늦추거나 부정확한 데이터를 유발할 수 있는 모든 것을 피해야 합니다. 
확인해야 할 사항은 다음과 같습니다.

- Join Keys

    - 전체 키를 사용하여 테이블이 `제대로 결합되었는지 확인`하십시오 . 그렇지 않으면 조인으로 인해 중복/또는 직교 곱이 발생할 수 있습니다.
    - `키 열이 모든 레코드에 대해 동일하더라도 제외하지 마십`시오(예: MANDT/클라이언트 ID).
    - 가능한 경우 `JOIN 조건에서 변환 함수(예: CAST(), RIGHT(), SUBSTRING() 등)를 사용하지 마십`시오.
    
    예를 들어 SAP 테이블의 경우 Leanx 에서 키 열을 찾을 수 있습니다 . 결합 키 정보에 대한 소스 시스템의 문서를 항상 확인하십시오.

- Table Filters

    1. `관련 레코드만 처리되도록 적절한 필터를 적용`합니다.
    2. WHERE 대신 `JOIN 내에서 테이블을 필터링`합니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/hll6mzst4vfn-image.png)

- all Tables의 필요성
    
    모든 테이블이 `의도적으로 조인되었는지 확인`합니다.
    
    1. SELECT 문에서 실제로 `필요하고 사용되는 테이블만 조인`합니다.
    SELECT 또는 WHERE 절에서 열을 제거하거나 주석 처리하는 경우 `중복 조인을 제거해야 합`니다.
    2. 테이블이 `필터링 목적으로만 조인된 경`우 JOIN 대신 `WHERE EXISTS를 사용`하십시오.

#### 157 배운 내용 확인 - 일반 모범 사례

### 16 임시 조인 테이블

#### 161 임시 조인 테이블 - 개요

유사한 조인을 여러 번 생성

경우에 따라 변환에서 동일한 조인을 여러 번 만들고 실행해야 합니다 . 
예를 들어 프로세스 커넥터에는 여러 문서(예: 판매 주문)에서 수행된 레코드 변경과 관련된 활동을 생성하는 여러 변환이 포함되는 경우가 많습니다. 
이러한 변환은 별도의 변환이지만 각각 문서 헤더 변경(CDHDR)과 라인 항목 변경(CDPOS) 테이블 간에 동일한 조인이 필요합니다.

각 변환에 대해 이 두 테이블을 `반복적으로 조인하는 대신` `임시 조인 테이블을 사용하여 쿼리 결과를 저장하고 재사용` 할 수 있습니다 . 
이렇게 하면 `값비싼 쿼리 처리 시간을 절약`할 수 있을 뿐만 아니라 코드를 더 쉽게 읽고 유지 관리할 수 있습니다.

임시 조인 테이블은 어떻게 작동합니까?

1. 먼저 별도의 변환에서 `임시 조인 테이블 (예: TMP_O2C_CDHDR_CDPOS) 을 만듭`니다 . 
여기에는 자주 조인되는 테이블과 이후 변환에 필요한 해당 열이 포함되어야 합니다.
2. `임시 조인 테이블을 사용`하면 조인을 한 번만 실행 하고 쿼리 결과를 `임시로 저장합`니다 .
3. 다음으로 변환에서 `반복되는 JOIN 문을 임시 조인 테이블로 바꾸기만 하면 됩`니다.
4. `변환이 끝날 때` 정리 변환을 추가하여 임시 조인 테이블을 `삭제합`니다. 
임시 조인 테이블의 이러한 사전 예방적 삭제는 Celonis에만 해당됩니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/70q8w5qjca1p-image.png)

예: SAP 프로세스 커넥터에서 CDPOS의 CDHDR 테이블 조인

우리는 종종 O2C(Order-to-cash), P2P(Purchase-to-pay), AR(Accounts receivable) 및 AP(Accounts payable) 프로세스 커넥터에서 
CDHDR 및 CDPOS 테이블을 조인합니다. 다른 문서 변경 로그와 관련된 활동을 추가하려면 이 조인이 필요합니다. 
이 조인을 다루는 임시 테이블을 만들어 보겠습니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/wcna4v4ef30n-image.png)

이제 위에서 설명한 대로 기존 변환에서 CDHDR 및 CDPOS의 모든 조인을 TMP_CDHDR_CDPOS 테이블에 대한 조인으로 바꿀 수 있습니다.

#### 162 잘 설계된 임시 테이블

변환 단계에서 임시 조인 테이블(예: TMP_CDPOS_CDHDR)을 생성하면 여러 변환에서 동일한 테이블을 `반복적으로 조인할 필요성을 줄이는 데 도움이 됩`니다.

임시 테이블을 생성할 때 `임시 테이블의 디자인이 쿼리 성능에 상당한 영향을 미친다`는 점을 염두에 두십시오 . 
여러 변환에서 재사용하기 위해 임시 테이블을 생성합니다 . 
결과적으로 `잘 설계된 임시 테이블은 성능을 크게 향상시키는 반면` `잘못 설계된 임시 테이블은 전체 데이터 파이프라인에 병목 현상을 일으키`는 경우가 많습니다.

다음 질문을 사용하여 임시 테이블을 올바르게 설계했는지 확인하십시오.

- 임시 테이블이 제대로 정렬되어 있습니까?

    당신이 기억한다면 적절하게 정렬하면 병합 조인이 용이해집니다. 따라서 다음을 수행해야 합니다.
    
    - `CREATE TABLE 문의 시작 부분에` `키 열(예: MANDT, VBELN, POSNR)을 배치`합니다.
    - 또는 CREATE TABLE 문의 `끝에` 명시적 `ORDER BY { key columns } 절을 추가`합니다.
    
    ![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/rdozcr3fqvl1-image.png)
    
    정렬은 이 테이블을 사용하는 이후 변환에서 `보다 효율적인 병합 조인을 보장`합니다.

- 모든 열과 조인이 필요합니까?

    - 임시 조인 테이블에는 `필요한 조인과 열만 포함`되어야 하며 그 이상은 포함되지 않아야 합니다. 
    SELECT 또는 WHERE 절에서 열을 제거하거나 주석 처리하는 경우 `중복 조인을 제거해야` 합니다.
    - 사용하지 않는 열과 조인을 추가하면 스토리지와 쿼리 성능 모두에 부정적인 영향을 미칠 수 있습니다.

- 사용자 지정 또는 계산된 필드가 있습니까?

    테이블에 사용자 정의 또는 계산된 필드가 포함되어 있거나 
    다른 테이블과의 조인에 필수적이지 않은 연결된 열이 있는 경우 해당 열을 테이블 시작 부분에 배치하지 마십시오 . 
    그렇게 하면 Vertica가 쿼리를 실행하는 동안 추가 작업(예: 해시 테이블 생성)을 수행해야 할 수 있으므로 실행 시간이 크게 늘어납니다.

- 이 임시 테이블에 대한 테이블 통계가 수집됩니까?

    임시 테이블을 생성하는 각 변환에는 ANALYZE_STATISTICS 문이 포함되어야 합니다.
    
    SELECT ANALYZE_STATISTICS('TableName');를 추가하기만 하면 됩니다 . 
    테이블을 데이터로 채우는 각 명령문 다음에. 
    데이터베이스는 변환 또는 쿼리가 실행된 후 통계를 수집합니다.

#### 163 잘 설계된 임시 테이블의 예
#### 164 배운 내용 확인 - 임시 조인 테이블

### 17 테이블과 뷰의 사용

#### 171 테이블과 뷰

비교

변환에서 테이블 또는 보기를 사용할 시기를 결정하는 것이 어려울 수 있습니다. 다음은 테이블과 뷰가 수행하는 작업을 비교한 것입니다.

|||
|---|---|
|Table|	실행된 쿼리의 지속된 결과를 저장합니다 .|
|View|	뷰에 액세스할 때마다 실행되는 쿼리문을 저장합니다.|

사용 시기

Celonis EMS에서 변환 쿼리를 작성할 때 종종 임시 조인 테이블과 뷰를 생성하게 됩니다.
따라서 CREATE TABLE을 사용할 시기와 CREATE VIEW를 사용할 시기를 알아야 합니다. 
이는 변환 실행 및 데이터 모델 로드 기간에 큰 영향을 미치기 때문입니다. 올바른 선택은 테이블의 크기와 구조, 쿼리의 복잡성에 따라 크게 달라집니다. 
일반적으로 다음 규칙을 따를 수 있습니다.

|||
|---|---|
|CREATE TABLE|	- 쿼리에 복잡한 정의(예: 여러 조인 및 조건)가 포함된 경우|
| |- 다른 변환(예: 활동 스크립트)이 쿼리 결과에 액세스하는 경우|
|CREATE VIEW|	- 쿼리가 단순히 단일 테이블(예: VBAP)에서 레코드를 선택하고 간단한 조건을 적용하는 경우.|
| |- 일반적으로 대부분 데이터 모델 테이블로 제한되어야 합니다.|

일반적인 권장 사항이 특정 시나리오에 적합한지 여전히 확실하지 않은 경우 두 접근 방식을 모두 시도하고 런타임을 비교할 수 있습니다.

#### 172 Staging Tables 및 Views로 데이터 모델 로드

Staging Tables 및 Views 로 성능 향상

데이터 모델(DM)에 로드된 테이블의 경우 아래 다이어그램과 같이 
`스테이징 테이블을 뷰와 결합`하여 데이터 파이프라인에 필요한 `스토리지와 성능 간에 최상의 균형을 유지`합니다 .

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yddh9gnzs0pu-StagingDMTable.png)

이 접근 방식을 사용하면 `스토리지에 큰 영향을 주지 않고 더 나은 성능을 얻`을 수 있습니다. 이것을 분해합시다.

스테이징 테이블을 보기와 결합하는 방법

첫 번째 단계 는 `스테이징 테이블을 만드는 것`입니다. 준비 테이블은 기본 키와 계산 또는 파생 열만 포함하는 임시 테이블 유형입니다 . 
준비 테이블을 만드는 쿼리에는 열 값을 계산하거나 형식을 다시 지정하는 데 필요한 모든 조인과 함수가 포함되어야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/mmtoech1clhn-image.png)

두 번째 단계 는 데이터 모델 보기(예: O2C_VBAP)를 만드는 것입니다. 
이 보기에서 "원시 데이터" 테이블(예: VBAP)을 이전에 생성된 스테이징 테이블(예: O2C_VBAP_STAGING)과 조인합니다.

이 보기에서는 원시 테이블(VBAP)과 스테이징 테이블(O2C_VBAP_STAGING) 사이에 조인이 하나만 있습니다 .
 필드 계산에 필요한 다른 모든 조인은 이전 STAGING_TABLE 문의 일부여야 합니다.

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/t8301gb4dwxj-image.png)

마지막으로 데이터 모델 구성에서 생성된 O2C_VBAP 보기를 사용합니다.

이 접근 방식을 사용해야 하는 경우

스테이징 테이블과 뷰를 사용하는 것은 DM에 로드되기 전에 약간의 준비가 필요한 DM 테이블에 주로 유용합니다. 
대부분의 경우 프로세스 커넥터에는 주요 사례 및 기타 트랜잭션 데이터 테이블을 준비하고 확장하는 변환이 있습니다. 
이러한 쿼리에 조인 및 여러 형식 재지정 기능이 포함된 경우 스테이징 테이블과 뷰 사용을 고려해야 합니다. 
즉, 이 접근 방식은 더 작은 마스터 데이터 테이블에 큰 가치를 제공하지 않습니다.

좋은 경험 법칙은 주요 사례 및 트랜잭션 테이블에 대해 이 접근 방식을 사용하는 것입니다

#### 173 테이블 용어에 대한 검토

지금까지 이 과정 안팎에서 꽤 많은 테이블 유형과 용어를 접했을 것입니다.
 다음은 Celonis가 사용하는 가장 일반적인 테이블 용어에 대한 간략한 검토입니다.

이 과정에서:

|||
|---|---|
|Temporary Join Table	|변환의 경우: 하나의 테이블에서 반복 조인을 캡처하고 변환에서 재사용하여 쿼리 비용을 절약합니다. 더 이상 사용하지 않으면 일반적으로 변환이 끝날 때 삭제됩니다.|
| |명명 규칙은 TMP_{process_name}_{joined_table}_{joined_table}_... 예: TMP_O2C_CDPOS_CDHDR입니다.|
|Staging Table|	데이터 모델 로드의 경우: 기본 키와 계산 또는 파생 열만 포함하는 임시 테이블 유형입니다. 데이터 모델 로드에 사용되는 뷰에 테이블이 추가됩니다. 스테이징 테이블은 보기에서 사용자 지정 열을 계산하거나 파생시키지 않아도 되므로 쿼리 비용을 절감할 수 있습니다. 임시 조인 테이블과 달리 데이터 모델 로드에 필요하므로 생성 후 삭제되지 않습니다.|
| |명명 규칙은 {process_name}_{table_name}_STAGING입니다.|
|Data Model Table|	데이터 모델 로드에 사용되는 테이블을 가리키는 일반적인 용어입니다. 대부분의 경우 변환에서 이러한 테이블을 생성하고 원시 데이터 테이블에서 파생하여 불필요한 열을 제거하고 필요할 수 있는 다른 열을 추가합니다.|
|Projections System Table	|이 표는 Vertica에만 적용됩니다. 쿼리를 실행하면 통계가 없는 테이블을 확인할 수 있습니다. 이 쿼리는 다음을 사용했습니다.|
| |SELECT anchor_table_name AS TableName |
| |FROM projections |
| |WHERE has_statistics = FALSE ;|
|Raw Data Table|	소스 시스템에서 직접 추출한 테이블.|
|Master Data Table|	시스템 마스터 데이터를 포함하는 추출한 원시 데이터 테이블 유형을 가리킵니다.|

다른 과정에서:

|||
|---|---|
|Metadata Table|	추가 정보가 포함된 추출한 원시 데이터 테이블 유형을 가리킵니다. 종종 마스터 데이터 테이블과 같은 의미로 사용됩니다.|
|Transactional Table|	프로세스와 관련된 사례 및 트랜잭션에 대한 정보를 포함하는 추출한 원시 데이터 테이블 유형을 가리킵니다.|
|Trigger Table|	실시간 데이터 추출에서 변환을 트리거하는 추출된 테이블을 가리킵니다.|
|Staging Table|	실시간 변환에서 추출 후 델타 정보를 저장하는 중간 테이블을 가리킵니다.|
| |이러한 테이블의 명명 규칙은 _CELONIS_TMP_{trigger_table}_EKPO_TRANSFORM_DATA입니다.|

#### 174 배운 내용 확인 - 테이블 및 보기

### 18 DELETE 및 UPDATE 문

#### 181 DELETE 및 UPDATE 쿼리로 인해 파이프라인이 느려질 수 있음

Vertica에서 DELETE 및 UPDATE 쿼리는 INSERT 및 SELECT 쿼리만큼 성능이 좋지 않을 수 있습니다. 
특히 많은 레코드에 대한 변경 사항이 있는 대형 테이블(25% 이상):

1. 완료하는 데 시간이 오래 걸릴 수 있습니다.
2. 테이블에 대한 이후 쿼리의 성능에 부정적인 영향을 미칠 수 있습니다.

이 두 가지 이유를 살펴보겠습니다.

DELETE 및 UPDATE 쿼리를 완료하는 데 시간이 오래 걸리는 이유는 무엇입니까?

쿼리가 느리게 실행되는 이유는 다양할 수 있습니다. 일부 요인에는 다음이 포함되지만 이에 국한되지는 않습니다.

- 테이블의 크기
- 삭제 청크의 크기
- 테이블에서 삭제 키 및 위치 지정
- 삭제 필터(WHERE)
- 데이터 분포(부울 대 많은 개별 값)

DELETE 및 UPDATE 쿼리가 이후 쿼리에 부정적인 영향을 미칠 수 있는 이유는 무엇입니까?

먼저 Vertica에서 DELETE 및 UPDATE가 수행하는 작업을 이해해야 합니다.

- DELETE는 실제로 디스크 저장소에서 즉시 데이터를 삭제하지 않고 단순히 행을 삭제된 것으로 표시합니다 .
- UPDATEs는 새 데이터가 있는 행과 삭제된 것으로 표시된 행 의 두 행을 씁니다 .

따라서 대규모 UPDATE 또는 DELETE 다음에 테이블에서 SELECT 문을 실행할 때 
Vertica는 결과에서 "삭제된 것으로 표시된" 레코드를 생략하기 위해 추가 처리를 수행해야 합니다. 
이로 인해 성능이 느려집니다.

또한 DELETE 또는 UPDATE 문을 실행하면 테이블에 배타적 잠금이 설정되어 다른 쿼리가 동시에 실행되지 않습니다.

삭제 표시된 행은 어떻게 됩니까?

이러한 행은 궁극적으로 Vertica 데이터베이스에서 "제거"됩니다. 
삭제 메커니즘은 많은 리소스를 소비하며 그 빈도와 조건은 Vertica의 권장 사항에 따라 EMS 유지 관리 작업에서 처리합니다. 
Vertica에서 직접 이 주제에 대해 자세히 알아보려면 제거에 대한 이 페이지 와 DELETE 및 업데이트에 대한 이 페이지를 살펴보십시오 .

이야기의 교훈은 무엇입니까?

DELETE 및 UPDATE 문으로 인해 데이터 파이프라인이 느려지는 경우 대체 접근 방식을 적용하여 문제를 해결하는 것이 좋습니다. 다음 페이지에서 자세히 알아보세요!

#### 182 DELETE 및 UPDATE 방지

고려 사항

데이터 파이프라인에서 정기적인 DELETE 또는 UPDATE 변환을 설정하기 전에 정기적인 대량 삭제 또는 업데이트의 필요성과 이유를 재고하십시오.

- 추출 사용 - 추출 필터를 조정하면 삭제/업데이트 필요성을 줄일 수 있습니까?
- 중복 원인 찾기 및 수정 - 중복 제거를 위해 DELETE를 사용하는 경우 중복 레코드를 생성하는 작업을 찾습니다.
    - 나중에 삭제하거나 업데이트해야 하는 관련이 없거나 불완전한 레코드로 이어지는 변환이 있습니까?
    
예를 들어 정리 단계에서 "활동 이름" 또는 "이벤트 시간" 열이 NULL인 활동 레코드는 종종 삭제됩니다. 이러한 활동을 생성하는 변환을 검토하면 해당 레코드가 null 값으로 생성되는 이유를 감지하고 수정할 수 있습니다.

DELETE 및 UPDATE 대신 테이블 재구축

위의 방법이 도움이 되지 않고 성능을 최적화해야 하는 경우 DELETE 또는 UPDATE 문을 사용하는 대신 테이블을 다시 빌드하는 것이 좋습니다 .

다음은 DELETE 또는 UPDATE 시나리오에 대한 단계입니다.

DELETE 대신 다시 빌드

1억 개의 레코드가 포함된 Table_A가 있고 3천만 개의 레코드를 삭제하려고 합니다. DELETE 문을 실행하는 대신 유지하려는 70M 레코드가 포함된 NEW_Table_A를 만듭니다. 그런 다음 Table_A의 이름을 BACKUP_Table_A로 바꾸고 NEW_Table_A의 이름을 원래 이름인 Table_A로 바꿉니다. 샘플 쿼리가 포함된 단계는 다음과 같습니다.

1. 기존 테이블에서 관련 레코드를 선택하여 새 테이블을 만듭니다.
    ```
    CREATE TABLE NEW_Table_A AS (SELECT ... FROM Table_A WHERE ... );
    ```
2. 이름을 변경하여 이전 테이블을 백업합니다.
    ```
    ALTER TABLE Table_A RENAME TO BACKUP_Table_A;
    ```
3. 새 테이블의 이름을 원래 테이블 이름으로 바꿉니다.
    ```
    ALTER TABLE New_Table_A RENAME TO Table_A;
    ```
4. 이전 테이블을 삭제합니다.
    ```
    DROP TABLE BACKUP_Table_A;
   ```
5. 테이블 통계 추가
    ```
    ANALYZE_STATISTICS (‘Table_A’);
    ```
업데이트 대신 재구축

50개의 열과 3천만 개의 레코드가 있는 Table_A가 있습니다. 
50M 레코드의 대부분 또는 전체를 업데이트하고 Table_A.Column50의 값을 다른 테이블(예: Table_B)의 값으로 설정하려고 합니다. 
테이블 조인 및 UPDATE 문 실행은 종종 실행하는 데 매우 오랜 시간이 걸립니다. 이는 성능이 좋지 않은 옵션입니다.

```
UPDATE Table_A 
SET Table_A.Column50 = Table_B.ColumnX 
WHERE Table_A.key=Table_B.key
```

동일한 결과를 얻는 더 빠른 방법은 DELETE 예제에 표시된 것처럼 테이블을 다시 빌드하는 것입니다. 
업데이트의 경우 단계는 다음과 같습니다.

1. 새 테이블 NEW_Table_A를 관련 레코드(이 경우 49개의 동일한 필드와 값을 변경하는 하나의 필드가 있는 모든 레코드)의 선택으로 생성합니다.
   
    ```
   CREATE TABLE NEW_Table_A 
   AS
   SELECT Table_A.Column1
              ,Table_A.Column2
              ,Table_A.Column3
              ,Table_A.Column4
              ,Table_A.Column5
              ,Table_A.Column6
              ,Table_A.Column7
           …….
              ,Table_B.ColumnX as Column50
   
   FROM Table_A
           Inner join Table_B 
           ON Table_A.key=Table_B.key;
    ```
2. 이전 테이블의 이름을 바꿉니다.

    ```
   ALTER TABLE Table_A RENAME TO BACKUP_Table_A;
    ```
3. 새 테이블의 이름을 원래 테이블 이름으로 바꿉니다.

    ```
   ALTER TABLE New_Table_A RENAME TO Table_A;
    ```
4. 이전 테이블을 삭제합니다.

    ```
   DROP TABLE BACKUP_Table_A;
    ```
5. 테이블 통계 추가:

    ```
   ANALYZE_STATISTICS (‘Table_A’);
    ```

#### 183 불가피한 DELETE 및 UPDATE의 경우

복제 및/또는 테이블 재구축의 소스를 찾아 수정하기만 하면 대부분의 DELETE 및 UPDATE 문을 피할 수 있다고 생각합니다.

DELETE 또는 UPDATE를 반드시 사용해야 하는 경우 다음 모범 사례를 고려하십시오.

1. 더 작은 부분/청크 로 쿼리를 실행합니다 . 이렇게 하면 DETELE 및 UPDATE 문의 실행 시간이 짧아집니다. 
예를 들어 테이블에서 항목을 삭제하려는 경우(예: BSEG) 대규모 삭제 대신 연도별로 삭제할 수 있습니다.
    
    ```
    Delete from BSEG where GJAHR=2020;
    Delete from BSEG where GJAHR=2021;
    Delete from BSEG where GJAHR=2022;
   ```
2. 올바른 조건 선택 - 조건을 통해 쿼리를 제한할 때 테이블 필드 목록의 시작 부분에 표시되고
(예: Vertica는 일반적으로 초기 필드를 사용하여 테이블을 정렬함) 해당 값이 데이터 집합 전체에 고르게 분포된 필드를 선택합니다. 
이러한 필드는 날짜 및 문서 유형일 수 있습니다.

### 19 과정 요약 및 다음 단계

과정 요약

- 쿼리 성능 예측

    쿼리 실행 계획을 표시하려면 SELECT 또는 UPDATE 문 앞에 EXPLAIN을 입력합니다.
    
    쿼리 계획에서 다음에 집중하십시오.
    
    - 예상 쿼리 비용이 높은 단계
    - 조인 방식 - 큰 테이블 조인 시 병합 조인을 지향합니다 . 해시는 더 작은 테이블이나 병합이 불가능할 때 괜찮습니다.
    - 누락된 테이블 통계 표시기( NO STATISTICS )

- 테이블 통계

    테이블 통계는 성능 쿼리의 가장 중요한 요소 중 하나입니다 .
    
    테이블 통계는 Celonis 추출기를 사용하여 추출된 테이블(예: "원시 소스 시스템 테이블")에 대해서만 자동으로 수집됩니다. 
    변환(예: TMP_CDHDR_CDPOS)의 모든 사용자 지정 또는 임시 조인 테이블에 대해 명시적으로 통계를 만들어야 합니다 .
    
    SELECT ANALYZE_STATISTICS('TABLE_NAME')를 추가하기만 하면 됩니다 . 
    테이블을 채우는 각 "테이블 만들기" 쿼리 문 다음에(빈 테이블이 아님). 
    쿼리 또는 변환이 실행되면 시스템에서 데이터를 수집합니다.

- General Best Practices

    1. 전문적인 SQL 코드를 작성하는 모범 사례에는 훌륭한 형식화 기술이 필요합니다. 
    이는 읽기 쉽고 유지 관리 가능한 SQL 코드를 작성하는 데 도움이 됩니다.
    
    2. 데이터 세트만을 필터링할 목적으로 INNER JOIN을 사용하지 마십시오. 대신 WHERE EXISTS를 사용하십시오 .
    
    3. 계산 비용이 많이 들고 쿼리 속도가 느려지므로 기본적으로 DISTINCT를 사용하지 마십시오. 
    데이터 세트에 중복이 있는지 확인하고 조인으로 인해 중복이 발생하지 않는지 확인하십시오. 
    삭제, WHERE EXISTS 또는 하위 쿼리를 사용하여 결과에 따라 작업합니다.
    
    4. 테이블 조인을 확인합니다.
    
        - 전체 키를 사용하여 테이블을 조인해야 합니다(MANDT / ClientId를 잊지 마십시오).
        - 관련 레코드만 처리하도록 테이블을 필터링합니다. WHERE 대신 JOIN에 필터를 배치합니다.
        - SELECT 문에서 실제로 필요하고 사용되는 테이블만 조인하십시오.

- 임시 조인 테이블

    각 변환에 대해 동일한 테이블을 반복적으로 조인해야 하는 필요성을 줄이기 위해 임시 조인 테이블을 만듭니다.
    
    임시 테이블의 디자인은 쿼리 성능에 상당한 영향을 미친다는 점을 염두에 두십시오.
    
    - 키 열(예: MANDT, VBELN, POSNR)을 테이블 시작 부분에 배치하거나 CREATE TABLE 문에서 명시적 ORDER BY를 사용합니다.
    - 이후 변환에 실제로 필요한 데이터만 저장하십시오.
    - 추가하는 것을 잊지 마세요 SELECT ANALYZE_STATISTICS('TableName'); 임시 조인 테이블을 생성하는 각 문 다음에.

- 테이블과 뷰의 사용

    임시 테이블 대신 뷰를 잘못 사용하면 쿼리 성능이 크게 저하될 수 있습니다.
    
    |||
    |---|---|
    |CREATE TABLE| - 쿼리에 복잡한 정의(예: 여러 조인 및 조건)가 포함된 경우|
    | |- 다른 변환(예: 활동 스크립트)이 쿼리 결과에 액세스하는 경우|
    |CREATE VIEW|- 쿼리가 단순히 단일 테이블(예: VBAP)에서 레코드를 선택하고 간단한 조건을 적용하는 경우|
    | |- 일반적으로 대부분 데이터 모델 테이블로 제한되어야 합니다.|

- DELETE 및 UPDATE 문

    성능 저하가 감지되면 DELETE 및 UPDATE 문을 사용하여 데이터를 정리하지 않는 것이 좋습니다. 다음과 같이 할 수 있습니다.
    
    - 추출을 필터링하여 추가 기록 방지
    - 변환에서 중복 소스 찾기 및 수정
    - DELETE 및 UPDATE 문을 사용하는 대신 테이블 재구축

배운 내용 확인 - 최종 검토
