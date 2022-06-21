---
title: JAVASCRIPT
author: JUNG YoungKyun
date: 2022-05-29
category: 05 javascript
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

참조 [javascript | MDM](https://developer.mozilla.org/ko/docs/Web/JavaScript)

참조 [모던 javaScript 듀토리얼](https://ko.javascript.info/)

참조 [javascript - 나무위키](https://namu.wiki/w/JavaScript)

[액션-계산-데이터 관점으로 보는 함수형 프로그래밍 패러다임](https://yozm.wishket.com/magazine/detail/1485/?fbclid=IwAR1znXFQiqT2WOgMaKhwujQiNEEj_lszK3_C7NWqZzucxvICSTxVZSTm9qc)

[아토믹 디자인을 활용한 디자인 시스템 도입기](https://fe-developers.kakaoent.com/2022/220505-how-page-part-use-atomic-design-system/?fbclid=IwAR0p59AAcbIPJMv0u0Zolz79sz931qMn8hyDuO1sFz612icLNnN8FXDg86M)

세미나 일정

- 9월 프론트엔드 동향 (45분)
- 10월 프론트엔드 아키텍쳐 동향 (45분)