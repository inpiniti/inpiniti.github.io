---
title: mac os node 설치
author: ygjunginpiniti
date: 2023-01-19
category: 05 javascript
layout: post
---

>mac 에 뭔가 설치하려면 brew 라는걸 깔아야 되는 것 같습니다.
10년전 맥북 쓸때는 node가 깔려 있던거 같은데, m1 칩셋이라 그런가?
정확히 모르겠지만, 아무튼 설치를 해보겠습니다.

# brew
node를 설치하기 위해서는 패키지 관리프로그램인
brew 라는걸 설치해 줍니다.

아래의 명령어를 쳐 주면 설치 되는데, 혹시나 안되면 공식 홈페이지에 들어가길 바랍니다.

```
usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

그 뒤로는 별거 없고 아래 명령어 따라 쳐줍니다.
```
brew update
brew install node
node -v
npm -v
```

이게 끝입니다.