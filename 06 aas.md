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

중소벤처기업부에서 [스마트 제조혁신 기술개발 사업](https://www.smart-factory.kr/notice/read/60?page=6&bbsClCodeSe=00000013&bsnsClCodeSe=88888888) 을 시행하게 되었고,
어쩌다보니 저도 참여하게 되었습니다.

자세한 내용은 적을수는 없고, 다만 진행하면서 개인적으로 알아봤던 내용 중 공유해도 될 것 같은 내용들만 올릴 예정입니다.

카테고리 명인 AAS는 Asset Administration Shell 약자이며, 
인더스트리 4.0에서 디지털 트윈의 구현으로 매우 중요한 기술입니다.

포스팅을 어떻게 진행할지 모르겠지만, aas에 대한 내용을 많을 것 같아 이렇게 정했는데,
aas 만 올리지는 않을 것 같습니다.

검색을 해보면 [독일의 제조분야 디지털 트랜스포메이션](https://zdnet.co.kr/view/?no=20191227090925) 이라는 기사도 있으니 참조해봐도 좋을 것 같습니다.

- 프로젝트 하면서 정리했던 내용 (개인 내용만)
    - 22.05.13
        - 이해한 내용 정리 (공개 불가)
    - 22.05.17
        - 표준화 수행 관련 절차, 지침 조사
        - 표준화를 위한 조직의 구성 및 역할과 책임
    - 22.05.19
        - Industrie 4.0 스마트 제조 및 aas 표준 기술 (교육 과정 내용 일부 발췌한 것)
    - 22.05.24
        - 연계데이터 정합성 관리 방안 조사
    - 22.05.26
        - AAS 활용사례
    - 22.05.31
        - 산업별 핵심 운영 데이터 및 관련 DB 현황 조사
    - 22.06.02
        - AAS 활용사례 2
    - 22.06.07
        - 산업별 핵심 운영 데이터 및 관련 DB 현황 조사2
    - 22.06.10
        - 제품, 공정, 설비 sample data
    - 22.06.16
        - Type, Instance 등 Aasx PackEx 사용방법
    - 22.06.23
        - 산출물 맵핑 및 변환 방법
    - 22.06.30
        - Data Validation
    
- Todo list (정리한 자료 내용 중 미흡했던 부분 보완을 위해 다시 재연구 위함)
    - 일괄 등록 확인 필요 (자재가 몇 만 건인 경우 하나하나 넣기 힘듬)
    - aasx 를 바로 db로 저장하는 방법
    - 2번이 안될 경우 aasx 파일을 db로 변환하여 등록하는 기능에 대해