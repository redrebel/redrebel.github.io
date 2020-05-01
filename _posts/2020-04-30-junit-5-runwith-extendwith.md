---
layout: post
published: true
title: JUnit5 에서 @RunWith 대신 @ExendWith 사용
date: '2020-04-30'
tags: [junit5, test]
---

Spring5 + JUnit5 에서 테스트를 위하여 @RunWith(SpringRunner.class)를 선언해 사용하려고 하니 
class를 찾을 수 없다며 JUnit4를 다운받아서 classpath에 추가하라고한다.

<img src="https://cjred.net/img/blog/20200430-blog-01.png" alt="20200430-blog-01.png"  style="zoom:50%;" />

인터넷을 찾아보니 @RunWith가 @ExtendWith(..) 으로 바꿨다고 한다..

<img src="https://cjred.net/img/blog/20200430-blog-02.png" alt="20200430-blog-02.png" style="zoom:50%;" />


> 추가  
나중에 안 사실이지만 JUnit5는 JUnit Vintage라는 서브패키지를 통해 자체적으로 하위호환성을 포함하고 있다.  
내가 @RunWith를 사용할 수 없었던 이유는 아래와 같이 org.junit.vintage:junit-vintage-engine 모듈을 exclude 해주고 있기 때문이다.
<img src="https://cjred.net/img/blog/20200430-blog-03.png" alt="20200430-blog-03.png" style="zoom:50%;" />


참고 : 
- https://www.baeldung.com/junit-5-runwith
- https://junit.org/junit5/docs/current/user-guide/#migrating-from-junit4-tips
- https://junit.org/junit5/docs/current/user-guide/#running-tests-junit-platform-runner
