# 综述

#### 变量和字符串（Variable and String）

> “变量用来存储具体的值，“字符串”由一连串的字符组成，并用单引号或者双引号括起来。

打印 Hello World

````python
print("Hello World!")
````

Hello World 存储在变量里

````python
msg = "Hello World!"
print(msg)
````

字符串连接

````python
first_name = 'albert'
last_name = 'einstein'
full_name = first_name + ' ' + last_name
print(full_name)
````

#### 列表（Lists）

> 列表将元素按照一定顺序存储起来，用户可以使用索引 index 或者循环 loop 来对元素进行操作。

创建一个列表

````python
bikes = ['trek', 'redline', 'giant']
````

获取列表的第一个元素

````python
first_bike = bikes[0]
````

获取列表的最后一个元素

````python
first_bike = bikes[-1]
````

遍历列表（相当于把列表中所有元素撸一遍）

````python
for bike in bikes:
    print(bike)
````

向列表中增加元素

````python
bikes = []
bikes.append('trek')
bikes.append('redline')
bikes.append('giant')
````

创建数值列表

````python
squares = []
for x in range(1, 11):
    squares.append(x**2)
````

列表的推导

````python
squares = [x**2 for x in range(1, 11)]
````

列表的切片

````python
finishers = ['sam', 'bob', 'ada', 'bea']
first_two = finishers[:2]
````

列表的复制

````python
copy_of_bikes = bikes[:]
````

#### 元组（Tuples）

> 元组类似于列表，只不过元组中的元素不能够被操作。

创建一个元组

````python
dimensions = (1920, 1080)
````

#### If语句

> If语句用来判定在不同的情况下执行相应的语句。

条件判断

````python
equals x == 42
not equal x != 42
greater than x > 42
  or equal to x >= 42
less than x < 42
  or equal to x <= 42
````

列表条件判断

````python
'trek' in bikes
'surly' not in bikes
````

赋予布尔值（Boolean）

````python
game_active = True
can_edit = False
````

一个简单的if判定

````python
if age >= 18:
    print("You can vote!")
````

If-elif-else语句

````python
if age < 4:
    ticket_price = 0
elif age < 18:
    ticket_price = 10
else:
    ticket_price = 15
````

#### 字典

> 字典中存储有对应关系的成对信息，其中的每一个元素被称为一个“键值”对（key-value）。

一个简单的字典

````python
alien = {'color': 'green', 'points': 5}
````

取得该字典的一个值（color的值）

````python
print("The alien's color is " + alien['color'])
````

加入一个新的键值（key为x_position，value为0）

````python
alien['x_position'] = 0
````

遍历所有的键值（key-value）

````python
fav_numbers = {'eric': 17, 'ever': 4}
for name, number in fav_numbers.items():
    print(name + ' loves ' + str(number))
````

遍历所有的“键”（key）

````python
fav_numbers = {'eric': 17, 'ever': 4}
for name in fav_numbers.keys():
    print(name + ' loves a number')
````

遍历所有的“值”（value）

````python
fav_numbers = {'eric': 17, 'ever': 4}
for number in fav_numbers.values():
    print(str(number) + ' is a favorite')
````

#### 用户输入

> 程序提示用户需要输入，所有的输入都被存储在字符串中。

提示输入值

````python
name = input("What's your name? ")
print("Hello, " + name + "!")
````

#### while循环

> 当while后的条件为真时，会一直循环执行某段程序。

一个简单的while循环

````pytho
current_value = 1
while current_value <= 5:
    print(current_value)
    current_value += 1
````

用户决定什么时候退出

````python
msg = ''
while msg != 'quit':
    msg = input("What's your message? ")
    print(msg)
````

#### 函数

> 函数式用来实现特定功能的代码段，其中，提供给函数的参数叫做“实参”（argument），函数定义的参数叫做“形参”（parameter）。

一个简单的函数

````python
def greet_user():
    """Display a personalized greeting."""
    print("Hello!")
greet_user()
````

传递一个实参（argument）

````python
def greet_user(username):
    """Display a personalized greeting."""
    print("Hello, " + username + "!")
greet_user('Jesse')
````

形参（parameter）的默认值

````python
def make_pizza(topping='bacon'):
    """Make a single-topping pizza."""
    print("Have a " + topping + " pizza!")
make_pizza()
make_pizza('pepperoni')
````

返回一个值sum

````python
def add_numbers(x, y):
    """Add two numbers and return the sum."""
    return x + y
sum = add_numbers(3, 5)
print(sum)
````

#### 类

> 类定义了具有相同属性和方法的对象的集合，类的参数信息存储在属性（attribute）中，类中定义的函数叫做方法（method），子类继承了父类中所有的参数和方法。

创建一个名为dog的类

````python
class Dog():
    """Represent a dog."""

    def __init__(self,name):
        """Initialize dog object."""
        self.name = name
    def sit(self):
        """Simulate sitting."""
        print(slef.name + " is sitting.")

my_dog = Dog('Peso')

print(my_dog.name + " is a great dog.")
my_dog.sit()
````

继承Inheritance

````python
class SARDog(Dog):
    """Represent a search a dog."""

    def __init__(self, name):
        """Initialize the sardog."""
        super().__init__(name)
    def search (self):
        """Simulate searching."""
        print(self.name + " is searching.")

my_dog = SARDog('Willie')

print(my_dog.name + " is a search dog.")
my_dog.sit()
my_dog.search()
````

#### 学以致用

> 如果你有牛叉的编程技能，你会做点什么呢？

当你学习编程时，你一定想结合实际生活来做点学以致用的东西，有些同学平时就有一个好习惯，一旦想起来一些有意思的idea，就记在本子上。如果你暂时还没这个习惯，可以现在就想出几个想做的东西。

#### 文件files操作

> 程序可以读写文件，默认状态下，文件以“r”只读模式打开，但也能以“w”写模式和“a”追加模式打开。

读取文件并按顺序存储

````python
filename = 'siddhartha.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

for line in lines:
    print(line)
````

向文件中写（覆盖掉之前的内容）

````python
filename = 'journal.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.")
````

向文件中添加（不覆盖之前的内容）

````python
filename = 'journal.txt'
with open(filename, 'a') as file_object:
    file_object.write("\nI love programming.")
````

#### 异常处理 Exceptions

> 异常处理帮助你对错误做出适当的响应：首先将需要执行的程序放在try语句后，若程序出现异常，则执行except语句后的代码；若try语句后的代码没有异常，则执行else语句后的代码。

捕获一个异常

````python
prompt = "How many tickets do you need?"
num_tickets = input(prompt)

try:
    num_tickets = int(num_tickets)
except ValueError:
    print("Please try again.")
else:
    print("Your tickets are printing.")
````

#### Python 的佛性

> 告别繁文缛节，回归佛性极简主义

如果你有两个方案的代码：简单的和复杂的，并且都能解决问题，那么毫无疑问立马选择简单的。简洁的代码也更方便后期的维护和修改。