# 列表List

#### 什么是列表？

一系列的元素按照顺序存储在列表中，且没有数量限制。列表是python中对初学者来说最有用的元素类型，而且和程序中的很多概念都紧密相关。

#### 定义一个列表

> 使用方括号[]来定义列表，列表中存储的各个元素用逗号，隔开。最好用通俗易懂的名称来命名列表，让程序更容易阅读。

````python
users = ['val', 'bob', 'mia', 'ron', 'ned']
````

#### 访问列表

> 列表中的每一个元素的位置都会按顺序被分配一个值，这个值叫索引index，第一个元素的index是0，第二个元素的index是1，以此类推。如果index是负数，则表示从列表的尾部倒数的。要获取特定的元素，只需写出列表的名称，然后标出钙元素的索引。

获取第一个元素

````python
first_user = users[0]
````

获取第二个元素

````python
second_user = users[1]
````

获取最后一个元素

````python
last_user = user[-1]
````

#### 更新列表

> 一旦创建了列表，就可以通过个元素项的位置，来改变元素项的值。

更新元素

````python
users[0] = 'valerie'
users[-2] = 'ronald'
````

#### 增加元素

> 可以再列表中的任意为止增加元素。

列表尾部添加元素。

````python
users.append('amy')
````

像一个空的列表添加元素。

````python
users = []
users.append('val')
users.append('bob')
users.append('mia')
````

在列表中指定的位置插入元素。

````python
users.insert(0, 'joe')
users.insert(3, 'bea')
````

#### 删除元素

> 可以删除指定位置的元素，或直接指出元素的值来进行删除，若该值在列表中有多个，则删除第一个是该值的元素。

通过位置删除

````python
del users[-1]
````

通过具体的值删除

````python
users.remove('mia')
````

#### 弹出元素

> 如果想将某个元素从列表中弹出，并返回该元素的值，可以使用pop()函数。可以将列表想象成一叠堆起来的元素，最上面的是原来列表中最后面一个元素。默认情况下，pop函数删除的是列表中最后一个元素，当然你也可以让pop函数删除指定位置的元素，并返回该元素的值。

pop删除列表的最后一个元素

````python
most_recent_user = users.pop()
print(most_recent_user)
````

pop删除列表的第一个元素

````python
first_user = user.pop(0)
print(first_user)
````

#### 列表长度

> len()函数返回列表的长度(元素个数)。

求列表的长度

````python
num_users = len(users)
print("We have " + str(num_users) + " users.")
````

#### 列表排序

> sort()函数会永久改变列表中元素的顺序，sorted()函数会返回一个已经改变顺序的列表副本，原列表顺序依然保存。该函数可以让元素按照字母的顺序进行正向/反向排序。reverse()函数可以颠倒原列表的排列顺序。需要注意的是，小写字母和大写字母会影响排列顺序。

列表排序（按照元素字母的正向顺序排序）

````python
users.sort()
````

按照元素字母的反向顺序排序

````python
users.sort(reverse=True)
````

返回重新排序的列表

````python
print(sorted(users))
print(sorted(users， reverse=True))
````

反向列表元素

````python
users.reverse()
````

#### 遍历列表

> 遍历，就是整个列表撸一遍，循环访问所有的元素。列表中有很多元素，Python提供了高效的循环遍历的方法。当你建立一个循环时，Python一次一个地从列表中拉出每个元素，并将其存储在一个由用户命名的临时变量中，该变量名称应该是列表名称的单数形式。
> 缩进的代码段构成循环的主体，用户可以在循环中处理每一个元素。循环完成后，后面没有在缩进的代码会继续运行。

打印列表元素，user是用户命名的临时变量

````python
for user in users:
    print(user)
````

为每一个元素打印一条信息，循环完成后在打印一条单独的信息

````python
for user in users:
    print("Welcome, " + user + "!")

print("Welcome, we're glad to see you all!")
````

#### range()函数

> 你可以使用range()函数有效地处理一组数据。range()函数默认从0开始，在给定数字的前一个位置停止。使用list()函数可以方便的生成数量庞大的列表。

打印 0 到 1000 的数字

````python
for number in range(1001):
    print(number)
````

打印 1 到 1000 的数字

````python
for number in range(1, 1001):
    print(number)
````

创建一个列表，其元素的值为 1 到 100 万

````python
numbers = list(range(1, 1000001))
````

#### 简单的数据统计

> 你可以在包含数字元素的列表上进行一些简单的数据统计。

找出列表中元素的最小值

````python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
youngest = min(ages)
````

找出最大值

````python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
youngest = max(ages)
````

计算所有元素的和

````python
ages = [93, 99, 66, 17, 85, 1, 35, 82, 2, 77]
total_years = sum(ages)
````

#### 列表截取

> 你可以得到列表中的任何元素的集合。列表的一个部分成为一个切片。

截取前三个元素

````python
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
first_three = finishers[:3]
````

截取中间的三个元素

````python
middle_three = finishers[1:4]
````

截取最后三个元素

````python
last_three = finishers[-3:]
````

#### 复制列表

> 赋值列表其实就是截取整个列表，除此之外还真没有其他更高效的方法。

创建一个列表的副本

````python
finishers = ['kai', 'abe', 'ada', 'gus', 'zoe']
copy_of_finishers = finishers[:]
````

#### 列表生成式

> 使用循环，可以给予一个列表或一组数字生成一个新的列表。除此之外，还有一种更高效的方法：列表推导式。
> 要使用列表推导式，首先要为存储在列表中的值定义一个表格式，然后编写 for 循环来生成列表所需要的输入值。

使用 for 循环，生成一个平方数的列表

````python
squares = []
    for x in range(1, 11):
        square = x ** 2
        squares.append(square)
````

使用列表推导式，生成一个平方数的列表

````python
squares = [x**2 for x in range(1, 11)]
````

使用 for 循环，把列表中的小写字母转换成大写字母

````python
names = ['kai', 'abe', 'ada', 'gus', 'zoe']

upper_names = []
for name in names:
    upper_names = [name.append(name.upper())]
````

使用列表推导式，把列表中的小写字母转换成大写字母

````python
names = ['kai', 'abe', 'ada', 'gus', 'zoe']

upper_names = [name.upper() for name in names]
````

#### 元组 Tuples

> 元组类似于列表，只是一旦被定义后就不能改变元组中的值。所以在程序中，元组适合存储始终不变的信息。元组由括号而不是方括号来表示。（可以覆盖正噶元祖，但不能更改元组中的单个元素）

定义元组

````python
dimensions = (800, 600)
````

元组 for 循环

````python
for dimension in dimensions:
    print(dimensions)
````

重写覆盖元组

````python
dimensions = (800, 600)
print(dimensions)
dimensions = (1200, 900)
````

#### 代码运行可视化

> 当你第一次学习列表等数据结构时，他可以帮助你想象 Python 如何处理程序中的信息。pythontutor.com 是查看Python 如何跟踪列表中信息的好工具。尝试在 pythontutor.com 上运行以下代码，然后运行你自己的代码。

创建一个列表，打印出列表中的元素。

````python
dogs = []
dogs.append('willie')
dogs.append('hootz')
dogs.append('peso')
dogs.append('goblin')

for dog in dogs:
    print("Hello " + dog + "!")
print("I love these dogs!")

print("\nThese were my first two dogs:")
old_dogs = dogs[:2]
for old_dog in old_dogs:
    print(old_dog)

del dogs[0]
dogs.remove('peso')
print(dogs)
````

#### 代码风格

* 一个缩进使用四个空格
* 每行最多79个字符，或者更少
* 使用一个空白行把程序分段，视觉上更易阅读