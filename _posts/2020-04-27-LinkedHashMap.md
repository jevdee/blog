---
published: true
layout: single
title: "LinkedHashMap"
categories: java
tags: java, hashmap, linkedhashmap
comments: true
---

# LinkedHashMap
* 순서(access or insertion)를 유지하는 HashMap
* HashMap을 상속하여 HashMap의 기능을 모두 제공 (HashMap은 Map 인터페이스 구현)
* HashMap(버킷으로 구현)에서 순서 유지를 위한 추가 메모리 사용
* HashTable과 버킷을 기반으로 한 doubly linked list로 구현
 
### LinkedHashMap의 생성자
```java
public LinkedHashMap(int initialCapacity, float loadFactor) {
        super(initialCapacity, loadFactor);
        accessOrder = false;
}
public LinkedHashMap(int initialCapacity) {
        super(initialCapacity);
        accessOrder = false;
}
public LinkedHashMap() {
        super();
        accessOrder = false;
}
public LinkedHashMap(Map<? extends K, ? extends V> m) {
        super(m);
        accessOrder = false;
}
public LinkedHashMap(int initialCapacity,
                         float loadFactor,
                         boolean accessOrder) {
        super(initialCapacity, loadFactor);
        this.accessOrder = accessOrder;
}
```
### 파라메터 설명
* initialCapacity: hashmap의 크기(default 16)
* loadFactor: get()과 put()의 시간복잡도 O(1)을 유지하기 위해 hashmap을 늘리는 시점. default값은 0.75f(75% of the map size)
* accessOrder: true인 경우 접근 순서(access-order), false인 경우 삽입 순서대로 데이터 저장

# Leetcode 관련 문제: [링크](https://leetcode.com/problems/lru-cache/)
Capacity가 있는 Least-Recently Used(LRU) Cache를 구현하라는 문제로, 접근 순서를 유지하는 맵인 LinkedHashMap을 사용 가능하다.
LinkedHashMap을 초기화할 때 accessOrder를 true로 사용하면 접근 순서를 유지할 수 있으며, 
Capacity가 다 찼을 경우 removeEldestEntry() 함수를 통해 put()시 map에 입력된 엔트리 중 가장 오래된 엔트리를 삭제할 수 있다.

```java
@Override
protected boolean removeEldestEntry(Map.Entry<Integer, Integer> eldest) {
    //return false;   //기본 코드
    return size() > capacity;   //수정 후 코드
}
```

# HashMap, TreeMap, LinkedHashMap 비교표
Difference between HashMap, TreeMap, LinkedHashMap and hashtable in Java
![Difference between HashMap, TreeMap, LinkedHashMap and hashtable in Java.png](./assets/images/)

출처: [https://javarevisited.blogspot.com](https://javarevisited.blogspot.com/2015/08/difference-between-HashMap-vs-TreeMap-vs-LinkedHashMap-Java.html)
      [https://www.javatpoint.com](https://www.javatpoint.com/load-factor-in-hashmap)
