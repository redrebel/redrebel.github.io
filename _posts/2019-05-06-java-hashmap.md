---
layout: post
published: true
title: Java의 HashMap에 대하여 딱 이만큼만
tags: hashmap
date: '2019-05-06'
subtitle: HashMap에 대하여 자세히는 다루지는 않고 면접에 대응할 수 있는 수준까지만 정리하였다.
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
그외의 회사에서 면접시 이것과 관련된 질문을 한다면 솔찍히 오버라고 생각한다. 면접관님들은 괜히 이런거 물어보지 마시고 면접을 준비하는 분들도 혹시 모르니 공부해놔야지 하며 공부하는 시간에 다른거 공부하세요. 질문하지 않고 대답하지 않는게 제생각에 서로 공정거래입니다. 면접만을 고려한 싸구려 글이라고 생각하시는 분이 있을 수 있지만 나도 감히 자세히 안다고 말하지 못하고 완전히 이해하지도 못하는데 아는 척 글을 쓰는것이 더 싸구려 글을 만드는 거라고 생각한다. 

### Open-addressing 
해시 충돌이 일어나면 테이블 내의 새로운 주소를 계산하여 입력하는 것.
- 선형 탐사(Linear Probing)
- 제곱 탐사(Quadratic Probing)
- 이중 해싱(Double Hashing)

### Chaining 
해시 테이블의 각 버킷은 연결리스트(또는 트리)로 구성되며 해시 충돌 발생시 리스트에 추가하는 것

### Resizing 
해시 테이블의 크기를 더 크게 만들고, 새로운 크기에 맞추어 가지고 있던 모든 데이들을 다시 해싱하는 것

자세한 설명은 [여기참조](https://asfirstalways.tistory.com/332)

---  

java의 HashMap은 이러한 해시충돌을 줄이고자 크게 2가지를 사용한다.
- 보조 해시 함수 [여기참조](https://d2.naver.com/helloworld/831311)
- Separate Channing  

"보조 해시 함수에 대하여 자세히 설명해 주실 수 있나요?" 라고 물어보면 모른다고 답할지 아니면 위의 참조들을 찾아가서 대답할 수 있도록 준비할지는 여러분의 판단으로...

"자. 그럼 한번 HashMap을 짜보실래요?" 라고 물어보는건 그럴 수 있다고 생각한다.  

> 일반회사 - 나도 일반회사 다닌다 - 면접때 HashMap을 짜보게 시키는것을 찬성하는건 아니다. 면접관이 약간 개념없지만 어쩔수없는 대한민국의 현실인가 보다라고 생각하자. HashMap,HashTable의 차이점이나 String,StringBuffer,StringBuilder의 차이점에 대한 질문은 정말 구닥다리고 닭살돋는 질문이지만 구별해서 사용해야되는 경우가 있으므로 차라리 보다 의미있는 질문이다.

일반적으로 위에서 언급한 Map이라는 interface 조건을 충족하기 위해서는 아래의 method들이 제공되어야한다.
- containsKey(String key)
- get(String key)
- remove(String key)
- put(String key, String value)
- toString()

솔찍히 더 있어야한다.
[https://docs.oracle.com/javase/8/docs/api/java/util/Map.html](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)

---

코딩면접은 온라인사이트를 통한 테스트가 있고 손코딩등이 있는데 가장 원시적인 손코딩으로 한다는 가정으로 설명하겠다.  

우선 class를 먼저 선언해야한다.
```java
// MyHashMap. 클래스명으로 나쁘지 않다.
public class MyHashMap {
}

```

그리고 class를 사용할 main함수를 구현한다. 그저 막연히 `MyHashMap myHashMap = new MyHashMap()` 이라고 해놓고 동물이름 나라이름들을 넣지말고 지원하는 회사에서 의미있는 코딩을 하는게 좋다. 
음... 온라인 쇼핑몰이라고 하자
```java
public static void main(String[] args) {
        MyHashMap items = new MyHashMap();
        items.put("Apple", "50000");
        items.put("Banana", "30000");
        items.put("Mellon", "80000");
        items.put("PineApple", "100000");

        System.out.println("Initial map" + items);
		System.out.println("The price of Mango is: " + (items.containsKey("Mango") ? items.get("Mango") : "Unknown"));
        System.out.println("The price of PineApple is: " + (items.containsKey("PineApple") ? items.get("PineApple") : "Unknown"));
        
        System.out.println("Removing the price of Banana: " + items.remove("Banana"));
        System.out.println("Removing the price of PineApple: " + items.remove("PineApple"));
        System.out.println("Map after removals: " + items);
}

```

이제는 하나씩 구현해 나가자. MyHashMap을 구현하기 시작한다.
```java
public class MyHashMap {
  	// key가 array의 index가 아닌것 처럼 value도 링크드리스트class 의 value로 들어간다.
	class Entry {
        private String key;	
        private String value;
        private Entry next;	// Separate Channing를 위한
    }

    private final int INITIAL_SIZE = 10; 	// 초기사이즈

    private Entry[] buckets;

    public MyHashMap(){
        buckets = new Entry[INITIAL_SIZE];
    }

  	// HashMap을 만들려면 해시함수가 필요하다.
    private int hash(String key) {
        return key == null ? 0 : Math.abs(key.hashCode() % buckets.length);
    }
}
```


put함수를 구현한다. 해시함수의 결과값인 index를 이미 사용하고 있다면 링크드리스트의 마지막에 새로운 Entry를 추가한다.
```java
	public void put(String key, String value){
        int index = hash(key);
        Entry entry = new Entry();
        entry.key = key;
        entry.value = value;

        if(buckets[index] == null) {
            buckets[index] = entry;
        } else {
            Entry curEntry = buckets[index];
            while (curEntry.next != null){
                curEntry = curEntry.next;
            }
            curEntry.next = entry;
        }
    }
```

remove함수를 구현한다. key와 일치하는 Entry를 링크드리스트에서 제거한다.
```java
    public boolean remove(String key){
        int index = hash(key);

        if(buckets[index] != null){
            Entry curEntry = buckets[index];
            // found in first entry
            if(curEntry.key == key) {
                buckets[index] = curEntry.next;
                return true;
            }

            while (curEntry.next != null) {
                if(curEntry.next.key == key) {
                    curEntry.next = curEntry.next.next;
                    return true;
                }
            }
        }
        return false;
    }

```

나머지 함수들을 모두 구현한 최종 소스
```java

public class MyHashMap {
    class Entry {
        private String key;
        private String value;
        private Entry next;
    }

    private final int INITIAL_SIZE = 10;

    private Entry[] buckets;

    public MyHashMap(){
        buckets = new Entry[INITIAL_SIZE];
    }

    public void put(String key, String value){
        int index = hash(key);
        Entry entry = new Entry();
        entry.key = key;
        entry.value = value;

        if(buckets[index] == null) {
            buckets[index] = entry;
        } else {
            Entry curEntry = buckets[index];
            while (curEntry.next != null){
                curEntry = curEntry.next;
            }
            curEntry.next = entry;
        }
    }

    public boolean remove(String key){
        int index = hash(key);

        if(buckets[index] != null){
            Entry curEntry = buckets[index];
            // found in first entry
            if(curEntry.key == key) {
                buckets[index] = curEntry.next;
                return true;
            }

            while (curEntry.next != null) {
                if(curEntry.next.key == key) {
                    curEntry.next = curEntry.next.next;
                    return true;
                }
            }
        }
        return false;
    }

    public String get(String key) {
        int index = hash(key);

        if(buckets[index] != null) {
            Entry curEntry = buckets[index];
            while (curEntry.key == key) {
                return curEntry.value;
            }
            curEntry = curEntry.next;
        }
        return null;
    }

    public boolean containsKey(String key) {
        int index = hash(key);

        if(buckets[index] != null) {
            Entry curEntry = buckets[index];
            while (curEntry != null) {
                if (curEntry.key == key) {
                    return true;
                }
                curEntry = curEntry.next;
            }
        }

        return false;
    }

    @Override
    public String toString(){
        StringBuilder builder = new StringBuilder();

        for(int i = 0; i < buckets.length; i++) {
            if (buckets[i] != null) {
                Entry curEntry = buckets[i];
                builder.append("[Index_" + i + "=");
                while (curEntry != null) {
                    builder.append(curEntry.key + ":" + curEntry.value + ",");
                    curEntry = curEntry.next;
                }
                // removes last comma
                builder.replace(builder.length()-1, builder.length(), "");
                builder.append("],");
            }
        }

        builder.replace(builder.length()-1, builder.length(), "");
        return builder.toString();
    }

    // Hash function
    private int hash(String key) {
        return key == null ? 0 : Math.abs(key.hashCode() % buckets.length);
    }

    public static void main(String[] args) {
        MyHashMap items = new MyHashMap();
        items.put("Apple", "50000");
        items.put("Banana", "30000");
        items.put("Mellon", "80000");
        items.put("PineApple", "100000");

        System.out.println("Initial map" + items);
		System.out.println("The price of Mango is: " + (items.containsKey("Mango") ? items.get("Mango") : "Unknown"));
        System.out.println("The price of PineApple is: " + (items.containsKey("PineApple") ? items.get("PineApple") : "Unknown"));
        
        System.out.println("Removing the price of Banana: " + items.remove("Banana"));
        System.out.println("Removing the price of PineApple: " + items.remove("PineApple"));
        System.out.println("Map after removals: " + items);
	}
}
```

화이팅!
