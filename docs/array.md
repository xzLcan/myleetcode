## Binary Search
### Template
`[ , ]`

``` python
def search(self, nums, target):
    left = 0; right = len(nums)
    while left < right:
        mid = (left + right) / 2
        if condition:
            left = mid + 1
        else: 
            right = mid
    return left
```
### What I have done
[33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array)  
[153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)  
[162. Find Peak Element](https://leetcode.com/problems/find-peak-element/description/)  
[704. Binary Search](https://leetcode.com/problems/binary-search/description/)  

## Bisect
### What I have done
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

`position = bisect.bisect_left(sorted_list, element_to_insert) # position = 2` is same as
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
`position = bisect.bisect_right(sorted_list, element_to_insert) # position = 4` is same as
``` python
left = 0
right = n
while left < right:
    mid = (left + right) >> 1
    if nums[mid] <= target:
        left = mid + 1
    else:
        right = mid
```
When the element not exists in the array `left >= n or nums[left] != target`


### What I have done
[34. Find First and Last Position of Element in Sorted](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)
[1235. Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/description/)  
[2008. Maximum Earnings from Taxi](https://leetcode.com/problems/maximum-earnings-from-taxi/description/)  

## Sliding Window
### Template
``` python
left = right = 0
while left <= right and right < n:
    if case:
        right += 1
    else:
        left += 1
```
Along with priority queue.
### What I have done
[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)  
[76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)  
[209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)  
[239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/description/)  
[424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/description/)  
## Sort
### Template
Sort a dictionary by key
``` python 
result = sorted(test.items())
```   
Sort a dictionary by value  
``` python
list.sort(self, key, reverse) # no return
list.sort(key=lambda x: (x**3))

sorted(iterable, key=None, reverse) # with return
result = sorted(test, key=lambda x: x[1], reverse=True) # 
```

``` python
class comparator(str):
    def __lt__(self, number): # 重新定义 <
        return number + self > self + number
result = sorted(nums, key=comparator, reverse=True) 
```

``` python
lambda arguments: expression # 匿名函数，arguments是函数的参数列表，expression是函数的返回值表达式
map(function, iterable, ...) # 将一个函数应用于一个或多个可迭代对象的所有项目
squared = map(lambda x: x ** 2, numbers)

filter(function, iterable)
def is_even(n):
    return n % 2 == 0
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = filter(is_even, numbers)
```
### What I have done
[179. Largest Number](https://leetcode.com/problems/largest-number/description/)

## Heap
### Template
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
[560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)  
[209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)  

## Priority Queue
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
[496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/description/)  
[503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/description/)  
[739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/description/)  

也有简单的不用priority queue的  
[11. Container with Most Water](https://leetcode.com/problems/container-with-most-water/description/)
