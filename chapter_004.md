# 函数Functions

#### 什么是函数？

函数是用于执行一项特定工作的代码块。函数允许你编写一次代码，然后在需要完成相同任务时再次运行。函数可以接收它需要的信息，并返回它生成的信息。使用函数会让你的程序更高效，易于编写，读取，测试和修复。

#### 定义一个函数

> 函数的第一行是它的定义，用关键字 def 标记。该函数的名称后面跟着一组括号和一个冒号。文档字符串描述函数的功能，前后有三个双引号。函数的主体缩进一级。
> 要调用一个函数，给出函数的名字和后面的一组括号。

建立一个函数

````python
def greet_user():
    """Display a simple greeting."""
    print("Hello!")

greet_user()
````

#### 给函数传递信息

> 传递调用给函数的信息称为实参，实参可以是常量、变量、表达式、函数等. 由函数接收或定义的信息称为形参。实参包含在函数名称后面的圆括号中，形参列在函数定义的圆括号中。

传递单独的实参

````python
def greet_user(username):
    """Display a simple greeting."""
    print("Hello, " + username + "!")

greet_user('jesse')
greet_user('diana')
greet_user('brandon')
````

#### 位置和关键字实参

> 两种主要实参： 位置和关键字实参。当你使用位置实参时，Python 将调用函数中的第一个实参与函数定义中的第一个形参相匹配，以此类推。
> 使用关键字实参，可以在函数调用时，将指定的实参匹配给指定的形参。当你使用关键字实参时，实参的顺序无关紧要。

使用位置实参

````python
def describe_pet(animal, name):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet('hamster', 'harry')
describe_pet('dog', 'willie')
````

使用关键字实参

````py
def describe_pet(animal, name):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet(animal='hamster', name='harry')
describe_pet(name='willie', animal='dog')
````

#### 默认参数值

> 你可以为形参提供默认值。当函数调用忽略此实参时，将使用此默认值。具有默认值的形参位置必须在函数中没有默认值的形参之后，这样位置参数仍然可以正常工作。

使用默认参数值

````py
def describe_pet(name, animal='dog'):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    print("Its name is " + name + ".")

describe_pet('harry', 'hamster')
describe_pet('willie')
````

使用 None 值时实参可有可无

````py
def describe_pet(animal, name=None):
    """Display information about a pet."""
    print("\nI have a " + animal + ".")
    if name:
        print("Its name is " + name + ".")
describe_pet('hamster', 'harry')
describe_pet('snake')
````

#### 函数返回值

> 一个函数可以返回一个值或一组值。 当函数返回一个值时，调用行必须提供一个变量来存储返回值。 函数在到达 return 语句时停止运行。

返回一个值

其中 title() 方法返回"标题化"的字符串,就是说所有单词都是以大写开始

````py
def get_full_name(first, last):
    """Return a neatly formatted full name."""
    full_name = first + ' ' + last
    return full_name.title()

musician = get_full_name('jimi', 'hendrix')
print(musician)
````

返回一个字典

````py
def build_person(first, last):
    """Return a dictionary of information
    about a person.
    """
    person = {'first': first, 'last': last}
    return person

musician = build_person('jimi', 'hendrix')
print(musician)
````

返回一个字典，其中有些值为空

````py
def build_person(first, last, age=None):
    """Return a dictionary of information
    about a person.
    """
    person = {'first': first, 'last': last}
    if age:
        person['age'] = age
    return person

musician = build_person('jimi', 'hendrix', 27)
print(musician)

musician = build_person('janis', 'joplin')
print(musician)
````

#### 传递列表给函数

> 将列表作为参数传递给函数，并且函数可以使用列表中的值。函数对列表所做的任何更改都会影响原始列表。你可以通过传递列表副本作为参数来防止函数修改列表。

将列表作为参数传递

````py
def greet_users(names):
    """Print a simple greeting to everyone."""
    for name in names:
        msg = "Hello, " + name + "!"
        print(msg)

usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
````

允许函数修改列表

以下示例将 unprinted 和 printed 列表发送给函数打印。unprinted 列表被清空， printed 列表被填充。

````py
def print_models(unprinted, printed):
    """3d print a set of models."""
    while unprinted:
        current_model = unprinted.pop()
        print("Printing " + current_model)
        printed.append(current_model)

# Store some unprinted designs,
# and print each of them.
unprinted = ['phone case', 'pendant', 'ring']
printed = []
print_models(unprinted, printed)

print("\nUnprinted:", unprinted)
print("Printed:", printed)
````

防止函数修改列表
以下示例与前一个示例相同，只是在调用 print_models()后，unprinted 列表未更改。

````py
def print_models(unprinted, printed):
    """3d print a set of models."""
    while unprinted:
        current_model = unprinted.pop()
        print("Printing " + current_model)
        printed.append(current_model)

# Store some unprinted designs, and print each of them.
original = ['phone case', 'pendant', 'ring'] printed = []

print_models(original[:], printed)
print("\nOriginal:", original)
print("Printed:", printed)
````

#### 传递任意数量的实参

> 如果不知道函数要接受多少实参，那么在形参命名时，可以在形参名前加上*符号，表示该形参可以接受多个实参，带有*符号的形参必须放在其他形参的后面。
> ** 操作符允许形参接受多个关键字实参

传递任意数量的实参

````py
def make_pizza(size, *toppings):
    """Make a pizza."""
    print("\nMaking a " + size + " pizza.")
    print("Toppings:")
    for topping in toppings:
        print("- " + topping)

# Make three pizzas with different toppings.
make_pizza('small', 'pepperoni')
make_pizza('large', 'bacon bits', 'pineapple')
make_pizza('medium', 'mushrooms', 'peppers',
    'onions', 'extra cheese')
````

传递任意数量的关键字实参

````py
def build_profile(first, last, **user_info):
    """Build a user's profile dictionary."""
    # Build a dict with the required keys.
    profile = {'first': first, 'last': last}
    # Add any other keys and values.
    for key, value in user_info.items():
        profile[key] = value

    return profile

# Create two users with different kinds
# of information.
user_0 = build_profile('albert', 'einstein',
    location='princeton')
user_1 = build_profile('marie', 'curie',
    location='paris', field='chemistry')

print(user_0)
print(user_1)
````

#### 哪种方法写函数最好？

> 正如你所看到的，有很多方法来编写和调用一个函数。当你开始时，瞄准一些简单的工作。随着你获得经验，你将了解不同结构（如位置和关键字参数）以及导入函数的各种方法等更细微的优点。现在，如果你的函数满足你所需要的功能，说明你已经很不错了。

#### 模块化

> 你可以将函数存储在一个单独的文件中，该文件称为模块，若需要使用该函数，那就在主程序中导入该文件。这样会使得程序看起来更干净（确保你的模块和你的主程序存放在同一个目录中）。

在模块 File:pizza.py 中存储程序

````py
def make_pizza(size, *toppings):
    """Make a pizza."""
    print("\nMaking a " + size + " pizza.")
    print("Toppings:")
    for topping in toppings:
        print("- " + topping)
````

导入 File:pizza.py

模块中的每个函数在整个程序中都可以起作用

````py
import pizza

pizza.make_pizza('medium', 'pepperoni')
pizza.make_pizza('small', 'bacon', 'pineapple')
````

只导入特定的函数

只有导入的函数才在整个程序中起作用

格式为 from 文件名 inmport 文件中的函数名

````py
from pizza import make_pizza

make_pizza('medium', 'pepperoni')
make_pizza('small', 'bacon', 'pineapple')
````

给模块起个别名

as 后是别名，一般别名都是缩写

````py
from pizza import make_pizza as mp

mp('medium', 'pepperoni')
mp('small', 'bacon', 'pineapple')
````

导入模块中的所有函数

最好不要这样做，但是当你在别人的代码中看到它时你就会想到，这可能会导致命名冲突，进而产生错误。

````py
from pizza import *

make_pizza('medium', 'pepperoni')
make_pizza('small', 'bacon', 'pineapple')
````
