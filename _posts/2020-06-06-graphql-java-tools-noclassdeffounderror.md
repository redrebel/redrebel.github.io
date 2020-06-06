---
layout: post
published: true
title: NoClassDefFoundError when using GraphQL Java Tools > 5.4.x
date: '2020-06-06'
tags: [graphql, graphql-java-tools, kotlin]
---

https://github.com/graphql-java-kickstart/graphql-spring-boot#graphql-java-tools

만일 graphql-java-tools 와 spring-boot 2.1.x 이나 그이하 버전을 함께 사용하고 있다면 spring boot 설정에서 명시적으로 `kotlin.version`을 1.3.10 이나 그 이상으로 지정해야한다.

이유는 graphql-java-tools 에서 kotile 1.3.x 이상에서 지원하는 coroutine 을 사용하는데 spring-boot-parent 에서 kotlin 1.2.x를 선언하고 있기 때문이다.



해결방법은 2가지가 있다.

1. kotlin.version을 지정한다.(공식적으로 추천하는 방법)
2. 낮은 버전의 graph-java-tools 를 사용하는 방법



# 1.kotlin.version을 지정하는 방법

Using Gradle

gradle.properties 에 kotlin 버전을 지정한다.

`kotlin.version=1.3.70`

Using Maven

`<properties>` 섹션에 kotlin 버전을 지정한다.

```xml
<properties>
  <kotlin.version>1.3.70</kotlin.version>
</properties>
```



그런데 kotlin-stdlib-jdk1.8 에서는 잘안되는 것같다.

그냥 kotlin-stdlib 를 사용하자

```xml
<dependency>
  <groupId>org.jetbrains.kotlin</groupId>
  <artifactId>kotlin-stdlib</artifactId>
  <version>${kotlin.version}</version>
</dependency>
```





# 2. 낮은 버전의 graph-java-tools 를 사용하는 방법 <= 5.4.x

만일 5.4.x 을 사용하려면 관련  dependency 도 낮은 버전으로 낮추면 된다.

`graphql-java-tools` 5.4.x 는 2018년 버전이다. 지금(2020.06.06)은 6.0.2 이다.

https://mvnrepository.com/artifact/com.graphql-java-kickstart/graphql-java-tools

긴말은 생략하겠다....

```xml
<dependency>
  <groupId>com.graphql-java</groupId>
  <artifactId>graphql-java</artifactId>
  <version>11.0</version>
  <!-- 스프링버전이 2.1.x 버전이라서 아마도 예전버전인 11.0을 쓸수밖에 없는것 같다      
graphql.AssertException: Object required to be not null    at 
graphql.Assert.assertNotNull(Assert.java:22)    at 
graphql.execution.instrumentation.DocumentAndVariables.<init>
(DocumentAndVariables.java:19)    at 
graphql.execution.instrumentation.DocumentAndVariables.<init>
(DocumentAndVariables.java:13)    at 
graphql.execution.instrumentation.DocumentAndVariables$Builder.build(DocumentAndVariable
s.java:55)    at graphql.GraphQL.parse(GraphQL.java:561)  -->
</dependency>
<dependency>
  <groupId>com.graphql-java</groupId>
  <artifactId>graphql-spring-boot-starter</artifactId>
  <version>5.0.2</version>
</dependency>
<dependency>
  <groupId>com.graphql-java</groupId>
  <artifactId>graphiql-spring-boot-starter</artifactId>
  <version>5.0.2</version>
</dependency>
<dependency>
  <groupId>com.graphql-java</groupId>
  <artifactId>graphql-java-tools</artifactId>
  <version>5.2.4</version>
</dependency>
```

