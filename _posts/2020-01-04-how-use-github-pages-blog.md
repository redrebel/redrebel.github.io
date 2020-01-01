---
layout: post
published: true
title: GitHub Pages 에 Blog Theme 를 적용하고 글 올리는 방법
date: '2020-01-04'
tags: [blog, github, typora, vscode]
---

> 왜 블로그를 써야 하는 지, GitHub pages 가 무엇인지 등은 다루지 않는다



# 1. GitHub Pages 사용하기

Repository를 생성하고 Settings > GitHub Pages에서 Source 를 master branch로 선택한다.

![20200104-blog-01.png](https://cjred.net/img/blog/20200104-blog-01.png)



# 2. Blog Theme 적용하기

> 개인적으로 Ghost Theme ( [https://github.com/jekyller/jasper2](https://github.com/jekyller/jasper2) ) 를 좋아하지만 사용하기가 번거로워서 손쉬운 다른 테마를 사용 중 이다.

Google 에서 `GitHub Jekyll blog Themes` 등 으로 검색을 한다.

http://www.jekyllnow.com/ <-- 30초 안으로 블로그 생성이 가능하다고 한다.

https://deanattali.com/beautiful-jekyll/ <-- 5분이내로 블로그 생성가능하다고 한다.(저는 이것을 사용. 하지만 세부 설정까지 하려면 시간이 좀 더 걸림)



몇가지 [meta tag](https://github.com/daattali/beautiful-jekyll#yaml-front-matter-parameters) 를 포함하여 MarkDown 형식의 파일을 만들어서 _posts 폴더에 넣으면 바로 블로그로 포스팅 된다.

```yaml
# 예시
-----------------
layout: post #블로그글. page 이면 일반적인 웹페이지
published: true #배포. false 이면 main page에 보이지 않는다.
title: GitHub Pages 에 Blog Theme 를 적용하고 글 올리는 방법 #제목
date: '2020-01-04' #등록일자 지정
tags: [blog, github, typora, vscode] #테그를 지정
------------------
```



# 3. Blog 글 작성 방법(MarkDown 편집)

대표적으로 아래 3가지 방법으로 글을 작성하고 관리 하는 방법을 소개한다.



## 3.1. VS code 를 사용하는 방법

`Markdown Preview Github Styling` Extension 을 설치하면 GitHub스타일로 미리보기가 가능하다.



## 3.2. Typora 를 사용하는 방법

https://www.typora.io/

Typora를 사용하면 편집창에서 바로 결과를 보면서 Markdown 문서를 편집할 수 있고 여러가지 편한 기능들이 있다.

이미지 삽입 `![]()` 을 입력하면 자동으로 이미지를 지정하는 기능이 나타낸다.

![20200104-blog-02.png](https://cjred.net/img/blog/20200104-blog-01.png)

url을 지정하거나 로컬파일을 지정 가능하다.



## 3.3. prose.io 를 사용하는 방법
[https://prose.io](https://prose.io/)

prose.io 는 웹에서 GitHub 의 content를 관리( 파일을 생성, 수정, 삭제)하는 서비스를 제공하는 사이트이다.

주로 GitHub Pages 에서 Jekyll 사이트와 Markdown content를 편리하게 관리 할 수 있다.


