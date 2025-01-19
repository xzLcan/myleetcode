## Basic
* python都是引用传递
    * 不可变对象（如 int、float、str、tuple）会重新生成一个对象
    * 可变对象（如 list、dict、set）是引用传递，在原来的对象上直接修改
        * 不能这样写：dfs(node.right, path.append(str(node.val)))，因为返回值是NoneType，必须先append再pop
* C++
    * 值传递：`void function_name(type param);`
    * 引用传递： `void function_name(type& param);`
    * 按常量引用传递: 传递的是原始变量的引用，但不能修改原始变量 `void function_name(const type& param);`


## 1-D DFS

### Template
``` python
ans = []
def dfs(idx, sum, lst):
    if idx >= len(candidates):
        return
    if sum + candidates[idx] == target:
        lst.append(candidates[idx])
        ans.append(lst)
    elif sum + candidates[idx] < target:
        dfs(idx + 1, sum, list(lst))
        lst.append(candidates[idx])
        dfs(idx, sum + candidates[idx], list(lst))
        dfs(idx + 1, sum + candidates[idx], list(lst))
candidates = sorted(candidates)
dfs(0, 0, [])
return list(map(list, set(map(tuple, ans))))
```
``` python
def dfs(idx, target):
    if target == 0:
        ans.append(tmp_ans[:]) # 浅copy
        return
    for i in range(idx, len(candidates)):
        if i > idx and candidates[i] == candidates[i-1]: # 剪枝
            continue
        if candidates[i] > target:
            break
        tmp_ans.append(candidates[i])
        dfs(i + 1, target - candidates[i])
        tmp_ans.pop()
```
### What I have done
[39. Combination Sum](https://leetcode.com/problems/combination-sum/description/)  
[40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/description/)  
[216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)  

## 1-D Partition
### Template
``` python
def dfs(cur_idx):
    if cur_idx == len(matchsticks):
        if target_side == side_len[0] and side_len[0] == side_len[1] and side_len[1] == side_len[2] and side_len[2] == side_len[3]:
            return True
        return False
    
    for i in range(4):
        if i > 0 and side_len[i] == side_len[i-1]:
            continue
        if side_len[i] + matchsticks[cur_idx] <= target_side:
            side_len[i] += matchsticks[cur_idx]
            if dfs(cur_idx + 1):
                return True
            side_len[i] -= matchsticks[cur_idx]
    return False
```
### What I have done
[473. Matchsticks to Square](https://leetcode.com/problems/matchsticks-to-square/description/)  
[698. Partition to K Equal Sum Subsets](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/description/)

## 2-D DFS
### Template
```python
def dfs(row):
    if row == n:
        results.append(flag[:])
        return
    for i in range(n):
        if judge(row, i) or row == 0:
            flag[i] = row
            dfs(row+1)
            flag[i] = -1
```
### What I have done
[51. N-Queens](https://leetcode.com/problems/n-queens/description/)  
[52. N-Queens II](https://leetcode.com/problems/n-queens-ii/description/)  

### Template
``` python
directions = [(1, 0), (0, 1), (-1, 0), (0, -1)]
def dfs(i, j):
    for direct in directions:
        x = i + direct[0]
        y = j + direct[1]
        if x < 0 or y < 0 or x >= m or y >= n or visited[x][y] == 1:
            continue
        visited[x][y] = 1
```

### What I have done
[200. Number of Islands](https://leetcode.com/problems/number-of-islands/description/)  

## Trie & XOR
### Template
``` python
class TrieNode:
    def __init__(self):
        # 子节点（字典形式存储，键是字符，值是对应的子节点）
        self.children = {}
        # 是否是单词结尾
        self.is_word = False


class Trie:
    def __init__(self):
        # 初始化根节点
        self.root = TrieNode()

    # 插入单词
    def insert(self, word):
        node = self.root
        for char in word:
            # 如果子节点不存在，则创建新的节点
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]  # 移动到子节点
        node.is_word = True  # 标记为单词结尾

    # 查找单词
    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:  # 子节点不存在
                return False
            node = node.children[char]
        return node.is_word  # 检查是否为单词结尾


# 测试字典树
if __name__ == "__main__":
    trie = Trie()
    trie.insert("apple")
    print("Search 'apple':", trie.search("apple"))  # True
```
``` c++
struct TrieNode {
    vector<shared_ptr<TrieNode>> children; // 子节点数组
    bool isWord = false;                   // 是否是单词结尾

    TrieNode() : children(26) {}           // 初始化子节点数组大小为 26
};

class Trie {
private:
    shared_ptr<TrieNode> root; // 根节点

public:
    Trie() : root(make_shared<TrieNode>()) {} // 初始化根节点

    // 插入单词
    void insert(const string& word) {
        auto node = root;
        for (char c : word) {
            int index = c - 'a'; // 字母对应的索引
            if (!node->children[index]) { // 如果子节点为空，则创建新节点
                node->children[index] = make_shared<TrieNode>();
            }
            node = node->children[index]; // 移动到子节点
        }
        node->isWord = true; // 标记为单词结尾
    }

    // 查找单词
    bool search(const string& word) {
        auto node = root;
        for (char c : word) {
            int index = c - 'a';
            if (!node->children[index]) return false; // 子节点不存在
            node = node->children[index];
        }
        return node->isWord; // 检查是否为单词结尾
    }
};

int main() {
    Trie trie;
    trie.insert("apple");

    cout << "Search 'apple': " << trie.search("apple") << endl; // true
    return 0;
}
```
### What I have done
[208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/description/)  
[211. Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/description/)  
[421. Maximum XOR of Two Numbers in an Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/description/)  
[2935. Maximum Strong Pair XOR II](https://leetcode.com/problems/maximum-strong-pair-xor-ii/description/)  

## Tree
### What I have done
[112. Path Sum](https://leetcode.com/problems/path-sum/description/)  
[113. Path Sum II](https://leetcode.com/problems/path-sum-ii/description/)  
[437. Path Sum III](https://leetcode.com/problems/path-sum-iii/description/)  