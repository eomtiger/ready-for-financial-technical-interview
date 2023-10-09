# Garbage Collection이란?
> 자바의 메모리 관리 방법 중 하나로 JVM의 Heap 영역에서 동적으로 할당했던 메모리 중 필요 없게 된(참조하지 않는) 메모리 객체를 모아 주기적으로 제거하는 프로세스를 말합니다.

<br>

---

### 배경 지식

<br>

### 가비지 컬렉션 대상
객체에 참조가 이루어지고 있다면 `Reachable`로 구분되고,  
객체에 유효한 참조가 없다면 `Unreachable`로 구분되어 수거됩니다.
- `Reachable` : 객체가 참조되고 있는 상태
- `Unreachable` : 객체가 참조되고 있지 않은 상태(GC의 수거 대상)

<br>

### 가비지 컬렉션 단점
- 개발자가 메모리가 언제 해제되는지 정확하게 알 수 없습니다.
- 가비지 컬렉션이 동작하는 동안에는 다른 동작을 멈추기 때문에 오버헤드가 발생합니다.

<br>

# 가비지 컬렉션 작동 과정

## heap 메모리의 구조
![](https://github.com/gyoogle/tech-interview-for-developer/assets/83000975/49c83a2e-b0d5-403d-81ef-bc584cd20a98)
JVM의 힙(heap) 영역은 동적으로 레퍼런스 데이터가 저장되는 공간으로서, 가비지 컬렉션에 대상이 되는 공간입니다.

heap 영역은 처음 설계될 때 2가지의 전제로 설계되었습니다.
1. 대부분의 객체는 금방 접근 불가능한 상태(Unreachable)가 된다.
2. 오래된 객체에서 새로운 객체로의 참조는 아주 적게 존재한다.
> 즉, 객체는 대부분 일회성이며, 메모리에 오랫동안 남아있는 경우는 드물다는 것입니다.  

-> 위와 같은 특성을 이용해 JVM 개발자들은 효율적인 메모리 관리를 위해 Young과 Old 총 2가지 영역으로 설계했습니다. 

<br>

### Young 영역(Young Generation)
- 새롭게 생성된 객체가 할당되는 영역입니다.
- 대부분의 객체가 금방 Unreachable 상태가 되기 때문에, 많은 객체가 Young 영역에 생성되었다가 사라집니다.
- **Young 영역에 대한 가비지 컬렉션을 Minor GC**라고 부릅니다.

<br>

### Old 영역(Old Generation)
- Young 영역에서 Reachable 상태를 유지하여 살아남은 객체가 복사되는 영역입니다.
- Young 영역보다 크게 할당되며, 영역의 크기가 큰 만큼 가비지는 적게 발생합니다.
- **Old 영역에 대한 가비지 컬렉션을 Majon GC 또는 Full GC**라고 부릅니다.

<br>

---

## Young 영역에서의 3가지 영역
![](https://github.com/gyoogle/tech-interview-for-developer/assets/83000975/a498c73c-05f1-4a89-85a9-627060f3fc44)
### Eden
- new를 통해 새로 생성된 객체가 위치하는 영역입니다.
- 정기적인 가비지 수집 후 살아남은 객체들은 Survivor 영역으로 보냅니다.

<br>

### Survivor0 / Survivor1
- 최소 1번의 GC 이상 살아남은 객체가 존재하는 영역입니다.
- Survivor0과 Survivor1 중에 하나는 반드시 비어있어야한다는 규칙이 존재합니다.

<br>

### Minor GC 과정
Young Generation의 공간은 Old Generation에 비해 상대적으로 작기 때문에 메모리 상의 객체를 찾아 제거하는데 적은 시간이 걸립니다.
1. 생성된 객체는 Eden에 위치
2. 객체가 계속 생성되어 Eden 영역이 꽉차게 될 시 Minor GC 실행
3. `Reachable` 객체를 탐색(mark)해 한 개의 Survivor 영역으로 이동(Survivor 영역 하나는 비워둬야 하기 때문)
4. Eden 영역에서 `Unreachable` 객체의 메모리를 해제(sweep)
5. 살아남은 모든 객체들은 age 값이 1씩 증가

<br>

```markdown
**age 값이란?**
Survivor 영역에서 해당 객체가 살아남은 횟수를 의미하는 값으로 Object Header에 기록됩니다.
만일 age 값이 임계값에 다다르면 Old 영역으로의 이동 여부를 결정하게 됩니다.
-> JVM 중 일반적인 HotSpot JVM의 경우 임계값이 31입니다.(객체 헤더에 age를 기록하는 부분이 6bit로 되어있기 때문입니다.)
```
6. 1번부터 5번까지 반복합니다.(Survivor0에 객체가 존재하는 상황에서 Minor GC과정을 진행한다면 살아남은 Reachable 객체들은 모두 Survivor1로 이동)

<br>

### Major GC 과정
1. 객체의 age가 임계값에 도달하게 되면 Old Generation으로 이동(Promotion)합니다.
2. 1번의 과정이 반복되어 Old Generation 영역의 공간이 부족하게 되면 Major GC가 발생하게 됩니다.

<br>

### Minor GC vs Major GC
| GC 종류| 대상 | 실행 시점 | 실행 속도 |
| --- | --- | --- | --- |
| Minor GC | Young Generation | Eden 영역이 꽉 찬 경우 | 빠르다 |
| Major GC | Old Generation | Old 영역이 꽉 찬 경우 | 느리다 |

<br>

---
### 참조
- https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC#heap_%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%9D%98_%EA%B5%AC%EC%A1%B0
- https://coding-factory.tistory.com/829