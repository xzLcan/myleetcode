### time complexity: 
* `1 sec = 10^7 operations`
    * If the input size is 10^6, you can only do linear algorithms  
    * If the input size is 10^5, quasilinear (or better) algorithms  
    * If the input size is 3000, quadratic (or better)  
    * If the input size is 300, cubic (or better)  
    * If the input size is 13, `2^n`, `n^2`

### isinstance
* `isinstance(3, int)        # True`
* `isinstance(3.14, float)   # True`

### copy
* shallow copy: references to memory addresses
    * python: `b = copy.copy(a)`
* deep copy: 复制数据并保留原数据不变
    * python: `b = a[:]`, `b = copy.deepcopy(a)`
    * `vector<int> b = a;  // 复制构造函数，相当于 a[:], 修改 b，不会影响 a`
* `b = a`
    * 不可变对象 --> 深copy
    * 可变对象 --> 浅copy --> 修改b会修改a

### Reverse
* list / string: `s[::-1]`

### Remove
* dictionary: `del my_dict["b"]`, `my_dict.pop("b")` (`"b"` is the key)
* set: `my_set.remove(2)`, `my_set.discard(2)`
* list: `my_list.remove(3)` (`3` is element), `del my_list[2]`, `my_list.pop(2)` (`2` is index)


### Map / Dictionary
* `collections.OrderedDict()`
    * 保留了插入键的顺序
    * `dict.popitem(last=True)` True：最后一项，False：第一项
* `Mydict.pop(val)`


### Set
python中set()的add, remove, find都是O(1), C++中set()是O(logn), unordered_set是O(1)  


### Queue
* python: `collections.deque()`
    * pop:`d.popleft()`左边，`d.pop()`右边



### 指针
* `TreeNode `TreeNode* root = new TreeNode(10);`



## 匿名函数
### Python中的lambda函数
``` python
lambda arguments: expression # 匿名函数，arguments是函数的参数列表，expression是函数的返回值表达式
map(function, iterable, ...) # 将一个函数应用于一个或多个可迭代对象的所有项目
squared = map(lambda x: x ** 2, numbers)

filter(function, iterable)
def is_even(n):
    return n % 2 == 0
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = filter(is_even, numbers)
```