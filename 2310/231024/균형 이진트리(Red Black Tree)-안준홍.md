# Red-Black Tree
> 자가 균형 이진 탐색 트리로 탐색, 삽입, 삭제에서 모두 최소 O(log n)이 보장되는 자료구조입니다.

<br>

### 특징
- 각 노드는 Red or Black 입니다.
- 루트 노드와 모든 NIL 노드들은 항상 Black 입니다.
- Red 노드는 자식으로 Red 노드가 있으면 안 됩니다. Red 노드의 자식은 모두 Black 입니다.
- 그에 반해 Black 노드는 자식으로 어떤 노드든 상관없습니다.
- 루트 노드에서 모든 리프 노드까지의 경로에 대해서 거치는 Black 노드의 숫자는 같습니다.
- 삽입된 노드는 항상 Red 노드입니다.

<br>

## 균형이 깨진 경우
> 균형이 깨진 경우, Red-Black Tree는 두 가지 행동을 취합니다. 삼촌 노드(부모 노드의 형제 노드)가 Black일 경우 `Restructing`, Red일 경우 `Recoloring`을 하게 됩니다.

<br>

### Restructing
균형이 깨졌을 때 삼촌 노드가 Black일 경우 조부모, 부모, 자식 세 노드들 중 중간 값이 세 노드들 중 루트 노드(Black)가 되고 나머지 두 노드가 자식 노드(Red)가 됩니다.
![](https://github.com/junhong625/TIL/assets/83000975/0f98cf48-aa88-4805-9ab2-82c72b6aefb4)

<br>

### Recoloring
균형이 깨졌을 때 삼촌 노드가 Red일 경우 `Restructing`과 다르게 재구성 하지 않고 조부모를 Red, 부모와 삼촌을 Black으로 바꿉니다. 이 작업 후 또 다시 Red가 이어진 노드가 있는 경우 `Recoloring` 또는 `Restructing` 작업이 연쇄적으로 일어나게 됩니다. 추가적으로 조부모 노드가 루트 노드인 경우 조부모 노드만 Black으로 변경합니다.
![](https://github.com/junhong625/TIL/assets/83000975/5f3f7f41-3643-4705-b14e-fc8af6624ed7)

<br>

---

### 참조

- https://suhwanc.tistory.com/197
- https://code-lab1.tistory.com/62