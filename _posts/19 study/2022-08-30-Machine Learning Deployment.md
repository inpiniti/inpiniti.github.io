---
title: Machine Learning Deployment
author: JUNG YoungKyun
date: 2022-08-30
category: 19 study
layout: post
---

# 8주차 : Machine Learning Deployment
1. **Reading section: Revisit Machine Learning Deployment**
    - Understanding about Continuous Delivery for Machine Learning (CD4ML)
    - Read these following articles :
        - CD4ML: 
            [article](https://martinfowler.com/articles/cd4ml.html)
            [article](https://www.thoughtworks.com/insights/blog/getting-smart-applying-continuous-delivery-data-science-drive-car-sales) 
            [youtube](https://www.youtube.com/watch?v=um6Sq5EhW6A)
        - MLOps guide: 
            [article](https://mlops-for-all.github.io/docs/introduction/intro/)
            [article](https://mlops-guide.github.io/)
    - After reading articles, what kind of insights you got? Share with others !
    - If you have any good articles / books, please share it !

2. **Deploy Deep Learning Model using Flask (MNIST digit recognition)**
    - Please go to this following link: 
        [github_1](https://github.com/akashdeepjassal/mnist-flask)
        or 
        [github_2](https://github.com/Prajwal10031999/Handwritten-Digit-Recognition-CNN-Flask-App-)
    - You will find a flask project for MNIST digit recognition
    - **Try to replicate that project on your local computer (you can choose one of them)**
        - Please do not clone and run the project directly
        - Instead, you can try to create each files by yourself and run.
        - **Important: Please be careful with Library dependency (check requirements.txt).** You can get many errors.
            - You may use the older version and follow the code, or
            - You may use the new version and modify some parts.
    - The goal of this task are:
        - Getting know about another type of learning approach that is deep learning
        - Getting know on deep learning structure project (i.e., what’s the difference with previous tasks)
        - Able to run the (deep learning) project and show the result to others
        - If you have any questions or problems, please share it and let’s discuss it together
    - **Curious about MNIST digit recognition?**
        - MNIST dataset :
            [article](https://tensorflowkorea.gitbooks.io/tensorflow-kr/content/g3doc/tutorials/mnist/beginners/) 
        - MNIST digit recognition : you can find a lot of article discuss the digit recognition task

3. **Share your ideas !**
    Please share your ideas for next study ! 
    What kind of **topic** for our next study ?

# CD4ML
Data + Model + Code

> 언제든지 릴리스할 수 있는 엔지니어링 접근 방식

1. ML 모델을 교육하고 웹 애플리케이션과 통합하고 프로덕션에 배포하는 초기 프로세스

    ![그림2](../images/19 study/2022-08-30-Machine Learning Deployment/그림2.png){: .center} 
    
    예측모델 training -> 웹 애플리케이션 통합 -> 클라우드 프로덕션에 배포
    
    ![그림3](../images/19 study/2022-08-30-Machine Learning Deployment/그림3.png){: .center}
    
2. 대규모 조직의 일반적인 기능 사일로는 장벽을 만들어 ML 애플리케이션을 프로덕션에 배포하는 종단 간 프로세스를 자동화하는 기능을 저해할 수 있습니다.

    ![그림4](../images/19 study/2022-08-30-Machine Learning Deployment/그림4.png){: .center}
    
    - 조직의 구조
        - data engineers
        - data scientists
        - ML engineers, developers
        
    지연과 마찰로 이어질 수 있음
    
    코드 외 관리할 아티팩트가 늘어나고, 버전관리가 어려움

3. 판매 예측 문제에 대한 기계 학습 파이프라인과 DVC를 사용하여 이를 자동화하는 3단계

    ![그림5](../images/19 study/2022-08-30-Machine Learning Deployment/그림5.png){: .center}
    
    - DVC(Data Science Version Control) 오픈소스로 공식화
        - git과 유사
        - 버전 추적이 가능하여, 데이터가 변경될 때 모델을 다시 훈련
        - 다른 환경에서 프로세스 재현
    
    - 세가지 dvc run 명령으로 구성
        ```
        dvc run -f input.dvc \ ➊
          -d src/download_data.py -o data/raw/store47-2016.csv python src/download_data.py
        dvc run -f split.dvc \ ➋
          -d data/raw/store47-2016.csv -d src/splitter.py \
          -o data/splitter/train.csv -o data/splitter/validation.csv python src/splitter.py
        dvc run ➌
          -d data/splitter/train.csv -d data/splitter/validation.csv -d src/decision_tree.py \
          -o data/decision_tree/model.pkl -M results/metrics.json python src/decision_tree.py
        ```
    
