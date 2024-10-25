## Binary Search
### Template
`[ , )`

``` python
def search(self, nums, target):
    left = 0; right = len(nums)
    while left < right:
        mid = (left + right) / 2
        if nums[mid] < target: # nums[mid-1] < nums[mid] < nums[mid+1]
            left = mid + 1
        elif nums[mid] == target: # nums[mid-1] < nums[mid] > nums[mid+1]
            return mid
        else: # # nums[mid-1] > nums[mid] > nums[mid+1]
            right = mid
    return -1
```
### What I have done
[162. Find Peak Element](https://leetcode.com/problems/find-peak-element/description/)  
[704. Binary Search](https://leetcode.com/problems/binary-search/description/)  

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

## Sort
### Template
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
```
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
