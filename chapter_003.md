# if语句和while循环

#### 什么是if语句，while循环？

if 语句允许你检查程序的当前状态并适当地响应该状态。你可以写一个简单的 if 语句来检查一个条件，或者你可以创建一系列复杂的 if 语句来确定你正在寻找的条件。

只要某些条件保持正确，循环就会运行。若用户需要，可以使用 while 循环让程序一直运行。

#### 条件测试

> 条件测试就是判断是 True 或 False 的表达式。 Python 使用值True 和 False 来决定是否应执行 if 语句中的代码。

判断是否相等

一个=符号可以给变量赋值，双==符号则用来判读两个值是否相等

````python
>>> car = 'bmw'
>>> car == 'bmw'
True
>>> car = 'audi'
>>> car == 'bmw'
False
````

在进行比较时忽略大小写

````python
>>> car = 'Audi'
>>> car.lower() == 'audi'
True
````

判断是否不相等

````python
>>> topping = 'mushrooms'
>>> topping != 'anchovies'
True
````

#### 数值比较

> 既可比较字符串的值是否相等，也可比较数字的值是否相等。

测试是否相等

````python
>>> age = 18
>>> age == 18
True
>>> age != 18
False
````

对比符号

````python
>>> age = 19
>>> age < 21
True
>>> age <= 21
True
>>> age > 21
False
>>> age >= 21
False
````

#### 同时判断多个条件

> 你可以同时判断多个条件。如果列出的所有条件均为真，则 and 运算符将返回 True。如果任何条件为真，则 or 运算符返回 True。

使用 and 判断多个条件

````python
>>> age_0 = 22
>>> age_1 = 18
>>> age_0 >= 21 and age_1 >= 21
False
>>> age_1 = 23
>>> age_0 >= 21 and age_1 >= 21
True
````

使用 or 判断多个条件

````python
>>> age_0 = 22
>>> age_1 = 18
>>> age_0 >= 21 or age_1 >= 21
True
>>> age_0 = 18
>>> age_0 >= 21 or age_1 >= 21
False
````

#### 布尔值

> 布尔值只有两种： True 和 False，带布尔值的变量通常用于跟踪程序中的某些条件。

简单的布尔值

````python
game_active = True
can_edit = False
````

#### If语句

> If 语句有好几种，如何选择呢？首先要看判断条件的数量，条件多的情况下可以反复使用 elif 语句 (elif 是 else if 的缩写)，有些情况下 else 是不需要的。

一个简单的 If 语句

````python
age = 19
if age >= 18:
    print("You're old enough to vote!")
````

if-else 语句

````python
age = 17
if age >= 18:
    print("You're old enough to vote!")
else:
    print("You can't vote yet.")
````

if-elif-else 语句链

````python
age = 12

if age < 4:
    price = 0
elif age < 18:
    price = 5
else:
    price = 10
print("Your cost is $" + str(price) + ".")
````

#### 列表的条件测试

> 可以测试列表中是否含有某个值，在遍历列表前，也可以测试列表是否是空的。

测试某个值是否在列表中

````python
>>> players = ['al', 'bea', 'cyn', 'dale']
>>> 'al' in players
True
>>> 'eric' in players
False
````

测试某个值是否在列表中

````python
banned_users = ['ann', 'chad', 'dee']
user = 'erin'
if user not in banned_users:
    print("You can play!")
````

判断列表是否为空

````python
players = []
if players:
    for player in players:
        print("Player: " + player.title())
else:
    print("We have no players yet!")
````

#### 接收输入

> 在 python3 中， input()函数将所有的输入按照字符串进行处理，并返回一个字符串。

简单的输入

````python
name = input("What's your name? ")
print("Hello, " + name + ".")
````

接受数字输入

````python
age = input("How old are you? ")
age = int(age)
if age >= 18:
    print("\nYou can vote!")
else:
    print("\nYou can't vote yet.")
````

接受输入（ python2.7）

Python2.7 中，使用 raw_input()函数，同 python3 中的 input() 函数

````python
name = raw_input("What's your name? ")
print("Hello, " + name + ".")
````

#### While循环

> 只要条件为 True， while 循环中的代码会反复执行。

从 1 算到 5

````python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
````

用户决定何时退出

````python
prompt = "\nTell me something, and I'll "
prompt += "repeat it back to you."
prompt += "\nEnter 'quit' to end the program. "

message = ""
while message != 'quit':
    message = input(prompt)

    if message != 'quit':
        print(message)
````

使用 flag

````python
prompt = "\nTell me something, and I'll "
prompt += "repeat it back to you."
prompt += "\nEnter 'quit' to end the program. "

active = True
while active:
    message = input(prompt)
    if message == 'quit':
        active = False
    else:
        print(message)
````

使用 break 退出当前循环

````python
prompt = "\nWhat cities have you visited?"
prompt += "\nEnter 'quit' when you're done. "

while True:
    city = input(prompt)

    if city == 'quit':
        break
    else:
        print("I've been to " + city + "!")
````

#### 退出循环

在任何 python 循环中，都可以使用 break 语句和 continue 语句，使用 continue 跳出本次循环,使用 break 跳出整个循环。continue 语句用来告诉 Python 跳过当前循环的剩余语句，然后继续进行下一轮循环。

#### Continue

continue 用在循环中

````python
banned_users = ['eve', 'fred', 'gary', 'helen']

prompt = "\nAdd a player to your team."
prompt += "\nEnter 'quit' when you're done. "

players = []
while True:
    player = input(prompt)
    if player == 'quit':
        break
    elif player in banned_users:
        print(player + " is banned!")
        continue
    else:
        players.append(player)

print("\nYour team:")
for player in players:
    print(player)
````

#### 避免无限循环

> while 循环后的条件若为 Ture，程序会一直循环执行不会停止，直到条件为 False，循环才会停止运行。

一个无限的循环

````python
while True:
    name = input("\nWho are you? ")
    print("Nice to meet you, " + name + "!")
````

#### 删除列表中某个值的所有实例

> remove()方法从列表中删除特定值，但它只会删除这个值的第一个实例，所以可以用 while 循环来删除该值的所有实例。

删除 pets 列表中的所有 cat

````python
pets = ['dog', 'cat', 'dog', 'fish', 'cat',
'rabbit', 'cat']
print(pets)

while 'cat' in pets:
    pets.remove('cat')

print(pets)
````