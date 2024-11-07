## Two List
### Template
``` python 
dp = [[0 for _ in range(n+1)] for _ in range(m+1)]
for i in range(m):
    for j in range(n):
        dp[i+1][j+1] = max(dp[i+1][j+1], dp[i][j+1], dp[i+1][j], dp[i][j])
        if text1[i] == text2[j]:
            dp[i+1][j+1] = max(dp[i+1][j+1], dp[i][j] + 1)
```
### What I have done
[1143. Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/description/)

## 