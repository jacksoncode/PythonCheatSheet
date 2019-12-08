# 类Class

#### 什么是类？

> 类是面向对象编程的基础。类代表你想要在程序中建模的真实世界的东西：例如狗，汽车和机器人。你使用一个类来制作对象，这些对象是狗，汽车和机器人的特定实例（比如牧羊犬，大众 polo，和变形金刚）。 类定义了整个类别的对象可以拥有的共同行为以及可以与这些对象相关联的信息。
> 类可以相互继承：你可以编写一个扩展现有类功能的类。这样就可以针对多种情况进行高效的编程。

#### 创建并使用类

Car 类

````py
class Car():
    """A simple attempt to model a car."""

    def __init__(self, make, model, year):
        """Initialize car attributes."""
        self.make = make
        self.model = model
        self.year = year

        # Fuel capacity and level in gallons.
        self.fuel_capacity = 15
        self.fuel_level = 0

    def fill_tank(self):
        """Fill gas tank to capacity."""
        self.fuel_level = self.fuel_capacity
        print("Fuel tank is full.")

    def drive(self):
        """Simulate driving."""
        print("The car is moving.")
````

创建一个类的对象

````py
my_car = Car('audi', 'a4', 2016)
````

访问属性值

````py
print(my_car.make)
print(my_car.model)
print(my_car.year)
````

调用方法

````py
my_car.fill_tank()
my_car.drive()
````

创建多个对象

````py
my_car = Car('audi', 'a4', 2016)
my_old_car = Car('subaru', 'outback', 2013)
my_truck = Car('toyota', 'tacoma', 2010)
````

#### 修改属性

> 可以直接修改属性的值，或者编写方法更好的管理属性的值。
 
直接修改属性的值

````py
my_new_car = Car('audi', 'a4', 2016)
my_new_car.fuel_level = 5
````

写一个方法更新属性值

````py
def update_fuel_level(self, new_level):
    """Update the fuel level."""
    if new_level <= self.fuel_capacity:
        self.fuel_level = new_level
    else:
        print("The tank can't hold that much!")
````

写一个方法增加属性值

````py
def add_fuel(self, amount):
    """Add fuel to the tank."""
    if (self.fuel_level + amount
        <= self.fuel_capacity):
        self.fuel_level += amount
        print("Added fuel.")
    else:
        print("The tank won't hold that much.")
````

#### 命名规则

> 在 Python 中，类名称是用 CamelCase 写的，而对象名称用小写字母和下划线写的。包含类的模块仍应以小写字和下划线命名。

#### 类的继承

> 如果你要写的类是另一个类的制定版本，则可以使用继承。当一个类从另一个类继承时，它会自动接受父类的所有属性和方法。子类可以自由引入新的属性和方法，并覆盖父类的属性和方法。定义新类时，要从另一个类继承，请在括号中写上父类的名称。

子类的_init _()方法

````py
class ElectricCar(Car):
    """A simple model of an electric car."""

    def __init__(self, make, model, year):
        """Initialize an electric car."""
        super().__init__(make, model, year)

        # Attributes specific to electric cars.
        # Battery capacity in kWh.
        self.battery_size = 70
        # Charge level in %.
        self.charge_level = 0
````

向子类中添加新的方法

````py
class ElectricCar(Car):
    --snip--
    def charge(self):
        """Fully charge the vehicle."""
        self.charge_level = 100
        print("The vehicle is fully charged.")
````

使用子类和父类方法

````py
my_ecar = ElectricCar('tesla', 'model s', 2016)
my_ecar.charge()
my_ecar.drive()
````

#### 找到自己的方法

> 有许多方法可以用代码模拟真实世界的对象和情况，有时候方法太多也会让人感到压力。 那就选择一种方法并尝试 - 如果你的第一次尝试不起作用，请尝试不同的方法。

#### 类的继承

覆盖父类

````py
class ElectricCar(Car):
    --snip--
    def fill_tank(self):
        """Display an error message."""
        print("This car has no fuel tank!")
````

#### 实例为属性

Battery 类

````py
class Battery():
    """A battery for an electric car."""

    def __init__(self, size=70):
        """Initialize battery attributes."""
        # Capacity in kWh, charge level in %.
        self.size = size
        self.charge_level = 0

    def get_range(self):
        """Return the battery's range."""
        if self.size == 70:
            return 240
        elif self.size == 85:
            return 270
````

使用实例作为属性

````py
class ElectricCar(Car):
    --snip--

    def __init__(self, make, model, year):
        """Initialize an electric car."""
        super().__init__(make, model, year)

        # Attribute specific to electric cars.
        self.battery = Battery()

    def charge(self):
        """Fully charge the vehicle."""
        self.battery.charge_level = 100
        print("The vehicle is fully charged.")
````

使用实例

````py
my_ecar = ElectricCar('tesla', 'model x', 2016)

my_ecar.charge()
print(my_ecar.battery.get_range())
my_ecar.drive()
````

#### 导入类

> 在添加详细信息和函数时，类文件可能会变得很长。 为了保持程序文件的整洁，可以将类先存储在模块中，然后将模块导入到主程序中。

在文件 car.py 中存储类

````py
"""Represent gas and electric cars."""

class Car():
    """A simple attempt to model a car."""
    --snip--

class Battery():
    """A battery for an electric car."""
    --snip—

class ElectricCar(Car):
    """A simple model of an electric car."""
    --snip--
````

从模块 car.py 中导入各个类

````py
from car import Car, ElectricCar

my_beetle = Car('volkswagen', 'beetle', 2016)
my_beetle.fill_tank()
my_beetle.drive()

my_tesla = ElectricCar('tesla', 'model s', 2016)
my_tesla.charge()
my_tesla.drive()
````

导入整个模块

````py
import car

my_beetle = car.Car('volkswagen', 'beetle', 2016)
my_beetle.fill_tank()
my_beetle.drive()

my_tesla = car.ElectricCar('tesla', 'model s', 2016)
my_tesla.charge()
my_tesla.drive()
````

导入模块的所有类
（ 不要这样做，看到的时候知道是什么就可以了）

````py
from car import *

my_beetle = Car('volkswagen', 'beetle', 2016)
````

#### Python2.7类

类是从对象继承来的

````py
class ClassName(object):
````

Car class

````py
class Car(object):
````

子类的_init_()方法是不一样的

````py
class ChildClassName(ParentClass):
    def __init__(self):
        super(ClassName, self).__init__()
````

ElectricCar class

````py
class ElectricCar(Car):
    def __init__(self, make, model, year):
        super(ElectricCar, self).__init__(
            make, model, year)
````

#### 列表中存储对象

> 一个列表可以容纳任意数量的元素，因此你可以从一个类中创建大量对象并将它们存储在一个列表中。
> 下面是一个示例，展示如何创建一系列 rental cars，并确保所有car 都已准备好开车。

一系列 rental cars

````py
from car import Car, ElectricCar

# Make lists to hold a fleet of cars.
gas_fleet = []
electric_fleet = []

# Make 500 gas cars and 250 electric cars.
for _ in range(500):
    car = Car('ford', 'focus', 2016)
    gas_fleet.append(car)
for _ in range(250):
    ecar = ElectricCar('nissan', 'leaf', 2016)
    electric_fleet.append(ecar)

# Fill the gas cars, and charge electric cars.
for car in gas_fleet:
    car.fill_tank()
for ecar in electric_fleet:
    ecar.charge()

print("Gas cars:", len(gas_fleet))
print("Electric cars:", len(electric_fleet))
````
