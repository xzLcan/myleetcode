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
            dp[i][j] = max(dp[i+1][j], dp[i][j-1]) # 最长连续子串就没有这里
```
### What I have done
[5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/)  
🌟[115. Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/description/)  
[131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/description/)  
[516. Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/description/)  
[647. Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/description/)  
[718. Maximum Length of Repeated Subarray](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)  
[1035. Uncrossed Lines](https://leetcode.com/problems/uncrossed-lines/description/)  
[1312. Minimum Insertion Steps to Make a String](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/description/)

convert one string to another string
delete, insert, convert
### What I have done
[583. Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/description/)


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
[337. House Robber III](https://leetcode.com/problems/house-robber-iii/description/)  
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
[486. Predict the Winner](https://leetcode.com/problems/predict-the-winner/description/)both players are playing optimally??  
[1140. Stone Game II](https://leetcode.com/problems/stone-game-ii/)  

## Knapsack Problem
### 0-1 Knapsack Problem
#### Template
recursive formula 
> dp[j] 表示： 容量为j的背包，所背的物品价值最大可以为dp[j]
> dp[j] = max(dp[j], dp[j - weight[i]] + value[i])
``` python
for i in range(len(nums)):
    for j in range(target, nums[i] - 1, -1):  # Iterate from target down to nums[i]
        dp[j] = max(dp[j], dp[j - nums[i]] + nums[i])
```

#### What I have done
[416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/description/)  
[494. Target Sum](https://leetcode.com/problems/target-sum/description/)方案数就是+=  
[1049. Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/description/)转化为将一堆stone放进最大容量为sum/2的背包,求放进去的石头的最大重量MaxWeight,最终答案即为sum-2*MaxWeight  
[474. Ones and Zeroes](https://leetcode.com/problems/ones-and-zeroes/description/)weight可以是二维  

### Unbounded Knapsack Problem
#### Template
``` python
for i in range(len(weight)):
    for j in range(weight[i], bagWeight + 1): 
        dp[j] = max(dp[j], dp[j - weight[i]] + value[i])
```
组合数
``` python
for i in range(len(coins)):
    for j in range(coins[i], amount+1):
        dp[j] += dp[j-coins[i]]
```
排列数
``` python
for j in range(1, target+1):
    for i in range(len(nums)):
        if j < nums[i]:
            continue
        dp[j] += dp[j-nums[i]]
```
#### What I have done
[279. Perfect Squares](https://leetcode.com/problems/perfect-squares/description/)  
[377. Combination Sum IV](https://leetcode.com/problems/combination-sum-iv/description/)排列  
[518. Coin Change II](https://leetcode.com/problems/coin-change-ii/description/)组合  


## Other
### What I have done
[96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/description/)  
[343. Integer Break](https://leetcode.com/problems/integer-break/description/)
#### House Robber
``` python
dp[0] = nums[0]
dp[1] = max(nums[0], nums[1])
for i in range(2, len(nums)):
    dp[i] = max(dp[i-1], dp[i-2] + nums[i])
```
[198. House Robber](https://leetcode.com/problems/house-robber/description/)
[213. House Robber II](https://leetcode.com/problems/house-robber-ii/description/)

## Best Time to Buy and Sell Stock
### Template
### What I have done
[121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)  
[122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)  
[123. Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)  
[188. Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)    
[309. Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)  
[714. Best Time to Buy and Sell Stock with Transaction](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/)

## Math
### Template
``` python
nums = [1]
i_2 = 0
i_3 = 0
i_5 = 0
while len(nums) < n:
    nxt_2 = nums[i_2] * 2
    nxt_3 = nums[i_3] * 3
    nxt_5 = nums[i_5] * 5
    nxt = min(nxt_2, nxt_3, nxt_5)
    nums.append(nxt)
    if nxt == nxt_2:
        i_2 += 1
    if nxt == nxt_3:
        i_3 += 1
    if nxt == nxt_5:
        i_5 += 1
return nums[n-1]
```
### What I have done
[264. Ugly Number II](https://leetcode.com/problems/ugly-number-ii/description/)  
[313. Super Ugly Number](https://leetcode.com/problems/super-ugly-number/description/)  
🌟[1201. Ugly Number III](https://leetcode.com/problems/ugly-number-iii/description/)容斥+二分  

### What I have done
[467. Unique Substrings in Wraparound String](https://leetcode.com/problems/unique-substrings-in-wraparound-string/description/)  