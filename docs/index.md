## time complexity: 
* `1 sec = 10^7 operations`
    * If the input size is 10^6, you can only do linear algorithms  
    * If the input size is 10^5, quasilinear (or better) algorithms  
    * If the input size is 3000, quadratic (or better)  
    * If the input size is 300, cubic (or better)  
    * If the input size is 13, `2^n`, `n^2`

## copy
* 浅copy: references to memory addresses
    * python: `b = copy.copy(a)`
* 深copy: 复制数据并保留原数据不变
    * python: `b = a[:]`, `b = copy.deepcopy(a)`
    * `vector<int> b = a;  // 复制构造函数，相当于 a[:], 修改 b，不会影响 a`
* `b = a`
    * 不可变对象 --> 深copy
    * 可变对象 --> 浅copy --> 修改b会修改a

### Reverse
* python
    * list / string: `s[::-1]`
* c++
    * vector / string: `reverse(vec.begin(), vec.end())`

### Remove
* python
    * dictionary: `del my_dict["b"]`, `my_dict.pop("b")` (`"b"` is the key)
    * set: `my_set.remove(2)`, `my_set.discard(2)`
    * list: `my_list.remove(3)` (`3` is element), `del my_list[2]`, `my_list.pop(2)` (`2` is index)
* c++
    * `vector<int> my_vector = {1, 2, 3, 4}; my_vector.erase(my_vector.begin() + 2);` --> `{1, 2, 4}`  
    * `vector<int> my_vector = {1, 2, 3, 4}; remove(my_vector.begin(), my_vector.end(), 3)` --> `{1, 2, 4}`

## 基础数据结构
### Vector / List
* c++
    * `vector<vector<vector<int>>> dp(maxMove+1, vector<vector<int>>(m, vector<int>(n, 0)));`
    * 插入： `vec.push_back(a)`, `vec.insert(vec.begin() + 1, 10)`指定索引插入元素
    * 删除： `vec.pop_back()`, `vec.erase(vec.begin() + 1)`删除指定位置元素

### Map / Dictionary
* map是O(logn), 自动按键值升序排列， unordered_map是O(1)
    * map按降序排列 `std::map<int, std::string, std::greater<int>> myMap;`
* `map<int, string> myMap`  初始化<type(key), type(value)>
* 初始化赋值 `myMap2 = {{1, "one"}, {2, "two"}, {3, "three"}};`
* 插入新元素 `myMap.insert({1, "apple"})`
* 查找某个值是否存在 
    * `myMap.size()`
    * `myMap.find(c) != myMap.end()`
        * `auto it = myMap.find(2);`2是键 -> 有 -> 返回位置；没有 -> `it == s.end()`
    * `if (myMap.count(3) > 0)` -> 存在
* `myMap.erase(2);`
* `for (auto it = myMap.begin(); it != myMap.end(); ++it)`
* 迭代
``` c++
    for (auto it = myMap.begin(); it != myMap.end(); ++it) {
        cout << "Key: " << it->first << ", Value: " << it->second << std::endl;
    }
```

### Queue
* python: `collections.deque()`
    * pop:`d.popleft()`左边，`d.pop()`右边
* c++: `queue<int> q`
    * `q.push(10);`
    * `q.front()` `q.back()`
    * `q.pop()`左边，`q.pop_back()`右边
    * `q.empty()`,`q.size()`
* c++: `deque<int> q`
    * `push_back()`, `push_front()`
    * `pop_back()`, `pop_front`
    * `front()`, `back()`
    * `empty()`, `size()`
    * ``` c++
        for (auto it = dq.begin(); it != dq.end(); ++it) {
            cout << *it << " ";
        }
    ```

### Stack
* c++: `vector<int> myStack;`
    * `myStack.push();`
    * `myStack.top();`
    * `myStack.pop();`


### pair
* c++:
* `stack<pair<string, int>> stack;`  `stack.push(make_pair(currStr, currNum));`
* `vector<pair<int, int>> directions = {{-1, 0}, {1, 0}, {0, 1}, {0, -1}};`
    ``` c++                    
    for (auto dir : directions) {
        int x = i + dir.first;
        int y = j + dir.second;
    }
    ```
### Set
python中set()的add, remove, find都是O(1), C++中set()是O(logn), unordered_set是O(1)
* c++
    * `unordered_set<int> seen{nums.begin(), nums.end()};`
    * `seen.insert(a);`
    * `seen.erase(a);` 删除所有元素`s.clear();`
    * `if (seen.contains(a))`
    * `auto it = s.find(a);` 有 -> 返回位置；没有 -> `it == s.end()`

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