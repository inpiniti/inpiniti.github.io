---
title: AZURE
author: JUNG YoungKyun
date: 2022-05-10
category: 10 azure
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

Azure 가입을 2022년 5월 5일에 하고 가상 머신을 만들었습니다.

AWS를 기존에 사용 중이었는데, 무료 크래딧이 끝나 Azure로 넘어 왔는데, Azure의 무료 가상머신 생성에 진행은 조금 어려웠었습니다.

그 부분에 대해서 [크기선택이 안될 때](https://inpiniti.github.io/10%20azure/2022-05-15-%ED%81%AC%EA%B8%B0%EC%84%A0%ED%83%9D%EC%9D%B4-%EC%95%88%EB%90%A0-%EB%95%8C.html)
라는 제목으로 포스팅을 해두었습니다.

해결이 되고 나서는 [Docker](https://www.docker.com/) 와 Docker 를 웹상에서 관리할 수 있게 도와주는 툴인 [portainer](http://20.214.141.2:9000/) 를 올려두었습니다.

그 위에 클라이언트 역할을 하는 [react app](http://20.214.141.2/) 과, 서버 역할을 하는 [spring api](http://20.214.141.2:8080/) 를 올려두었습니다.

그리고 Azure 에는 가상머신 외에도 [Azure Database for MySQL 유동서버](mysql-5.mysql.database.azure.com) 를 생성 해두었습니다.

Database 생성에는 별 다른 어려움이 없었던 것 같습니다.

아무래도 여기에서는 제 포트폴리오 관련 내용을 올리게 될 것 같습니다.