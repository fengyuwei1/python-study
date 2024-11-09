# python面向对象

## 1初识对象

### 1.1使用对象组织数据

![image-20240528144345317](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528144345317.png)

示例：

```python
class student:
    name = None
stu1 = student()
stu1.name = 1
print(stu1.name)
```

## 1.2成员变量和成员方法

### 1.2.1类的定义和使用

![image-20240528145400700](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528145400700.png)

![image-20240528150041561](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528150041561.png)

### 1.2.2成员方法的定义语法

![image-20240528150309029](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528150309029.png)

![image-20240528150423461](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528150423461.png)

示例：

```py
class student:
    name = None
    age = None
    def say_hello(self):
        print(f'Hello {self.name}')
stu = student()
stu.name = 'ab'
stu.say_hello()
stu1 = student()
stu1.name = 'adw'
stu1.say_hello()
```

## 1.3类和对象

![image-20240528153651490](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528153651490.png)

示例：

```python
class clock:
    id = None
    price = None

    def ring(self):
        import winsound
        winsound.Beep(2000,3000)
clock1 = clock()
clock1.id = "003032"
clock1.price = 1000
print(f'{clock1.id}: {clock1.price}')
clock1.ring()
```

### 1.3.1实例属性

在Python面向对象编程中，实例属性是指绑定到具体实例对象上的属性，而不是绑定到类本身的属性。每个实例对象可以有不同的属性值。下面是一些关于实例属性的详细说明和示例。

```python
class Person:
    def __init__(self, name, age):
        # 实例属性
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")

# 创建实例对象
person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

# 访问实例属性
print(person1.name)  # 输出: Alice
print(person1.age)   # 输出: 30

print(person2.name)  # 输出: Bob
print(person2.age)   # 输出: 25

# 调用方法
person1.greet()  # 输出: Hello, my name is Alice and I am 30 years old.
person2.greet()  # 输出: Hello, my name is Bob and I am 25 years old.

```

可以直接访问和修改实例属性。

可以使用`del`关键字删除实例属性。

如：

```python
del person1.age
# 试图访问已删除的属性将引发AttributeError
try:
    print(person1.age)
except AttributeError as e:
    print(e)  # 输出: 'Person' object has no attribute 'age'

```

### 1.3.2区别类属性

类属性是绑定到类本身的属性，而实例属性是绑定到实例对象的属性。类属性在所有实例之间共享，而实例属性在每个实例之间独立。

```python
class Person:
    species = "Homo sapiens"  # 类属性

    def __init__(self, name, age):
        self.name = name  # 实例属性
        self.age = age    # 实例属性

# 创建实例对象
person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

# 访问类属性
print(person1.species)  # 输出: Homo sapiens
print(person2.species)  # 输出: Homo sapiens

# 修改类属性
Person.species = "Homo erectus"
print(person1.species)  # 输出: Homo erectus
print(person2.species)  # 输出: Homo erectus

# 修改实例属性
person1.species = "Homo neanderthalensis"
print(person1.species)  # 输出: Homo neanderthalensis
print(person2.species)  # 输出: Homo erectus
print(Person.species)   # 输出: Homo erectus

```

实例属性可以通过方法来访问和修改，以确保封装性和数据完整性

```python
class Person:
    def __init__(self, name, age):
        self.__name = name  # 私有实例属性
        self.__age = age    # 私有实例属性

    def get_name(self):
        return self.__name

    def set_name(self, name):
        self.__name = name

    def get_age(self):
        return self.__age

    def set_age(self, age):
        if age > 0:
            self.__age = age
        else:
            print("Age must be positive")

# 创建实例对象
person = Person("Alice", 30)

# 通过方法访问实例属性
print(person.get_name())  # 输出: Alice
print(person.get_age())   # 输出: 30

# 通过方法修改实例属性
person.set_name("Bob")
person.set_age(25)
print(person.get_name())  # 输出: Bob
print(person.get_age())   # 输出: 25

```

在 Python 中，使用单下划线 `_` 和双下划线 `__` 来表示属性的访问控制：

- **单下划线 `_`** 表示属性是**内部的**，但可以被访问（是一种约定，不是真正的私有）。
- **双下划线 `__`** 将属性或方法**真正私有化**，外部无法直接访问。

## 1.4构造方法

![image-20240528154051641](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528154051641.png)

构造方法注意事项

![image-20240528155000450](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528155000450.png)

```python
class Person:
    name = None
    age = None
    tel = None
    def __init__(self, name,age,tel):
        self.name = name
        self.age = age
        self.tel = tel
stu = Person("abcd",20,"123456")
print(stu.name,stu.age,stu.tel)
```

### 1.4.1实例方法

实例方法是与实例对象相关的方法，可以访问和修改实例属性。它们是最常见的方法类型。

#### 定义和使用

- **定义**：实例方法的第一个参数必须是`self`，它指向调用该方法的实例对象。
- **使用**：实例方法通过实例对象调用，能够访问该实例的属性和其他方法。

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")

# 创建实例对象
person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

# 调用实例方法
person1.greet()  # 输出: Hello, my name is Alice and I am 30 years old.
person2.greet()  # 输出: Hello, my name is Bob and I am 25 years old.

```

### 1.4.2类方法

类方法是与类相关的方法，而不是与实例对象相关。它们通常用于操作类属性或者执行与类本身相关的操作。

**类方法**：

- 第一个参数是 `cls`，表示类本身。
- 只能访问类属性，不能访问实例属性。
- 可以通过类或实例调用。

#### 定义和使用

- **定义**：类方法使用`@classmethod`装饰器，方法的第一个参数必须是`cls`，它指向类本身。
- **使用**：类方法可以通过类或者实例对象调用，但通常通过类调用。

```python
class Person:
    species = "Homo sapiens"  # 类属性

    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def set_species(cls, species):
        cls.species = species

    @classmethod
    def get_species(cls):
        return cls.species

# 调用类方法
Person.set_species("Homo erectus")
print(Person.get_species())  # 输出: Homo erectus

# 通过实例对象调用类方法
person = Person("Alice", 30)
person.set_species("Homo neanderthalensis")
print(person.get_species())  # 输出: Homo neanderthalensis
print(Person.get_species())  # 输出: Homo neanderthalensis

```

### 1.4.3静态方法

静态方法是一种不需要访问实例或类属性的方法。它们主要用于在类的上下文中组织功能性的代码，类似于类的普通函数。静态方法使用`@staticmethod`装饰器进行定义。

### 静态方法的特点

- **无绑定**：静态方法不绑定到实例或类，因此它们不接受`self`或`cls`参数。
- **独立性**：静态方法不能访问实例属性或类属性，它们完全独立于类的实例和类本身。
- **调用方式**：静态方法可以通过类或实例调用，但通常通过类调用。

### 定义和使用

#### 定义静态方法

静态方法使用`@staticmethod`装饰器定义。它们不需要接受实例（`self`）或类（`cls`）参数。

```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

    @staticmethod
    def multiply(a, b):
        return a * b

# 调用静态方法
result_add = MathUtils.add(3, 5)
result_multiply = MathUtils.multiply(4, 6)

print(f"Addition: {result_add}")        # 输出: Addition: 8
print(f"Multiplication: {result_multiply}")  # 输出: Multiplication: 24

# 通过实例调用静态方法
math_utils = MathUtils()
result_add_instance = math_utils.add(10, 20)
print(f"Addition (via instance): {result_add_instance}")  # 输出: Addition (via instance): 30

```



## 1.5其他内置方法

### 1.魔术方法

![image-20240528192637157](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528192637157.png)

### 2.`__str__字符串方法`

![image-20240528193208993](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528193208993.png)

示例：

```python
class student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self):
        return f'{self.name} {self.age}'

stu = student("abab",31)
print(stu)
print(str(stu))
```

### 3.`__lt__小于符号的比较`

![image-20240528193758111](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528193758111.png)

示例：

```py
class student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __lt__(self, other):
        return self.age < other.age
stu1 = student("abab",31)
stu2 = student("abb",32)
print(stu1<stu2)
```

### 4.`__le__小于等于比较符方法`

![image-20240528194118401](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528194118401.png)

### 5.`__eq__比较运算符`

![image-20240528194339720](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528194339720.png)

示例：

```py
class student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __eq__(self, other):
        return self.name == other.name and self.age == other.age
st1 = student("abab",31)
st2 = student("abb",32)
print(st1 == st2)
```

##  1.6封装

![image-20240528195032908](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528195032908.png)

 

### 1.私有成员

![image-20240528195408192](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528195408192.png)

示例：

```python
class phone:
    __current_voltage = None

    def __keep_single_core(self):
        print("让CPU以单核模式运行")
phone = phone()
phone.__keep_single_core()
print(phone.__current_voltage)
```

私有成员无法被类对象使用，但是可以被其他成员使用

示例：

![image-20240528200318845](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528200318845.png)

私有成员的实际意义：

在类中提供仅供内部使用的属性和方法，而不对外开放(类对象无法使用)

## 1.7继承

![image-20240528201736367](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528201736367.png)

### 1.7.1单继承

```python
class phone:
    IMEI = None
    producer = "HM"

    def call_by_4g(self):
        print("4g通话")
class phone2022(phone):
    face_id = "10001"
    def call_by_5g(self):
        print("2022年新功能:5g通话")
phone = phone2022()
print(phone2022.IMEI)
```

### 1.7.2多继承

![image-20240528202419566](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528202419566.png)

多继承的注意事项：

![image-20240528202748207](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528202748207.png)

![image-20240528202809654](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528202809654.png)

同名属性和方法，谁先来谁优先级高

### 1.7.3复写和使用父类成员

#### 1.复写

![image-20240528203239195](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528203239195.png)

```py
class phone:
    IMEI = None
    producer = "HM"

    def call_by_4g(self):
        print("4g通话")
# 定义子类，复写父类成员
class myphone(phone):
    producer = "ITHEIMA"
    def call_by_4g(self):
        print("开启CPU单核模式，确保通话的时候省电")
        print("4g通话")
```

#### 2.调用父类的同名成员

![image-20240528203822228](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528203822228.png)

```py
class phone:
    IMEI = None
    producer = "HM"

    def call_by_4g(self):
        print("4g通话")
class myphone(phone):
    producer = "ITHEIMA"
    def call_by_4g(self):
        print("开启CPU单核模式，确保通话的时候省电")
        super().phone.call_by_4g(self)
phone = myphone()
my_phone.call_by_4g()
print(phone.producer)
```

## 1.8类型注解

### 1.8.1变量的类型注解

![image-20240528210345865](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528210345865.png)

类型注解的语法：

![image-20240528211057038](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528211057038.png)

 ![image-20240528211746528](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528211746528.png)

只是对程序的标记，即使标记错误也没有问题

### 1.8.2函数的类型注解

#### 1.形参注解

![image-20240528223842966](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528223842966.png)

![image-20240528223949441](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528223949441.png)

#### 2.返回值注解

![image-20240528224104039](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528224104039.png)

也是提示性的，不是决定性的

### 1.8.3Union

#### 1.Union类型

![image-20240528225132286](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528225132286.png)

![image-20240528232021965](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528232021965.png)

## 1.9多态

### 1.9.1多态

![image-20240528232635162](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528232635162.png)

![image-20240528234345437](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528234345437.png)

![image-20240528234607179](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528234607179.png)

### 1.9.2抽象类(接口)

![image-20240528234738079](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240528234738079.png)

**抽象**是将对象的复杂性隐藏起来，仅显示必要的部分。在 Python 中，抽象可以通过定义抽象类和抽象方法来实现。抽象类不能被实例化，必须通过继承来实现其中的抽象方法。

Python 提供了 `abc` 模块来支持抽象类：

```py
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * (self.radius ** 2)
```

