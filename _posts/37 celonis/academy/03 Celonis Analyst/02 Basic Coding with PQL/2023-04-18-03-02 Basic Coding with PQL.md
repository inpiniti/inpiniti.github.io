---
title: 03 02 Basic Coding with PQL
author: JUNG YoungKyun
date: 2023-04-18
category: 37 celonis
layout: post
---

![](../images/37 celonis/230418/20230418105256.png)

![](../images/37 celonis/230418/20230418105323.png)

![](../images/37 celonis/230418/20230418105345.png)

![](../images/37 celonis/230418/20230418105416.png)

![](../images/37 celonis/230418/20230418105437.png)

![](../images/37 celonis/230418/20230418105457.png)

![](../images/37 celonis/230418/20230418105512.png)

![](../images/37 celonis/230418/20230418110244.png)

![](../images/37 celonis/230418/20230418150559.png)

![](../images/37 celonis/230418/20230418110303.png)

약어가 어려워 매핑할때 쓰는 것 같아보입니다.

![](../images/37 celonis/230418/20230418111127.png)

![](../images/37 celonis/230418/20230418111257.png)

null 값 치환 용인것 같습니다.

![](../images/37 celonis/230418/20230418111456.png)

![](../images/37 celonis/230418/20230418111737.png)

![](../images/37 celonis/230418/20230418111757.png)

![](../images/37 celonis/230418/20230418111921.png)

![](../images/37 celonis/230418/20230418112119.png)

![](../images/37 celonis/230418/20230418112216.png)

FILTER "EKPO"."TXZ01" LIKE 'Apple%';

FILTER "EKPO"."TXZ01" IN_LIKE ('Apple%', 'NacBook Pro');

![](../images/37 celonis/230418/20230418120219.png)

![](../images/37 celonis/230418/20230418130849.png)

![](../images/37 celonis/230418/20230418130924.png)

LOWER | UPPER | REVERSE

소문자로 | 대문자로 | 거꿀로

![](../images/37 celonis/230418/20230418131341.png)

![](../images/37 celonis/230418/20230418131353.png)

trim 공백 자르기임

![](../images/37 celonis/230418/20230418131514.png)

![](../images/37 celonis/230418/20230418131819.png)

![](../images/37 celonis/230418/20230418131905.png)

![](../images/37 celonis/230418/20230418131955.png)

![](../images/37 celonis/230418/20230418132042.png)

![](../images/37 celonis/230418/20230418132059.png)

![](../images/37 celonis/230418/20230418132306.png)

![](../images/37 celonis/230418/20230418132358.png)

날짜 반올림

![](../images/37 celonis/230418/20230418132558.png)

![](../images/37 celonis/230418/20230418132651.png)

![](../images/37 celonis/230418/20230418133305.png)

![](../images/37 celonis/230418/20230418133510.png)

![](../images/37 celonis/230418/20230418133512.png)

![](../images/37 celonis/230418/20230418133517.png)

![](../images/37 celonis/230418/20230418133519.png)


"Process Equals"를 사용하면 항상 특정 프로세스 패턴을 정의할 수 있습니다. 이는 특정 활동이 특정 순서로 발생함을 의미합니다.

"Start"을 추가하여 고정 시작 활동을 지정할 수 있습니다.

수식의 마지막 활동이 프로세스의 종료 활동이어야 함을 정의하기 위해 "End"를 추가하여 동일한 작업을 수행할 수 있습니다.

"To Any To" 대신 "To"를 사용하여 활동이 중간 프로세스 단계 없이 다른 활동 이후에 직접 발생하도록 지정할 수 있습니다.

또한 추가 "To Any To" 또는 "To" 문을 사용하여 원하는 만큼 활동을 추가할 수 있습니다.

![](../images/37 celonis/230418/20230418150938.png)

![](../images/37 celonis/230418/20230418150945.png)

![](../images/37 celonis/230418/20230418150949.png)

![](../images/37 celonis/230418/20230418150953.png)

![](../images/37 celonis/230418/20230418151000.png)

![](../images/37 celonis/230418/20230418151009.png)

![](../images/37 celonis/230418/20230418151027.png)

훨씬 더 강력한 관련 함수인 MATCH_PROCESS_REGEX

RegEx 또는 정규식은 특정 검색 패턴에 따라 텍스트 내에서 검색하는 방법입니다.

PQL 구문은
- "Match Process Regex"
 
- "open parenthesis" 
- "Activity Table" 
- "Dot" 
- "String Column" 
- "Comma" 
- "Regular Expression" 
- "close parenthesis"


![](../images/37 celonis/230418/20230418152200.png)

![](../images/37 celonis/230418/20230418152306.png)

![](../images/37 celonis/230418/20230418152323.png)

'A' 앞의 곡절 부호[written: ^]는 시작 식별자입니다. 즉, 케이스는 활동 'A'로 시작해야 하며 그 전에는 다른 활동이 발생할 수 없습니다.

![](../images/37 celonis/230418/20230418152336.png)

2개의 "greater than" 기호는 "직접 다음"을 나타내는 PQL 기호입니다.

![](../images/37 celonis/230418/20230418152342.png)

'B' 및 'C' 주변의 대괄호는 활동 'B' 또는 활동 'C'가 'A' 바로 다음에 발생함을 의미합니다.

![](../images/37 celonis/230418/20230418152348.png)

![](../images/37 celonis/230418/20230418152356.png)

"Any"는 모든 활동에 대한 자리 표시자입니다.

![](../images/37 celonis/230418/20230418152416.png)

둥근 괄호와 그 뒤에 있는 별[쓰기: ()*]은 괄호 안의 활동이 0회 또는 여러 번 발생할 수 있음을 의미하며, 다른 활동이 임의로 자주 발생할 수 있음을 의미합니다.
따라서 "Any" 주변의 둥근 괄호와 그 뒤에 있는 별표[쓰기: (ANY)*]는 모든 활동이 임의의 횟수만큼 발생할 수 있음을 의미합니다.

![](../images/37 celonis/230418/20230418152420.png)

'Y' 2개의 "보다 큼" 기호 'Z' 뒤에 달러 기호[쓰기: 'Y' >> 'Z' $]가 있는 경우 케이스 끝에서 'Y' 바로 뒤에 'Z'가 오는 것을 의미합니다.

![](../images/37 celonis/230418/20230418152436.png)

달러 기호[쓰기: $]는 케이스 종료 식별자이며 그 이후에는 다른 활동이 발생할 수 없음을 의미합니다.

![](../images/37 celonis/230418/20230418152446.png)














