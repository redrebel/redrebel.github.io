---
layout: post
published: true
title: Spring Cloud Eureka Server Tutorial
subtitle: 스프링 클라우드 유레카 서버 실습해보기
date: '2019-06-03'
tags: [eureka, spring, cloud]
---

스프링클라우드(이하 Spring Cloud) 컨포넌트중에 유레카(이하 Eureka) 를 통하여 서비스 등록(이하 service registry)과 발견(이하 discovery)를 간단히 실습해본다.  

Spring Cloud 와 Eureka에 대한 자세한 이론적 배경은 구글링을 하면 알수있다.



1. ​	Eureka Server
   - 서비스를 등록하고 어플리케이션을 찾고 관리하는 가장 잘 알려진 Discovery 서버이다.
   - 모든 microservice 는  Discovery 클라이언트로써 Eureka 서버에 등록된다.
   - Eureka 서버는 클라이언트 microserver의 실행상태와 포트번호, 그리고 IP 주소를 알고있다.
   
   
   
2. 실습환경
  
   - IntelliJ , JDK 8, Maven
  
  
  
3. 프로젝트 구조

   ![20190603-eureka01](/Users/red/pro/github-blog/img/20190603-eureka01.png)
   ![20190603-eureka02](/Users/red/pro/github-blog/img/20190603-eureka02.png)

4. 프로젝트 생성

   - 빈프로젝트로 생성한다.

   ![20190603-eureka03](/Users/red/pro/github-blog/img/20190603-eureka03.png)

   - 프로젝트명을 기입한다.
     ![20190603-eureka04](/Users/red/pro/github-blog/img/20190603-eureka04.png)
   
   - server 모듈을 생성한다.  
   
     
   
   - client 모듈을 생성한다.   
