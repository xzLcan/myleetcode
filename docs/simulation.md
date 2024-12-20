## Number & Calculation
* 数字：
    * 长度变化：进位， 借1
* 运算：
    * 优先级
    * 从左到右
### What I have done
[227. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/description/)  
[738. Monotone Increasing Digits](https://leetcode.com/problems/monotone-increasing-digits/description/)


## Else
### What I have done
[54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/description/)  
[59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/)  

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
random.uniform(0, 1) # 生成一个在 [0, 1) 区间的均匀随机浮点数。
```

### What I have done
[497.Random Point in Non-overlapping Rectangles](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles/description/)  
