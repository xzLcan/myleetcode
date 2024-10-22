## Binary Search
### Template
`[ , )`

``` python
def search(self, nums, target):
    left = 0; right = len(nums)
    while left < right:
        mid = (left + right) / 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] == target:
            return mid
        else:
            right = mid
    return -1
```
### What I have done
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

## Sort & Heap
### Template
Sort a dictionary by value  
``` python
sorted_freq = dict(sorted(freq.items(), key=lambda item: item[1], reverse=True))
```
heap
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
[15. 3Sum](https://leetcode.com/problems/3sum/description/)
[18. 4Sum](https://leetcode.com/problems/4sum/description/)