# NumPy

## 1.基础入门

### 1. **什么是 `ndarray` 对象？**

`ndarray` 是 NumPy 中的核心对象，全称为 “N-dimensional array”，即多维数组。它是一个固定大小、同质数据类型的容器，用于存储相同类型的元素（例如整数、浮点数、布尔值等）。`ndarray` 的特点如下：

- **多维**：可以是1维（向量）、2维（矩阵）、或者更高维度的数组。
- **固定数据类型**：数组中的所有元素必须具有相同的数据类型。
- **高效运算**：支持向量化操作，相比于传统 Python 列表操作，速度更快且内存占用更少。

```py
import numpy as np

# 创建一个简单的一维数组
a = np.array([1, 2, 3, 4, 5])
print(a)  # 输出 [1 2 3 4 5]
```

### 2. **创建数组**

NumPy 提供了多种方式来创建数组，包括手动创建数组和使用函数自动生成数组。

**使用 `array()` 函数**

`array()` 是最常用的数组创建方式，可以通过将 Python 的列表、元组等传递给 `array()` 来生成数组。

```py
import numpy as np

# 从列表创建一维数组
a = np.array([1, 2, 3, 4])

# 从列表创建二维数组
b = np.array([[1, 2, 3], [4, 5, 6]])

print(a)
print(b)
```

**使用 `zeros()` 创建全零数组**

`zeros()` 创建一个全为零的数组，可以指定数组的形状（行数和列数）。

```py
# 创建一个3x3的全零数组
zero_array = np.zeros((3, 3))
print(zero_array)
```

**使用 `ones()` 创建全一数组**

`ones()` 类似于 `zeros()`，它会创建一个全为1的数组。

```py
# 创建一个2x4的全一数组
ones_array = np.ones((2, 4))
print(ones_array)
```

**使用 `arange()` 创建等差数列**

`arange()` 类似于 Python 内置的 `range()` 函数，可以生成一个有步长的等差数列，默认步长为1。

```py
# 创建从0到9的等差数列
arange_array = np.arange(0, 10)
print(arange_array)

# 创建一个从0到20，步长为2的等差数列
arange_step_array = np.arange(0, 20, 2)
print(arange_step_array)
```

**使用 `linspace()` 创建等间距数组**

`linspace()` 用于在指定区间生成指定数量的等间距点，适用于精确生成数据点。

```py
# 在0到1的区间内生成5个等间距的数
linspace_array = np.linspace(0, 1, 5)
print(linspace_array)
```

### 3. **数组的属性**

每个 `ndarray` 对象都有一些重要的属性，可以帮助我们了解数组的结构和内容：

**形状 (`shape`)**

`shape` 表示数组的维度，返回一个包含每一维大小的元组。

```py
a = np.array([[1, 2, 3], [4, 5, 6]])
print(a.shape)  # 输出 (2, 3)，表示2行3列
```

**维度 (`ndim`)**

`ndim` 表示数组的维数，即该数组是几维的（1维、2维、3维等）。

```py
print(a.ndim)  # 输出 2，表示二维数组
```

**数据类型 (`dtype`)**

`dtype` 表示数组中元素的类型，如整型、浮点型等。

```py
print(a.dtype)  # 输出 int64，表示数组中的元素为64位整数
```

**数组大小 (`size`)**

`size` 表示数组中元素的总数，即数组中所有元素的数量。

```py
print(a.size)  # 输出 6，表示该数组总共有6个元素
```

### 4.NumPy数组的索引和切片

#### 1. **一维数组的索引与切片**

**一维数组的索引**

在 NumPy 中，一维数组的索引操作与 Python 列表类似，使用方括号 `[]` 访问数组中的单个元素。索引从 0 开始。

```py
import numpy as np

a = np.array([10, 20, 30, 40, 50])

# 访问第一个元素（索引为 0）
print(a[0])  # 输出 10

# 访问最后一个元素
print(a[-1])  # 输出 50
```

**一维数组的切片**

通过切片操作可以获取数组中的一部分。`start:end:step` 的格式用于定义切片，其中 `start` 是起始索引，`end` 是结束索引（不包含），`step` 是步长（可选）。

```py
# 获取从索引 1 到 3 的子数组
print(a[1:4])  # 输出 [20 30 40]

# 获取从索引 0 开始，每隔一个元素取值
print(a[::2])  # 输出 [10 30 50]

# 反转数组
print(a[::-1])  # 输出 [50 40 30 20 10]
```

**修改一维数组元素**

你可以通过索引或切片来修改数组中的元素。

```py
# 修改索引为 1 的元素
a[1] = 25
print(a)  # 输出 [10 25 30 40 50]

# 修改一部分元素
a[1:4] = [21, 31, 41]
print(a)  # 输出 [10 21 31 41 50]
```

#### 2. **多维数组的索引与切片**

**多维数组的索引**

多维数组的索引类似于一维数组，但每一维度都需要提供一个索引。你可以通过逗号分隔的方式为每一维度提供索引值。

```py
b = np.array([[10, 20, 30], [40, 50, 60], [70, 80, 90]])

# 访问第 1 行第 2 列的元素
print(b[1, 2])  # 输出 60

# 访问最后一行最后一列的元素
print(b[-1, -1])  # 输出 90
```

**多维数组的切片**

在多维数组中，每一维都可以进行切片操作，切片格式和一维数组相同。

```py
# 获取第 0 行到第 1 行，第 1 列到第 2 列的子数组
print(b[0:2, 1:3])  # 输出 [[20 30]
                    #       [50 60]]

# 获取第 2 行的所有列
print(b[2, :])  # 输出 [70 80 90]

# 获取所有行的第 1 列
print(b[:, 1])  # 输出 [20 50 80]

# 获取最后两行的最后两列
print(b[-2:, -2:])  # 输出 [[50 60]
                   #        [80 90]]
```

**修改多维数组元素**

同样，通过索引或切片可以修改多维数组中的元素。

```py
# 修改第 1 行第 2 列的元素
b[1, 2] = 65
print(b)  # 输出 [[10 20 30]
          #       [40 50 65]
          #       [70 80 90]]

# 修改子数组
b[0:2, 1:3] = [[22, 32], [52, 62]]
print(b)  # 输出 [[10 22 32]
          #       [40 52 62]
          #       [70 80 90]]
```

#### 3. **条件筛选：通过布尔索引筛选数据**

布尔索引允许我们通过条件表达式来筛选出数组中符合条件的元素，这在数据处理和分析中非常有用。

**布尔索引基本用法**

当条件表达式应用到数组时，返回的是一个布尔值数组，用于表示哪些元素满足条件。

```py
c = np.array([1, 2, 3, 4, 5, 6])

# 筛选出大于 3 的元素
print(c > 3)  # 输出 [False False False  True  True  True]

# 使用布尔数组筛选元素
print(c[c > 3])  # 输出 [4 5 6]
```

**多维数组中的布尔索引**

布尔索引同样适用于多维数组，可以使用条件表达式来筛选符合条件的元素。

```py
d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# 筛选出大于 5 的元素
print(d[d > 5])  # 输出 [6 7 8 9]
```

**组合条件筛选**

可以使用逻辑操作符（如 `&`, `|`, `~`）组合多个条件进行筛选。

```py
# 筛选出大于 2 且小于 8 的元素
print(d[(d > 2) & (d < 8)])  # 输出 [3 4 5 6 7]

# 筛选出等于 2 或等于 9 的元素
print(d[(d == 2) | (d == 9)])  # 输出 [2 9]

# 筛选不等于 5 的元素
print(d[d != 5])  # 输出 [1 2 3 4 6 7 8 9]
```

### 5.NumPy数组操作

#### 1. **改变数组形状**

改变数组形状是 NumPy 中常见的操作，常用的方法包括 `reshape()` 和 `ravel()`。

**`reshape()`：改变数组形状**

`reshape()` 方法允许我们改变数组的形状而不改变其数据本身。新形状必须与原数组的元素数量一致（即总大小相同）。

```py
import numpy as np

a = np.array([[1, 2, 3], [4, 5, 6]])

# 将 2x3 的数组重塑为 3x2
reshaped_a = a.reshape(3, 2)
print(reshaped_a)
# 输出:
# [[1 2]
#  [3 4]
#  [5 6]]
```

**自动推导形状**：你可以使用 `-1` 来自动推导某一维的大小。

```py
# 将 2x3 的数组重塑为 1x6 的数组
reshaped_a = a.reshape(-1)
print(reshaped_a)  # 输出 [1 2 3 4 5 6]

# 将 2x3 的数组重塑为 3x2，NumPy 会自动推导第一个维度
reshaped_a = a.reshape(-1, 2)
print(reshaped_a)
# 输出:
# [[1 2]
#  [3 4]
#  [5 6]]
```

**`ravel()`：将数组展平为一维数组**

`ravel()` 返回一个展开的一维数组，改变形状后的数组与原数组共享内存。因此，修改其中一个数组会影响另一个数组。

```py
# 将二维数组展平成一维数组
flattened_a = a.ravel()
print(flattened_a)  # 输出 [1 2 3 4 5 6]
```

如果你不需要共享内存，可以使用 `flatten()`，它返回的是原数组的副本。

```py
flattened_copy = a.flatten()
print(flattened_copy)
```

#### 2. **数组拼接**

数组拼接用于将多个数组沿某个轴合并成一个新的数组。常见的方法有 `concatenate()` 和 `stack()`。

**`concatenate()`：沿指定轴拼接数组**

`concatenate()` 函数用于沿现有轴拼接两个或多个数组。默认情况下，它沿第一个轴（行）拼接。

```py
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6]])

# 沿行（axis=0）拼接数组
concatenated = np.concatenate((a, b), axis=0)
print(concatenated)
# 输出:
# [[1 2]
#  [3 4]
#  [5 6]]

# 沿列（axis=1）拼接数组
b = np.array([[5], [6]])
concatenated = np.concatenate((a, b), axis=1)
print(concatenated)
# 输出:
# [[1 2 5]
#  [3 4 6]]
```

**`stack()`：沿新轴拼接数组**

`stack()` 用于在新的轴上拼接数组。它与 `concatenate()` 的不同之处在于，它会创建一个新的维度。

```py
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# 沿新的第0轴拼接
stacked = np.stack((a, b), axis=0)
print(stacked)
# 输出:
# [[1 2 3]
#  [4 5 6]]

# 沿新的第1轴拼接
stacked = np.stack((a, b), axis=1)
print(stacked)
# 输出:
# [[1 4]
#  [2 5]
#  [3 6]]
```

其他常见的 `stack` 函数：

- **`vstack()`**：垂直拼接数组（沿第 0 轴）。
- **`hstack()`**：水平拼接数组（沿第 1 轴）。

```py
# 垂直拼接
v_stacked = np.vstack((a, b))
print(v_stacked)  # 输出 [[1 2 3] [4 5 6]]

# 水平拼接
h_stacked = np.hstack((a, b))
print(h_stacked)  # 输出 [1 2 3 4 5 6]
```

#### 3. **数组拆分**

数组拆分用于将一个数组分割为多个数组。常见的方法有 `split()`、`hsplit()` 和 `vsplit()`。

**`split()`：按索引分割数组**

`split()` 函数可以根据指定的索引位置将数组分割成多个子数组。

```py
a = np.array([1, 2, 3, 4, 5, 6])

# 将数组分割成 3 个子数组
splitted = np.split(a, 3)
print(splitted)
# 输出:
# [array([1, 2]), array([3, 4]), array([5, 6])]

# 按索引位置进行分割
splitted = np.split(a, [2, 4])
print(splitted)
# 输出:
# [array([1, 2]), array([3, 4]), array([5, 6])]
```

**`hsplit()`：水平拆分**

`hsplit()` 用于水平拆分数组，通常用于列方向上的拆分。

```py
a = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])

# 将数组水平拆分成 2 个子数组
h_splitted = np.hsplit(a, 2)
print(h_splitted)
# 输出:
# [array([[1, 2],
#        [5, 6]]), array([[3, 4],
#                         [7, 8]])]
```

**`vsplit()`：垂直拆分**

`vsplit()` 用于垂直拆分数组，通常用于行方向上的拆分。

```py
# 将数组垂直拆分成 2 个子数组
v_splitted = np.vsplit(a, 2)
print(v_splitted)
# 输出:
# [array([[1, 2, 3, 4]]), array([[5, 6, 7, 8]])]
```

### 6.NumPy数组的基本数学操作

#### 1. **数组的加减乘除运算**

NumPy 允许对数组进行元素级别的加、减、乘、除运算，类似于标量运算，但这些操作会自动应用到数组的每一个元素上。

**数组加法**

数组可以进行元素对应位置的加法运算。

```py
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# 数组加法
print(a + b)  # 输出 [5 7 9]
```

**数组减法**

类似地，数组减法也是元素对应位置的相减。

```py
# 数组减法
print(a - b)  # 输出 [-3 -3 -3]
```

**数组乘法**

数组乘法是元素对应位置的相乘。

```py
# 数组乘法
print(a * b)  # 输出 [ 4 10 18]
```

**数组除法**

数组除法是元素对应位置的相除。

```py
# 数组除法
print(a / b)  # 输出 [0.25 0.4  0.5 ]
```

**标量和数组的运算**

NumPy 允许将标量（单一数值）与数组进行运算，标量会自动广播（扩展）到数组的每个元素。

```py
# 标量与数组相加
print(a + 10)  # 输出 [11 12 13]

# 标量与数组相乘
print(a * 2)  # 输出 [2 4 6]
```

#### 2. **数组元素的累积操作**

NumPy 提供了多种累积操作函数，用于对数组元素进行逐步求和、连乘等操作。

**`sum()`：求和**

`sum()` 用于求数组所有元素的和，或在指定轴上进行累加。

```py
a = np.array([1, 2, 3, 4])

# 求数组所有元素的和
print(a.sum())  # 输出 10

# 对多维数组沿特定轴求和
b = np.array([[1, 2], [3, 4]])
print(b.sum(axis=0))  # 输出 [4 6]，沿行方向求和
print(b.sum(axis=1))  # 输出 [3 7]，沿列方向求和
```

**`prod()`：连乘积**

`prod()` 用于求数组所有元素的乘积，或在指定轴上进行连乘。

```py
# 求数组所有元素的乘积
print(a.prod())  # 输出 24 (1*2*3*4)
```

**`cumsum()`：累加和**

`cumsum()` 返回一个包含累加和的数组，表示从第一个元素到当前元素的逐步累加。

```py
# 逐步累加和
print(a.cumsum())  # 输出 [ 1  3  6 10]
```

**`cumprod()`：累积乘积**

`cumprod()` 返回一个包含累积乘积的数组，表示从第一个元素到当前元素的逐步连乘。

```py
# 逐步累积乘积
print(a.cumprod())  # 输出 [ 1  2  6 24]
```

#### 3. **常用数学函数**

NumPy 提供了许多常用的数学函数，类似于标准数学库中的函数，但它们可以直接作用于数组中的每个元素。

**`sin()` 和 `cos()`：正弦和余弦函数**

`sin()` 和 `cos()` 分别用于计算数组中每个元素的正弦值和余弦值。

```py
angles = np.array([0, np.pi/2, np.pi])

# 计算正弦值
print(np.sin(angles))  # 输出 [0.0000000e+00 1.0000000e+00 1.2246468e-16]

# 计算余弦值
print(np.cos(angles))  # 输出 [ 1.000000e+00  6.123234e-17 -1.000000e+00]
```

**`exp()`：指数函数**

`exp()` 计算数组中每个元素的指数值，即 `e` 的幂次方。

```py
a = np.array([1, 2, 3])

# 计算指数值
print(np.exp(a))  # 输出 [  2.71828183   7.3890561   20.08553692]
```

**`log()`：自然对数**

`log()` 计算数组中每个元素的自然对数（以 e 为底数）。

```py
# 计算自然对数
print(np.log(a))  # 输出 [0.         0.69314718 1.09861229]
```

**`sqrt()`：平方根**

`sqrt()` 用于计算数组中每个元素的平方根。

```py
# 计算平方根
print(np.sqrt(a))  # 输出 [1.         1.41421356 1.73205081]
```

**`power()`：幂运算**

`power()` 用于计算数组中每个元素的幂次值。

```py
# 计算每个元素的平方
print(np.power(a, 2))  # 输出 [1 4 9]

# 计算每个元素的立方
print(np.power(a, 3))  # 输出 [ 1  8 27]
```

## 2.进阶操作

### **1. 数组的广播机制**

**理解广播机制的基本原理**

广播机制是 NumPy 中的一个强大特性，它允许不同形状的数组进行数学运算。广播机制会自动扩展较小的数组，使它的形状与较大的数组兼容，避免显式地重复数据。

广播的规则：

- 如果数组的维度不同，NumPy 会自动在较小的数组前面补充维数为1的轴。
- 如果两个数组的形状在某个维度上不一致，NumPy 会尝试匹配形状为1的维度，并自动扩展该维度。
- 如果无法通过上述方式使数组形状一致，则会抛出错误。

```py
import numpy as np

a = np.array([1, 2, 3])  # 形状为 (3,)
b = np.array([[1], [2], [3]])  # 形状为 (3, 1)

# 自动广播，a 会扩展为 (3, 3)，与 b 进行加法
result = a + b
print(result)
# 输出：
# [[2 3 4]
#  [3 4 5]
#  [4 5 6]]
```

在这个例子中，`a` 被广播成了形状为 `(3, 3)`，然后与 `b` 进行加法运算。

**掌握不同维度数组的运算规则**

- 两个数组在维度上兼容，如果它们在每个维度上的长度是相同的，或者其中一个数组在该维度的长度为1。
- 数组的维度不同，较小的数组会先自动扩展成与较大数组相同的维度。
- 如果存在不兼容的维度，运算将会抛出错误。

```py
# a 的形状是 (3,)
a = np.array([1, 2, 3])

# b 的形状是 (3, 1)
b = np.array([[10], [20], [30]])

# a 被广播成形状 (3, 3)，然后与 b 相加
result = a + b
print(result)
# 输出：
# [[11 12 13]
#  [21 22 23]
#  [31 32 33]]
```

### **2. 统计与聚合操作**

NumPy 提供了多种统计方法来进行数据的汇总、统计分析以及排序操作。

**统计方法**

**`mean()`**：计算数组的平均值。

```py
a = np.array([1, 2, 3, 4, 5])
print(np.mean(a))  # 输出 3.0
```

**`median()`**：计算数组的中位数。

```py
print(np.median(a))  # 输出 3.0
```

**`std()` 和 `var()`**：计算数组的标准差和方差。

```py
print(np.std(a))  # 输出 1.4142135623730951
print(np.var(a))  # 输出 2.0
```

**`min()` 和 `max()`**：获取数组的最小值和最大值。

```py
print(np.min(a))  # 输出 1
print(np.max(a))  # 输出 5
```

**`argmin()` 和 `argmax()`**：获取最小值和最大值的索引。

```py
print(np.argmin(a))  # 输出 0
print(np.argmax(a))  # 输出 4
```

**排序操作**

**`sort()`**：对数组进行排序。

```py
b = np.array([3, 1, 2, 5, 4])
print(np.sort(b))  # 输出 [1 2 3 4 5]
```

**`argsort()`**：返回排序后的元素的索引。

```py
print(np.argsort(b))  # 输出 [1 2 0 4 3]
```

**`lexsort()`**：基于多个键进行排序。

```py
names = ('Alice', 'Bob', 'Charlie')
grades = (90, 85, 95)
indices = np.lexsort((grades, names))  # 按 names 排序
print(indices)  # 输出 [0 1 2]
```

**唯一值**

**`unique()`**：返回数组中的唯一值。

```py
c = np.array([1, 2, 2, 3, 3, 3])
print(np.unique(c))  # 输出 [1 2 3]
```

### **3. 随机数生成**

NumPy 的 `random` 模块提供了生成随机数的功能，可以生成各种类型的随机数，包括整数、浮点数以及不同分布的随机数。

#### **生成随机数**

**`rand()`**：生成 [0, 1) 范围内均匀分布的随机数。

```py
print(np.random.rand(3, 3))  # 生成 3x3 的随机数数组
```

**`randn()`**：生成标准正态分布（均值为 0，标准差为 1）的随机数。

```py
print(np.random.randn(3, 3))  # 生成 3x3 的正态分布随机数
```

**`randint()`**：生成指定范围内的随机整数。

```py
print(np.random.randint(1, 10, size=(3, 3)))  # 生成 1 到 9 之间的整数
```

**`choice()`**：从给定数组中随机选择元素。

```py
choices = np.random.choice([1, 2, 3, 4], size=5)
print(choices)  # 从 [1, 2, 3, 4] 中随机选择 5 个元素
```

#### **设置随机种子**

**`seed()`**：设置随机数生成器的种子，以确保每次生成的随机数相同。

```py
np.random.seed(42)
print(np.random.rand(3, 3))  # 生成的随机数将是相同的
```

#### **生成服从不同分布的随机数**

正态分布：np.random.normal(loc, scale, size)

- `loc`：均值，`scale`：标准差，`size`：输出形状。

```py
normal = np.random.normal(0, 1, size=(3, 3))  # 生成标准正态分布的随机数
print(normal)
```

**均匀分布**：`np.random.uniform(low, high, size)`

- `low`：下限，`high`：上限，`size`：输出形状。

```py
uniform = np.random.uniform(1, 10, size=(3, 3))  # 生成均匀分布的随机数
print(uniform)
```

### **4. 线性代数操作**

NumPy 提供了许多线性代数的运算函数，能够处理矩阵运算、求逆、特征值分解等。

#### **矩阵运算**

**`dot()`**：计算两个数组的点积（矩阵乘法）。

```py
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

# 矩阵乘法
result = np.dot(a, b)
print(result)
# 输出:
# [[19 22]
#  [43 50]]
```

**`matmul()`**：矩阵乘法，等价于 `dot()`。

```py
result = np.matmul(a, b)
print(result)  # 输出 [[19 22] [43 50]]
```

#### **求矩阵的逆**

- **`linalg.inv()`**：计算矩阵的逆，要求矩阵是可逆的（方阵）。

```py
inv_a = np.linalg.inv(a)
print(inv_a)
# 输出：
# [[-2.   1. ]
#  [ 1.5 -0.5]]
```

#### **矩阵的特征值和特征向量**

- **`linalg.eig()`**：计算矩阵的特征值和特征向量。

```py
eigenvalues, eigenvectors = np.linalg.eig(a)
print("特征值:", eigenvalues)
print("特征向量:\n", eigenvectors)
```

#### **奇异值分解**

- **`linalg.svd()`**：奇异值分解，用于将矩阵分解为 3 个矩阵的乘积。

```py
u, s, vh = np.linalg.svd(a)
print("U 矩阵:\n", u)
print("奇异值:\n", s)
print("V 矩阵:\n", vh)
```

#### **解线性方程组**

- **`linalg.solve()`**：解线性方程组 `Ax = B`，其中 `A` 为系数矩阵，`B` 为结果向量。

```py
A = np.array([[3, 1], [1, 2]])
B = np.array([9, 8])
x = np.linalg.solve(A, B)
print(x)  # 输出 [2. 3.]
```
