## About string
* 长度为n的字符串，子串数量是 n * (n + 1) / 2
* convert char to number `rec[ord(s[left]) - ord('A')]`
* covert number to char  `chr(i + ord('A'))`
* `sorted(string)` get a list of char
* s[::-1] reverse the string, but time complexity is O(n)
* `s.strip()`去掉开头和结尾的空格
* `fruits = s.split(",")`默认按空格分割
* list(string) -> string `"/".join(stack)`
* string和int互相转化：`num = int(s)`, `s = str(num)`

### What I have done
[5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/)  
[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)  
[467. Unique Substrings in Wraparound String](https://leetcode.com/problems/unique-substrings-in-wraparound-string/description/)  

### Template
``` python
for token in input.split('\n'):
    depth = token.count('\t')
    token = token.replace('\t', '')
```
### What I have done
[316. Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/description/)greedy  
[388. Longest Absolute File Path](https://leetcode.com/problems/longest-absolute-file-path/description/)  
[592. Fraction Addition and Subtraction](https://leetcode.com/problems/fraction-addition-and-subtraction/description/)  

