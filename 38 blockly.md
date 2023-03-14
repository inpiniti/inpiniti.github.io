---
title: blockly
author: JUNG YoungKyun
date: 2023-03-14
category: 38 blockly
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

Blockly는 구글에서 만든 블록 코딩 언어입니다. 이 언어는 시각적인 블록을 사용하여 코딩을 할 수 있도록 해줍니다. Blockly는 어린이들을 위해 만들어졌지만, 대부분의 연령층이 사용할 수 있습니다.

Blockly를 사용하면 쉽고 빠르게 코딩을 할 수 있습니다. 블록을 조합하여 프로그램을 만들 수 있으며, 이는 전문적인 코딩을 할 필요가 없는 사용자에게 좋은 옵션입니다. 또한, Blockly는 JavaScript, Python, PHP 등과 같은 다양한 프로그래밍 언어로 변환할 수 있습니다.

Blockly는 다양한 분야에서 사용될 수 있습니다. 예를 들어, 교육 분야에서는 초등학생부터 중학생까지 다양한 연령층이 Blockly를 사용하여 코딩 교육을 받을 수 있습니다. 또한, IoT (사물 인터넷) 분야에서도 사용됩니다. Blockly를 사용하면 IoT 기기를 제어하거나 IoT 앱을 만들 수 있습니다.

Blockly는 무료로 사용할 수 있으며, 온라인에서 바로 사용할 수 있습니다. 또한, Blockly를 사용하는 방법에 대한 많은 자료와 지원이 있습니다. 예를 들어, Blockly 공식 웹사이트에서는 사용자들이 만든 다양한 블록을 공유하고 있습니다.

블록 코딩 언어인 Blockly는 코딩을 처음 시작하는 사람들에게 좋은 옵션입니다. 블록을 조합하여 프로그램을 만들 수 있으며, 이는 전문적인 코딩을 할 필요가 없는 사용자에게 좋은 옵션입니다. Blockly는 다양한 분야에서 사용될 수 있으며, 무료로 사용할 수 있습니다.
