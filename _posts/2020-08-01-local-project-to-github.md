---
layout: post
published: true
title: 기존 폴더를 github로 관리하기
date: '2020-08-01'
tags: [github]
---
기존 로컬에 저장해서 사용중인 프로젝트나 폴더를 github에 올려놓고 관리하면 편하다.  

우리 회사는 자체서버를(on-premise) 사용중이라서 vpn으로 접속 후 일부 작업파일을 commit push 하는 방식으로 재택시 활용하고 있다.  

물론 아무리 vpn으로 접속해야 접근이 가능하지만 개인정보등 민감한 정보를 github에 올려놓지 않는다.  

그외에도 처음부터 github에 repository를 만들는 것을 까먹고 나중에 프로젝트 파일을 github에 올리려하면 어떻게 할지몰라 버벅이게 된다.  
(나만 그런듯...)   

중간에 기존 폴더를 github에 올리고 관리하는 방법은 아래와 같다.  
```bash
# github에 repository를 생성한다.

# 그후 로컬폴더에서 git를 초기화한다.
git init

# 생성된 git-주소 를 remote로 등록한다.
git remote add origin [git-주소]

# master를 가저온다.
git pull origin master

# 로컬폴더의 내용을 추가한다.
git add .

# commit 을 한다.
git commit -m 'first commit'

# github에 올린다.
git push -u origin master
```