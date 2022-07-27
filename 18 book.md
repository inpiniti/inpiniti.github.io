---
title: Book 정리
author: JUNG YoungKyun
date: 2022-07-11
category: 18 book
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
                                    {% if post.title == "파이썬 머신러닝 완벽가이드" %}
                                        <img alt="객체지향의 사실과 오해" class="sd-width-auto-book" src="./images/ai/index/파이썬 머신러닝 완벽가이드 책.jpg">
                                    {% elsif post.title == "객체지향의 사실과 오해" %}
                                        <img alt="객체지향의 사실과 오해" class="sd-width-auto-book" src="./images/18 book/01 객체지향의 사실과 오해/객체지향의 사실과 오해.png">
                                    {% elsif post.title == "프로그래머의 뇌" %}
                                        <img alt="프로그래머의 뇌" class="sd-width-auto-book" src="./images/18 book/02/프로그래머의뇌.jpg">
                                    {% elsif post.title == "개발자에서 아키텍트로" %}
                                        <img alt="개발자에서 아키텍트로" class="sd-width-auto-book" src="./images/18 book/03 개발자에서 아키텍트로/개발자에서 아키텍트로.jpg">
                                    {% elsif post.title == "헤드 퍼스트 디자인 패턴" %}
                                        <img alt="헤드 퍼스트 디자인 패턴" class="sd-width-auto-book" src="./images/18 book/04 헤드 퍼스트 디자인 패턴/헤드퍼스트 디자인패턴.jpg">
                                    {% elsif post.title == "오브젝트" %}
                                        <img alt="오브젝트" class="sd-width-auto-book" src="./images/18 book/05 오브젝트/오브젝트 표지.jpg">
                                    {% endif %}
                                    
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

책을 읽고 정리하고자 함