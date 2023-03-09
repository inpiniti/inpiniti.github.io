---
title: typescript error
author: JUNG YoungKyun
date: 2023-03-09
category: 35 error
layout: post
---

# Property 'attributes' does not exist on type 'xxx'.

이 에러는 TypeScript 컴파일러가 해당 객체 또는 클래스에 'attributes'라는 속성이 존재하지 않는다는 것을 감지했을 때 발생합니다. 즉, 해당 객체 또는 클래스가 'attributes'라는 속성을 가지고 있지 않은데, 코드에서 해당 속성을 참조하려고 할 때 이 에러가 발생합니다.

이러한 에러는 대개 TypeScript에서 정적 타입 검사를 수행하는 과정에서 발생합니다. TypeScript는 코드에서 참조하려는 속성이나 메서드가 해당 객체 또는 클래스에 실제로 존재하는지를 검사하며, 이를 통해 코드의 안정성을 높이고 디버깅을 용이하게 합니다.

이러한 에러를 해결하기 위해서는 해당 객체 또는 클래스가 'attributes' 속성을 가지고 있도록 정의해주어야 합니다. 예를 들어, 다음과 같이 객체를 정의할 때 'attributes' 속성을 추가할 수 있습니다.

```
interface MyObject {
  attributes: {
    name: string;
    age: number;
    // ...
  };
  // ...
}
```
또는 클래스를 정의할 때 'attributes' 속성을 추가할 수도 있습니다.

```
class MyClass {
  attributes: {
    name: string;
    age: number;
    // ...
  };
  // ...
}
```
이러한 방식으로 해당 객체 또는 클래스에 'attributes' 속성을 추가하면, TypeScript 컴파일러는 이제 해당 속성이 존재한다는 것을 인식하고, 에러가 발생하지 않게 됩니다.