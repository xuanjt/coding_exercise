# Python List Notes

## 1. 切片与复制

`a[l:r]` 会返回一个新列表，包含 `l`，不包含 `r`。

```python
a = [1, 2, 3, 4]
b = a[:2]   # [1, 2]
```

所以：

- 读切片不会直接修改原列表
- `nums[:m]` 本身就已经是在复制
- `nums[:m].copy()` 通常只是多复制一次

## 2. 切片赋值

`a[l:r] = ...` 不是取值，而是直接修改原列表。

```python
a = [1, 2, 3, 4]
a[:2] = [9, 8]
# a = [9, 8, 3, 4]
```

所以：

- `a[l:r]` = 读切片，返回新列表
- `a[l:r] = ...` = 写切片，修改原列表

## 3. `range` 边界

`range(start, stop)`：

- 包含 `start`
- 不包含 `stop`

```python
range(1, 2)   # 有 1
range(1, 1)   # 空
```

所以：

- `range(1, 1)` 不会执行
- 想包含右边界，常写 `right + 1`
- 倒序想包含左边界，常写 `left - 1`

```python
range(left, right + 1)
range(right, left - 1, -1)
```

## 4. 刷题时最实用的记忆

- `nums[:m]`：复制出一个新列表
- `nums[:m] = ...`：直接修改 `nums`
- `range(a, b)`：左闭右开
- 矩阵题优先用坐标和边界，少用切片

## 5. `set` 为什么 lookup 快

`set` 底层通常是哈希表。

做：

```python
x in my_set
```

时，一般不是从头到尾扫描，而是：

1. 先算 `x` 的哈希值
2. 根据哈希值定位到某个位置
3. 在那个位置附近查找

所以：

- `x in list`：通常是 `O(n)`
- `x in set`：平均是 `O(1)`

刷题时，`set` 最常用来做三件事：

- 判断某个值是否存在
- 去重
- 记录访问过的元素

## 6. `isalnum()`

`c.isalnum()` 用来判断一个字符是不是字母或数字。

```python
'a'.isalnum()   # True
'Z'.isalnum()   # True
'3'.isalnum()   # True
' '.isalnum()   # False
'?'.isalnum()   # False
```

刷题时常用在：

- 跳过空格
- 跳过标点
- 判断一个字符是不是有效字母数字字符

## 7. `set.add()` 和 `set.remove()`

### `set.add(x)`

把 `x` 加入集合。

```python
s = set()
s.add('a')
```

如果 `x` 已经在集合里，不会报错，也不会重复添加。

### `set.remove(x)`

把 `x` 从集合里删除。

```python
s = {'a', 'b'}
s.remove('a')
```

如果 `x` 不在集合里，会报错。

### 和 `discard()` 的区别

```python
s.discard(x)
```

如果 `x` 不在集合里，不会报错。

## 8. 刷题时怎么用

在滑动窗口里常见写法：

```python
chars = set()

chars.add(s[right])
chars.remove(s[left])
```

意思是：

- `add()`：把新进入窗口的元素放进去
- `remove()`：把离开窗口的元素删掉

## 9. `float('inf')`

`float('inf')` 表示正无穷。

```python
x = float('inf')
```

刷题时常用来初始化“最小值答案”。

例如：

```python
min_len = float('inf')
```

意思是：

- 先假设当前最小值非常大
- 后面一旦遇到真正答案，就可以用 `min()` 去更新

常见用法：

```python
min_len = float('inf')
min_len = min(min_len, new_value)
```

最后如果发现它还是 `float('inf')`，通常说明没有找到有效答案。

例如：

```python
return 0 if min_len == float('inf') else min_len
```

## 10. `del dict[key]`

```python
del count[key]
```

作用是：

- 直接删除字典里的这个键值对

例如：

```python
count = {'a': 2, 'b': 1}
del count['b']
# count = {'a': 2}
```

刷题时常见场景：

- 某个字符计数减到 `0`
- 这个键已经没有保留意义
- 直接删掉，让字典更干净

例如：

```python
count[s[left]] -= 1
if count[s[left]] == 0:
    del count[s[left]]
```

## 11. 两个字典可以直接比较

Python 里两个字典可以直接用 `==` 比较。

```python
count == target
```

返回 `True` 的条件是：

- 键完全相同
- 每个键对应的值也完全相同

例如：

```python
{'a': 2, 'b': 1} == {'b': 1, 'a': 2}   # True
{'a': 2} == {'a': 1}                   # False
{'a': 2} == {'a': 2, 'b': 0}           # False
```

刷题时常用来判断：

- 当前窗口计数是否和目标计数完全一样
