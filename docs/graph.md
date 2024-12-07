## Topological sorting
#### Template
> 对于图 G 中的任意一条有向边 (u,v)，u 在排列中都出现在 v 的前面  

* 有环则没有拓扑排序  
* 拓扑排序不唯一
DFS
``` python
def dfs(x):
    nonlocal valid
    visited[x] = 1
    for end in edges[x]:
        if not visited[end]:
            visited[end] = 1
            dfs(end)
            if not valid:
                return
        elif visited[end] == 1:
            valid = False
            return
    visited[x] = 2
    topo.append(x)

for i in range(numCourses):
    if valid and not visited[i]:
        dfs(i)
```
BFS
``` python
Q = deque()
for i in range(1, n+1):
    if ind[i] == 0:
        Q.append(i)
while Q:
    u = Q.popleft()
    topo.append(u)
    for v in graph[u]:
        ind[v] -= 1
        if ind[v] == 0:
            Q.append(v)
```
#### What I have done
[207. Course Schedule](https://leetcode.com/problems/course-schedule/description/)  
[210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)  
[1462. Course Schedule IV](https://leetcode.com/problems/course-schedule-iv/description/)  
[2192. All Ancestors of a Node in a Directed Acyclic Graph](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/submissions/1465214609/)  
[2392. Build a Matrix With Conditions](https://leetcode.com/problems/build-a-matrix-with-conditions/description/)  
### Has Cycle
#### Template
``` python
n = len(graph)
status = [0] * n # 0 init, 1, visiting, 2, visited

def has_cycle(node):
    if status[node] == 1:
        return True
    if status[node] == 2:
        return False
    
    status[node] = 1
    for v in graph[node]:
        if has_cycle(v):
            return True
    status[node] = 2

ans = []
for i in range(n):
    if not has_cycle(i):
        ans.append(i)
return ans
```
#### What I have done
[802. Find Eventual Safe States](https://leetcode.com/problems/find-eventual-safe-states/description/)  
[1591. Strange Printer II](https://leetcode.com/problems/strange-printer-ii/description/)🌟  
[2115. Find All Possible Recipes from Given Supplies](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/description/)  

## Union-Find
### Template
简易版
``` python
def find(x):
    if p[x] != x:
        p[x] = find(p[x])
    return p[x]
```
完整版（按秩）
``` python
class UnionFind:
    def __init__(self, size):
        self.parent = list(range(size))  
        self.rank = [1] * size  # height

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x]) 
        return self.parent[x]

    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)
        if rootX != rootY:
            if self.rank[rootX] > self.rank[rootY]:
                self.parent[rootY] = rootX
            elif self.rank[rootX] < self.rank[rootY]:
                self.parent[rootX] = rootY
            else:
                self.parent[rootY] = rootX
                self.rank[rootX] += 1
```
### What I have done
[547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/description/)  
[684. Redundant Connection](https://leetcode.com/problems/redundant-connection/description/)  
[685. Redundant Connection II](https://leetcode.com/problems/redundant-connection-ii/description/)  
[947. Most Stones Removed with Same Row or](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/description/)  
[990. Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/description/)  

## Shortest Path
### Template
Dijkstra
``` python
while Q:
    u = Q.popleft()
    for v in graph[u]:
        dist[v] = max(dist[v], dist[u] + time[v])
        ind[v] -= 1
        if ind[v] == 0:
            Q.append(v)
```
Dijkstra with heap
``` python
def Dijkstra(self, graph, src):
    dis = [float('inf')] * len(graph)
    dis[src] = 0
    minHeap = [(dis[src], src)]

    while minHeap:
        d, u = heapq.heappop(minHeap)
        if d > dis[u]:
            continue
        for v, w in graph[u]:
            if d + w < dis[v]:
                dis[v] = d + w
                heapq.heappush(minHeap, (dis[v], v))
```
#### What I have done
[797. All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/description/)  
[1514. Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/description/)
[2050. Parallel Courses III](https://leetcode.com/problems/parallel-courses-iii/description/)  

## BFS Variants
### What I have done
[310. Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/description/)