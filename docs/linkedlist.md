## Basis
``` python
 class ListNode(object):
    def __init__(self, val, next=None):
        self.val = val
        self.next = next
```
* head = [ ]
* only 1 item
* odd and even


## Fast & Slow Pointer
### Template
``` python
fast = slow = head
while fast and fast.next:
    fast = fast.next.next
    slow = slow.next
```
### What I have done
[19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)  
[24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/)  
[142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)  


## Dummy Head
### Template
``` python
dummy_head = ListNode(next=head)
current = dummy_head
while current.next:

return dummy_head.next
```
### What I have done
[203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/)

## Reverse LinkedList
### Template
reverse nodes between [start + 1, end - 1], return node on (end - 1)  
<img src="../images/linked_list_reverse.jpg" alt="Example Image" width="300"/>
``` python
    def reversek(self, start, end):
        pre, cur = start, start.next
        first = cur
        while cur != end:
            nxt = cur.next
            cur.next = pre
            pre = cur
            cur = nxt
        start.next = pre
        first.next = cur
        return first
```

### What I have done
[25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/description/)

## Other
### What I have done
[141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description/)  
[206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)  
[707. Design Linked List](https://leetcode.com/problems/design-linked-list/description/)