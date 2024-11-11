## bitwise operations
0xffffffff
0x7fffffff
0x7ffffffff
### Template
```python
x = 0xffffffff
a = a & x
b = b & x # 把最高位设为0
while b != 0:
    a, b = (a^b), (a&b)<<1 & x
return a if a <= 0x7fffffff else ~(a^x)
```
``` python
# int和二进制字符串转换
s = bin(n)[2:]
int(s, 2)
```

### What I have done
[190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/)  
[191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)  
[268. Missing Number](https://leetcode.com/problems/missing-number/description/)  
[338. Counting Bits](https://leetcode.com/problems/counting-bits/description/)  
[371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/description/)  