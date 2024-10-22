## 1-D DFS

### Template
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