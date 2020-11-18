---
layout: post
published: true
title: MacOS 에서 HomeBrew 로 Git Install(Upgrade)하기
date: "2020-11-19"
tags: [git, homebrew]
---

github에서 기본branch 를 master에서 main으로 바꾼다고 한다.

[New GitHub Repositories Default to Main Branch](https://www.infoq.com/news/2020/10/github-main-branch/#:~:text=Git%20version%202.28%20introduced%20a,user's%20defaults%20configuration%2C%20or%20systemwide.)

[https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/changing-the-default-branch](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/changing-the-default-branch)

이에 따라 git 2.28 이후 버전부터 init 직접 지정할 수 있는 옵션이 추가되었다.

[https://github.blog/2020-07-27-highlights-from-git-2-28/](https://github.blog/2020-07-27-highlights-from-git-2-28/)

이 기능을 사용하고 싶어서 git를 homebrew를 통해 install 하였다.



macOS를 사용하면 git의 기본버전은 대충 2.27이다.  
(각자 다를 수 있다.)

```bash
$ git --version
git version 2.27.0
```



Homebrew 를 통해 최신버전의 git를 설치

```bash
$ brew install git
```



그런데 설치를 하고나서 아무리해도 Homebrew를 통해 설치된 git를 찾지 못하였다.

해결책은 git에 대한 link를 새로 정의하는 것이다.

```bash
$ brew link --overwrite git
```



