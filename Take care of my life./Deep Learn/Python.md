# Python

## 优点

* 简单、易读、易记	类似英语的语法
* 可读性高、性能高(针对动态语言)
* 目前最为流行的 AI 语言，最适合数据科学领域的编程语言

## Python 解释器

可以进行对话式(交互式)编程

## Python 运算符

* 算数计算

| 运算符 | 意义             |
| ------ | ---------------- |
| +      | 加法             |
| -      | 减法             |
| *      | 乘法             |
| **     | 乘方             |
| /      | 除法             |
| //     | 取整除(向下取整) |
| %      | 求余             |

* 比较运算

| 运算符 | 意义     |
| ------ | -------- |
| ==     | 等于     |
| !=     | 不等于   |
| >      | 大于     |
| <      | 小于     |
| >=     | 大于等于 |
| <=     | 小于等于 |

* 赋值运算

| 运算符 | 意义       |
| ------ | ---------- |
| =      | 向左赋值   |
| +=     | 加法赋值   |
| -=     | 减法赋值   |
| *=     | 乘法赋值   |
| **=    | 幂赋值     |
| /=     | 除法赋值   |
| //=    | 取整除赋值 |
| %=     | 取模赋值   |

* 位运算符

| 运算符 | 意义         |
| ------ | ------------ |
| &      | 按位与       |
| \|     | 按位或       |
| ^      | 按位异或     |
| ～     | 按位取反     |
| <<     | 左移动运算符 |
| >>     | 右移动运算符 |

* 逻辑运算符

| 运算符 | 逻辑表达式 |
| ------ | ---------- |
| and    | x and y    |
| or     | x or y     |
| not    | not x      |

* 成员运算符

| 运算符 | 意义                                                    |
| ------ | ------------------------------------------------------- |
| in     | 如果在指定的序列中找到值返回 True，否则返回 False。     |
| Not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 |

* 身份运算符

| 运算符 |                                             |
| ------ | ------------------------------------------- |
| is     | is 是判断两个标识符是不是引用自一个对象     |
| is not | is not 是判断两个标识符是不是引用自不同对象 |

* 优先级

  | **                       |
  | ------------------------ |
  | ~ + -                    |
  | * / // %                 |
  | + -                      |
  | >> <<                    |
  | &                        |
  | ^ \|                     |
  | <= < > >=                |
  | == !=                    |
  | = %= /= //= -= += *= **= |
  | is is not                |
  | in not in                |
  | not and or               |

## Python 数据类型

​	数据类型用来表示数据的性质

> Python 的五个标准类型
>
> * Numbers（数字）
> * String（字符串）
> * List（列表）
> * Tuple（元组）
> * Dictionary（字典）

​	借助 type()函数可以查看数据类型

## Python 变量

​	可以使用 x 或 y 等字母定义变量(variable)

​	可对变量赋值也可变量可进行计算

> Python 是属于“动态类型语言”的编程语言，所谓动态，是指变量的类 型是根据情况自动决定的。

## Python 列表

> 列表(数组)用于汇总数据

* 数组初始化

  `array_name = [SIZE1,SIZE2,...,SIZEn]`

* 访问列表元素

  `array_name[SIZE] #访问数组中索引 SIZE 对应的元素`

* 访问列表的子列表(部分列表)

  ```python
  array_name[START SIZE:END SIZE] # 获取索引为 START SIZE 到 END SIZE （不包括 END SIZE ）的元素
  array_name[START SIZE:] # 获取索引为 START SIZE 到最后一个元素
  array_name[:END SIZE] # 获取从第一个元素到索引为 END SIZE （不包括 END SIZE ）的元素
  array_name[:-1] # 获取从第一个元素到最后一个元素的前一个元素之间的元素
  array_name[:-2] # 获取从第一个元素到最后一个元素的前两个元素之间的元素
  ```

## Python 字典

> 字典以键值对的形式来存储数据

* 初始化字典

  ​	`Dictionary_name = {'key1':value1,'key2':value2,...,'keyn':valuen}`

* 访问元素

  ​	`Dictionary_name['keyn']`

* 添加新值

  ​	`Dictionary_name['newKey'] = newValue`

## Python if语句

```python
if 判断条件：
    执行语句……
else：
    执行语句……
```

## Python for语句

```python
for iterating_var in sequence:
   statements(s)
```

## Python 函数

> 一连串处理的定义定义为函数

* 无参数

  ```python
  def hello():
    print("Hello Python!")
  ```

* 有参数

  ```python
  def hello(object):
    print("Hello "+ object + ",welcome to Python!")
  ```

## Python 类

> 类可以自己 创建数据类型并定义原创的方法(类的函数)和属性

```python
class class_name:
  def __init__(self,object,...): # 构造函数
    ...
  def way1(self,object,...): # 方法一
    ...
  def way2(self,object,...): #	方法二
    ...
```

```python
# 定义一个叫做 Man 的类
class Man:
  	# 构造函数
     def __init__(self,name):
             self.name = name
             print("Initialized")
    # 定义方法
     def hello(self):
             print("Hello " + self.name + "!")
     def goodbye(self):
             print("Goodbye " + self.name + "!")

# 类 Man 生成实例(对象) m
m = Man("Wen")
m.hello()
m.goodbye()

'''
类 Man 的构造函数(初始化方法)会接受参数 name ，然后用这个参数初始化实例变量 self.name
实例变量是存储在各个实例中的变量
Python中可以像 self.name 这样，通过在 self 后面添加属性名来生成或访问实例变量
'''
```

## NumPy

> 深度学习中经常出现数组和矩阵的计算。NumPy 的数组类 (numpy.array)中提供了很多便捷的方法。

* 导入 NumPy

  `import numpy as np`

  > Python 中使用 import 语句来导入库，as 则意味 NumPy 库中的方法可以通过 np 来调用

* 生成 NumPy 数组

  `x = np.array([1.0,2.0,3.0])`

  > 生成 NumPy 数组，需要使用 np.array() 方法。
  >
  > Np.array() 接受 Python 列表作为参数，生成 NumPy 数组(dumpy.ndarray)

* NumPy 算术运算

  > * 对应元素运算(element-wise 运算)
  >
  >   当 x 和 y 的元素个数相同时，可以对各个元素进行算术运算。如果元素个数不同，程序就会报错，所以元素个数保持一致非常重要
  >
  > * 广播
  >
  >   单一的数值(标量)组合起来进行运算
  >
  >   NumPy 中，形状不同的数组之间也可以进行运算，先将标量或数组进行扩充，然后再与矩阵进行运算

* NumPy N维数组

  `x = np.array([[1,2],[3,4])`

  > 矩阵元素的数据类型可以通过 dtype 查看
  >
  > 矩阵形状可以通过 shape 查看

  > 数学上将一维数组成为**向量**，二维数组称为**矩阵**，一般化后的向量或矩阵等统称为**张量**(tensor)
  >
  > 深度学习中一般将二维数组称为**矩阵**，将三维数组及三维以上的数组称为**张量**

* 访问 NumPy 数组元素

  * 访问单个元素

    `darray_name[SIZE]`

  * for语句遍历数组

    ```python
    for row in darray_name:
      print(row)
    ```

  * 使用数组访问各个元素

    ```python
    X = darrary_name.flatten() # 将X转换为一维数组
    X[np.array([0, 2, 4])] # 获取索引为0、2、4的元素
    ```

  * 获取满足一定条件的元素

    ```python
    X > 15
    array([ True, True, False, True, False, False], dtype=bool) X[X>15]
    array([51, 55, 19])
    ```

    > 对NumPy数组使用不等号运算符等(上例中是X > 15),结果会得到一个 布尔型的数组。上例中就是使用这个布尔型数组取出了数组的各个元素(取 出 True 对应的元素)。

## Matplotlib

> Matplotlib 是用于绘制图形的库，使用 Matplotlib 可以轻松地绘制图形和实现数据的可视化

* 绘制图形

  ```python
  import numpy as np
  import matplotlib.pyplot as plt
  # 生成数据
  x = np.arange(0, 6, 0.1) # 以0.1为单位，生成0到6的数据 y = np.sin(x)
  # 绘制图形
  plt.plot(x, y) # 生成二维图形
  plt.show()
  
  '''
  使用NumPy的arange方法生成了[0, 0.1, 0.2, ..., 5.8, 5.9]的 数据，将其设为 x。对 x 的各个元素，应用 NumPy 的 sin 函数 np.sin()，将 x、 y 的数据传给 plt.plot 方法，然后绘制图形。最后，通过 plt.show() 显示图形。
  '''
  ```

* pyplot 

  > pyplot 可以实现添加标题和 x 轴标签名等其他功能

  ```python
  # 引入所需要的包
  import numpy as np # 数据处理
  import matplotlib.pyplot as plt # 图形绘制
  
  # 生成数据
  x = np.arange(0,6,0.1) # 生成 x 轴数据
  y1 = np.sin(x) # 生成 y 轴 sin 函数曲线数据
  y2 = np.cos(x) # 生成 y 轴 cos 函数曲线数据
  
  # 绘制图形
  plt.plot(x,y1,label = "sin") # 绘制 sin 的二维曲线
  plt.plot(x,y2,linestyle = "--",label = "cos") # 绘制 cos 的二维曲线 lifestyle 用虚线绘制
  plt.xlabel("x") # x 轴标签
  plt.ylabel("y") # y 轴标签
  plt.title('sin& cos') # 标题
  plt.legend() # 为图形添加图例
  plt.show() # 展示生成图形
  ```

  * pyplot 显示图像
  
    * pyplot 中用于显示图像的方法：
  
      ​	imshow() 
  
    * pyplot 中用于读取图像的方法：
  
      ​	Matplotlib.image 模块中的 imread() 方法
  
  ```python
  import matplotlib.pyplot as plt
  from matplotlib.image import imread
  
  img = imread('lena.png') # 读入图像
  plt.imshow(img)
  
  plt.show()
  ```
  
  