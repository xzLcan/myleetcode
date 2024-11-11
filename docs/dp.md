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

## Range DP --> Palindromic Substring / Sequence
### Template

palindromic substring
``` python
for i in range(n):
    dp[i][i] = 1
    if i > 0:
        dp[i][i-1] = 1
for length in range(2, n + 1):
    for i in range(0, n-length+1):
        j = i + length - 1
        if s[i] == s[j] and dp[i+1][j-1]:
            dp[i][j] = 2 + dp[i+1][j-1]
```
palindromic sequence
``` python
for length in range(2, n + 1):
    for i in range(0, n-length+1):
        j = i + length - 1
        if s[i] == s[j] and dp[i+1][j-1]:
            dp[i][j] = 2 + dp[i+1][j-1]
        else:
            dp[i][j] = max(dp[i+1][j], dp[i][j-1])
```
### What I have done
[5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/)
[131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/description/)
[516. Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/description/)
[647. Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/description/)  

## Tree DP
