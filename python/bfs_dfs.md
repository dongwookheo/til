## BFS vs. DFS

| 구분 | DFS (깊이 우선 탐색) | BFS (너비 우선 탐색) |
|:---:|---|---|
| 탐색 원리 | 한 경로를 최대한 깊이 파고든 후, 막히면 되돌아와 다른 경로 탐색 | 시작점에서 가까운 정점(vertex)부터 순서대로, 넓게 탐색 |
| 자료 구조 | 스택(Stack) 또는 재귀 함수 (후입선출, LIFO) | 큐(Queue) (선입선출, FIFO) |
| 메모리 | - 현재 경로만 기억하면 되므로 상대적으로 적게 사용<br>- 경로가 매우 길 경우 스택 오버플로우 발생 가능 | - 인접한 모든 정점을 큐에 저장해야 하므로 상대적으로 많이 사용 |
| 사용 사례 | - 모든 경로 탐색 (완전 탐색)<br>- 경로의 존재 여부 확인<br>- 사이클 판별<br>- 위상 정렬 | - 최단 경로 찾기 (미로 탐색 등)<br>- 네트워크 브로드캐스팅 |

```Python
from collections import deque


def bfs(graph, root):
    visited = []
    q = deque([root])

    while q:
        n = q.popleft()
        if n not in visited:
            visited.append(n)
            if n in graph:
                q.extend(graph[n])

    return visited


def dfs(graph, root):
    """DFS 알고리즘 템플릿"""
    visited = []
    stack = [root]

    while stack:
        n = stack.pop()
        if n not in visited:
            visited.append(n)
            if n in graph:
                stack.extend(graph[n])

    return visited


if __name__ == "__main__":
    graph = {
        "A": ["B", "C"],
        "B": ["A", "D", "E"],
        "C": ["A", "F"],
        "D": ["B"],
        "E": ["B", "F"],
        "F": ["C", "E"],
    }
    print("BFS: ", bfs(graph, "A"))
    print("DFS: ", dfs(graph, "A"))
```
