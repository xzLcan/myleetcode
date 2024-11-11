## 2-D

### Template
* 0-1 matrix
* 最短路
* 长度 >= 100 (用dfs会超时)

DFS:
* 找到一条路径就可以返回
``` python
directions = [(0,1), (0,-1), (-1,-1), (-1,0), (-1,1), (1,-1), (1,0), (1,1)]
Q = deque([(0, 0)])
ans = 1
grid[0][0] = 1
while Q:
    for _ in range(len(Q)):
        x, y = Q.popleft()
        if x == n - 1 and y == n - 1:
            return ans
        for dir in directions:
            x_new = x + dir[0]
            y_new = y + dir[1]
            if 0<=x_new<n and 0<=y_new<n and grid[x_new][y_new] == 0:
                grid[x_new][y_new] = 1
                Q.append((x_new, y_new))
    ans += 1
```

### What I have done
[542. 01 Matrix](https://leetcode.com/problems/01-matrix/description/)  
[1091. Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/description/)