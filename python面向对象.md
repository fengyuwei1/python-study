# python面向对象

## 1初识对象

### 1.1使用对象组织数据

面向对象编程是一种通过对象的方式组织代码的编程范式。Python 是一种面向对象的编程语言，OOP 主要涉及类和对象的概念。

类是创建对象的蓝图。类可以包含属性（数据）和方法（行为）。以下是定义一个简单类的例子：

```python
class student:
    name = None
stu1 = student()
stu1.name = 1
print(stu1.name)
```

## 1.2成员变量和成员方法

### 1.2.1类的定义和使用

在 Python 中，使用 `class` 关键字定义类。类名通常采用首字母大写的方式。

```py
class MyClass:
    # 定义属性
    def __init__(self, attribute1, attribute2):
        self.attribute1 = attribute1
        self.attribute2 = attribute2
    
    # 定义方法
    def display_attributes(self):
        print(f"Attribute 1: {self.attribute1}, Attribute 2: {self.attribute2}")
```

**解释：**

- `__init__` 方法是类的构造函数，在创建类的实例时自动调用，用于初始化实例的属性。
- `self` 是类实例的引用，用于访问实例的属性和方法。

### 1.2.2成员方法的定义语法

在 Python 中，成员方法（即类方法）的定义语法与普通函数类似，但在类的内部定义，并且第一个参数通常是 `self`，用于引用类的实例。下面是成员方法的定义语法及说明。

Python 中的类成员方法主要有三种：实例方法、类方法和静态方法。

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

**类**是一个用于定义对象的模板或蓝图。它封装了对象的属性（数据）和行为（方法）。在 Python 中，使用 `class` 关键字定义类。类通常包含构造方法 `__init__` 和其他成员方法，用于定义该类的行为。

**对象**是类的实例。每个对象都包含特定于该实例的数据，并可以调用类中定义的方法。在创建对象时，Python 会自动调用类的构造方法 `__init__` 进行初始化。

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

**构造方法**（Constructor）是类的一种特殊方法，在创建类的对象时自动调用，用于初始化对象的属性。Python 中的构造方法使用 `__init__` 进行定义。

构造方法注意事项

**1. `self` 参数**

- **`self` 必须是第一个参数**：构造方法的第一个参数必须是 `self`，这是类的实例对象的引用，使得对象可以访问它的属性和方法。
- `self` 不是关键字，可以用其他名称替换，但不建议这样做，因为 `self` 是通用约定，便于代码的可读性和理解。

**2. 不要返回任何值**

- 构造方法 **不能显式返回任何值**，例如 `return something`，即使是 `return None` 也不能写。Python 的构造方法隐式返回新创建的对象。
- 任何带 `return` 的构造方法会导致运行时错误。

**3. 避免在构造方法中定义类属性**

- **区分类属性和实例属性**：构造方法中定义的属性应是实例属性（特定对象独有的属性），而不是类属性。
- 使用 `self.attribute` 来定义实例属性，而类属性应在类外定义，避免所有实例共享属性的情况。

**4. 使用默认参数**

- **构造方法的参数可以有默认值**，这样可以在实例化对象时省略某些参数，增加代码的灵活性。

**5. 避免在构造方法中定义复杂的逻辑**

- 构造方法应只做对象的初始化，避免过于复杂的逻辑，以提高代码的可读性。
- 如果需要复杂的初始化过程，考虑将其分解到类中的其他方法。

**6. `__init__` 的重载**

- Python 不支持传统的构造方法重载，即同一个类中不能定义多个 `__init__` 方法。但可以通过设置参数的默认值、使用可变参数 `*args` 和 `**kwargs` 来实现类似重载的效果。

**7. 避免循环调用**

- 如果使用了继承，确保子类的构造方法正确调用父类的构造方法，避免引起无限递归的错误。
- 使用 `super()` 函数来调用父类的 `__init__` 方法，而不是直接调用类名（可能引发混乱）。

**8. 避免在 `__init__` 中使用未定义的外部变量**

- 确保在构造方法中使用的所有变量都是方法参数、局部变量、或类属性，避免依赖外部未定义的变量，增加代码的稳健性。

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

**魔术方法**（Magic Methods）是 Python 中内置的特殊方法，用于实现对象的特殊行为，比如运算符重载、对象打印格式等。这些方法通常以双下划线开头和结尾（例如 `__init__`、`__str__`），也被称为“dunder（double underscore）”方法。

### 2.`__str__字符串方法`

`__str__()`方法可以改变对象的字符串显示。在打印某个对象的时候，会调用这个对象的`__str__`方法，打印这个方法的返回值。

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

`__lt__` 是 Python 中用于支持小于符号 `<` 比较的魔术方法。这个方法允许我们定义自定义类的实例在使用 `<` 比较时的行为，例如比较实例属性的大小。`__lt__` 方法接受两个参数：`self`（当前对象）和 `other`（用于比较的对象），并返回一个布尔值，表示 `self < other` 是否为真。

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

`__le__` 是 Python 中的魔术方法，用于定义自定义类在使用小于等于符号 `<=` 时的行为。它的全称是 “less than or equal to”，即“小于等于”。这个方法允许我们在类中定义自定义对象实例的“小于等于”比较规则。

示例：

```py
def __le__(self, other):
    # 返回 True 或 False
```

### 5.`__eq__比较运算符`

说到__eq__()魔法方法，就必须提到Python中的is和==。先来看看这两者的区别：

is 比较两个对象的 id 值是否相等，是否指向同一个内存地址；
== 比较的是两个对象的内容是否相等，即内存地址可以不一样，内容一样就可以了。
==在比较类时，会默认调用object.__eq__方法，默认比较两个对象的地址（id）。

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

在面向对象编程中，**封装**是一种重要的思想。封装的核心是将对象的状态（属性）和行为（方法）封装在一起，通过隐藏内部细节、限制直接访问，实现数据保护和模块化，方便用户操作。

### 1.封装的核心概念

1. **隐藏内部数据**：将类的内部数据设为私有，以防止外部代码直接修改，从而保护数据的完整性。
2. **通过方法访问数据**：提供公有（public）的方法来获取或设置内部数据，使得类内部实现细节可以灵活改变，而不会影响外部代码。
3. **模块化设计**：封装有助于将代码模块化，方便管理和维护，同时提高了代码的可读性和可扩展性。

### 2.私有成员

在 Python 中，我们通过前缀下划线 `_` 或双下划线 `__` 来设置私有属性或方法。

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

私有成员的实际意义：

在类中提供仅供内部使用的属性和方法，而不对外开放(类对象无法使用)

## 1.7继承

**继承**是面向对象编程中的一个核心特性，允许一个类（子类）从另一个类（父类或基类）获取属性和方法。继承的主要目的是重用代码，提高代码的可读性和可维护性，并使得程序结构更加清晰。

**继承的基本概念**

1. **父类（基类）**：提供属性和方法的类。
2. **子类（派生类）**：从父类继承属性和方法的类。
3. **继承关系**：子类可以访问和使用父类的公有（public）和保护（protected）成员，但不能直接访问私有（private）成员。

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

- 单继承指的是一个类只继承一个父类。子类可以重用父类的属性和方法。
- 多继承指的是一个类可以继承多个父类，从而获得所有父类的属性和方法。这在某些情况下非常有用，但也可能导致复杂性增加，比如遇到方法解析顺序（MRO）问题。

同名属性和方法，谁先来谁优先级高

### 1.7.3复写和使用父类成员

#### 1.复写

在Python中，子类可以重写父类的同名方法和属性。这意味着子类可以提供自己的实现来覆盖父类中的方法和属性。这样可以使得子类具有独特的行为，同时保留与父类的接口一致性。

重写方法：当子类重写父类的方法时，子类的方法会覆盖父类的方法。在调用该方法时，将执行子类的实现。
重写属性：当子类重写父类的属性时，子类中的属性将覆盖父类中的同名属性

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

在 Python 中，可以使用 `super()` 函数来调用父类的同名方法，也可以直接使用父类名称调用其方法或属性。

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

## 1.9多态

### 1.9.1多态

在 Python 中，多态是一种对象在多种情境下表现不同形式的能力，它允许不同类的对象使用相同的接口。Python 的多态特性体现在动态类型和方法重写等方面。以下是 Python 中实现多态的主要方式。

#### 1. 方法重写与动态类型

在 Python 中，不需要显式声明类型，因此多态可以自然地通过继承和方法重写来实现。子类可以继承父类并重写父类的方法，而使用该父类的对象可以调用不同的子类方法。

```py
class Animal:
    def sound(self):
        return "Some generic sound"

class Dog(Animal):
    def sound(self):
        return "Woof"

class Cat(Animal):
    def sound(self):
        return "Meow"

def make_sound(animal: Animal):
    print(animal.sound())

dog = Dog()
cat = Cat()

make_sound(dog)  # 输出：Woof
make_sound(cat)  # 输出：Meow
```

在这个例子中，`make_sound()` 函数不需要知道传入的是 `Dog` 还是 `Cat`，只要对象实现了 `sound()` 方法，函数就可以调用它。这种方式可以让代码更具灵活性和扩展性。

#### 2. Duck Typing（鸭子类型）

Python 中的多态依赖于鸭子类型的概念，即“如果一个对象看起来像鸭子、叫起来像鸭子，那么它就是鸭子”。在 Python 中，对象不需要继承同一个基类或实现接口，只要具有相同的方法名称，就可以在相同的上下文中使用。

```py
class Bird:
    def fly(self):
        print("Bird flies high in the sky")

class Plane:
    def fly(self):
        print("Plane flies across the continents")

def take_off(entity):
    entity.fly()

bird = Bird()
plane = Plane()

take_off(bird)   # 输出：Bird flies high in the sky
take_off(plane)  # 输出：Plane flies across the continents
```

在这个例子中，`take_off()` 函数不关心传入的 `entity` 是 `Bird` 还是 `Plane`，只要 `entity` 实现了 `fly()` 方法，它就可以被传入并使用。这种松散的类型系统使得 Python 多态非常灵活。

#### 3. 抽象基类实现多态

虽然 Python 不强制要求接口和类型检查，但在复杂项目中，使用抽象基类（`abc` 模块）可以定义接口来实现多态。这使得代码更具结构性，且更加规范。

```py
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

def print_area(shape: Shape):
    print(f"The area is: {shape.area()}")

circle = Circle(5)
rectangle = Rectangle(4, 6)

print_area(circle)     # 输出：The area is: 78.5
print_area(rectangle)  # 输出：The area is: 24
```

在这个例子中，`Shape` 是一个抽象基类，`Circle` 和 `Rectangle` 继承了 `Shape`，并实现了 `area()` 方法。`print_area()` 函数可以处理任何 `Shape` 类型的对象，从而实现了多态。

### 1.9.2抽象类(接口)

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

