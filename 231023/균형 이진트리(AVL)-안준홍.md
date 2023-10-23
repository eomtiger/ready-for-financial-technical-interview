# 균형 이진트리(AVL)
> 균형 이진트리란 부모 노드를 기준으로 좌측 서브트리의 높이와 우측 서브트리의 높이가 1이하인 트리를 말합니다. 그 중 AVL 트리는 부모 노드 기준 좌우측 서브 트리의 높이 차이 즉, `균형 인수`가 1이하가 아니게 되면 자동적으로 재분배를 통해 균형을 맞추는 트리를 말합니다.
```md
균형 인수(BF : Balance Factor)란?

- 부모 노드 기준으로 양쪽 서브트리의 높이 차이를 균형 인수라고 합니다.
- 균형 인수는 BF라고 부르기도 합니다.
```

<br>

### 장점
- BF가 모두 1이하(높이 차이가 비슷함)이므로 삽입, 삭제, 탐색이 O($log2n$)안에 가능합니다.
    - 균형 없는 트리의 경우 사향 이진트리와 같이 한쪽으로 노드가 쏠릴 경우 O(n) 시간이 걸리게 됩니다.

<br>

### 단점
- 자료가 많아지면 트리의 높이가 커지고, 한번의 정렬이 연쇄적인 정렬을 일으켜 재배치에 많은 시간을 쏟게 될 수 있습니다.

<br>

### 균형을 잃은 경우
> 기본 전제 조건 : 길이가 더 긴 서브 트리의 3개 노드 중 중간 값을 루트 노드로 바꾸고 나머지 2개의 노드 중 작은 노드를 왼쪽에, 큰 노드를 오른쪽에 재배치
> 

1. LL Case
- BF가 2이상 차이나는 노드가 Left → Left에 위치할 경우

![LL Case](https://github.com/junhong625/junhong625.github.io/assets/83000975/435b737d-517b-48a6-b2d8-be6beeae2f1e)

→ 균형을 왼쪽 서브트리로 인해 깨진 경우 오른쪽 방향으로 회전합니다.

2. RR Case
- BF가 2이상 차이나는 노드가 Right → Right에 위치할 경우

![RR Case](https://github.com/junhong625/junhong625.github.io/assets/83000975/be3576e3-e529-45cb-831e-3964fd2c78e2)

→ 균형이 오른쪽 서브트리로 인해 깨진 경우 왼쪽 방향으로 회전 합니다.

3. RL Case
- BF가 2이상 차이나는 노드가 Right → Left에 위치할 경우

![RL Case](https://github.com/junhong625/junhong625.github.io/assets/83000975/b26c9a0d-2ca2-439c-8643-9b9c19c69f1d)

→ 균형을 맞추기 위해 자식 노드들을 우회전, 부모 노드

4. LR Case
- BF가 2이상 차이나는 노드가 Left → Right에 위치할 경우

![LR Case](https://github.com/junhong625/junhong625.github.io/assets/83000975/db421feb-b4cd-4215-9cb2-b3c0203c8505)

<br>

---

### 참조
- https://code-lab1.tistory.com/61
- https://gdlovehush.tistory.com/156