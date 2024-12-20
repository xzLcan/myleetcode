## bitwise operations
* 0xffffffff
* 0x7fffffff 0 + 31个1，是 32 位整数的最大正数  2^{31} - 1 ，即最高位（第 31 位）为 0，其他位全为 1。
* 0x7ffffffff  32个1， 2^{32}-1
* 负数以补码形式储存，取反再加一
    * 正数 3 的二进制表示: 00000000 00000000 00000000 00000011
    * 取反             : 11111111 11111111 11111111 11111100
    * 负数 3 的二进制表示: 11111111 11111111 11111111 11111101
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
bin(i).count('1') # Hamming weight or population count
num.bit_length() # 二进制数长度
```
[477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/description/)按位处理  

### What I have done
[190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/)  
[191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)  
[268. Missing Number](https://leetcode.com/problems/missing-number/description/)  
[338. Counting Bits](https://leetcode.com/problems/counting-bits/description/)  
