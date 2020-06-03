---
layout: post
published: true
title: create-react-app 생성시 template이 생성되지 않을 경우
date: '2020-06-04'
tags: [react, create-react-app, template]
---

새로운 react 프로젝트를 시작하려고 아래와 같이 create-react-app 를 실행하니 마지막에 이상한 문구가 뜨면서 template도 생성되지 않는것 같았다. 

```bash
$ npx create-reacte-app
.
..
...
A template was not provided. This is likely because you're using an outdated version of create-react-app.
Please note that global installs of create-react-app are no longer supported.
```

그래서 구글링을 해보니

[https://github.com/facebook/create-react-app/issues/8085](https://github.com/facebook/create-react-app/issues/8085)

global로 설치된 creat-react-app 을 지우고 다시 해보라는 댓글이 있다.

```bash
$ npm uninstall -g create-react-app 
```

그리고 나서 다시 create-react-app 를 해보니 깔끔한 마지막 메시지를 볼수 있었다.

```bash
We suggest that you begin by typing:

  cd contact-app
  npm start

Happy hacking!
```