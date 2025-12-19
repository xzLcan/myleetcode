## Binary Search
### Template
* `left <= right, right = n - 1` 是在找“元素”
* `left < right, right = n` 是在找“位置”
For lower_bound, I use a left-closed right-open interval `[0, n)` so that the insertion position itself is included in the search space. Using left < right avoids extra boundary handling and guarantees that left is the first index where nums[left] >= target

``` python
left = 0; right = len(nums) # len(nums)-1也可以
while left < right:
    mid = (left + right) / 2
    if condition:
        left = mid + 1
    else: 
        right = mid
return left
```
with duplicate
``` python
left, right = 0, len(nums) - 1
while left < right:
    mid = (left + right) // 2
    if nums[mid] > nums[right]:
        left = mid + 1
    elif nums[mid] < nums[right]:
        right = mid
    else:
        right -= 1
return nums[left]
```
with duplicate
``` python
left = 0
right = len(nums) - 1 
while left <= right: # <=
    mid = (left + right) >> 1
    if nums[mid] == target:
        return True
    if nums[left] == nums[mid] == nums[right]:
        left += 1
        right -= 1
    elif nums[left] <= nums[mid]:  # nums[l..m] are sorted
        if nums[left] <= target < nums[mid]:
            right = mid - 1
        else:
            left = mid + 1
    else:  # nums[m..n - 1] are sorted
        if nums[mid] < target <= nums[right]:
            left = mid+ 1
        else:
            right = mid - 1
return False
```
#### What I have done
[33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array)找数字的要用modified binary search  
🌟[81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/description/)duplicate  
[153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)  
[154. Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/description/)duplicate  
[162. Find Peak Element](https://leetcode.com/problems/find-peak-element/description/)  
[436. Find Right Interval](https://leetcode.com/problems/find-right-interval/description/)需要能想到是二分  
[704. Binary Search](https://leetcode.com/problems/binary-search/description/)  

### Bisect
``` python 
sorted_list = [1, 3, 4, 4, 5, 7]
element_to_insert = 4
position = bisect.bisect_left(sorted_list, element_to_insert) # position = 2
position = bisect.bisect_right(sorted_list, element_to_insert) # position = 4
lo = 1  # 开始查找的索引
hi = 4  # 结束查找的索引（不包括）
position_left = bisect.bisect_left(sorted_list, element_to_insert, lo, hi) # position_left = 2
```
``` python
jobs = sorted(zip(endTime, startTime, profit))
n = len(profit)
dp = [0] * (n + 1)
for i, (e, s, p) in enumerate(jobs):
    j = bisect_right(jobs, s, hi=i, key=lambda x: x[0])
    dp[i + 1] = max(dp[i], dp[j] + p)
return dp[n]
```

第一个 >= target的位置
`position = bisect.bisect_left(sorted_list, element_to_insert) # position = 2` 
``` python
left = 0
right = n
while left < right:
    mid = (left + right) >> 1
    if nums[mid] >= target:
        right = mid
    else:
        left = mid + 1
return left
```
第一个 > target 位置
`position = bisect.bisect_right(sorted_list, element_to_insert) # position = 4` 
``` python
left = 0
right = n
while left < right:
    mid = (left + right) >> 1
    if nums[mid] > target:
        right = mid
    else:
        left = mid + 1
    return left
```
最后一个<= target 位置
``` python
left, right = 0, n
while left < right:
    mid = (left + right) >> 1
    if nums[mid] <= target:
        left = mid + 1
    else:
        right = mid
    return left - 1
```
When the element not exists in the array `left >= n or nums[left] != target`


#### What I have done
[34. Find First and Last Position of Element in Sorted](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)  
[1235. Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/description/)   
[2008. Maximum Earnings from Taxi](https://leetcode.com/problems/maximum-earnings-from-taxi/description/)  

## Sliding Window
### Template
``` python
left = right = 0
while left <= right and right < n: # sliding window的判断调价
    if case:
        right += 1 # 别忘了right也要加一
    else:
        left += 1
```
``` python
left = right = 0
while left <= right and right < n:
    if reach condition:
        while overage:
            left += 1
        compute ans
    right += 1
```
Along with priority queue.
### What I have done
[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)  
[76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)  
[209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)  
[239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/description/)  
[424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/description/)  
[438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)把字符串转换成counter的时间比较久  


## Sort
### Template
``` python 
result = sorted(test.items(), key=lambda x: x[0])
```   
Sort a dictionary by (value, key)
``` python
result = sorted(test.items(), key=lambda x: (x[1], x[0]), reverse=True) 

# Customized comparator
class comparator(str):
    def __lt__(self, number): # 重新定义 <
        return number + self > self + number
result = sorted(nums, key=comparator, reverse=True) 
```

### What I have done
[179. Largest Number](https://leetcode.com/problems/largest-number/description/)

## Heap
### Template
Python -> heapq
``` python
import heapq
# Create a heap
def heapsort(nums):
    h = []
    for num in nums:
        heapq.heappush(h, num)
    return [heapq.heappop(h) for i in range(len(h))] # Only min-heap

# Create a heap from a list
heapq.heapify(heap)

# delete target item
index = heap.index(target_item)  
heap[index] = heap[0]  
heap[0] = target_item       

heapq.heappop(heap)
```

### What I have done
[215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)  
[347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)  
[451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/description/)  

## Two Pointer
### Template
``` python
for i in range(n):
    if i > 0 and nums[i] == nums[i-1]:
        continue
    left = i+1; right = n-1
    while left < right:
        if nums[i] + nums[left] + nums[right] == 0:
            ans.append([nums[i], nums[left], nums[right]])
            while nums[left] == nums[left+1] and left < n - 2 :
                left += 1
            while nums[right] == nums[right-1] and right > left:
                right -= 1
        if nums[i] + nums[left] + nums[right] < 0:
            left += 1
        else:
            right -= 1
```
### What I have done
[11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/description/)  
[15. 3Sum](https://leetcode.com/problems/3sum/description/)  
[18. 4Sum](https://leetcode.com/problems/4sum/description/)  

## Prefix Sum
### Template
``` python
for i in range(len(nums)):
    prefix_num += nums[i]
    if prefix_num - k in dic:
        ans += dic[prefix_num-k]
    if prefix_num in dic:
        dic[prefix_num] += 1
    else:
        dic[prefix_num] = 1
```
### What I have done
[209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)  
[253. Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/description/)转化为前缀和  
[560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)  

## 单调栈
### Template
通常是一维数组，要寻找任一个元素的右边或者左边第一个比自己大或者小的元素的位置，此时可以用单调栈
``` python
for i in range(len(nums)):
    if not Q or nums[Q[-1]] >= nums[i]:
        Q.append(i)
    else:
        while Q and nums[Q[-1]] < num2[i]:
            next_greater[Q[-1]] = i
            Q.pop()
        Q.append(i)
```

有许多高度，求最大面积
``` python
for i in range(len(height)):
    if not Q or height[Q[-1]] > height[i]:
        Q.append(i)
    elif height[Q[-1]] == height[i]:
        Q.pop()
        Q.append(i)
    else:
        while Q and height[i] > height[Q[-1]]:
            bottom = height[Q[-1]]; Q.pop()
            if Q:
                h = min(height[Q[-1]], height[i]) - bottom
                w = i - Q[-1] - 1
                ans += h * w
        Q.append(i)
```
### What I have done
[42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/description/)  
[84. Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)  
[456. 132 Pattern](https://leetcode.com/problems/132-pattern/)  
[496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/description/)  
[503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/description/)  
[556. Next Greater Element III](https://leetcode.com/problems/next-greater-element-iii/description/)考虑全面  
[739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/description/)  

也有简单的不用priority queue的  
[11. Container with Most Water](https://leetcode.com/problems/container-with-most-water/description/)

## Boyer-Moore Voting Algorithm
### Template
多数元素: 严格超过一半
1.	候选阶段：找到一个可能是多数元素的候选者
2.	验证阶段：检查该候选者是否真的为多数元素
``` python
def majority_element(nums):
# Step 1: Find the candidate
candidate = None
count = 0
for num in nums:
    if count == 0:  # Reset candidate
        candidate = num
    count += 1 if num == candidate else -1

# Step 2: Verify the candidate
count = 0
for num in nums:
    if num == candidate:
        count += 1

# Check if the candidate is actually the majority element
if count > len(nums) // 2:
    return candidate
else:
    return None
```
### What I have done
[229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)  

## Segment Tree
### Template
```python
class NumArray:

    def __init__(self, nums: List[int]):
        self.n = len(nums)
        self.tree = [0] * self.n + nums
        for i in range(self.n, 0, -1): # 不计算0
            self.tree[i] = self.tree[i << 1] + self.tree[i << 1 | 1]

    def update(self, i: int, val: int) -> None:
        i += self.n
        self.tree[i] = val
        while i > 0:
            self.tree[i >> 1] = self.tree[i] + self.tree[i ^ 1]
            i >>= 1

    def sumRange(self, i: int, j: int) -> int:
        i += self.n
        j += self.n + 1 # [i, j)
        result = 0
        while i < j:
            if i & 1: # 当前节点是一个完整区间
                result += self.tree[i]
                i += 1
            if j & 1:
                j -= 1
                result += self.tree[j]
            i >>= 1
            j >>= 1
        return result
```
### What I have done
#### Inversions
[307. Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/description/)  
[493. Reverse Pairs](https://leetcode.com/problems/reverse-pairs/description/)  


## Step🌟
### What I have done
[390. Elimination Game](https://leetcode.com/problems/elimination-game/description/)  
