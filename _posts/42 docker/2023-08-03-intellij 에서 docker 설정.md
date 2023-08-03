---
title: intellij 에서 docker 설정
author: JUNG YoungKyun
date: 2023-08-03
category: 42 docker
layout: post
---

# docker server 설정 했던 내용
혹시나 또 다시 설정을 할 수도 있을 것 같아서, 설정했던 내용을 기록해 두고자 합니다.

1. AAS
    - TCP socket
        - Engine API URL : tcp://192.168.55.102:4000
        
2. AAS CLOUD
    - TCP socket
        - Engine API URL : tcp://20.214.234.252:4000

3. api
    - TCP socket
        - Engine API URL : tcp://43.201.20.32:4000

4. Docker
    - TCP socket
        - Engine API URL : tcp://20.214.141.2:4000

5. MY DOCKER
    - TCP socket
        - Engine API URL : tcp://113.131.145.133:4000

# docker file 설정 했던 내용

Edit Configurations... 를 눌러 설정 했던 내용입니다.

```
Name : Dockerfile
Server : AAS CLOUD
Dockerfile : Dockerfile
Context folder : .
Image tag : iochord/aas_client
[ v ] Run built image
Container name : AasClient
Bind ports : 80:3000
```
 
