# python

> 参考[python官方文档]()以及[python编程：从入门到实践]()

[代码规范](#代码规范) \
[表达式](#表达式) \
[数据结构](#数据结构) \ [数字](#数字) \ [字符串](#字符串) \ [列表](#列表操作) \ [栈](栈) \ [队列](#队列) \ [元组](#元组) \ [集合](#集合) \ [字典](#字典) \
[语句](#语句) \ [赋值语句](#赋值语句) \ [选择语句](#选择语句) \ [循环语句](#循环语句) \ [pass](#pass语句) \ [lambda表达式](#lambda表达式) \
[模块](#模块) \
[函数](#函数) \
[类](#类) \ [迭代器](#迭代器) \ [生成器](#生成器) \
[文件读写](#文件读写) \ [json](#使用-json-保存结构化数据) \
[异常处理](#异常处理)

## 代码规范
1. ***`代码块缩紧必须到位！！！`***
2. 缩进用`[space]` * 4而不是`[tab]`
3. 语句结尾不加`;`
4. 与其他语句类似 \
   运算符周围要有空格 \
   e.g.
   ```
   a=b+c        # wrong!
   a = b + c    # right
   ```
5. 函数中给形参赋值的=左右不要有空格
6. 命名规范
   |类型|规范|举例|
   |:-:|:-:|:-:|
   |变量|小写字母，使用_连接|my_first_value|
   |函数|小写字母，使用_连接|def my_first_func()|
   |类|首字母大写，直接连接|class MyFirstClass|
   |常量|全部大写，用_连接|MY_FIRST_CONST|
7. 换行，使一行不超过 79 个字符
8. 使用空行分隔函数和类，以及函数内的较大的代码块

## 表达式
1. 身份运算符 is
    > 比较的时对象id, 也即是cpython中的地址
2. 成员运算符 in
    > 判断对象是否时某个容器中的值
3. 比较运算符
    |运算|含义|
    |:-|:-:|
    |<|严格小于|
    |<=|小于或等于|
    |>|严格大于|
    |>=|大于或等于|
    |==|等于|
    |!=|不等于|
    > python比较的特殊性质 \
    > `比较操作可以传递`
    ```
    a < b < c   # a < b and b < c
    a < b == c  # a < b and b == c
    ```
    > 序列比较与字符串比较类似
    ```
    (1, 2) < (1, 1, 3) # False
    (1, 2) < (3)       # True
    ```
4. 逻辑运算符
    |运算|结果|含义|
    |:-:|:-:|:-:|
    |x or y|如果x为True, 返回x, 否则返回y|或|
    |x and y|如果x为False, 返回x, 否则返回y|与|
    |not x|如果x为False, 返回True, 否则返回False|非|

## 数据结构
### 数字
> 整数 \ 浮点数
- 数字转字符串
    ```
    str(number)
    ```
- 字符串转数字
    - 字符串转整数
        ```
        int(str)
        ```
    - 字符串转浮点数
        ```
        float(str)
        ```
### 字符串
- 修改大小写
    ```
    str.upper() # 全部大写
    str.lower() # 全部小写
    ```
- 字符串运算
    - `+` 合并两个字符串
    - `*` 将一个字符串重复出现多次
        ```
        'a' * 4 # 结果'aaaa'
        ```
- 删除空白
    ```
    str.rstrip() # 删除末尾的空白
    str.lstrip() # 删除开头的空白
    str.strip()  # 删除两端的空白
    ```
### 列表操作
- list.append(x)
    > 在列表的末尾添加一个元素。相当于a\[len(a):\] = \[x\]
- list.extend(iterable)
    > 使用可迭代对象中的所有元素来扩展列表。相当于a\[len(a):\] = iterable
- list.insert(i, x)
    > 在给定的位置插入一个元素。第一个参数是要插入的元素的索引，所以 a.insert(0, x) 插入列表 头部，a.insert(len(a), x)等同于a.append(x)
- list.remove(x)
    > 移除列表中第一个值为 x 的元素。如果没有这样的元素，则抛出 ValueError 异常
- list.pop([i ])
    > 删除列表中给定位置的元素并返回它。如果没有给定位置，a.pop() 将会删除并返回列表中的最后一 个元素。(方法签名中 i 两边的方括号表示这个参数是可选的，而不是要你输入方括号。你会在 Python 参考库中经常看到这种表示方法)
- list.clear()
    > 移除列表中的所有元素。等价于 del a[:]
- list.index(x[, start[, end ] ])
    > 返回列表中第一个值为 x 的元素的从零开始的索引。如果没有这样的元素将会抛出 ValueError 异 常。 \
    > 可选参数 start 和 end 是切片符号，用于将搜索限制为列表的特定子序列。返回的索引是相对于整个序 列的开始计算的，而不是 start 参数。
- list.count(x)
    > 返回元素 x 在列表中出现的次数。
- list.sort(key=None, reverse=False)
    > 对列表中的元素进行排序(参数可用于自定义排序，解释请参见 sorted())
- list.reverse()
    > 翻转列表中的元素
- list.copy()
    > 返回列表的一个浅拷贝，等价于 a[:]   
#### 列表切片
> 类似于matlab
```
a = [1, 2, 3, 4, 5, 6]
a[0 : 2]  # [1, 2]
a[4 : -1] # [5, 6]
a[:]      # 复制列表
```
#### 列表lambda
> 详见[lambda表达式](#lambda表达式)
### 栈
    > 列表就可作为栈使用
### 队列
使用collections.deque即可充当队列
```
from collections import deque
queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")
`queue.popleft()`
```
### 元组
> 由()包围，不可更改，中间可嵌套任意数据类型
- 构造方式
    ```
    tuple = (1, 2, 3)
    tuple = 1, 2, 3
    ```
### 集合
> 集合是由不重复元素组成的无序的集。它的基本用法包括成员检测和消除重复
元素。集合对象也支持像联合，交集，差集，对称差分等数学运算。
- 构造方式
    ```
    a = set()          # {}
    a = set('aaaabcd') # { 'a', 'b', 'c', 'd' }
    ```
- 运算
    ```
    a = set('abracadabra')  # {'a', 'r', 'b', 'c', 'd'}
    b = set('alacazam')     # {'a', 'l', 'z', 'c', 'm'}
    a - b                   # {'r', 'd', 'b'} 集合减运算
    a | b                   # {'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'} 并集
    a & b                   # {'a', 'c'} 交集
    a ^ b                   # {'r', 'd', 'b', 'm', 'z', 'l'} a | b - a & b
    ```
- 集合lambda运算
    > 详见[lambda表达式](#lambda表达式)
### 字典
> 与列表类似，不过依据键值对索引
- 构造方式
    ```
    a = {}      # 空字典
    a = dict()  # 空字典
    ```
    ```
    dict(sape=4139, guido=4127, jack=4098)
    # 生成{'sape': 4139, 'guido': 4127, 'jack': 4098}
    ```
- keys()
    > keys函数返回所有key的列表
- values()
    > values函数返回所有value的列表

## 语句
### 赋值语句
```
string1, string2, string3 = '', 'Trondheim', 'Hammer Dance' # 对应位置进行赋值
```
### 选择语句 
> 注意: \
> 缩进: `代码块`缩进比`if`语句多一个，`elif`和`else`的语句与`if`对齐 \
> 冒号: 注意每个`if`, `else`, `elif`后都要加`:` \
> 可以没有`else`, `elif` \
> py没有`switch case`
```
if ...:
    pass
elif ...:
    pass
else:
    pass
```
e.g.
```
if x < 0:
    print('negative')
elif x = 0: 
    print('zero')
else: 
    print('positive')
```
关于`switch case`:\
一个 `if ... elif ... elif ... `序列可以看作是其他语言中的 `switch` 或 `case` 语句的替代。
### 循环语句
- for 循环
    > 一般用于循环遍历某个列表、集合或类似的
    ```
    b = [1, 2, 3]
    for a in b:
        print(a ** 2)
    # 输出结果
    # 1
    # 2
    # 3
    ```
    - break、continue、else
        > break, continue与java, c, cpp用法类似

        `其中else不会在break状态下被执行`
        ```
        for n in range(2, 10):
            for x in range(2, n): if n % x == 0:
                print(n, 'equals', x, '*', n//x)
                break 
            else:
                print(n, 'is a prime number')
        # 输出：
        # 2 is a prime number
        # 3 is a prime number
        # 4 equals 2 * 2
        # 5 is a prime number
        # 6 equals 2 * 3
        # 7 is a prime number
        # 8 equals 2 * 4
        # 9 equals 3 * 3
        ```
- while语句
    > 用于计数循环较多
    ```
    i = 1
    while i <= 3:
        print(i ** 2)
        i++
    # 输出结果与上例类似
    ```
- 循环技巧
    1. 当在字典中循环时，用 items() 方法可将关键字和对应的值同时取出
        ```
        knights = {'gallahad': 'the pure', 'robin': 'the brave'}
        for k, v in knights.items():
            print(k, v)
        ```
        输出
        ```
        gallahad the pure
        robin the brave
        ```
    2. 当在序列中循环时，用 enumerate() 函数可以将索引位置和其对应的值同时取出
        ```
        for i, v in enumerate(['tic', 'tac', 'toe']):
            print(i, v)
        ```
        输出
        ```
        0 tic
        1 tac 
        2 toe
        ```
    3. 当同时在两个或更多序列中循环时，可以用 zip() 函数将其内元素一一匹配。
        ```
        questions = ['name', 'quest', 'favorite color']
        answers = ['lancelot', 'the holy grail', 'blue']
        for q, a in zip(questions, answers):
            print('What is your {0}? It is {1}.'.format(q, a))
        ```
        输出
        ```
        What is your name? It is lancelot.
        What is your quest? It is the holy grail. What is your favorite color? It is blue.
        ```
        *注意这里用到了字符串的format函数*
    4. 逆向循环使用reversed函数
    5. 删除包含特定值的所有列表元素
        ```
        while 'cat' in pets:
            pets.remove('cat')
        ```

### pass语句
> 当语法上需要一个语句，而有什么都不需要做的时候使用

### lambda表达式
- 列表
    ```
    a  = range(10)
    s1 = [x ** 2 for x in a] 
    s2 = list(map(lambda x: x**2, range(10)))
    ```
    ```
    [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
    ```
    上式等同于
    ```
    combs = []
    for x in [1,2,3]:
        for y in [3,1,4]:
            if x != y:
                combs.append((x, y))
    ```
    - 多重lambda嵌套
        ```
        matrix = [
            [1, 2, 3, 4],
            [5, 6, 7, 8],
            [9, 10, 11, 12]
        ]
        [[row[i] for row in matrix] for i in range(4)]
        ```
- 集合
    > 把list中的[]换成{}即可，并未发现其他不同
- 字典
    ```
    {x: x**2 for x in (2, 4, 6)}
    ```

## 模块
- dir()
    > 内置函数 dir() 用于查找模块定义的名称。它返回一个排序过的字符串列表
    ```
    import fibo
    dir(fibo) # 输出['__name__', 'fib', 'fib2']
    ```

## 函数
0. python的函数中可以嵌套函数！！！
    ```
    def a():
        def b():            # 合法
            print('b')
        b()                 # 合法
    ```
1. 函数修改列表
    - 将列表传递给函数后，函数就可对其进行修改。在函数中对这个列表所做的任何修改都是永久性的
        > 这里类似于cpp函数传入列表指针
    - 禁止函数修改列表
        > 要将列表的副本传递给函数
        ```
        mod_list(list[:])
        ```
2. 传递任意数量的参数
    > 形参前加*, 类似cpp指针的语法 

    即将用户输入的所有参数变为一个元组 \
    e.g.
    ```
    def make_pizza(*toppings): 
        """打印顾客点的所有配料""" 
        print(toppings)
    make_pizza('pepperoni')
    make_pizza('mushrooms', 'green peppers', 'extra cheese')
    ```
    输出
    ```
    ('pepperoni',)
    ('mushrooms', 'green peppers', 'extra cheese')
    ```
3. 使用任意数量的关键字实参
    > 形参前加**

    将用户的输入转换成一个字典 \
    e.g.
    ```
    def build_profile(first, last, **user_info):
        """创建一个字典，其中包含我们知道的有关用户的一切"""
        profile = {}
        profile['first_name'] = first
        profile['last_name'] = last
        for key, value in user_info.items():  # 这里访问输入的字典参数
            profile[key] = value
        return profile
    ```

## 类
- 构造函数
    > \_\_init\_\_()
    ```
    class A:
        def __init__():
            print('A\'s constructor')
    ```
- `私有变量`

    在变量前加两个下划线，编译器会解释为_classname__name \
    e.g.
    ```
    class Mapping:
        def __init__(self, iterable):
            self.items_list = [] 
            self.__update(iterable)

        def update(self, iterable): 
            for item in iterable:
            self.items_list.append(item)

        __update = update       # 私有函数的别名

    class MappingSubclass(Mapping):

        def update(self, keys, values):
            # provides new signature for update() 
            # but does not break __init__() <-这里指父类的__init__()
            for item in zip(keys, values):
            self.items_list.append(item)
    ```
### `迭代器`
for语句会在in后边的容器对象上调用iter()，该函数返回一个定义了 \_\_next\_\_() 方法的迭代器对象\
当元素用尽时，\_\_next\_\_() 将引发 StopIteration 异常来通知终止 for 循环\
e.g.
```
>>> s = 'abc'
>>> it = iter(s)
>>> it
<iterator object at 0x00A1DB50> 
>>> next(it)
'a'
>>> next(it)
'b'
>>> next(it)
'c'
>>> next(it)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
    next(it)
StopIteration
```
- 在类中设置迭代器\
    定义一个 \_\_iter\_\_() 方法来`返回一个带有 \_\_next\_\_() 方法的对象`。如果类已定义了 \_\_next\_\_()，则 \_\_iter\_\_() 可以简单地返回 self

    e.g.
    ```
    class Reverse:
    """Iterator for looping over a sequence backwards.""" 
    def __init__(self, data):
        self.data = data self.index = len(data)
    def __iter__(self): 
        return self                     # 简单地返回 self
    def __next__(self):
        if self.index == 0:
            raise StopIteration         # 引发 StopIteration 异常
        self.index = self.index - 1 
        return self.data[self.index]
    ```
    使用
    ```
    >>> rev = Reverse('spam')
    >>> for char in rev: 
    ...     print(char)
    ...
    m
    a
    p
    s
    ```
### `生成器`
> Generator 是一个用于创建迭代器的简单而强大的工具

它们的写法类似标准的函数，但当它们要返回数据时 会使用 yield 语句。每次对生成器调用 next() 时，它会从上次离开位置恢复执行
e.g.
```
def reverse(data):
    for index in range(len(data)-1, -1, -1):
        yield data[index]
```
使用
```
>>> for char in reverse('golf'): 
... print(char)
...
f
l
o
g
```

## 文件读写
- 打开文件
    ```
    open(filename, mode='r')
    ```
    mode参数
    - 'r' 表示文件只能读取
    - 'w' 表示只能写入(已存在的同名文件会被删除)
    - 'a' 表示 打开文件以追加内容;任何写入的数据会自动添加到文件的末尾。
    - 'r+' 表示打开文件进行读写
    - 追加的 'b' 则以 binary mode 打开文 件

    在处理文件对象时，最好使用 with 关键字。优点是当子句体结束后文件会正确关闭，即使在某个时刻引发 了异常。而且使用 with 相比等效的 try-finally 代码块要简短得多:\
    e.g.
    ```
    >>> with open('workfile') as f: ... read_data = f.read() >>> f.closed
    True
    ```
- 使用文件
    1. f.read(size)
        > size 是一个可选的数值参数\
        > 当 size 被省略或者为负数时，将读取并返回 整个文件的内容

        将读取并返回至多 size 个字符(在文本模式下)或 size 个字节(在二进制模式下)\
        如果已到达文件末尾，f.read() 将返回一 个空字符串 ('')
    2. f.readline()

        f.readline() 从文件中读取一行\
        换行符(\n)留在字符串的末尾\
        空行使用 '\n' 表示\
        文件末尾使用''表示
    3. f.readlines()
        > 读取所有行
    4. 迭代访问文件每行
        ```
        >>> for line in f:
        ...     print(line, end='')
        ...
        ```
    5. f.write(string) 
        > 会把 string 的内容写入到文件中，并返回写入的字符数。

## 使用 json 保存结构化数据
1. json.dumps(object)
    ```
    >>> import json
    >>> json.dumps([1, 'simple', 'list']) 
    ... '[1, "simple", "list"]
    ```
2. json.dump(object, textfile) 与 json.load(textfile)
    > 它只是将对象序列化为text file
    ```
    json.dump(x, f)
    ```
    要再次解码对象，如果 f 是一个打开的以供阅读的text file 对象:
    ```
    x = json.load(f)
    ```
    > 这种简单的序列化技术可以处理列表和字典，但是在 JSON 中序列化任意类的实例需要额外的努力

## 异常处理
1. try ... except ... \[finally\] ...
    > 这些与在java中类似
    ```
    try:
        pass
    except Exception as _:
        pass
    finally:
        pass
    ```
    e.g.
    ```
    import sys 
    try:
        f = open('myfile.txt') 
        s = f.readline()
        i = int(s.strip())
    except OSError as err:
        print("OS error: {0}".format(err))
    except ValueError:
        print("Could not convert data to an integer.")
    except:
        print("Unexpected error:", sys.exc_info()[0]) 
        raise   # 重新引发异常
    ```
    - else语句
        > 未引发异常时使用
        ```
        for arg in sys.argv[1:]: 
        try:
            f = open(arg, 'r') 
        except OSError:
            print('cannot open', arg) 
        else:
            print(arg, 'has', len(f.readlines()), 'lines') 
            f.close()
        ```
2. 异常参数
    >参数存储在 instance. args 中
    ```
    >>> try:
    ...     raise Exception('spam', 'eggs')
    ... except Exception as inst:
    ...     print(type(inst))
    ...     print(inst.args)
    ...     print(inst) ...
    ...     x, y = inst.args
    ...     print('x =', x)
    ...     print('y =', y) 
    ...
    <class 'Exception'> 
    ('spam', 'eggs') 
    å('spam', 'eggs')
    x = spam
    y = eggs
    ```
3. 抛出异常
    ```
    raise exception
    ```
4. 自定义异常
    
    需要继承Exception\
    e.g.
    ```
    class TransitionError(Error):
    """Raised when an operation attempts a state transition that's not allowed.

    Attributes:
        previous -- state at beginning of transition
        next -- attempted new state
        message -- explanation of why the specific transition is not allowed
    """
        def __init__(self, previous, next, message): 
            self.previous = previous
            self.next = next
            self.message = message]
    ```