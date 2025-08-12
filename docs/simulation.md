## Number & Calculation
* 数字：
    * 长度变化：进位， 借1
* 运算：
    * 优先级
    * 从左到右
``` python
def evaluate(operator, x, y = 0):
    if operator == "+":
        return x
    if operator == "-":
        return -x
    if operator == "*":
        return x * y
    return int(float(x) / y)
    # Python2: (-3/2) --> floor(-1.5) --> -2
    # Python3: (-3/2) --> (-1.5) --> int(-1.5) = -1

stack = []
curr = 0
previous_op = "+"
s += "@"

for ch in s:
    if ch.isdigit():
        curr = curr * 10 + int(ch)
    elif ch == "(":
        stack.append(previous_op)
        previous_op = "+"
    else:
        if previous_op in "*/":
            stack.append(evaluate(previous_op, stack.pop(), curr))
        else:
            stack.append(evaluate(previous_op, curr, 0))
        
        curr = 0
        previous_op = ch
        if ch == ")":
            while type(stack[-1]) == int:
                curr += stack.pop()
            previous_op = stack.pop()
return sum(stack)
```
### What I have done
[227. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/description/)  
[772. Basic Calculator III](https://leetcode.com/problems/basic-calculator-iii/description/)  
[738. Monotone Increasing Digits](https://leetcode.com/problems/monotone-increasing-digits/description/)


## Else
### What I have done
[54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/description/)  
[59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/)  
[735. Asteroid Collision](https://leetcode.com/problems/asteroid-collision/description/)while loop看清楚边界条件，容易数组越界

## Random
### Template
``` python
random.randrange(start, stop[, step])
random.randint(1, stop)
```

``` python
random.uniform(0, 1) # 生成一个在 [0, 1) 区间的均匀随机浮点数。
math.sqrt(random.uniform(0, 1)) # 对生成的随机数求平方根，目的是为了在圆内生成点时保证每个位置的概率分布是均匀的
# 若直接使用随机数的比例，会导致生成的点集中在圆心附近，因为面积密度和半径成平方关系。平方根修正可以平衡分布
```

### What I have done
[497.Random Point in Non-overlapping Rectangles](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles/description/)  


## Read Data / OOD / Data Structure

### What I have done
[355. Design Twitter](https://leetcode.com/problems/design-twitter/description)  
[1268. Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/description/)  
[1347. Minimum Number of Steps to Make Two Strings Anagram](https://leetcode.com/problems/minimum-number-of-steps-to-make-two-strings-anagram/description/)  
[1472. Design Browser History](https://leetcode.com/problems/design-browser-history/description/)  

### File System
[588. Design In-Memory File System](https://leetcode.com/problems/design-in-memory-file-system/description/)  
[1166. Design File System](https://leetcode.com/problems/design-file-system/description/)  