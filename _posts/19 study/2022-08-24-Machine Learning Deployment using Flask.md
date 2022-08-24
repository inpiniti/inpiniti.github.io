---
title: Machine Learning Deployment using Flask
author: JUNG YoungKyun
date: 2022-08-24
category: 19 study
layout: post
---

# 8주차 : Machine Learning Deployment using Flask
1. **Study: REST API with Flask**
    - Please read and try to understand about flask REST API (e.g.., how to create rest api with flask, how to call the api, etc.)
        - References:
            [article1](https://www.sqlshack.com/create-rest-apis-in-python-using-flask/),
            [article2](https://pythonbasics.org/flask-rest-api/),
            [article3](https://justkode.kr/python/flask-restapi-1)
    - Create a **simple project** on how to implement flask rest api !

2. **Deploying a Machine Learning Model with REST API Flask (모델 배포)**
    - Please read this following article: 
        [link](https://hackernoon.com/machine-learning-w22g322x)
    - Deploy a machine learning model using flask (with rest api)
        - Please follow the steps in the above-mentioned article and run on your local computer !
    - Additional Task:
        - On the article, they used **RandomForestRegressor** as classifier, **please change it with another type of classifier !**
            - You can choose the classifiers freely, e.g., linear model, decision tree, support vector machine, etc.
        - (optional) **Please make a simple UI** for this project (similar with the last week task)
            ```python
            # creating model
            from sklearn.ensemble import RandomForestRegressor
            classifier = RandomForestRegressor()
            classifier.fit(X_train, y_train)
            ```
3. **Deploying the project on the server**
    - Instead run the project on your local computer, **you can deploy the project on server** so other members can access your work
    - You might choose the server based on your preferences (e.g., Heroku, etc)  **give us any recommendations !**
    - Share your works with others ^^

4. **Try with other projects**
    - You can try with other problems/projects
    - For your references (choose one of them):
        - [https://wikidocs.net/143898](https://wikidocs.net/143898)
        - [https://niceman.tistory.com/192](https://niceman.tistory.com/192) 
        - [https://github.com/akashdeepjassal/mnist-flask](https://github.com/akashdeepjassal/mnist-flask)
        - Digital covid detection: 
            [link](https://blogs.sap.com/2020/06/28/digital-covid-19-detection-kit-based-on-chest-x-ray-using-machine-learning-and-sap-conversational-ai/) 

세팅중 에러
```
  File "./app.py", line 3, in <module>

    from flask_restx import Resource, Api # Api 구현을 위한 Api 객체 import

  File "/usr/local/lib/python3.8/site-packages/flask_restx/__init__.py", line 5, in <module>

    from .api import Api  # noqa

  File "/usr/local/lib/python3.8/site-packages/flask_restx/api.py", line 50, in <module>

    from .swagger import Swagger

  File "/usr/local/lib/python3.8/site-packages/flask_restx/swagger.py", line 18, in <module>

    from werkzeug.routing import parse_rule

ImportError: cannot import name 'parse_rule' from 'werkzeug.routing' (/usr/local/lib/python3.8/site-packages/werkzeug/routing/__init__.py)
```

stackoverflow Answers

The solution (workaround) was that I additionally included werkzeug in the version 2.1.2 in the requirements.txt

```
werkzeug==2.1.2
```

azure 데이터 베이스 연결 에러

```
UserWarning: pandas only support SQLAlchemy connectable(engine/connection) ordatabase string URI or sqlite3 DBAPI2 connectionother DBAPI2 objects are not tested, please consider using SQLAlchemy
```