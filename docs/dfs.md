## 1-D DFS

### Template
``` python
ans = []
def dfs(idx, sum, lst):
    if idx >= len(candidates):
        return
    if sum + candidates[idx] == target:
        lst.append(candidates[idx])
        ans.append(lst)
    elif sum + candidates[idx] < target:
        dfs(idx + 1, sum, list(lst))
        lst.append(candidates[idx])
        dfs(idx, sum + candidates[idx], list(lst))
        dfs(idx + 1, sum + candidates[idx], list(lst))
candidates = sorted(candidates)
dfs(0, 0, [])
return list(map(list, set(map(tuple, ans))))
```
``` python
def dfs(idx, target):
    if target == 0:
        ans.append(tmp_ans[:]) # 浅copy
        return
    for i in range(idx, len(candidates)):
        if i > idx and candidates[i] == candidates[i-1]: # 剪枝
            continue
        if candidates[i] > target:
            break
        tmp_ans.append(candidates[i])
        dfs(i + 1, target - candidates[i])
        tmp_ans.pop()
```
### What I have done
[39. Combination Sum](https://leetcode.com/problems/combination-sum/description/)  
[40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/description/)  
[216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)  

## 2-D DFS
### Template
```python
def dfs(row):
    if row == n:
        results.append(flag[:])
        return
    for i in range(n):
        if judge(row, i) or row == 0:
            flag[i] = row
            dfs(row+1)
            flag[i] = -1
```
### What I have done
[51. N-Queens](https://leetcode.com/problems/n-queens/description/)  
[52. N-Queens II](https://leetcode.com/problems/n-queens-ii/description/)  

### Template
``` python
directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
def dfs(i, j):
    for direct in directions:
        x = i + direct[0]
        y = j + direct[1]
        if x < 0 or y < 0 or x >= m or y >= n or visited[x][y] == 1:
            continue
        visited[x][y] = 1
```

### What I have done
[200. Number of Islands](https://leetcode.com/problems/number-of-islands/description/)  
