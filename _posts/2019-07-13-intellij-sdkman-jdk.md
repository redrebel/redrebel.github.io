---
layout: post
published: true
title: (MacOS) IntelliJ 에서 SDKMAN의 JDK 경로 설정하기
date: '2019-07-14'
tags: [intelliJ, sdkman, jdk]
---

다양한 버전의 JDK 설치하고 사용하는 방법은 다양하다.  
[https://blog.benelog.net/installing-jdk.html](https://blog.benelog.net/installing-jdk.html)

그중 SDKMAN은 범용적으로 사용할 수 있는 도구이다.  
[https://sdkman.io/](https://sdkman.io/)

그런데 intelliJ 를 사용하게 되면 JDK 경로를 추가해야되는데 (cmd + : )
MacOS의 경우에 ./sdkman 가 기본적으로 숨김폴더이기 때문에 경로를 찾을 수 없는 경우가 있다.

이런 경우에는 아래와 같이 심볼릭링크를 만들어서 접근하도록 해야한다.

```
ln -s ~/.sdkman ~/sdkman
```

[https://www.programmingmitra.com/2019/03/how-to-install-multiple-versions-of-java-on-the-same-machine.html](https://www.programmingmitra.com/2019/03/how-to-install-multiple-versions-of-java-on-the-same-machine.html)
