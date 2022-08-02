---
title: AAS
author: JUNG YoungKyun
date: 2022-05-29
category: 06 aas
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

|참고 사이트|링크|
|---|---|
|cdd|[link](https://cdd.iec.ch/){:target="_blank"}|
|독일의 제조분야 디지털 트랜스포메이션|[link](https://zdnet.co.kr/view/?no=20191227090925){:target="_blank"}|
|스마트 제조혁신 기술개발 사업|[link](https://www.smart-factory.kr/notice/read/60?page=6&bbsClCodeSe=00000013&bsnsClCodeSe=88888888){:target="_blank"}|
|admin-shell-io by IDTA|[link](https://github.com/admin-shell-io){:target="_blank"}|
|aasx-package-explorer download|[link](https://github.com/admin-shell-io/aasx-package-explorer/releases){:target="_blank"}|