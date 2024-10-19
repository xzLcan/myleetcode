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
