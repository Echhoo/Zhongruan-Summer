# Python note1(1-10)

## 第2章 变量和简单数据类型

### 变量的命名和使用

（1）只能包含字母、数字和下划线，变量名可以字母或下划线打头，但不能以数字打头

（2）不能包含空格

（3）关键字和函数名不能用作变量名

（4）既简短由具有描述性

（5）慎用小写字母l和大写字母O

注意：避免大写



### 字符串

单引号和双引号都可以表示字符串

`tilte()` 首字母大写显示单词

`upper()` 全部大写

`lower()` 全部小写

`+` 拼接字符串

`\t`或空格表示空白 `\n`表示换行 `\n\t`换到下一行，并在下一行开头添加一个制表符

`rstrip()` 字符串末尾没有空白

`lstrip()` 去除字符串两端空白 `strip()` 去除字符串两端空白



### 数字

整数 `+`、`-`、`*`、`\`（3/2=1.5）、`**`乘方

浮点数 `+`、`-`、`*`、`\` 可能产生多余位数

`str(age)`将数字转为字符串



### `#`注释



### Python之禅

`import this`





## 第3章 列表简介

### 基本概念

列表：由一系列按特定顺序排列的元素组成，元素之间可以没有任何关系，名称一般为复数（如letters）。

用方括号`[]`表示，用逗号`,`分隔元素

索引从0开始，-1表示最后一个元素，-2表示倒数第二个元素，以此类推（列表为空时，这种访问会报错）



### 修改、添加和删除元素

修改--访问下标

添加--`append()`末尾添加、`insert(0,'ducati')`在索引0处添加空间，并存值

删除：

不继续使用--`del motorcycles[1]` 删除某位置元素

继续使用--`popped_motorcycle = motorcycles.pop()` 删除列表末尾元素并继续使用、`first_owned = motorcycles.pop(0)` 删除列表中任何位置元素

按值删除元素--`motorcycles.remove('ducati')`，如果需要继续使用，就提前存入一个变量



### 组织列表

`cars.sort()`永久排序

`cars.sort(reverse=True)`反向排序

`sorted(cars)`临时排序，对列表不做修改

`cars.reverse()`反转排序

`len(cars)`获取列表长度





## 第4章 操作列表

### 遍历列表

```python
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician)
```

### 创建数值列表

```python
for value in range(1,5): #打印结果为1,2,3,4 不包含5
	print(value)

numbers = list(range(1,6)) #numbers=[1,2,3,4,5]

even_numbers = list(range(2,11,2)) #even_numbers = [2,4,6,8,10] 步长为2


min(digits)
max(digits)
sum(digits)

#列表解析
squares = [value**2 for value in range(1,11)] #squares = [1,4,9,16,25,36,49,64,81,100] 

#切片
players = ['charles','martina','florence','eli']
print(players[0:3]) #打印结果为['charles','martina','michael']，不包含索引3
print(players[:4]) #从头开始
print(players[2:]) #结尾结束
for player in players[:3]: #遍历切片
    print(player.title())
other_players = players[:] #复制列表
```

### 元组

——不可变的列表，圆括号 `（）` 表示

```python
dimensions = (200, 50) #定义

for dimension in dimensions: #遍历
    print(dimension)

dimensions = (400, 100) #不能修改元组中的元素，但可以重新赋值

```





## 第5章 if语句

```python
if answer !=42: #单个判断
    print('wrong')

if age_0 >=21 and age_1 >= 21: #多个条件
    print('wrong')
if age_0 >=21 or age_1 >= 21: 
    print('wrong')

if 'mushrooms' in requested_toppings: #检查是否包含某值
    pring('wrong')
if 'mushrooms' not in requested_toppings: #检查是否不包含某值
    pring('wrong')

if age >= 18: #if-else
    print("")
else:
    print("")

if age < 4: #if-elif-else
    print("")
elif age <18:
    print("")
else:
    print("")

requested_toppings = []
if requested_toppings: #确定列表非空
    print("")
```





## 第6章 字典

一系列键—值对，通过键来访问值，不关心顺序

```python
alien_0 = {'color': 'green', 'points': 5}
print(aline_0['color'])  #green
print(aline_0['points'])  #5

#添加键—值对
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)  #{'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}

#修改
alien_0['color'] = 'yellow'

#删除
del alien_0['points']

#遍历, 返回顺序与存储顺序不同，不关心顺序
for key, value in user_0.items():
    print(key)
    print(value)

for name in favorite_language.keys():  #只遍历所有键，省略.keys()默认遍历键，.keys()返回了列表
    print(name.title())

for name in sorted(favorite_languages.keys()): #顺序遍历
    print(name)

for language in favorite_languages.values():  #遍历所有值
    print(language)

for language in set(favorite_languages.values()):  #去重
    print(language)

#嵌套
#字典列表
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}

aliens = [alien_0, alien_1, alien_2]

#字典中存储列表,一个键关联到多个值
pizza = {'curst': 'thick', 'toppings': ['mushrooms', 'extra cheese']}

#字典中存储字典
users = {
	'aeinstein': {
		'first': 'albert',
		'last': 'einstein',
		'location': 'princeton',
		},
	'mcurie': {
		'first': 'marie',
		'last': 'curie',
		'location': 'paris',
		},
	}
```





## 第7章 用户输入和while循环

### 输入函数 `input`

```python
name = input("Please enter your name: ") #引号中为提示信息
print("Hello, " + name + "!")

prompt = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name? "  #多行提示信息写法

age = int(age) #input默认传入为字符串，int()将字符串转为整数

#求模运算符%，常用于判断奇偶
```



### while 循环

for 循环处理列表和字典时，不能对其修改

while 循环处理列表和字典时，可以对其修改

```python
# 移动
# 首先，创建一个待验证用户列表
# 和一个用于存储已验证用户的空列表
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []
# 验证每个用户，直到没有未验证用户为止
# 将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:
	current_user = unconfirmed_users.pop()
	print("Verifying user: " + current_user.title())
	confirmed_users.append(current_user)
# 显示所有已验证的用户
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
	print(confirmed_user.title())
    
# 删除（多次出现同一元素）
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)
while 'cat' in pets:
	pets.remove('cat')
print(pets)

#通过用户输入填充字典
responses = {}
# 设置一个标志，指出调查是否继续
polling_active = True
while polling_active:
# 提示输入被调查者的名字和回答
	name = input("\nWhat is your name? ")
	response = input("Which mountain would you like to climb someday? ")
# 将答卷存储在字典中
	responses[name] = response
# 看看是否还有人要参与调查
	repeat = input("Would you like to let another person respond? (yes/ no) ")
	if repeat == 'no':
		polling_active = False
# 调查结束，显示结果
print("\n--- Poll Results ---")
for name, response in responses.items():
	print(name + " would like to climb " + response + ".")

```





## 第8章 函数

```python
def greet_user():  
    pritn("Hello!")
greet_user()

def greet_user(username):
	print("Hello, " + username.title() + "!")
greet_user('jesse')

def describe_pet(animal_type, pet_name):
	print("\nI have a " + animal_type + ".")
	print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet('hamster', 'harry')  # 位置实参

def describe_pet(animal_type, pet_name):
	print("\nI have a " + animal_type + ".")
	print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(animal_type='hamster', pet_name='harry') # 关键字实参

def describe_pet(pet_name, animal_type='dog'):
	print("\nI have a " + animal_type + ".")
	print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(pet_name='willie') # 默认值

#返回值
def get_formatted_name(first_name, last_name):  #返回简单值
	full_name = first_name + ' ' + last_name
	return full_name.title()
musician = get_formatted_name('jimi', 'hendrix')
print(musician)

def build_person(first_name, last_name):
"""返回一个字典，其中包含有关一个人的信息"""
	person = {'first': first_name, 'last': last_name}
	return person
musician = build_person('jimi', 'hendrix')
print(musician)

#传递列表，在函数中对于列表的修改是永久性的
def greet_users(names):
"""向列表中的每位用户都发出简单的问候"""
for name in names:
	msg = "Hello, " + name.title() + "!"
	print(msg)
usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)

function_name(list_name[:]) #传递切片，即传递列表副本，函数不会改变原列表

#传递任意数量的实参，*toppings是一个空元组
def make_pizza(*toppings):
"""打印顾客点的所有配料"""
	print(toppings)
make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')

def make_pizza(size, *toppings):  #任意数量实参放最后
	"""概述要制作的比萨"""
	print("\nMaking a " + str(size) +
	"-inch pizza with the following toppings:")
	for topping in toppings:
		print("- " + topping)
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

def build_profile(first, last, **user_info):  #任意数量的关键字实参
"""创建一个字典，其中包含我们知道的有关用户的一切"""
	profile = {}
	profile['first_name'] = first
	profile['last_name'] = last
	for key, value in user_info.items():
		profile[key] = value
		return profile
user_profile = build_profile('albert', 'einstein',
							location='princeton',
							field='physics')
print(user_profile)
```



### 将函数存储在模块中

（1）导入整个模块：将函数写入xx.py文件中，然后用 `import xx`进行导入，用 `module_name.function_name()`调用

（2）导入特定函数：`from module_name import function_name`、`from module_name import function_0,function_1,function_2`，调用时无需添加模块名

（3）导入模块中所有函数：`from pizza import *`不建议使用





## 第9章 类

```python
class Dog():
	"""一次模拟小狗的简单尝试"""
    
	def __init__(self, name, age): #self不可以省略
		"""初始化属性name和age"""
		self.name = name
		self.age = age
        self.xx = 0 #给属性增加默认值
        
	def sit(self):
		"""模拟小狗被命令时蹲下"""
		print(self.name.title() + " is now sitting.")
        
	def roll_over(self):
		"""模拟小狗被命令时打滚"""
		print(self.name.title() + " rolled over!")
        
my_dog = Dog('willie', 6)  #创建实例
print("")

```



### 修改属性的值

（1）直接修改属性的值，通过实例进行访问

（2）通过方法修改

（3）通过方法对属性的值进行递增



### 继承

首先给父类的所有属性赋值

```python
class Car():
	"""一次模拟汽车的简单尝试"""
	def __init__(self, make, model, year):
		self.make = make
		self.model = model
		self.year = year
		self.odometer_reading = 0
        
	def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    		
	def read_odometer(self):
		print("This car has " + str(self.odometer_reading) + " miles on it.")
        
	def update_odometer(self, mileage):
        if mileage >= self.odometer_reading:
        self.odometer_reading = mileage
        else:
        print("You can't roll back an odometer!")
        
	def increment_odometer(self, miles):
        self.odometer_reading += miles
        
class ElectricCar(Car):
	"""电动汽车的独特之处"""

    def __init__(self, make, model, year):
		"""初始化父类的属性"""
        super().__init__(make, model, year)
        self.bettery_size = 70
    
    def describe_battery(self):
        print("")

my_tesla = ElectricCar('tesla', 'model s', 2016)        
print(my_tesla.get_descriptive_name())
```

重写：同名即可

将实例用作属性

```python
class Car():
	--snip--
    
class Battery():
    """一次模拟电动汽车电瓶的简单尝试"""
    def __init__(self, battery_size=70):
        """初始化电瓶的属性"""
        self.battery_size = battery_size

	def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kWh battery.")
            
class ElectricCar(Car):
	"""电动汽车的独特之处"""
	def __init__(self, make, model, year):
		"""初始化父类的属性，再初始化电动汽车特有的属性"""
		super().__init__(make, model, year)
        self.battery = Battery()
        
my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()
```



### 导入类

（1）导入单个类：将类写入另一个模块文件xx.py，用 `from xx import xx`

（2）从一个模块导入多个类：`from car import Car, ElectricCar`

（3）导入整个模块：`import car`

（4）导入模块中的所有类：`from module_name import *`



### Python标准库

`from collections import xx`



### 编码风格

类名，首字母大写不使用下划线。

实例名、模块名采用小写，单词之间加下划线。

每个类，在类定义后面包含一个文档字符串，简要描述类的功能，每个模块也应包含一个文档字符串，对其中的类可用于做什么进行描述。



## 第10章 文件和异常

### 从文件中读取数据

（1）读取整个文件

```python
with open('pi_digits.txt') as file_object:
    contents = file_object.read()
    print(contents)
    #如果需要去除最后一行的空行，print(contents.rstrip())
```

（2）文件路径

相对文件路径：`with open('text_files\filename.txt') as file_object`

绝对文件路径：

```python
file_path = 'C:\Users\ehmatthes\other_files\text_files\filename.txt'
with open(file_path) as file_object:
```

（3）逐行读取

```python
filename = 'pi_digits.txt'
with open(filename) as file_object:
	for line in file_object:
		print(line)
        #消除空行用rstrip()
```

（4）创建一个包含文件各行内容的列表--文件对象只能在with代码块内使用，列表可在外部使用

```python
filename = 'pi_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()
for line in lines:
    print(line.rstrip())
```



### 写入文件

（1）写入空文件（读取模式 `'r'`、写入模式 `'w'`、 附加模式 `'a'`、能够读取和写入文件 `'r+'`）

```python
filename = 'programming.txt'
with open(filename, 'w') as file_object:
	file_object.write("I love programming.")
```

（2）写入多行--手动加入换行符

```python
filename = 'programming.txt'
with open(filename, 'w') as file_object:
file_object.write("I love programming.\n")
file_object.write("I love creating new games.\n")
```

（3）附加到文件

```python
filename = 'programming.txt'
with open(filename, 'a') as file_object:
	file_object.write("I also love finding meaning in large datasets.\n")
	file_object.write("I love creating apps that can run in a browser.\n")
```



### 异常

try-except

（1）处理ZeroDivisionError异常

```Python
try:
	print(5/0)
except ZeroDivisionError:
	print("You can't divide by zero!")
```

（2）else代码块

```python
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
	first_number = input("\nFirst number: ")
	if first_number == 'q':
		break
	second_number = input("Second number: ")
	try:
		answer = int(first_number) / int(second_number)
	except ZeroDivisionError:
		print("You can't divide by 0!")
	else:
		print(answer) #成功执行的代码块
```

（3）失败时一声不吭

```python
def count_words(filename):
	"""计算一个文件大致包含多少个单词"""
	try:
		--snip--
	except FileNotFoundError:
		pass
	else:
		--snip--
filenames = ['alice.txt', 'siddhartha.txt', 'moby_dick.txt', 'little_women.txt']
for filename in filenames:
	count_words(filename)
```



### 存储数据

使用模块json存储数据

（1）使用`json.dump()`和`json.load()`

```python
import json
numbers = [2, 3, 5, 7, 11, 13]
filename = 'numbers.json'
with open(filename, 'w') as f_obj:
	json.dump(numbers, f_obj) #接受两个实参：要存储的数据，可用于存储数据的文件对象
    
import json
filename = 'numbers.json'
with open(filename) as f_obj:
	numbers = json.load(f_obj)
print(numbers)
```

（2）重构--将代码划分为一系列完成具体工作的函数