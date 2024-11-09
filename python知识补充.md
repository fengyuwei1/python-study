# python知识补充

## 1.小数点的读取

在 Python 中，可以使用几种方法来读取小数点后特定的位数。以下是一些常见的方法：

**1.使用字符串格式化**

```py
number = 3.14159265359
formatted_number = "{:.2f}".format(number)  # 保留两位小数
print(formatted_number)  # 输出: 3.14
```

**2.使用 f-字符串（Python 3.6 及以上）**

```py
number = 3.14159265359
formatted_number = f"{number:.2f}"  # 保留两位小数
print(formatted_number)  # 输出: 3.14
```

**3.使用 `round()` 函数**

```py
number = 3.14159265359
rounded_number = round(number, 2)  # 保留两位小数
print(rounded_number)  # 输出: 3.14
```

**4.使用%符号**

```py
a = 1.0
print("%.2f"%a)
```

## 2.进制转换

### 2.1 基本用法

```py
int(x=0, base=10)
```

#### 参数

1. **`x`**：可选参数，可以是：
   - 一个数字（如 `3.14`），则返回该数字的整数部分（向下取整）。
   - 一个字符串（如 `'123'`），表示要转换的数字。如果这个字符串表示的数是浮点数（如 `'3.14'`），则会引发错误。
   - 如果提供的是一个十六进制或其他进制的字符串，必须指定 `base`。
2. **`base`**：可选参数，用于指定字符串 `x` 的进制。可以是：
   - 2（用于二进制）
   - 8（用于八进制）
   - 10（用于十进制，默认值）
   - 16（用于十六进制）
   - 其他进制（范围在 2 到 36 之间）

返回 `x` 转换后的整数。如果输入无效（如尝试转换不合法的字符串），将引发 `ValueError`。

## 3.字符串

### 3.1 输出字符串的长度

```py
a = input()
print(len(a))
```

### 3.2 字符串大小写和首字母大写

```py
.lower() --- 全部小写
.upper() --- 全部大写
.title() --- 各个字符的首字母大写
.capitalize() --- 首字母大写
```

### 3.3 消除字符串的空格

```py
.strip() --- 删除两边空格
.lstrip() --- 删除左边空格
.rstrip() --- 删除右边空格
.replace(" ","") --- 删除所有空格
.split() --- 先切分，"".join() --- 再拼接
```

## 4.input的补充

在 Python 中，`input().split()` 结合多变量赋值是一种常见的方式，用来从用户输入中获取多个值并将它们赋值给多个变量。

**使用 `split()` 方法**

`split()` 是字符串对象的一个方法，默认会根据空白字符（空格、Tab、换行等）来拆分字符串，将其转换为一个由子字符串组成的列表。

例如：

```py
x, y, z = input("请输入三个值，并用空格分隔: ").split()
print(f"x = {x}, y = {y}, z = {z}")
```

## 5.字典里的zip函数

`zip()` 函数是 Python 中一个非常有用的内置函数，它用于将多个可迭代对象（如列表、元组、字符串等）“压缩”在一起，生成一个包含对应元素的元组的迭代器。

### 基本语法

```py
zip(*iterables)
```

`*iterables`: 表示任意数量的可迭代对象（如列表、元组、字符串等）。

### 功能

`zip()` 会将多个可迭代对象的对应位置的元素“打包”成一个个元组，返回一个迭代器。使用 `zip()` 可以很方便地同时迭代多个可迭代对象。

### 示例

1.**基本使用：将两个列表压缩在一起**

```py
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
zipped = zip(list1, list2)

print(list(zipped))  # 转换为列表后打印
```

2.**不同长度的可迭代对象** 如果传入的可迭代对象长度不同，`zip()` 会以最短的一个为准，只压缩到最短的那个可迭代对象为止。

3.**解压缩** 使用 `zip()` 的反向操作，可以解压列表或元组。通过将解压操作与星号（`*`）运算符结合使用，达到解压效果。

例如：

```py
zipped_list = [(1, 'a'), (2, 'b'), (3, 'c')]
list1, list2 = zip(*zipped_list)

print(list1)  # 输出 (1, 2, 3)
print(list2)  # 输出 ('a', 'b', 'c')
```

4.**用于同时迭代多个可迭代对象** `zip()` 常用于需要同时遍历两个或多个列表的场景。

5.**与 `dict` 一起使用** 你可以使用 `zip()` 将两个列表转换为字典，其中一个列表作为键，另一个列表作为值。

## 6.正则表达式

Python 中的正则表达式（Regular Expressions，简称 "regex" 或 "re"）通过内置的 `re` 模块来处理，允许你在字符串中执行复杂的搜索、匹配和替换操作。正则表达式使用特殊的语法来匹配字符串中的特定模式。

### 基本语法与 `re` 模块

首先，你需要导入 `re` 模块来使用正则表达式功能：

```py
import re
```

### 常用正则表达式函数

**`re.search(pattern, string)`**

- 在字符串中查找第一个匹配的子串，如果找到则返回一个匹配对象，否则返回 `None`。

示例：

```py
match = re.search(r'\d+', 'The year is 2024')
if match:
    print(match.group())  # 输出: 2024
```

**`re.match(pattern, string)`**

- 尝试从字符串的开头匹配指定的模式。如果匹配成功，则返回匹配对象；否则返回 `None`。注意，`match` 只在字符串的开始处匹配。

示例：

```py
match = re.match(r'\d+', '2024 is the year')
if match:
    print(match.group())  # 输出: 2024
```

**`re.findall(pattern, string)`**

- 返回字符串中所有与模式匹配的子串，返回的是一个列表。

示例：

```py
result = re.findall(r'\d+', 'There are 2 cats, 5 dogs, and 3 birds')
print(result)  # 输出: ['2', '5', '3']
```

**`re.sub(pattern, repl, string)`**

- 替换字符串中与模式匹配的部分，将其替换为指定的替换内容 `repl`，返回替换后的新字符串。

示例：

```py
result = re.sub(r'\d+', 'X', 'I have 2 apples and 5 oranges')
print(result)  # 输出: I have X apples and X oranges
```

**`re.split(pattern, string)`**

- 根据正则表达式中的模式拆分字符串，返回一个列表。

```py
result = re.split(r'\s+', 'Split this sentence into words')
print(result)  # 输出: ['Split', 'this', 'sentence', 'into', 'words']
```

### 常用的正则表达式符号

- **`.`**: 匹配任意字符，除了换行符。
- **`^`**: 匹配字符串的开头。
- **`$`**: 匹配字符串的结尾。
- **`\*`**: 匹配前面的元素 0 次或多次。
- **`+`**: 匹配前面的元素 1 次或多次。
- **`?`**: 匹配前面的元素 0 次或 1 次。
- **`\d`**: 匹配任何数字字符，相当于 `[0-9]`。
- **`\D`**: 匹配非数字字符。
- **`\w`**: 匹配任何字母数字字符（包括下划线），相当于 `[a-zA-Z0-9_]`。
- **`\W`**: 匹配非字母数字字符。
- **`\s`**: 匹配任何空白字符（空格、Tab、换行符等）。
- **`\S`**: 匹配非空白字符。
- **`[]`**: 匹配方括号中的任意字符，例如 `[abc]` 匹配 'a'、'b' 或 'c'。
- **`|`**: 表示“或”，例如 `a|b` 匹配 'a' 或 'b'。
- **`()`**: 用来分组和提取匹配的子字符串。

## 7.lambda函数

`lambda` 函数是 Python 中的一种匿名函数，也叫做 **lambda 表达式**。它允许你创建简单的函数，而不需要用 `def` 关键字来显式地定义函数。`lambda` 函数的主要特点是简洁，只适用于表达式较简单的情况。

**语法**

```py
lambda 参数列表: 表达式
```

**`lambda`**：声明一个匿名函数。

**参数列表**：可以包含多个参数，类似于普通函数的参数。

**表达式**：这是一个单一的表达式，lambda 函数的返回值即为该表达式的计算结果。

实例：

```py
add = lambda x, y: x + y
print(add(5, 3))  # 输出：8
```

**无参数的 `lambda` 函数**：

```py
greet = lambda: "Hello, World!"
print(greet())  # 输出："Hello, World!"
```

**结合其他函数使用**： `lambda` 函数通常和一些高阶函数（比如 `map`、`filter`）一起使用，下面是两个常见的例子。

- **`map` 函数**：将 `lambda` 应用于列表中的每一个元素。

```py
numbers = [1, 2, 3, 4]
squares = map(lambda x: x ** 2, numbers)
print(list(squares))  # 输出：[1, 4, 9, 16]
```

**`filter` 函数**：使用 `lambda` 来过滤列表中的元素。

```py
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = filter(lambda x: x % 2 == 0, numbers)
print(list(even_numbers))  # 输出：[2, 4, 6]
```

## 8.迭代器与生成器

#### 1. **迭代器**

迭代器是一种能够记住遍历位置的对象，可以从容器（如列表、元组）中一个一个地获取元素。迭代器对象从第一个元素开始访问，直到所有元素被访问完，无法回到开头。迭代器与常规的容器类型不同，它只计算下一个值，不会一次性生成整个序列，因而在内存和性能方面更高效。

**基本概念**

- **`iter()`**：用来获取可迭代对象的迭代器。
- **`next()`**：通过调用 `next()` 函数获取迭代器的下一个元素。

实例：

```py
# 列表是可迭代对象
numbers = [1, 2, 3]
it = iter(numbers)  # 创建迭代器对象

# 使用 next() 获取下一个元素
print(next(it))  # 输出：1
print(next(it))  # 输出：2
print(next(it))  # 输出：3
# 如果再调用 next(it)，会抛出 StopIteration 异常
```

**自定义迭代器类**

你可以通过定义一个类并实现 `__iter__()` 和 `__next__()` 方法来自定义迭代器：

- `__iter__()` 方法返回迭代器对象本身。
- `__next__()` 方法返回序列中的下一个元素，如果没有元素了，则引发 `StopIteration` 异常。

自定义迭代器示例：

```py
class MyIterator:
    def __init__(self, limit):
        self.limit = limit
        self.count = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.count < self.limit:
            self.count += 1
            return self.count
        else:
            raise StopIteration

it = MyIterator(5)
for i in it:
    print(i)  # 输出：1 2 3 4 5
```

#### 2. **生成器**

生成器（generator）也是一种迭代器，它更为简洁。生成器的定义方式不同于迭代器，使用 `yield` 关键字即可创建生成器。生成器不会一次性将所有数据存储在内存中，而是“按需生成”，这使得它在处理大量数据时非常高效。

**`yield` 关键字的使用**

`yield` 和 `return` 类似，用于从函数返回值，但 `yield` 不会终止函数的执行，而是保存当前状态并“暂停”函数的执行，直到调用 `next()` 时，函数会从上次 `yield` 语句处继续执行。

**生成器的工作原理**

每次调用 `next()` 时，生成器从上次挂起的地方恢复执行，直到再次遇到 `yield`。

```py
def my_generator():
    print("Start")
    yield 1
    print("Continue")
    yield 2
    print("End")
    yield 3

gen = my_generator()
print(next(gen))  # 输出：Start \n 1
print(next(gen))  # 输出：Continue \n 2
print(next(gen))  # 输出：End \n 3
```

每次 `next()` 调用时，生成器函数会恢复执行，直到再次遇到 `yield`，返回值之后暂停。

**生成器的优势**

生成器相比于普通函数或列表构建器有以下几个优势：

- **节省内存**：生成器在需要的时候才生成数据，并不会将所有数据一次性存入内存中。
- **惰性求值**：生成器可以用于处理大数据集或无限序列，例如流式处理。

**生成器函数与生成器表达式**

- **生成器函数**：通过 `yield` 关键字实现惰性求值。
- **生成器表达式**：类似于列表解析，但返回的是一个生成器对象，不会立刻生成所有元素。

**生成器表达式的语法**

生成器表达式和列表解析的语法非常相似，区别在于生成器表达式使用圆括号 `()`，而列表解析使用方括号 `[]`。生成器表达式不会立即计算结果，而是返回一个生成器对象。

```py
# 列表解析：一次性生成整个列表
list_comp = [x * 2 for x in range(5)]
print(list_comp)  # 输出：[0, 2, 4, 6, 8]

# 生成器表达式：按需生成值
gen_exp = (x * 2 for x in range(5))
print(next(gen_exp))  # 输出：0
print(next(gen_exp))  # 输出：2
```

生成器表达式示例

```py
# 生成器表达式用于节省内存
gen = (x ** 2 for x in range(1000000))

# 每次取下一个值，不会占用大量内存
print(next(gen))  # 输出：0
print(next(gen))  # 输出：1
```

在内存敏感的场合，生成器表达式非常有用，它通过惰性计算可以避免一次性占用大量内存。

## 9.常用标准库详解

### **`os` 模块：文件与目录操作**

`os` 模块提供了与操作系统交互的功能，特别是与文件和目录相关的操作。你可以通过 `os` 模块执行许多系统级的任务，如文件和目录的创建、删除、遍历，以及获取系统相关的信息。

**常用功能**

**获取当前工作目录**：

```py
import os
print(os.getcwd())  # 获取当前工作目录路径
```

**列出目录中的所有文件**：

```py
print(os.listdir("."))  # 列出当前目录下的文件
```

**创建和删除目录**：

```py
os.mkdir("new_dir")   # 创建新目录
os.rmdir("new_dir")   # 删除空目录
```

**检查文件或目录是否存在**：

```py
print(os.path.exists("test.txt"))  # 检查文件或目录是否存在
```

**重命名文件或目录**：

```py
os.rename("old_name.txt", "new_name.txt")  # 文件或目录重命名
```

**删除文件**：

```py
os.remove("file.txt")  # 删除文件
```

**文件路径操作**：

- 获取文件名、文件路径和扩展名：

```py
path = "/path/to/file.txt"
print(os.path.basename(path))  # 输出：file.txt
print(os.path.dirname(path))   # 输出：/path/to
print(os.path.split(path))     # 输出：('/path/to', 'file.txt')
print(os.path.splitext(path))  # 输出：('/path/to/file', '.txt')
```

### **`sys` 模块：命令行参数与系统操作**

`sys` 模块允许你访问与 Python 解释器和命令行相关的变量和函数，常用于获取命令行参数、退出程序等。

**常用功能**

**获取命令行参数**： `sys.argv` 是一个列表，包含命令行传入的参数，列表的第一个元素是程序的名称。

```py
import sys
print(sys.argv)  # 输出命令行参数列表
```

**退出程序**：

```py
sys.exit(0)  # 正常退出程序，参数为状态码，0 表示正常退出
```

**标准输入与输出**：

​	**获取用户输入**：

```py
sys.stdin.read()  # 读取标准输入
```

​	**输出到标准输出和错误流**：

```py
sys.stdout.write("Hello, World!\n")
sys.stderr.write("Error occurred!\n")
```

**获取 Python 解释器的版本信息**：

```py
print(sys.version)  # 输出当前 Python 版本信息
```

### **`datetime` 模块：日期与时间处理**

`datetime` 模块提供了用于操作日期和时间的类和函数。它支持获取当前时间、时间差计算、格式化输出等操作。

**常用功能**

**获取当前日期与时间**：

```py
from datetime import datetime
now = datetime.now()
print(now)  # 输出：当前日期和时间
```

**格式化日期输出**： 使用 `strftime()` 方法自定义日期和时间的输出格式

```py
print(now.strftime("%Y-%m-%d %H:%M:%S"))  # 输出：2024-10-06 12:34:56
```

**解析日期字符串**： 使用 `strptime()` 方法将日期字符串解析为 `datetime` 对象。

```py
date_str = "2024-10-06"
date_obj = datetime.strptime(date_str, "%Y-%m-%d")
print(date_obj)  # 输出：2024-10-06 00:00:00
```

**计算日期差**： `timedelta` 类可以用于表示时间间隔，适合进行日期加减计算

```py
from datetime import timedelta
future_date = now + timedelta(days=5)
print(future_date)  # 当前日期加上5天后的日期
```

### **`random` 模块：随机数生成**

`random` 模块提供了生成随机数的函数，可以生成整数、浮点数，甚至从序列中随机选择元素。

**常用功能**

- **生成随机整数**：

```py
import random
print(random.randint(1, 10))  # 生成1到10之间的随机整数
```

**生成随机浮点数**：

```py
print(random.random())  # 生成0到1之间的随机浮点数
```

**从列表中随机选择元素**：

```py
choices = ['apple', 'banana', 'cherry']
print(random.choice(choices))  # 从列表中随机选择一个元素
```

**随机打乱列表顺序**：

```py
random.shuffle(choices)  # 打乱列表中的元素
print(choices)
```

**生成指定范围内的随机浮点数**：

```py
print(random.uniform(1.5, 6.5))  # 生成1.5到6.5之间的随机浮点数
```

