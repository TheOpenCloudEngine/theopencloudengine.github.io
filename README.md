## Local Server Running

Jekyll 설치는 아주 쉽고 직관적이지만, 시작하기 전에 먼저 확인해야 할 몇 가지 준비물이 있습니다.

 - [Ruby](http://www.ruby-lang.org/en/downloads/) (Jekyll 2 사용 시 v1.9.3 이상, Jekyll 3 사용 시 v2 이상의 개발 패키지 포함)
 - [RubyGems](http://rubygems.org/pages/download) 
 - 리눅스, 유닉스, 또는 맥 OS X
 - [NodeJS](http://nodejs.org/), 또는 다른 JavaScript 실행환경 (Jekyll 2 와 그 이전 버전에서, CoffeeScript 지원에 필요함).

```
$ git clone https://github.com/TheOpenCloudEngine/theopencloudengine.github.io
$ cd theopencloudengine.github.io
$ gem install jekyll
$ jekyll serve
```

## 메뉴 꾸미기

_data/uris.json 파일수정에서 항목을 더하거나, 뺍니다.

#### 단일 메뉴

```
[
  {
    "name": "Home",  -> 이름
    "url": "/index"  -> 링크
  }
]  
```

#### 좁은 메뉴

![](https://github.com/TheOpenCloudEngine/theopencloudengine.github.io/blob/master/document/image/short.png)

```
[
  {
    "name": "Case Studies",  -> 이름
    "panel": {
      "type": "single",
      "child": [  -> 서브 메뉴
        {
          "name": "금융 및 보험",
          "url": "/case/case01"
        },
        {
          "name": "공공 및 제조/건설/물류",
          "url": "/case/case02"
        },
        {
          "name": "IT 및 통신",
          "url": "/case/case03"
        }
      ]
    }
  }
]
```


#### 넓은 메뉴

![](https://github.com/TheOpenCloudEngine/theopencloudengine.github.io/blob/master/document/image/large.png)

```
[
  {
    "name": "Products", -> 이름
    "panel": {
      "type": "large",
      "menu": [
        {
          "title": "BPM Products",  -> 분기 패널별 이름
          "col": 4, -> 분기 패널의 사이즈 (풀 사이즈는 12)
          "child": [  -> 분기 패널 하위의 서브 메뉴
            {
              "name": "uEngine BPM",
              "url": "/products/bpm"
            },
            {
              "name": "Essencia",
              "url": "/products/essencia"
            },
            {
              "name": "SNS",
              "url": "/products/sns"
            }
          ]
        }
        .
        .
      ]
    }
  }
]
```

## 마크다운 꾸미기

#### 마크다운 파일 위치

신규 메뉴를 추가했을 경우, 신규 매뉴의 url 과 콘텐츠 파일위 위치 및 이름이 일치해야 합니다.

```
[
  {
    "name": "Library",
    "panel": {
      "type": "single",
      "child": [
        {
          "name": "Tutorial Video",
          "url": "/library/video"  -> /library/video.md 파일의 마크다운 파일이 있어야 합니다.
        }
      ]
    }
  }
]
```

 - /library/video.md
 
 
```
---
layout: default  -> (_layouts 폴더 내의 html 템플릿)
permalink: /library/video  -> url, 메뉴의 url 과 일치해야 합니다.
showgroup: true -> 화면 좌측의 서브메뉴 노출
---

마크다운 작성 필요  -> 화면 출력 내용
```

![](https://github.com/TheOpenCloudEngine/theopencloudengine.github.io/blob/master/document/image/normal.png)


#### 프로덕트 페이지 또는 인덱스 페이지처럼, 큰 배너 화면이 있는 마크다운 작성시

```
---
category: products  -> 카테고리
layout: products -> 레이아웃 (_layouts 폴더 내의 html 템플릿)
title: uEngine Billing
intro: 유엔진 빌링(UEngine Billing) 은 Subscription 청구 및 지불을 위한 통합 플랫폼입니다. 결제에 관련된 Full Cycle 을 지원하고, 플러그인 아키텍처를 통해 타사 시스템과 쉽게 통합 할 수 있습니다.
permalink: /products/billing
banner: ../assets/img/banner/banner-4.jpg
video: <iframe width="100%" height="315" src="https://www.youtube.com/embed/PL9F7S6sG1A" frameborder="0" allowfullscreen="" class="style-scope uengine-products"></iframe>
github: https://github.com/TheOpenCloudEngine/uEngine-bill
demo: http://billing.uengine.io
---

```





