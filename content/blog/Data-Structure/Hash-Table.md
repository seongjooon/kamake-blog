---
title: 'Hash Table'
date: 2019-8-09 19:10:03
category: 'Data-Structure'
---

Hash는 내부적으로 배열을 활용해서 데이터를 저장하기 때문에 검색 속도가 빠르다. 특정한 값을 검색하는데 데이터 고유의 인덱스로 접근한다. Average Case의 Time Complexity는 O(1)이 된다. 하지만 문제는 이 인덱스로 저장되는 key값이 불규칙하다는 것이다.

Hash Table의 Big-O의 Average는 O(1)으로 Search, Insertion, Deletion을 할때 효율적으로 빠르다. 하지만 hashing function을 거쳐서 key값의 충돌이 생긴 경우에는 여러가지 방법을 동원하여 해결해야하므로 Worst는 O(n)이다.

> #### Big-O (when there is no collisions)

- Insertion: O(1) (해싱 함수가 복잡해도 동일한 조건에 의해서 시간이 걸린다)

- Deletion: O(1)

- Search: O(1)

> #### is Hash Table Perfect?

- Not suitable for ordered data

  순서가 있는 배열에는 어울리지 않는다.
  억지로 끼워맞출수는 있지만 랜덤하게 추가되기때문에 정확하지 않다.

- Might need large space allocation

  테이블의 크기를 확보해놓아야 하기때문에 공간 효율성이 떨어진다.

- Must have a good

  해쉬 함수의 성능에 따라 테이블의 질도 달라진다.

> #### Hash Function (needs)

- to be **idempotent.**

  인풋에 따라 아웃풋이 동일하게 생성되어야한다. 절대 다른 조건이 생기면 안된다.

- to have a good dstribution of values.

  확보해놓은 공간에 분포가 잘되는 것이 좋다. 함수의 성능이 빨라야 쓰는 의미가 있다.
  해쉬 테이블은 해쉬 함수에 의해 성능이 보장된다.

- to be performant

좋은 hash function는 어떠한 조건들을 갖추고 있어야 하는가?
일반적으로 좋은 hash function는 키의 일부분을 참조하여 해쉬 값을 만들지 않고 키 전체를 참조하여 해쉬 값을 만들어 낸다. 하지만 좋은 해쉬 함수는 키가 어떤 특성을 가지고 있느냐에 따라 달라지게 된다.

> #### 보조 해시 함수

보조 해시 함수(supplement hash function)의 목적은 key의 해시 값을 변형하여 해시 충돌 가능성을 줄이는 것이다. Separate Chaining 방식을 사용할 때 함께 사용되며 보조 해시 함수로 Worst Case 에 가까워지는 경우를 줄일 수 있다.

> #### 해시 버킷 동적 확장(Resize)

해시 버킷의 개수가 적다면 메모리 사용을 아낄 수 있지만 해시 충돌로 인해 성능 상 손실이 발생한다. 그래서 HashMap 은 key-value 쌍 데이터 개수가 일정 개수 이상이 되면 해시 버킷의 개수를 두 배로 늘린다. 이렇게 늘리면 해시 충돌로 인한 성능 손실 문제를 어느 정도 해결할 수 있다. 또 애매모호한 '일정 개수 이상'이라는 표현이 등장했다. 해시 버킷 크기를 두 배로 확장하는 임계점은 현재 데이터 개수가 해시 버킷의 개수의 75%가 될 때이다. 0.75라는 숫자는 load factor 라고 불린다.

> #### 실제예시

주소록, 블록체인, JS엔진은 객체를 해쉬 테이블로 처리한다.
**map**은 not stable yet.
