---
layout: post
published: false
title: Java의 HashMap에 대하여 딱 이만큼만
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
```
"korea" --> "seoul"  
"japan" --> "tokyo"  
```
과 같은 식이다.




Java에서 Map은 interface이다.  
즉 먼가 내부적으로 구현되어있는 것이 아니고 역활과 기능을 정리한 개념이라는 뜻이다.  
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

그런데 hash함수와 array로는 모든 key들을 다 포함할 수 없다.
어느 순간부터 hash함수로는 처리못하거나 hash함수의 결과로 같은 값이 나올수가 있는데
이것을 해시충돌(hash collision)이라고 한다.  

> 해시충돌을 줄이는 다양한 아래 방법에 대하여 논해야한다면 구글이나 삼성전자, sk, 네이버, 카카오 등의 면접시이다.
아니면 정말 기술력이 있는 공인된 스타트업이거나 실제로 그 개념들을 사용해야하는 회사들이다. 
그외의 회사에서 면접시 이것과 관련된 질문을 한다면 솔찍히 오버라고 생각한다. 면접관님들은 괜히 이런거 물어보지 마시고 면접을 준비하는 분들도 혹시 모르니 공부해놔야지 하며 공부하는 시간에 다른거 공부하세요. 질문하지 않고 대답하지 않는게 제생각에 서로 공정거래입니다.

### Open-addressing 
해시 충돌이 일어나면 테이블 내의 새로운 주소를 계산하여 입력하는 것.
- 선형 탐사(Linear Probing)
- 제곱 탐사(Quadratic Probing)
- 이중 해싱(Double Hashing)

### Chaining 
해시 테이블의 각 버킷은 연결리스트(또는 트리)로 구성되며 해시 충돌 발생시 리스트에 추가하는 것

### Resizing 
해시 테이블의 크기를 더 크게 만들고, 새로운 크기에 맞추어 가지고 있던 모든 데이들을 다시 해싱하는 것

---  

java의 HashMap은 이러한 해시충돌을 줄이고자 크게 2가지를 사용한다.
- 보조 해시 함수
- Separate Channing  



![hashmap-vs-treemap.png]({{site.baseurl}}/img/hashmap-vs-treemap.png)

https://jaybdev.net/2017/06/10/Algorithm-7/
https://d2.naver.com/helloworld/831311
https://odol87.tistory.com/3

해시충돌
- Open Addressing
- Separate Chaining

Java HashMap에서 사용하는 방식은 Separate Channing.
