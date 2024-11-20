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
[1312. Minimum Insertion Steps to Make a String](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/description/)

## Tree DP
### Template
``` python
def dfs(node):
    nonlocal ans
    if not node:
        return 2
    left_state = dfs(node.left)
    right_state = dfs(node.right)
    if left_state == 0 or right_state == 0:
        ans += 1
        return 1
    if left_state == 1 or right_state == 1:
        return 2
    return 0
```

### What I have done
[968. Binary Tree Cameras](https://leetcode.com/problems/binary-tree-cameras/description/)

## Alice and Bob
### Template
1-D
``` python 
for i in range(n-1, -1, -1):
    for m in range(1, n+1):
        if i + 2 * m >= n:
            dp[i][m] = suffix[i]
        else:
            for x in range(1, 2 * m + 1):
                bob_score = dp[i+x][max(x, m)]
                alice_score = suffix[i] - bob_score
                dp[i][m] = max(dp[i][m], alice_score)
```
### What I have done
[1140. Stone Game II](https://leetcode.com/problems/stone-game-ii/)

## Knapsack Problem
### Template
recursive formula 
> dp[j] 表示： 容量为j的背包，所背的物品价值最大可以为dp[j]
> dp[j] = max(dp[j], dp[j - weight[i]] + value[i])
``` python
for i in range(len(nums)):
    for j in range(target, nums[i] - 1, -1):  # Iterate from target down to nums[i]
        dp[j] = max(dp[j], dp[j - nums[i]] + nums[i])
```

### What I have done
[416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/description/)  
[494. Target Sum](https://leetcode.com/problems/target-sum/description/)方案数就是+=  
[1049. Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/description/)转化为将一堆stone放进最大容量为sum/2的背包,求放进去的石头的最大重量MaxWeight,最终答案即为sum-2*MaxWeight  

## Other
### What I have done
[96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/description/)  
[343. Integer Break](https://leetcode.com/problems/integer-break/description/)

