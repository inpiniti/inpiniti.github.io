---
title: UX/UI DESIGN 변경안
author: JUNG YoungKyun
date: 2022-05-26
category: inpiniti
layout: post
---

![ux](https://img.shields.io/badge/UX-2022.05.26-red.svg)

트렌드에 대해서 알아보았는데, 웹 접근성, 동적 컨텐츠, 모바일 친화적인 디자인, 다크모드, 뉴모피즘, 애미메이션 등등 약간 

이미 적용되어 있거나 당장 적용하기 어렵거나 또는 저희가 만들고 있는 제품특성과는 맞지 않는 듯한 느낌을 받았습니다.

# 유사한 사이트와 비교를 해보자

그래서 트렌드를 살펴보는 것 보다는 아예 비슷한 느낌의 제품과 비교해보는 것이 좋지 않을까 생각이 들었습니다.

아래는 저희 제품과 마이크로소프트 Azure 입니다.

<img src="../images/ux ipr.png" alt="ipr" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux azure.png" alt="azure" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

사실 제가 느끼기에는 디자인이 투박하거나 80년대스럽다라는 느낌은 솔직히 말해서 1도 받지 못했습니다.

Azure 와 비교시 미세한 차이점은 있을지언정 어느게 훨씬 디자인이 잘되어 있다 라고 판단하기에도 어렵지 않나라고 생각이 듭니다.

# 리소스

일단 전체적인 느낌은 넘어가기로 하고 다른 부분도 살펴보겠습니다.

Azure에서는 리소스가 저희 제품에서는 이벤트 로그랑 매칭될 수 있으리라 생각이 듭니다.

직접 사용자가 만들기 버튼을 클릭해서 몇 단계의 절차를 거처서 만들어야 하는 것이기 때문에 그렇습니다.

그런 절차로 만들어진 리소스나, 이벤트 로그는 최신 리소스와 데이터 관리나 홈 화면에 목록형태로 나오게 됩니다.

하나는 카드 형태이고, 하나는 테이블 형태인데 여기에서는 형태만 다를뿐 뭔가 다르다는 느낌은 크게 느끼지 못했습니다.

# 조회

클릭하여 조회를 하게 되면 이때부터는 확연한 차이가 느껴지는데요.

디자인이라기보다 사용자 경험에서 차이가 많이 느껴지지 않나 생각이 듭니다.

Azure의 경우는 클릭한 리소스의 이름과 상세 정보를 보여주는 반면,

저희 제품에서는 로딩화면을 보여줍니다. 심지어 이 로딩은 시간이 제법 길기까지 합니다.

사용자는 단순히 해당 이벤트 로그가 무었인지 알기 위해서 정보 조회를 목적으로 클릭했을 가능성이 높을텐데, 분석을 하는 것은 제가 보기에는 사용자의 의도를 벗어나지 않았을까 생각이 듭니다.  

<img src="../images/ux ipr 조회.png" alt="ipr 조회" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux azure 조회.png" alt="azure 조회" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

# 대시보드

여기서 부터는 저희 제품의 이미지를 더 올리는건 좀 그렇고, Azure의 이미지만 올리도록 하겠습니다.

사실 대시보드화면은 아니고, 개요에서 아래쪽으로 드래그해서 보면 차트가 나옵니다.

<img src="../images/ux azure 대시보드.png" alt="대시보드" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

최소한의 UI

less si more

사용자가 보는 콘텐츠가 적을 수록 좋다.

기본 속성

핵심 콘텐츠와 기능에 더 집중할 수 있는

깔끔한 레이아웃

## 동향. 추세

1. a general direction in which something is developing or changing
2. a fashion


- 무언가 발전하거나 변화하는 일반적인 방향
- 패션, 마케팅, 경제 동향 분석 등 여러 분야에서 널리 사용

사회 전반적인 흐름을 읽어내는 과정

```
미래를 예측하는 힘
```

`과거와 현재를 시간의 흐름속에서 연결`하고
들여다보는 통시적 접근이 중요하다.

이렇듯 트렌드를 읽는다는 것은
`시공간을 넘나들며 변화의 흐름을 추적`하는 것이다.

관찰자의 시선에 따라 트렌드를 파악하는
깊이와 넓이의 차이가 생겨나게 된다.

```
새로운 트렌드를 읽고
거기서 새로운 기회를 찾아 낼 수 있다. 
```

# 02 소비 트렌드 이해

# UX/UI 디자인 트렌드


웹접근성은 수년간 중요성을 인정받아 이어져온 시스템으로 *사실상 이제는 트렌드가 아닌 의무*입니다. 
웹사이트는 *다양한 능력의 사람들이 모두 사용하기 때문에 반드시 접근성을 고려*해야 합니다. 
예를 들면 시력이 좋지 않은 사람은 더 큰 글자를 필요로 할 수도 있고 앞이 전혀 보이지 않다면 음성으로만 사이트를 이용할 수도 있습니다. 
이런 환경에서 디자이너는 *사이트를 이용하게 될 어떤 사람들도 배제하지 않을 능력이 필요*합니다. 
2022년에는 온전히 웹사이트를 사용하기에 불편함이 있는 사용자들을 차별없이 끌어들일 수 있는 웹접근성을 고려한 사이트의 수가 상당량 증가할 것으로 예상한다고 합니다. 
*웹접근성을 고려하는 몇가지 방법*은 *대비되는 색상을 사용하는 것* (ex. 밝은 배경에 어두운 텍스트, 어두운 배경에 밝은 텍스트), *사용자가 텍스트 크기를 늘릴 수 있도록 하는 것*, *동영상에 캡션을 제공하는 것*, *이미지에 대한 대체텍스트를 제공하는 것* 등이 있습니다. 

![웹 접근성](https://blog.kakaocdn.net/dn/brl9Vg/btrn7rfGYOw/FcSYeIgfV4DBt4IOd5zuY1/img.jpg)

![웹 접근성](https://blog.kakaocdn.net/dn/blmEVr/btrn20i95YF/WlwVb6LS4W7BDLrrObIjJ1/img.jpg)

![웹 접근성](https://blog.kakaocdn.net/dn/c3BVQi/btrn4rukbjQ/CLqERYmNrTSSpLTJHAA9T1/img.png)

![웹 접근성](https://blog.kakaocdn.net/dn/EMyiU/btrn7Rei7z8/1P8jnfRrXLcne1xfvuKtM0/img.png)

## 웹 사이트의 이미지에 캡션을 적용한다
- alt
- longdesc
- figure/figcaption
```html
<img onerror="removeImage($(this));" src=”https://yoursite.com/deckard.jpg” alt=”외투를 입은 짧은 머리의 남자”> 
```

## 헤더 태그를 사용해 문서를 정리한다
- h1, h2, h3

## 서식에 라벨을 적용하고 가독성을 유지한다
- label
- 플레이스 홀더
- tooltip

## 요소에 대한 키보드 탐색의 일관성과 접근성을 확보한다
- tab-indexable (Tab 키를 이용하여 이동)
- 단축키 (Alt-S ...)

## 확대/축소뿐 아니라 수동 글꼴 크기 조정을 허용한다
- +- 아이콘 구현

## 레이아웃을 위해 테이블을 사용하지 않는다
- Flexbox, 기타 블록 레벨 스타일 이용

## 웹 사이트의 다크 또는 고대비 모드를 생성한다

## 색상과 디자인을 활용해 페이지 요소를 강조한다

## 가능하면 서술적인 URL을 사용한다
```text
https://magazino.com/article/2125451 (x)
https://magazino.com/article/ten-best-harrison-ford-films/2125451 (o)
```

## WAVE 도구를 사용해 웹 사이트 접근성을 테스트한다

![WAVE](https://www.ciokorea.com/files/itworld/2021/05_01/website-accessibility-wave-100886349-orig.jpg)

# 동적 컨텐츠
*동적인 컨텐츠는 웹사이트의 참여도와 전환율을 높이기* 때문에 이번 2022년도 인기있는 트렌드가 될 것 같습니다. 
*사용자의 현재 위치, 이전의 검색기록이나 최근에 구매한 상품 등에 따라 사용자에게 다른 정보를 표시*할 수 있습니다. 
동적으로 디자인하지 않은 웹사이트는 페이지 안에서의 변동사항이 없기 때문에 오래된, 비전문적인 사이트로 보이며 지루하고 사용자가 정보를 얻는데에 더 많은 시간을 소요하게 될 수 있습니다. 
동적인 사이트는 *사용자 참여와 전환율을 증가*시키고 *SEO순위 를 향상*시키며 결과적으로 *더 많은 방문자를 끌어들일* 수 있습니다.

![동적 컨텐츠](https://blog.kakaocdn.net/dn/R7T7D/btrocqVKg9f/Z2lZkpWA9y36xwMEgMtTL1/img.png)

![동적 컨텐츠](https://blog.kakaocdn.net/dn/GZs14/btrobUC09jT/TOZuLqFctZN9CmmyYSPkbK/img.png)

![동적 컨텐츠](https://blog.kakaocdn.net/dn/dFYU6I/btroaMFgPoi/sKkFZlIJPX7KK4Lg0HKso1/img.jpg)

![동적 컨텐츠](https://blog.kakaocdn.net/dn/bYmoYW/btroaNqH7yZ/UtbsKNPYNobG6rwIkCXTKk/img.png)

# 모바일 친화적인 디자인

# 동적 스크롤링

# 인터렉티브 컨텐츠

# 그라디언트, 글래스모피즘



# 미니멀리즘

# 다크모드

# VUI

# Air Gesture Control

# 3D 요소

# 마이크로 인터렉션

# Glassmorphsim

# AR/VR

# AI

# 고급 개인화

# 사라진 비밀번호

# 스토리 탤링

# UX Writing

# 불완전한 디자인 요소

# 사진과 그래픽의 혼합

# 비대칭 레이아웃

# 사실적 질감

# 플로팅 요소