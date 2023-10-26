# B-Tree
B-Tree는 탐색 성능을 높이기 위해 균형 있게 높이를 유지하는 Balanced Tree의 일종이다. 모든 leaf node(단말 노드)가 같은 level로 유지되도록 자동으로 밸런스를 맞춰준다. 자식 node의 개수가 2개 이상이며, node 내의 key가 1개 이상일 수 있다.

node의 자식 수 중 최댓값을 K라고 하면, 해당 B-Tree를 K차 B-Tree라고도 한다. 

*Balanced Tree : 트리의 노드가 한 방향으로 쏠리지 않도록, 노드 삽입 및 삭제 시 특정 규칙에 맞게 재정렬하여 왼쪽과 오른쪽 자식 양쪽 수의 밸런스를 유지하는 트리 (최악의 경우에도 O(logN))

---
B-Tree의 조건은 다음과 같다.
1. node의 key의 수가 k개라면, 자식 node의 수는 k+1개이다. 
2. node의 key는 반드시 정렬된 상태여야 한다. 
3. 자식 node들의 key는 현재 node의 key를 기준으로 크기 순으로 나뉘게 된다. 
4. root node는 항상 2개 이상의 자식 node를 갖는다. (root node가 leaf node인 경우 제외) 
5. M차 트리일 때, root node와 leaf node를 제외한 모든 node는 최소 M/2, 최대 M개의 서브 트리를 갖는다. 
6. 모든 leaf node들은 같은 level에 있어야 한다.
![image](https://github.com/eomtiger/ready-for-financial-technical-interview/assets/81467332/892f9e49-1ce2-44c5-b64e-26ed13b78c4e)

위의 트리는 3차 B-Tree의 예시이다. 주황색 부분은 '자식 node를 가리키는 포인터'이고, 살구색 부분은 '각 node의 key'이다. key와 데이터가 1대1 대응하고 있다.

node 안에서 key들은 항상 정렬된 상태를 유지하며, 이진 탐색 트리처럼 항상 각 key의 왼쪽 자식은 자신보다 작고, 오른쪽 자식은 자신보다 크다. 

 

### Balanced tree를 사용하는 이유는 뭘까?

일반적인 트리인 경우 탐색하는데 평균적인 시간 복잡도로 O(logN)을 갖지만, 트리가 편향된 경우 최악의 시간복잡도로 O(N)을 갖게 된다.

![image](https://github.com/eomtiger/ready-for-financial-technical-interview/assets/81467332/f45447a0-d5b6-4592-9a69-e44f604badaa)

root node부터 탐색을 한다고 가정하고, 왼쪽처럼 편향된 트리에서 leaf node까지 탐색한다면 모든 node를 방문하기 때문에 O(N)의 시간이 걸리게 된다. 이러한 단점을 보완하기 위해 트리가 편향되지 않도록 항상 밸런스를 유지하는 트리가 필요하다. 자식들의 밸런스를 잘 유지하면 최악의 경우에도 O(logN)의 시간이 보장된다.


### 참고
- https://velog.io/@dbsrud11/CS-%EB%A9%B4%EC%A0%91-%EC%A7%88%EB%AC%B8-%EC%A0%95%EB%A6%AC#b-tree
- https://rebro.kr/169
