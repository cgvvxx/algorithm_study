# DFS/BFS



### DFS(Depth-First Search; 깊이 우선 탐색)

### & BFS(Breadth-First Search; 너비 우선 탐색)

> DFS : 루트 노드(혹은 임의의 노드)에서 시작하여 다음 분기로 넘어가기 전에 해당 분기를 완벽히 탐색하는 방법
>
> BFS : 루트 노드(혹은 임의의 노드)에서 시작하여 인접한 노드를 우선적으로 탐색하는 방법



### 1. Graph

- 그래프는 꼭지점(V; Vertex) 또는 정점(Node)과 간선(E, Edge)로 이루어진 자료구조. G = (V, E)

- 그래프 탐색 알고리즘이란 하나의 정점에서 시작하여 순서대로 모든 정점들을 한 번씩 방문하는 것 (따라서 노드의 탐색 여부를 확인하기 위한 체크배열이 필요)

- 그래프를 구현하는 대표적인 방법으로는 

  ###### 1. 인접행렬(Adjacency Matrix) : 정점(V)이 N개 일때 N x N의 2차원 배열 형태로 표현

  ###### 2. 인접리스트(Adjacency List) : 각각의 정점에 인접한 정점들을 리스트로 표현

- DFS의 시간복잡도 인접행렬 : O(V^2) , 인접리스트 : O(V+E)

<img src="C:\Users\XD\Dropbox\adj.png" alt="adj" style="zoom:70%;" />



### 2. DFS/BFS

- 1. DFS : 스택 또는 재귀함수로 구현

  2. BFS : 큐로 구현

     <img src="C:\Users\XD\Dropbox\dfs.png" alt="dfs" style="zoom:40%;" /> <img src="C:\Users\XD\Dropbox\bfs.png" alt="bfs" style="zoom:40%;" />

- 일반적으로 구현은 DFS가 BFS보다 간단하지만 검색속도는 BFS가 DFS보다 빠름

- 모든 노드를 방문하고자 할 경우 DFS, BFS 중 선택
- 경로의 특징을 저장해둬야 하는 경우 DFS, 최단거리를 구해야 하는 경우 BFS
- 검색 대상인 그래프가 큰 경우 DFS, 그래프의 규모가 크지 않고 시작 지점으로부터 원하는 대상이 그리 멀지 않은 경우 BFS



### Ex. DFS/BFS

```python
# DFS ; 재귀함수 형태의 알고리즘
# 인접리스트로 표현된 graph
graph = [[], [2, 3, 8], [1, 7], [1, 4, 5], [3, 5], [3, 4], [7], [2, 6, 8], [1, 7]]
visited = [False] * len(graph)

def dfs(graph, v, visited):
    visited[v] = True
    print(b, end=' ')
    for i in graph[v]:
        if not visited[i]:
            dfs(graph, i, visited)
            
dfs(graph, 1, visited)

>> Result ; 1 2 7 6 8 3 4 5
```

```python
# BFS ; Queue 활용
# 인접리스트로 표현된 graph
graph = [[], [2, 3, 8], [1, 7], [1, 4, 5], [3, 5], [3, 4], [7], [2, 6, 8], [1, 7]]
visited = [False] * len(graph)

from collections import deque

def bfs(graph, start, visited):
    queue = deque([start])
    visited[start] = True
    while queue:
        v = queue.popleft()
        print(v, end=' ')
        for i in graph[v]:
            if not visited[i]:
                queue.append(i)
                visited[i] = True
                
bfs(graph, 1, visited)

>> Result ; 1 2 3 8 7 4 5 6
```



### 참고 문제

- Baekjoon #1012 - [유기농 배추] : [problem](https://www.acmicpc.net/problem/1012), [solution]()

- Baekjoon #2178 - [미로 탐색] : [problem](https://www.acmicpc.net/problem/2178), [solution]()

  
