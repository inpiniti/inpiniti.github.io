---
title: MaxListenersExceededWarning
author: JUNG YoungKyun
date: 2023-03-15
category: 32 mqtt
layout: post
---

MaxListenersExceededWarning: Possible EventEmitter memory leak detected. 11 message listeners added to [MqttClient]. Use emitter.setMaxListeners() to increase limit (Use `node --trace-warnings ...` to show where the warning was created)

일단 먼저 chatGPT 에게 에러의 원인과 해결방안에 대해서 물어보았습니다.

# 에러의 원인

이 에러는 Node.js의 이벤트 시스템(Event System)에서 발생하는 경고입니다. Node.js의 이벤트 시스템은 EventEmitter 클래스를 통해 구현되며, 이 클래스는 이벤트를 발생시키는 객체입니다. EventEmitter 클래스는 다수의 리스너(listener)를 등록할 수 있습니다. 그러나, EventEmitter 객체에서 동시에 등록할 수 있는 리스너의 수에는 제한이 있습니다.

MaxListenersExceededWarning 경고는 EventEmitter 객체에 등록된 리스너 수가 제한을 초과할 경우 발생합니다. 이 경고는 메모리 누수(memory leak)를 방지하기 위해 Node.js에서 자동으로 발생시키는 경고입니다.

# 해결방안

해결 방법은 EventEmitter 객체에서 동시에 등록할 수 있는 리스너의 수를 늘리는 것입니다. emitter.setMaxListeners() 메소드를 사용하여 이 값을 늘릴 수 있습니다. 하지만, 이는 메모리 누수를 일으킬 가능성이 있으므로, 신중하게 적용해야 합니다.

예를 들어, 다음과 같이 MqttClient 객체에서 등록된 리스너 수를 20으로 늘리는 코드를 작성할 수 있습니다.

```
const client = new MqttClient(options);
client.setMaxListeners(20);
```
만약, 이 경고를 무시하고 싶다면, Node.js를 실행할 때 --max-http-header-size 옵션을 사용하여 경고를 끌 수 있습니다. 다음과 같이 실행합니다.

```
node --max-http-header-size=80000 app.js
```
그러나, 경고를 무시하는 것은 메모리 누수를 일으킬 가능성이 있으므로, 신중하게 판단해야 합니다.

# client.setMaxListeners

chatGPT 말고도 인터넷을 검색해보면 `setMaxListeners` 를 사용하라고 나옵니다.

```
client.setMaxListeners(100)
```

먼저 100으로 설정 해보았습니다. 하지만 똑같은 에러가 발생하였습니다.

```
client.setMaxListeners(0)
```

0으로 설정하라는 이야기도 있어서 설정해 보았으나 마찬가지로 해결이 되지 않았습니다.

# ... 11 message listeners added to ...

인터넷에서 알려준 방법들로는 해결이 되지 않았고,
topic 11개 구독부터 문제가 되는 건 아닌가? 하는 생각이 들었습니다.

그리고 구독을 1개만 해보니 같은 문제가 발생하지 않았습니다.

제가 구축한 테스트 서버에서는 11개 이상의 구독도 잘되었으나, 실제 운영 서버에는 제한을 둔게 아닐까 생각이 됩니다. 
