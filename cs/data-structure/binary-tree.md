## Binary Tree

바이너리트리, 이진트리 같은 말이다.

각각의 노드가 최대 두 개의 자식 노드를 가지는 트리 자료 구조이다.

<img src="images/binary_tree.png" style="background-color: white">

*크기가 9이고, 높이가 3인 이진 트리*

### 탐색
```
in-order : 왼쪽 자식노드, 내 노드, 오른쪽 자식노드 순서로 방문한다.
pre-order : 내 노드, 왼쪽 자식노드, 오른쪽 자식노드 순서로 방문한다.
post-order : 왼쪽 자식노드, 오른쪽 자식노드, 내 노드 순서로 방문한다.
level-order : 내 노드, 내 노드로부터 깊이 1인 노드들, 내 노드로부터 깊이 2인 노드들, ... , 내 노드로부터 깊이 N인 노드들 (N: 나(트리)의 깊이)
```

### Referfence

https://ko.wikipedia.org/wiki/%EC%9D%B4%EC%A7%84_%ED%8A%B8%EB%A6%AC