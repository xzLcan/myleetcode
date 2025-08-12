## bitwise operations
* 0xffffffff
* 0x7fffffff 0 + 31个1，是 32 位整数的最大正数  2^{31} - 1 ，即最高位（第 31 位）为 0，其他位全为 1。
* 0x7ffffffff  32个1， 2^{32}-1
* 负数以补码形式储存，取反再加一  ->  -x = ~x + 1
    * 原码 <-> 补码 都是数字位取反加一
    * 正数 3 的二进制表示: 00000000 00000000 00000000 00000011
    * 取反             : 11111111 11111111 11111111 11111100
    * 负数 3 的二进制表示: 11111111 11111111 11111111 11111101
* x & -x 只有最右边是1的那一位有1，其余都是0
* C++中, 对-2147483648取反要用unsigned int
    * unsigned int: 0 到 2^32 - 1
    * int: -2^31 到 2^31 - 1
* 各个进制开头
    * 0b表示二进制 0b10 -> 十进制的2
    * ox表示16进制 0x1A -> 十进制的26
### Template
``` python
# int和二进制字符串转换
int range [-2^31, 2^31-1]
s = bin(n)[2:]
int(s, 2)
```
### What I have done
🌟[89. Gray Code](https://leetcode.com/problems/gray-code/description/)找规律  

### Template
```python
x = 0xffffffff # 32个1， 2^32-1
a = a & x # Python 的整数没有固定位数（理论上可以无限大）。
b = b & x # 将高于32位清零, 如果输入的 a 和 b 是负数，转换成 32 位补码 表示。
while b != 0:
    # 1. 计算无进位加法（异或）
    temp_a = a ^ b
    # 2. 计算进位信息（按位与后左移一位）
    temp_b = (a & b) << 1
    # 3. 将进位结果限制在 32 位范围内
    temp_b = temp_b & 0xffffffff
    # 4. 更新 a 和 b
    a = temp_a
    b = temp_b

if a <= 0x7fffffff: # a是正数
    return a
else:
    return ~(a^x) # 将补码恢复为十进制负数
```
### What I have done
[371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/description/)  

### Template
``` python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        ans = 0
        for i in range(31):
            cnt1 = sum(x >> i & 1 for x in nums)
            ans |= cnt1 % 3 << i
        # 最高位是符号位，下面这行相当于统计负数的个数
        cnt1 = sum(x >> 31 & 1 for x in nums)
        # 如果 cnt1 % 3 == 1，那么答案的最高位是 1，否则是 0
        # Python 只能通过减法把最高位置为 1
        return ans - (cnt1 % 3 << 31)
```
### What I have done
[136. Single Number](https://leetcode.com/problems/single-number/description/)  
🌟[137. Single Number II](https://leetcode.com/problems/single-number-ii/description/)  
🌟[260. Single Number III](https://leetcode.com/problems/single-number-iii/description/)  

### Template
``` python
bin(i).count('1') # Hamming weight or population count
num.bit_length() # 二进制数长度
```
[476. Number Complement](https://leetcode.com/problems/number-complement/description/)  
[477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/description/)按位处理  

### What I have done
[190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/)  
[191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)  
[268. Missing Number](https://leetcode.com/problems/missing-number/description/)  
[338. Counting Bits](https://leetcode.com/problems/counting-bits/description/)  
[384. Shuffle an Array](https://leetcode.com/problems/shuffle-an-array/description/)  
[470. Implement Rand10() Using Rand7()](https://leetcode.com/problems/implement-rand10-using-rand7/description/)概率平均 --> 拒绝采样  

## Mathematical theorem

### What I have done
* 中位数能够最小化绝对差的和 
[462. Minimum Moves to Equal Array Elements II](https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/description/)  


## 取整
* 向下取整
    * python: `result = math.floor(num)`
    * c++: `int result = floor(num);`
* 向上取整
    * python: `result = math.ceil(num)`
    * c++: `int result = ceil(num);`
* 四舍五入取整
    * python: `result = round(num)`, `result = round(num, 2)` 保留两位
    * c++: `int result = std::round(num);`, `double result = std::round(num * 100) / 100;` 保留两位


## 运算
### c++
* `double result = sqrt(25.0); // result = 5.0`
* `result = pow(2.0, 3.0); // result = 8.0 (2^3)`
* `double result = log(2.718281828459); // result ≈ 1.0`
* `double result = log10(100.0); // result = 2.0`
* `double result = sin(3.141592653589 / 2); // result ≈ 1.0`
* `double result = abs(-5.0); // result = 5.0`
* `double maxVal = fmax(3.5, 4.5); // maxVal = 4.5`