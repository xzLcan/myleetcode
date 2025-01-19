## Topological sorting
#### Template
> 对于图 G 中的任意一条有向边 (u,v)，u 在排列中都出现在 v 的前面  

* 有环则没有拓扑排序  
* 拓扑排序不唯一
DFS
``` python
def dfs(x):
    visited[x] = 1
    for v in edges[x]:
        if visited[v] == 0:
            visited[v] = 1
            if not dfs(v):
                return False
        elif visited[v] == 1:
            return False
    visited[x] = 2
    topo.append(x)

for i in range(numCourses):
    if valid and not visited[i]:
        valid &= dfs(i)

if valid:
    topo.reverse()
    return topo
return []
```
``` c++
class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> graph(numCourses);
        vector<int> visited(numCourses, 0);

        for (vector<int> prerequisite : prerequisites) {
            graph[prerequisite[1]].push_back(prerequisite[0]);
        }

        for (int i = 0; i < numCourses; ++i)
            if (!hasCycle(graph, i, visited))
                return false;
        return true;
  }

private:
    bool hasCycle(const vector<vector<int>>& graph, int u, vector<int>& visited) {
        visited[u] = 1;
        for (const int v : graph[u])
            if (visited[v] == 0) {
                visited[v] = 1;
                if (!hasCycle(graph, v, visited)) return false;
            }
            else if (visited[v] == 1) return false;
        visited[u] = 2;
        return true;
    }
};
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

two pointer space complexity -> O(1)
``` python
while True:
    slow = next_index(slow)
    fast = next_index(fast)
    if nums[fast] * nums[i] <= 0 or nums[next_index(fast)] * nums[i] <= 0:
        break
    fast = next_index(fast)
    if slow == fast:
        if slow == next_index(slow): 
            break
        return True
```
#### What I have done
[457. Circular Array Loop](https://leetcode.com/problems/circular-array-loop/description/)🌟  
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
[1334. Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/description/)  
[1514. Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/description/)  
[1631. Path With Minimum Effort](https://leetcode.com/problems/path-with-minimum-effort/description/)变一下  
[2050. Parallel Courses III](https://leetcode.com/problems/parallel-courses-iii/description/)  

## BFS Variants
### What I have done
[310. Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/description/)  

## Tarjan
### Template
find cut vertex
``` python
dfn = [0] * n
low = [0] * n
ans = []
cur_time = 0

def tarjan(node, parent):
    nonlocal cur_time
    cur_time += 1
    dfn[node] = low[node] = cur_time
    for neighbor in graph[node]:
        if neighbor == parent:
            continue
        if not dfn[neighbor]:
            tarjan(neighbor, node)
            low[node] = min(low[node], low[neighbor])
            if low[neighbor] > dfn[node]:
                ans.append([node, neighbor])
            low[node] = min(low[node], dfn[neighbor])

graph = [[] for _ in range(n)]
for a, b in connections:
    graph[a].append(b)
    graph[b].append(a)
tarjan(0, -1)
return ans  
```
### What I have done
[1192. Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/description/)  

## MST
### Template
Kruskal
``` python
def find(self, parent, node):
    if parent[node] == node:
        return node
    parent[node] = self.find(parent, parent[node])
    return parent[node]

def union(self, parent, rank, x, y):
    root_x = self.find(parent, x)
    root_y = self.find(parent, y)

    if root_x != root_y:
        if rank[root_x] < rank[root_y]:
            parent[root_x] = root_y
        elif rank[root_x] > rank[root_y]:
            parent[root_y] = root_x
        else:
            parent[root_y] = root_x
            rank[root_x] += 1

edges = sorted(edges)

parent = list(range(len(points)))
rank = [0] * len(points)
min_cost = 0

for edge in edges:
    distance, u, v = edge
    if self.find(parent, u) != self.find(parent, v):
        min_cost += distance
        self.union(parent, rank, u, v)
```

### What I have done
[1584. Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/description/)

