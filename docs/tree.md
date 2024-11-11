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