## dfs
### Template
``` python
def check_same(node1, node2):
    if node1 is None and node2 is None:
        return True
    if node1 is None or node2 is None:
        return False
    return node1.val==node2.val and check_same(node1.left, node2.left) and check_same(node1.right, node2.right)
    
def dfs(node):
    if not node:
        return False
    if check_same(node, subRoot):
        return True
    return dfs(node.left) or dfs(node.right)
```
### What I have done
[572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

## Serialization
### Template
``` python
class Codec:

    def serialize(self, root):
        if not root:
            return '[]'
        Q = deque()
        Q.append(root)
        ans = []
        while Q:
            node = Q.popleft()
            if node:
                ans.append(str(node.val))
                Q.append(node.left)
                Q.append(node.right)
            else:
                ans.append('null')
        return '[' + ",".join(ans) + ']'

    def deserialize(self, data):
        if data == '[]':
            return None
        node_val = data[1:-1].split(',')
        root = TreeNode(val = node_val[0])
        i = 1
        Q = deque()
        Q.append(root)
        while Q:
            node = Q.popleft()
            if node_val[i] != 'null':
                node.left = TreeNode(val = node_val[i])
                Q.append(node.left)
            i += 1
            if node_val[i] != 'null':
                node.right = TreeNode(val = node_val[i])
                Q.append(node.right)
            i += 1
        return root
```

### What I have done
[297. Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/)

## Trie
### Template
``` python
class Trie(object):

    def __init__(self):
        self.root = {}
        self.end = '#'
        

    def insert(self, word):
        """
        :type word: str
        :rtype: None
        """
        node = self.root
        for c in word:
            node = node.setdefault(c, {})
        node[self.end] = True
        

    def search(self, word):
        """
        :type word: str
        :rtype: bool
        """
        node = self.root
        for c in word:
            if c not in node:
                return False
            node = node[c]
        if self.end not in node:
            return False
        return True


    def search_with_dot(self, word):
        """
        :type word: str
        :rtype: bool
        """
        def dfs(node, word):
            if word == "":
                if '#' in node:
                    return True
                else:
                    return False
            c = word[0]
            if c != '.':
                if node.get(c):
                    node = node.get(c)
                    if dfs(node, word[1:]):
                        return True
            else:
                for key, value in node.items():
                    if key == '#':
                        continue
                    if dfs(value, word[1:]):
                        return True
            return False
        return dfs(self.root, word)

    def startsWith(self, prefix):
        """
        :type prefix: str
        :rtype: bool
        """
        node = self.root
        for c in prefix:
            if c not in node:
                return False
            node = node[c]
        return True
```
### What I have done
[208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/description/)
[211. Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/description/)