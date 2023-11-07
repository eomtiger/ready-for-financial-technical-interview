# Hash란?
> 단방향 암호화 기법인 해시함수(HashFunction)을 이용하여 생성된 고정된 길이의 비트열을 의미합니다.
```md
**단방향 암호화 기법**
-> 암호화는 가능하지만 복호화는 불가능한 암호화 기법
```
  
해시 함수로 변경 전 원래의 데이터 값을 키(Key), 변경 후 데이터 값을 값(Value)이라고 하는데 변환하는 이 과정을 해싱(Hashing)이라고 합니다.

<br>

## HashMap
- Key와 Value에 Null을 허용합니다.
- 동기화를 보장하지 않습니다.
    - thread-safe하지 않기에 싱글 스레드 환경에서 사용하는게 좋습니다.
    - 하지만 동기화를 보장하지 않기에 속도가 빠릅니다.

-> 데이터를 찾는 속도는 빠르지만, 신뢰성과 안정성이 떨어집니다.

<br>

## HashTable
- Key와 Value에 Null을 허용하지 않습니다.
- 동기화를 보장합니다.
    - thread-safe하기 때문에 멀티 스레드 환경에서 사용할 수 있습니다.
    - 데이터 무결성을 보장합니다.

-> 스레드간 동기화 락으로 인해 매우 동작이 느립니다.

<br>

## ConcurrentHashMap
- Key와 Value에 Null을 허용하지 않습니다.
- 동기화를 보장합니다.
    - thread-safe하기 때문에 멀티 스레드 환경에서 사용할 수 있습니다.
- HashMap의 동기화 문제를 보완합니다.
    - 조작하는 Entry에 대해서만 락을 겁니다.
    - 따라서 HashTable보다 데이터를 다루는 속도가 빠릅니다.

-> Entry 아이템 별로 락을 걸기에 멀티 스레드 환경에서의 성능을 향상시킵니다.

<br>

## 결론
싱글 스레드 환경에서는 HashMap을, 멀티 스레드 환경이면 HashTable이 아닌 ConcurrentHashMap을 쓰는게 좋습니다.

<br>

---
### 참조
[HashMap vs HashTable vs ConcurrentHashMap](https://tecoble.techcourse.co.kr/post/2021-11-26-hashmap-hashtable-concurrenthashmap/)
[[자료구조]Hash, HashMap, HashTable](https://velog.io/@kwj2435/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-Hash-HashMap-HashTable)