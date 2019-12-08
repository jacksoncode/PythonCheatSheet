# 文件和异常

#### 什么是文件？什么是异常？

你的程序可以从文件中读取信息，也可以将数据写入文件。读取文件时，可以访问各种信息，把文本写入文件时，也可以把Python 结构体（如列表）存储在文件中。

异常是帮助程序以适当方式响应错误的特殊对策。例如，如果你的程序尝试打开不存在的文件时，可以使用异常来显示带有提示性的错误消息，而不是让程序崩溃。

#### 读取文件

> 要读取文件，程序需要先打开文件，然后读取文件的内容。你可以一次读取文件的全部内容，或者逐行读取文件。 with 语句确保在程序访问完文件后该文件已正确关闭。

一次读取文件的全部内容

````py
filename = 'siddhartha.txt'
with open(filename) as f_obj:
    contents = f_obj.read()

print(contents)
````

逐行读取

从文件中读取的每一行在行尾都有一个换行符，并且打印函数会添加它自己的换行符。 rstrip()方法消除了打印到终端时会产生的额外空白行。

````py
filename = 'siddhartha.txt'

with open(filename) as f_obj:
    for line in f_obj:
        print(line.rstrip())
````

把每行内容存储在列表中

````py
filename = 'siddhartha.txt'

with open(filename) as f_obj:
    lines = f_obj.readlines()

for line in lines:
    print(line.rstrip())
````

#### 写文件

> 将'w'参数传递给 open()可以告诉 Python 你想写入文件。注意了，如果文件已经存在，这将删除文件的内容。传递'a'参数告诉 Python 你想添加内容到现有文件的末尾。

向空文件写入

````py
filename = 'programming.txt'

with open(filename, 'w') as f:
    f.write("I love programming!")
````

向空文件中写入多行内容

````py
filename = 'programming.txt'

with open(filename, 'w') as f:
    f.write("I love programming!\n")
    f.write("I love creating new games.\n")
````

添加到文件末尾

````py
filename = 'programming.txt'

with open(filename, 'a') as f:
    f.write("I also love working with data.\n")
    f.write("I love making apps as well.\n")
````

#### 文件路径

> 当 Python 运行 open()函数时，执行的程序位于哪个文件夹下， open()函数就在哪个文件夹下查找文件。你可以使用相对路径从子文件夹打开文件。你也可以使用绝对路径打开系统上的任何文件。

从子文件夹中打开文件

````py
f_path = "text_files/alice.txt"
with open(f_path) as f_obj:
    lines = f_obj.readlines()

for line in lines:
    print(line.rstrip())
````

使用绝对路径打卡文件

````py
f_path = "/home/ehmatthes/books/alice.txt"

with open(f_path) as f_obj:
    lines = f_obj.readlines()
````

在 windows 中打开文件

Windows 有时会错误地编译正斜杠。如果遇到这种情况，请在文件路径中使用反斜杠。

````py
f_path = "C:\Users\ehmatthes\books\alice.txt"

with open(f_path) as f_obj:
    lines = f_obj.readlines()
````

#### try-except 异常处理

> 当你认为可能发生错误时，你可以编写 try-except 程序来处理可能引发的异常。 try 程序告诉 Python 尝试运行的代码，而except 程序告诉 Python 如果代码导致某种特定类型的错误该怎么做。

处理 ZeroDivisionError 异常

````py
try:
    print(5/0)
except ZeroDivisionError:
    print("You can't divide by zero!")
````

处理 FileNotFoundError 异常

````py
f_name = 'siddhartha.txt'

try:
    with open(f_name) as f_obj:
        lines = f_obj.readlines()
except FileNotFoundError:
    msg = "Can't find file {0}.".format(f_name)
    print(msg)
````

#### 知道要处理的是什么异常

> 写程序时很难知道处理什么样的异常。先试试在没有 try 的情况下编写代码，并使其生成错误。根据反馈的错误来找到需要处理什么样的异常。