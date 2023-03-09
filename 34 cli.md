---
title: cli
author: JUNG YoungKyun
date: 2023-03-08
category: 34 cli
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

CLI(커맨드 라인 인터페이스)는 텍스트 기반으로 작동하는 인터페이스로, 컴퓨터 프로그램을 사용하는 방법 중 하나입니다. CLI는 명령어를 입력하고 그 결과를 텍스트로 반환합니다. CLI는 그래픽 사용자 인터페이스(GUI)와는 다릅니다. GUI는 아이콘, 버튼, 창 등의 시각적 요소를 사용하여 프로그램을 제어합니다.

CLI는 특히 서버 운영체제에서 사용되는데, 서버는 보통 GUI 환경이 아닌 텍스트 기반으로 작동합니다. 따라서 CLI를 통해 서버를 관리할 수 있습니다. 또한, CLI는 스크립트를 작성하고 실행할 수 있는 데에도 이용됩니다. 스크립트를 작성하면 CLI를 사용하여 자동화된 작업을 수행할 수 있습니다.

CLI를 사용하면 명령어를 통해 파일 관리, 프로그램 설치, 시스템 관리 등 다양한 작업을 수행할 수 있습니다. 일반적으로 CLI에서는 명령어와 함께 옵션을 추가하여 원하는 결과를 얻을 수 있습니다. 예를 들어, "ls -l" 명령어는 현재 디렉토리의 파일 목록을 자세히 보여줍니다.

CLI는 몇 가지 장점이 있습니다. 첫째, CLI는 GUI보다 더욱 빠릅니다. GUI는 그래픽 처리에 많은 자원을 사용하기 때문입니다. 둘째, CLI는 더욱 정확합니다. GUI는 종종 사용자의 실수로 인해 예상치 못한 결과가 발생할 수 있습니다. 반면 CLI는 명령어가 정확하면 항상 같은 결과를 반환합니다. 셋째, CLI는 배치 작업을 수행할 때 매우 유용합니다. 스크립트를 작성하여 자동화된 작업을 수행할 수 있습니다.

하지만 CLI에는 몇 가지 단점도 있습니다. 첫째, CLI는 사용법을 익히는 데 시간이 걸릴 수 있습니다. GUI보다는 명령어를 입력하는 것이 더욱 어렵습니다. 둘째, CLI는 명령어를 외울 필요가 있습니다. GUI는 대부분의 경우 그래픽 요소를 사용하여 기능을 수행할 수 있습니다. CLI는 그렇지 않습니다.

마지막으로, CLI는 일반 사용자보다는 전문가나 개발자에게 더욱 유용합니다. 일반 사용자에게는 GUI가 더욱 친숙하고 쉽습니다. 하지만 CLI는 개발자나 시스템 관리자 등 전문가에게는 매우 강력한 도구가 될 수 있습니다. CLI를 사용하면 더욱 복잡한 작업도 자동화할 수 있고, 작업의 효율성도 높일 수 있습니다.
                                                                   
CLI는 주로 유닉스 계열 운영체제에서 사용됩니다. 이는 유닉스에서 CLI가 처음 개발되었기 때문입니다. 그러나 최근에는 윈도우 운영체제에서도 CLI를 지원하는 도구들이 나와서 윈도우에서도 CLI를 사용할 수 있게 되었습니다.

CLI를 사용하는 도구는 다양합니다. 대표적으로는 셸(shell)이 있습니다. 셸은 CLI를 제공하는 프로그램으로, 사용자가 명령어를 입력하면 그 결과를 반환해줍니다. 유닉스에서는 보통 bash, zsh, csh 등의 셸을 사용하고, 윈도우에서는 cmd.exe나 PowerShell 등의 셸을 사용합니다.

CLI를 사용하는 도구 중에는 특별한 기능을 수행하는 명령어들도 있습니다. 예를 들어, grep은 파일에서 특정 문자열을 찾는 명령어이고, sed는 파일 내용을 수정하는 명령어입니다. 이런 명령어들은 개발자나 시스템 관리자에게 매우 유용합니다.

최근에는 CLI를 지원하는 도구들이 계속해서 개발되고 있습니다. 예를 들어, Docker는 CLI를 사용하여 컨테이너를 관리할 수 있습니다. Kubernetes도 마찬가지입니다. 이런 도구들은 CLI를 사용하여 자동화된 작업을 수행하는 것이 가능합니다.

결론적으로, CLI는 개발자나 시스템 관리자에게 매우 유용한 도구입니다. CLI를 사용하면 작업의 효율성을 높일 수 있고, 자동화된 작업도 수행할 수 있습니다. CLI는 초기에는 사용법을 익히는 데 시간이 걸리지만, 익숙해지면 GUI보다 더욱 빠르고 정확한 작업이 가능합니다.