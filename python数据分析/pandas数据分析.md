#  Pandas数据结构

## 1.Series

![image-20240506200311742](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506200311742.png)

![image-20240506200543589](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506200543589.png)

### 1.Series的创建

两种创建形式:

#### 1.由列表或numpy数组创建

默认索引为0到N-1的整数型索引

index和value：

![image-20240506201344138](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506201344138.png)

修改索引index:

![image-20240506201628481](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506201628481.png)

其他操作:

![image-20240506201954417](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506201954417.png)

#### 2.用字典实现

![image-20240506203301328](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506203301328.png)

### 2.Series的索引

![image-20240506203504718](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506203504718.png)

#### 2.1显示索引

![image-20240506203540328](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506203540328.png)

实例：

![image-20240506203958026](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506203958026.png)

#### 2.2隐式索引

![image-20240506204338012](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506204338012.png)

实例：

![image-20240506204648745](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506204648745.png)

### 3.Series的切片

![image-20240506205319892](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506205319892.png)

### 4.Series的基本属性和方法

![image-20240506223106939](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506223106939.png)

![image-20240506223724430](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506223724430.png)

![image-20240506224222162](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506224222162.png)

![image-20240506225930634](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506225930634.png)

![image-20240506230034946](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506230034946.png)

### 5.Series的运算

![image-20240506230157146](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506230157146.png)

![image-20240506230221835](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506230221835.png)

#### 5.1基本算术运算

![image-20240506230659987](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506230659987.png)

#### 5.2注意

![image-20240506231124565](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506231124565.png)

![image-20240506231618518](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506231618518.png)

### 6.总结

Series:可以看作是一个有序的字典结构

## 2.DataFrame

![image-20240506200343993](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240506200343993.png)

### 2.1DataFrame介绍

![image-20240507145519173](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507145519173.png)

### 2.2DataFrame的创建

![image-20240507145818555](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507145818555.png)

### 2.3DataFrame的基本属性和方法

![image-20240507150404864](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507150404864.png)

### 2.4DataFrame的其他创建方式

![image-20240507151334171](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507151334171.png)

### 2.5DataFrame的索引

#### 2.5.1对列进行索引

![image-20240507151558331](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507151558331.png)

例子：

![image-20240507152817213](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507152817213.png)

#### 2.5.2对行进行索引

![image-20240507152843216](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507152843216.png)

例子：

![image-20240507153407055](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507153407055.png)

#### 2.5.3对元素索引的方法

![image-20240507153740275](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507153740275.png)

例子：

![image-20240507154703399](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507154703399.png)

### 2.6DataFrame的切片

![image-20240507154909612](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507154909612.png)

#### 2.6.1行切片

![image-20240507155353883](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507155353883.png)

#### 2.6.2列切片

![image-20240507160000982](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507160000982.png)

#### 2.6.3总结

要么取一行或一列 ：索引

要么取连续的多行或多列 ：切片

要么取不连续的多行或多列 ：中括号

### 2.7DataFrame的运算

#### 2.7.1DataFrame之间的运算

![image-20240507174456041](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507174456041.png)

#### 2.7.2DataFrame和标量之间的运算

![image-20240507181117827](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507181117827.png)

#### 2.7.3DataFrame之间的运算

![image-20240507181354657](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507181354657.png)

#### 2.7.4使用.add()函数，进行填充

![image-20240507181833511](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507181833511.png)

#### 2.7.5Series与DataFrame之间的运算

![image-20240507182104481](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507182104481.png)

### 2.8Pandas层次化索引

#### 2.8.1创建多层行索引

##### 1.隐式构造

![image-20240507185456786](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507185456786.png)

例子：

![image-20240507190459689](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507190459689.png)

注：

![image-20240507190551665](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507190551665.png)

例子：

![image-20240507190740496](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507190740496.png)

##### 2.显式构造pd.Multilndex

###### 1.使用数组

![image-20240507191341251](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507191341251.png)

###### 2.使用tuple

![image-20240507191552582](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507191552582.png)

###### 3.使用product

使用笛卡尔积

 ![image-20240507192619514](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507192619514.png)

## 3.多层索引对象的索引与切片操作

### 3.1Series的操作

![image-20240507203504474](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507203504474.png)

#### 3.1.1索引

![image-20240507204311147](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507204311147.png)

#### 3.1.2切片

![image-20240507204819181](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240507204819181.png)

### 3.2DataFrame的操作

#### 3.2.1索引

![image-20240508160737832](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508160737832.png)

![image-20240508161228849](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508161228849.png)

![image-20240508161404082](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508161404082.png)

#### 3.2.2切片

![image-20240508162235903](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508162235903.png) 

### 3.3索引的堆叠

![image-20240508162430151](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508162430151.png)

#### 1.stack

![image-20240508163128706](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163128706.png)

#### 2.unstack

![image-20240508163342962](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163342962.png)

#### 3.fill_value填充

![image-20240508163542397](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163542397.png)

### 3.4聚合操作

![image-20240508163632485](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163632485.png)

#### 3.4.1sum操作

![image-20240508163904016](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163904016.png)

#### 3.4.2其他操作

![image-20240508163952787](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508163952787.png)

#### 3.4.3多层索引聚合操作

![image-20240508164212478](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508164212478.png)

![image-20240508164555645](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240508164555645.png)

### 3.5pandas数据合并

#### 1.pd.concat()

pandas使用pd.concat函数，与np.concatenate函数类似

##### 1.简单级联

```python
df1 = make_df([1,2],['A','B'])
df2 = make_df([3,4],['A','B'])
#默认上下合并，垂直合并
print(pd.concat([df1,df2]))
#左右合并，水平合并
pd.concat([df1,df2],axis=1)
#忽略行索引 ignore_index(会重置索引)
pd.concat([df1,df2],ignore_index=True)
#使用多层索引 keys
pd.concat([df1,df2],keys=['x','y'])
```

##### 2.不匹配级联

不匹配级联指的是级联的维度的索引不一致，例如纵向级联时列索引不一致，横向级联时行索引不一致

```python
df3=make_df([1,2,3,4],list('ABCD'))
df4=make_df([2,3,4,5],list('BCDE'))
#对应索引没有值，会自动用NaN填充
pd.concat([df3,df4])
```

1.外连接:补NaN(默认模式)

外连接：类似并集，显示所有数据

`pd.concat([df3,df4],join='outer')`

2.内连接：只连接匹配的项

内连接：类似交集，只显示共同的项

```pd.concat([df3,df4],join='inner'```

#### 2.pd._append()

由于在后面级联的使用非常普遍，因此有一个函数append专门用于在后面添加

```df3.append(df4)```

#### 3.pd.merge()

![image-20240509192656973](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509192656973.png)

##### 3.1一对一合并

![image-20240509193322081](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509193322081.png)

注：```df1.merge(df2)```

##### 3.2多对一合并

![image-20240509193754335](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509193754335.png)

##### 3.3多对多合并

![image-20240509194020619](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509194020619.png)

##### 3.4key的规范化

![image-20240509194123836](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509194123836.png)

![image-20240509194452754](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509194452754.png)

![image-20240509194706100](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509194706100.png)

![image-20240509194909804](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509194909804.png)

##### 3.5内合并与外合并

![image-20240509195044901](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195044901.png)

![image-20240509195309953](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195309953.png)

![image-20240509195406829](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195406829.png)

  ![image-20240509195553233](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195553233.png)

![image-20240509195618287](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195618287.png)

##### 3.6列冲突的解决

![image-20240509195710006](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195710006.png)

![image-20240509195836233](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195836233.png)

##### 3.7merge合并总结

![image-20240509195909540](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509195909540.png)

### 3.6Pandas的缺失值处理

![image-20240509200142102](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509200142102.png)

#### 1.None

![image-20240509200217023](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509200217023.png)

#### 2.np.nan

##### 2.1

![image-20240509200651302](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509200651302.png)

##### 2.2

![image-20240509200810526](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509200810526.png)

![image-20240509200833584](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509200833584.png)

#### 3.pandas中的None与NaN

##### 3.1pandas中None与np.nan都视作np.nan

#### 4.pandas中None与np.nan的操作

![image-20240509201713712](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509201713712.png)

##### 1.判断函数

![image-20240509201738952](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509201738952.png)

![image-20240509201850243](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509201850243.png)

##### 2.any()和all()

![image-20240509202045807](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509202045807.png)

![image-20240509202316929](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509202316929.png)

![image-20240509202448515](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509202448515.png)

##### 3.使用bool值索引过滤数据

1.对行进行过滤

![image-20240509202807303](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509202807303.png)

2.对列进行过滤

![image-20240509203007740](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509203007740.png)

##### 4.过滤函数

dropna()

1.可以选择过滤的是行还是列(默认为行)

![image-20240509203202270](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509203202270.png)

2.也可以选择过滤的方法how = 'all'

![image-20240509203431604](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509203431604.png)

3.inplace = True 修改原数据

![image-20240509203608075](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509203608075.png)

##### 5.填充函数 Series/DataFrame

fillna()

![image-20240509203821783](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509203821783.png)

![image-20240509204024133](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509204024133.png)

可以选择向前填充还是向后填充

![image-20240509204323428](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509204323428.png)

#### 5.pandas重复值处理

##### 1.duplicated()函数检测重复的行

![image-20240509204648768](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509204648768.png)

![image-20240509204931601](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509204931601.png)

 ![image-20240509205216432](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509205216432.png)

##### 2.drop_duplicates()函数删除重复的行

![image-20240509205302399](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509205302399.png)

#### 6.pandas数据映射

![image-20240509205358892](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509205358892.png)

##### 1.replace()函数：替换元素

![image-20240509205727215](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509205727215.png)

##### 2.map()函数：适合处理某一单独的列

map()函数中可以使用lambda函数

  

![image-20240509210245353](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509210245353.png)

![image-20240509210437239](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509210437239.png)

![image-20240509210651354](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509210651354.png)

##### 3.rename函数：替换索引

   ![image-20240509210947128](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240509210947128.png)

##### 4.重置索引 reset_index()

![image-20240510143719065](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510143719065.png)

##### 5.apply()函数：既支持Series，也支持DataFrame

1.用于Series

![image-20240510144450497](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510144450497.png)

2.用于DataFrame

![image-20240510145058204](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510145058204.png)

3.自定义方法

![image-20240510145319255](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510145319255.png)

4.applymap：DataFrame专有的方法

![image-20240510145542902](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510145542902.png)

##### 6.transform()函数

![image-20240510145948240](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510145948240.png)

 

#### 7.Pandas异常值处理

![image-20240510150133034](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510150133034.png)

##### 1.describe():查看每一列的描述性统计量

![image-20240510150413229](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510150413229.png)

![image-20240510150506230](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510150506230.png)

![image-20240510150608387](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510150608387.png)

##### 2.df.std():可以求得DataFrame对象每一列的标准差

![image-20240510150731196](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510150731196.png)

##### 3.df.drop()：删除特定索引

![image-20240510151027947](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510151027947.png)

##### 4.unique():唯一，去重

![image-20240510151240140](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510151240140.png)

##### 5.df.query:按条件查询

![image-20240510151758404](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510151758404.png)

##### 6.df.sort_values():根据值排序 && df.sort_index()：根据索引排序

1.values

![image-20240510153202918](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510153202918.png)

2.index

![image-20240510153346191](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510153346191.png)

##### 7.df.info():查看数据信息

![image-20240510153708424](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510153708424.png)

#### 8.抽样

![image-20240510154559649](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510154559649.png)

##### 1.无放回抽样

![image-20240510154937601](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510154937601.png)

##### 2.有放回抽样

![image-20240510155239049](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510155239049.png)

## 4.Pandas数学函数

![image-20240510155454977](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510155454977.png)

### 1.聚合函数

![image-20240510160007820](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510160007820.png)

### 2.方差和标准差

![image-20240510160055573](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510160055573.png)

![image-20240510160513881](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240510160513881.png)

### 3.其他数学函数

#### 1.统计元素出现次数

![image-20240511092344757](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092344757.png)

#### 2.累加运算

![image-20240511092412033](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092412033.png)

#### 3.累乘运算

![image-20240511092448846](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092448846.png)

### 4.协方差

![image-20240511092554185](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092554185.png)

![image-20240511092837589](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092837589.png)

### 5.相关系数r

![image-20240511092910717](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511092910717.png)

![image-20240511093018273](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511093018273.png)

## 5.pandas数据分组聚合

![image-20240511095402776](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511095402776.png)

#### 1.数据分类处理的核心：groupby()函数

![image-20240511095919645](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511095919645.png)

#### 2.使用.groups属性查看各行的分组情况

![image-20240511100021676](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511100021676.png)

#### 3.分组＋聚合

![image-20240511100122845](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511100122845.png)

## 6.pandas加载数据

![image-20240511101041027](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511101041027.png)

### 1.csv数据

#### 1.df.to_csv:保存到csv

![image-20240511131748178](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511131748178.png)

#### 2.df.read_csv:加载csv数据

![image-20240511132013745](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511132013745.png)

不获取列：header=None

#### 3.pd.read_table

![image-20240511132146606](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511132146606.png)

### 2.excel数据

#### 1.df.to_excel:保存到excel文件

![image-20240511134804141](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511134804141.png)

#### 2.pd.read_excel:读取excel

![image-20240511135058090](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511135058090.png)

### 3.MySQL

![image-20240511140222239](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511140222239.png)

#### 1.df.to_sql:保存到MySQL

![image-20240511140501113](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511140501113.png)

#### 2.df.read_sql:从MySQL中加载数据

## ![image-20240511140608361](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511140608361.png)

## 7.pandas的分箱操作

![image-20240511140737453](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511140737453.png)

#### 1.等宽分箱

![image-20240511143041481](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511143041481.png)

![image-20240511143649283](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511143649283.png)

#### 2.等频分箱

![image-20240511143827392](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511143827392.png)

## 8.pandas的时间序列

### 1.时间戳

![image-20240511144630030](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511144630030.png)

### 2.转换方法

 ![image-20240511145007768](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511145007768.png)

### 3.时间戳的索引和切片

![image-20240511145334085](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511145334085.png)

![image-20240511145453975](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511145453975.png)

![image-20240511145703952](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511145703952.png)

### 4.时间序列常用方法

对时间做一些移动/滞后，频率转换，采样等相关操作

![image-20240511145956935](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511145956935.png)

#### 1.移动

![image-20240511150131573](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511150131573.png)

#### 2.频率转换

 ![image-20240511151227683](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511151227683.png)

### 5.resample:根据日期维度进行数据聚合

按照分钟，小时，日，周，月， 年等来作为日期维度

#### 1.重采样

![image-20240511152359107](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240511152359107.png)

#### 2.时区

 ![image-20240512100024864](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512100024864.png)

![image-20240512100212598](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512100212598.png)

## 9.pandas绘图

![image-20240512165728545](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512165728545.png)

### 1.折线图

#### 1.series图表

![image-20240512170530620](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512170530620.png)

#### 2.画正弦曲线

![image-20240512170928403](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512170928403.png)

#### 3.DataFrame图表

图例的位置可能会随着数据的不同而不同

![image-20240512171434619](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512171434619.png)

![image-20240512171503843](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512171503843.png)

### 2.条形图和柱状图

#### 1.Series

![image-20240512171903966](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512171903966.png)

![image-20240512172116503](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512172116503.png)

#### 2.DataFrame

![image-20240512172302070](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512172302070.png)

### 3.直方图

![image-20240512172532725](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512172532725.png)

![image-20240512183056245](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512183056245.png)

kde图：核密度估计，用于弥补直方图由于参数bins设置的不合理导致的精度缺失问题

![image-20240512183351373](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512183351373.png)

### 4.饼图

![image-20240512192132361](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512192132361.png)

### 5.散点图

散点图是观察两个一维数据数列之间的关系的有效方法，DataFrame对象可用

![image-20240512192422291](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512192422291.png)

![image-20240512192505543](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512192505543.png)

### 6.面积图

![image-20240512192749174](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512192749174.png)

### 7.箱型图

![image-20240512193102654](C:\Users\冯煜炜\AppData\Roaming\Typora\typora-user-images\image-20240512193102654.png)

​    
