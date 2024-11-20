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