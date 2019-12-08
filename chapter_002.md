# 字典Dictionaries

#### 什么是字典

Python的字典可以让你存储一对有关联的信息。字典中的每条信息都存储为一个键值对key-value。当你提供键（key）时，Python会返回与该键匹配的值（value）。你可以遍历所有的键值对，或所有键，或所有值。

#### 定义字典

> 使用大括号{}来定义字典。使用冒号来连接键和值，并使用逗号分隔开键值对。

创建一个字典

````python
alien_0 = {'color': 'green', 'points': 5}
````

#### 访问值

> 要想访问字典中的一个值value，首先给出与值匹配的键的名称，然后把该键放在[]中，如果你想放置的键不在这个字典中，那就会出现错误。
> 也可以使用 get()函数来访问值，如果是不存在的键，该函数会返回一个空值None，或返回一个事先设定的值。

使用 key 来访问value

````python
alien_0 = {'color': 'green', 'points': 5}

print(alien_0['color'])
print(alien_0['points'])
````

使用 get() 访问 value

````python
alien_0 = {'color': 'green'}

alien_color = alien_0.get('color')
alien_points = alien_0.get('points')

print(alien_color)
print(alien_points)
````

#### 添加新的键值对

> 只要电脑内存足够，就可以在字典里存储尽可能多的键值对。如何在字典中添加新的键值对？首先写出字典的名称，然后把新的键 key 放在方括号里，并将其等于新的值 value。
> 如果字典是空的，也可以这样来添加新的键值对。

增加一个键值对

````python
alien_0 = {'color': 'green', 'point': 5}
alien_0['x'] = 0
alien_0['y'] = 25
alien_0['speed'] = 1.5
````

向空字典中增加键值对

````python
alien_0 = {}
alien_0['color'] = 'green'
alien_0['point'] = 5
````

#### 修改值

> 字典中的任何值都可以进行修改，只需要知道与该值配对的键的名称，然后把这个键放在方括号中，最后赋予新的值。

修改字典里的值

````python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

# Change the alien's color and point value.
alien_0['color'] = 'yellow'
alien_0['points'] = 10
print(alien_0)
````

#### 删除键值对

> 字典中的任何键值对都可以被删除，使用 del 关键字和字典名称，最后把键的名称放在方括号中，这样就可以删除这个键值对。

删除一个键值对

````python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
del alien_0['points']
print(alien_0)
````

#### 字典可视化

登录pythontutor.com，再看看字典如何在程序中运行的。

#### 遍历字典

> 有三种遍历字典的方法：遍历所有键值对，遍历所有键，遍历所有值。
> 字典只能标记处键值对中键与值的匹配关系，而不能标记字典中的键值对顺序。如果想按顺序处理元素，需要在循环中对键进行排序。

遍历所有的键值对

````python
# Store people's favorite languages.
fav_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python'
    }

# Show each person's favorite language.
for name, language in fav_languages.items():
    print(name + ": " + language)
````

遍历所有的键

````python
# Show everyone who's taken the survey.
for name in fav_languages.key():
    print(name)
````

遍历所有的值

````python
# Show all the languages thathave been chosen.
for language in fav_languages.values():
    print(language)
````

按照顺序遍历所有的键

````python
# Show each person's favorite language,
# in order by the person's name.
for name in stored(fav_languages.keys()):
    print(name + ": " + language)
````

#### 字典长度

> 使用 len() 函数可以得出字典的长度（键值对的个数）。

求字典长度

````python
num_responses = len(fav_languages)
````

#### 嵌套——字典嵌套在列表中

> 在列表中存储一系列字典，成为嵌套 nesting

列表中存储字典

````python
# Start with an empty list.
users = []
# Make a new user, and add them to the list.
new_user = {
    'last': 'fermi',
    'first': 'enrico',
    'username': 'efermi',
    }
users.append(new_user)
# Make another new user, and add them as well.
new_user = {
    'last': 'curie',
    'first': 'marie',
    'username': 'mcurie',
    }
users.append(new_user)
# Show all information about each user.
for user_dict in users:
    for k, v in user_dict.items():
        print(k + ": " + v)
    priint("\n")
````

不使用 append()，直接定义含字典的列表

````python
# Define a list of users, where each user
# is represented by a dictionary.
users = [
    {
        'last': 'fermi',
        'first': 'enrico',
        'username': 'efermi',
    },
    {
        'last': 'curie',
        'first': 'marie',
        'username': 'mcurie',
    },
]
# Show all information about each user.
for user_dict in users:
    for k, v in user_dict.items():
        print(k + ": " + v)
    print("\n")
````

#### 嵌套——列表嵌套在字典中

> 在字典中存储一系列列表，可以让一个键与多个值配对。

字典中存储列表

````python
# Store multiple languages for each person.
fav_languages = {
    'jen': ['python', 'ruby'],
    'sarah': ['c'],
    'edward': ['ruby', 'go'],
    'phil': ['python', 'haskell'],
}

# Show all responses for each person.
for name, langs in fav_languages.items():
    print(name + ": ")
    for lang in langs:
        print("- " + lang)
````

#### 嵌套——字典嵌套在字典中

> 可以在字典中存储字典，那么一个键就和一个字典匹配。

字典中存储字典

````python
users = {
    'aeinstein': {
        'first': 'albert','last': 'einstein',
        'location': 'princeton',},
    'mcurie': {
        'first': 'marie'， 'last': 'curie',
        'location': 'paris',},
    }
for username, user_dict in users.items():
    print("\nUsername: " + username)
    full_name = user_dict['first'] + " "
    full_name += user_dict['last']
    location = user_dict['location']
print("\tFull name: " + full_name.title())
print("\tLocation: " + location.title())
````

> 嵌套的使用情况下非常有用，不过嵌套会让程序看起来有点复杂，如果你定义的嵌套比刚才介绍的还要复杂，那你得注意了，有可能有更简单的方法来定义你的数据，比如类(class)。

#### 有序字典 OrderedDict

> 往字典中增加键值时，键值在字典中的位置是随机无序的，字典只保留键值本身的配对关系。如果想保留添加减值的顺序，需要用到 OrderedDict()函数。

保留添加键值的顺序

````python
from collections import OrderedDict

# Store each person's languages, keeping
# track of who respoded first.
fav_languages = OrderedDict()

fav_languages['jen'] = ['python', 'ruby']
fav_languages['sarah'] = ['c']
fav_languages['edward'] = ['ruby', 'go']
fav_languages['phil'] = ['python', 'haskell']

# Display the results, in the same order they
# were entered.
for name, langs in fav_languages.items():
    print(name + ":")
    for lang in langs:
        print("- " + lang)
````

#### 创建大量字典

> 如果字典的起始数据类似，可以使用循环很快的创建大量的字典。

大量外星人

````python
aliens = []

# Make a million green aliens, worth 5 points
# each. Have them all start in one row.
for alien_num in range(1000000):
    new_alien = {}
    new_alien['color'] = 'green'
    new_alien['points'] = 5
    new_alien['x'] = 20 * alien_num
    new_alien['y'] = 0
    aliens.append(new_alien)

# Prove the list contains a million aliens.
num_aliens = len(aliens)
print("Number of aliens created:")
print(num_aliens)
````
