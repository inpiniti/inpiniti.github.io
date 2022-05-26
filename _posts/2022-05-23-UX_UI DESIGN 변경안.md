---
title: UX/UI DESIGN 변경안
author: JUNG YoungKyun
date: 2022-05-26
category: inpiniti
layout: post
---

![ux](https://img.shields.io/badge/UX-2022.05.26-red.svg)

트렌드에 대해서 알아보았는데, 웹 접근성, 동적 컨텐츠, 모바일 친화적인 디자인, 다크모드, 뉴모피즘, 애니메이션 등등 약간 

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

저희 제품에서는 로딩화면을 보여줍니다. 심지어 이 로딩은 시간이 제법 길기까지 하며, 내가 무엇을 선택했었는지 표시가 조금은 미약하지 않나 생각이 듭니다.

사용자는 단순히 해당 이벤트 로그가 무었인지 알기 위해서 정보 조회를 목적으로 클릭했을 가능성이 높을텐데, 분석을 하는 것은 제가 보기에는 사용자의 의도를 벗어나지 않았을까요?  

<img src="../images/ux ipr 조회.png" alt="ipr 조회" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux azure 조회.png" alt="azure 조회" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

# 그외

여기서 부터는 저희 제품의 이미지를 더 올리는건 좀 그렇고, Azure의 이미지만 올리도록 하겠습니다.

아래는 대시보드까진 아니고 간략한 현황을 나타내는 차트입니다.

<img src="../images/ux azure 대시보드.png" alt="대시보드" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

로딩 시간은 1초 미만으로 매우 빠르고,

사용자가 기간을 지정할 수 있는데, 1시간 6시간, 1일, 7일, 30일 정도만 제공이 되는데, 기간을 선택과 동시에 차트는 실시간으로 변경되게 됩니다.

기능이야 당연히 조금 더 세세한 컨트롤을 할 수 있는 저희 제품쪽이 더 나을수도 있을텐데, 

사용자 관점에서 굳이 일자까지 선택하는건 조금 번거로웠던거 같고, 저는 로딩을 조금 더 줄일수 있으면 좋겠다는 느낌이 사실 좀 듭니다.

<img src="../images/ux azure 기타.png" alt="기타" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

다른 기능들도 눌러봤는데, 별다른건 없어 보입니다.

# 리스트

아래는 어떠한 리스트를 보여주는 화면입니다.

클릭하여 상세 버튼을 눌렀을 때,

<img src="../images/ux azure 리스트.png" alt="리스트" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux azure 리스트 상세.png" alt="리스트 상세" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

리스트의 화면을 가리느냐 안가리느냐의 정도의 차이는 있었지만 차이는 크다고 생각하지 못하였습니다.

# 차트 

사실 저는 전반적인 느낌은 저희 제품의 디자인 퀄리티가 떨어진다는 느낌은 아직도 느끼지 못하겠습니다.

다만 어쩌면 차트가 조금 올드 하다고 느낄수 있지 않을까? 생각이 듭니다.

<img src="../images/ux ipr 차트.png" alt="ipr 차트" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux 기타 차트.png" alt="기타 차트" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

<img src="../images/ux 기타 차트2.png" alt="기타 차트" style="border-radius: 10px; border: 1px solid #eaeaea;"/>

차트를 완전히 갈아업는건 조금 어렵겠지만, 색상이나 폰트, 두깨 등을 변경해서 조금 더 세련되게 바꿀수 있지 않을까 생각이 됩니다.

 
