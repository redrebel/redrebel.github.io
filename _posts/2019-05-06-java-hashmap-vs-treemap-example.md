---
layout: post
published: false
title: Java의 HashMap 과 TreeMap
---

[이전](https://cjred.net/2018-12-03-how-to-use-java-hashmap-effectively/) 글에서 다루었듯이 HashMap은 매우 유용한 자료형(?)이다.  
HashMap의 개념에 대하여 나름 쉽게 정리 역시 앞서 글에서 정리되어 있으므로 따로 반복하지 않겠다.

해시테이블과 관련된 안좋은 기억이 있는데 쓰다보니 내용이 길어져서 관련된 글은 따로 작성하겠다.

그럼... 본글에서는 어떤 내용을 담을 것인가...

면접에서 "HashMap 아세요?" 로 시작하는 패턴(?)에 어떻게 대응 할지에 대하여 적어 보겠다.  
사실 면접에서 HashMap에 대하여 물어보는 것에 대하여 회의를 느끼는 1인이다.(이유는 다음에...)

Java에서 HashMap과 HashTable의 비교하는 글은 인터넷에 많이 있으므로 따로 정리하지 않겠다.

HashMap은 key 와 value로 구성되는데 Map이라는 자료구조를 사용한다.
Map은 key와 value을 연결하는 개념의 자료구조이다.  

    "korea" --> "seoul"  
    "japan" --> "tokyo"  

과 같은 식이다.

Java에서 Map은 interface이다. 즉 먼가 내부적으로 구현되어있는 것이 아니고 역활과 기능을 정리한 개념이라는 뜻이다.  
[https://docs.oracle.com/javase/8/docs/api/java/util/Map.html](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)  

Map은 하나의 key에 하나의 value가 mapping된다.  
그외에도 여러가지 개념과 조건들이 있다.

하지만 쉽게 생각해서 사용자가 입력한 key를 바로 Map의 구현체에서 key로 사용하기에는 어려움이 많다.  
만일 내부적으로 array을 사용한다면 array의 index는 숫자형이 된다.

HashMap은 사용자가 입력한 key를 Hash함수로 계산된 값을 index로 사용하는 배열에 value를 담는 개념으로 Map 구현한 자료형이다.

만일  
key = "korea"  
value = "seoul"  
으로 저장되야 하고  
hash("korea") 의 결과가 1이면  
arr[1] = "seoul"로 저장한다는 것이다.  

한줄로 요약하면 
arr[hash("korea")] = "seoul" 이다.



![hashmap-vs-treemap.png]({{site.baseurl}}/img/hashmap-vs-treemap.png)

https://jaybdev.net/2017/06/10/Algorithm-7/
https://d2.naver.com/helloworld/831311
https://odol87.tistory.com/3

해시충돌
- Open Addressing
- Separate Chaining

Java HashMap에서 사용하는 방식은 Separate Channing.