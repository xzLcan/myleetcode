## About string
* 长度为n的字符串，子串数量是 n * (n + 1) / 2
* Python
    * convert char to number `rec[ord(s[left]) - ord('A')]`
    * covert number to char  `chr(i + ord('A'))`
    * `sorted(string)` get a list of char
    * s[::-1] reverse the string, but time complexity is O(n)
    * `s.strip()`去掉开头和结尾的空格
    * `fruits = s.split(",")`默认按空格分割
    * list(string) -> string `"/".join(stack)`
    * string和int互相转化：`num = int(s)`, `s = str(num)`
* C++
    * string / char merge: 
        * 两个string: `string merged = str1 + str2` or `str1.push_back(str2)`
        * string + char: `str.push_back(c)`
        * 两个char -> 转化为两个或一个string
    * char -> string: `string s(1, c); merged += c2 // 用 c1 初始化一个长度为 1 的字符串 merged`
    * int -> string: `str = to_string(num);`
    * 0 -> 'A': `string(1, 'A' + 0)`
    * string -> int: `num = stoi(str);`  "123" -> 123
    * char -> int: `(int)c`; 判断char是否是数字: `if (isdigit(c))`
    * int -> char: `(char)num` eg. char(65) -> 'A'
    * vector<char/string> -> string:
        * `vector<char> s = {'H', 'e', 'l', 'l', 'o'}; string result(s.begin(), s.end());`
        * `vector<string> s = {"Hello", " ", "World"}; string result = accumulate(s.begin(), s.end(), string());`
    * reverse: `reverse(str.begin(), str.end());`

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
[388. Longest Absolute File Path](https://leetcode.com/problems/longest-absolute-file-path/description/)  



## string in C++
``` c++
list<char> stack;
string str(stack.begin(), stack.end()); // [ , )
```

### What I have done
[316. Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/description/)greedy  

``` c++
istringstream iss(expression);
int a; int b; char _;
while (iss >> a >> _ >> b) {}
```
### What I have done
[592. Fraction Addition and Subtraction](https://leetcode.com/problems/fraction-addition-and-subtraction/description/)  

