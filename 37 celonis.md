---
title: celonis
author: JUNG YoungKyun
date: 2023-03-09
category: 37 celonis
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
                                    {% if post.title == "객체지향의 사실과 오해" %}
                                        <img alt="jest" class="sd-width-auto-book" src="./images/18 book/01 객체지향의 사실과 오해/객체지향의 사실과 오해.png">
                                    {% elsif post.title == "프로그래머의 뇌" %}
                                        <img alt="jest" class="sd-width-auto-book" src="./images/18 book/02/프로그래머의뇌.jpg">
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

셀로니스(Celonis)는 프로세스 마이닝 소프트웨어 분야에서 매우 유명한 기업입니다. 프로세스 마이닝은 기업이나 조직 내부의 프로세스를 데이터 분석 기술을 활용하여 분석하고, 개선하는 방법입니다. 셀로니스는 이러한 프로세스 마이닝을 쉽고 간단하게 수행할 수 있는 소프트웨어 도구를 제공합니다.

셀로니스는 대규모의 데이터를 수집하고 분석하여, 기업이나 조직 내부의 프로세스를 시각화하고, 분석할 수 있습니다. 이를 통해, 기업이나 조직은 프로세스 내부에서 발생하는 문제점을 파악하고, 개선점을 찾아내어 프로세스의 효율성을 높일 수 있습니다. 또한, 셀로니스는 프로세스의 실시간 모니터링 및 문제 발생 시 신속한 대처를 도와줍니다.

셀로니스의 주요 기능으로는 프로세스 시각화, 데이터 분석, 실시간 모니터링, 프로세스 자동화 및 최적화 등이 있습니다. 이러한 기능을 통해, 셀로니스는 다양한 산업 분야에서 활용되고 있으며, 금융, 제조, 유통 등에서 성공적인 사례가 많이 보고되고 있습니다.

셀로니스는 최근 AI(Artificial Intelligence)와 같은 기술을 활용하여, 기업이나 조직 내부의 프로세스를 자동으로 분석하고 개선할 수 있는 방법을 개발하고 있습니다. 또한, RPA(Robotic Process Automation)와 같은 자동화 기술과 연계하여, 조직 내부의 프로세스를 자동화하고, 최적화하는 것에 더욱 집중하고 있습니다.

이러한 셀로니스의 기술적인 발전은 프로세스 마이닝 분야에서 큰 관심을 받고 있으며, 앞으로도 많은 기업이 셀로니스의 소프트웨어 도구를 활용하여 프로세스 분석 및 개선을 수행할 것으로 예상됩니다.
