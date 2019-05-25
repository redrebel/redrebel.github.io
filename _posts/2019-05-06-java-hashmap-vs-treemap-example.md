---
layout: post
published: false
title: Java의 HashMap 과 TreeMap
---

[이전](https://cjred.net/2018-12-03-how-to-use-java-hashmap-effectively/) 글에서 다루었듯이 HashMap은 매우 유용한 자료형(?)이다. HashMap의 개념에 대하여 나름 쉽게 정리 역시 앞서 글에서 정리되어 있으므로 따로 반복하지 않겠다.

해시테이블과 관련된 안좋은 기억이 있는데 쓰다보니 내용이 길어져서 관련된 글은 따로 작성하겠다.

그럼... 본글에서는 어떤 내용을 담을 것인가...

면접에서 "HashMap 아세요?" 로 시작하는 패턴(?)에 어떻게 대응 할지에 대하여 적어 보겠다.
사실 면접에서 HashMap에 대하여 물어보는 것에 대하여 회의를 느끼는 1인이다.(이유는 다음에...)

Java에서 HashMap과 HashTable의 비교하는 글은 인터넷에 많이 있으므로 따로 정리하지 않겠다.


![hashmap-vs-treemap.png]({{site.baseurl}}/img/hashmap-vs-treemap.png)

https://jaybdev.net/2017/06/10/Algorithm-7/
https://d2.naver.com/helloworld/831311
https://odol87.tistory.com/3

해시충돌
- Open Addressing
- Separate Chaining

Java HashMap에서 사용하는 방식은 Separate Channing.