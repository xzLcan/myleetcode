## Topological sorting
### Template
> 对于图 G 中的任意一条有向边 (u,v)，u 在排列中都出现在 v 的前面  

* 有环则没有拓扑排序  
* 拓扑排序不唯一
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
### What I have done
[207. Course Schedule](https://leetcode.com/problems/course-schedule/description/)  
[210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)