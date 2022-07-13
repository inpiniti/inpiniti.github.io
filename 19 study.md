---
title: study
author: JUNG YoungKyun
date: 2022-06-11
category: 19 study
layout: post
---

<div class="sd-container-fluid ">
    <div class="docutils">
    {% assign sorted_cats = site.categories | sort %}

    {% for category in sorted_cats %}
        {% assign _posts = category.last %}
        {% assign _post = _posts.last %}
        {% assign _url = _post.url %}
        {% assign category_name = category | first %}
        {% assign page_name = page.category | escape %}
        {% if category_name == page_name %}
            {% for posts in category %}
                {% assign reversed_posts = posts | reverse %}
                {% for post in reversed_posts %}
                    {% if post.url %}
                        <a class="docutil" href="{{site.baseurl}}{{post.url}}">
                            <div class="sd-card">
                                <div class="sd-card-body">
                                    <p class="sd-card-text">
                                        <strong>{{ post.title | escape }}</strong><br>
                                    </p>
                                </div>
                            </div>
                        </a>
                    {% endif %}
                {% endfor %}
            {% endfor %}
        {% endif %}
    {% endfor %}
    </div>
</div>

# JupyterHub

회사 jupyterHub 링크 : [http://192.168.55.117](http://192.168.55.117)

# Postgres DB

|key|value|
|---|---|
|Host|192.168.55.115|
|Port|30432|
|DB name|2022_aistudy|
|User/Pass|aistudy / aistudy|
|Table name|titanic|

# 1주차 : Orientation day
1. 아나콘다 설치
    1. Anaconda Distribution - [https://www.anaconda.com](https://www.anaconda.com/products/individual)
        
        Conda는 Windows, macOS 및 Linux에서 실행되는 오픈 소스 패키지 및 환경 관리 시스템입니다. Conda는 패키지를 빠르게 설치, 실행 및 업데이트하고 ...

    2. 옵션 체크 :
        ```
        [v]Register Anaconda  as my default Python ..
        ```
    
    3. Anaconda Prompt 에서 버전 확인
        ```python
        conda --version
        python --version 
        ```
   
    4. Path 설정
        ```python
        `c:/users/../anaconda3`
        ```

    5. 패키지 설치
        ```python
        pip install pandas
        ```

    6. 주요 패키지
        1. Pandas
        2. Numpy
        3. Matplotlib
        4. Seaborn
        5. Sklearn
        6. PM4PY
        7. Psycopg2
    
2. 주피터 허브 로그인 - [http://192.168.55.117](http://192.168.55.117)

3. 주피터 허브 인스톨
    1. PIP
        ```python
        import sys
        !{sys.executable} - m pip install PACKAGE
        ```
    2. Conda
        ```python
        import sys
        !conda install -y --prefix {sys.prefix} PACKAGE
        ```