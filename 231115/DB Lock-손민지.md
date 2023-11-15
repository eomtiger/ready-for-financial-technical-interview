# DB Lock
트랜잭션 처리의 순차성을 보장하기 위한 방법

## 종류
### 공유락(LS, Shared Lock)  
- Read Lock이라고도 하며 트랜잭션이 읽기를 할 때 사용하는 락
- 데이터를 읽기만하기 때문에 같은 공유락끼리는 동시에 접근이 가능

### 베타락(LX, Exclusive Lock)
- Write Lock이라고도 하며 데이터를 변경할 때 사용하는 락
- 트랜잭션이 완료될 때까지 유지되며, 베타락이 끝나기 전까지 어떠한 접근도 허용하지 않음

<br>

## 출처
https://dev-coco.tistory.com/158
