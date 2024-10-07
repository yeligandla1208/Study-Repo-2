<div align="center">
  <h1>Python 30 天挑战：第 13 天 - 列表推导式</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>作者:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small>第二版: 2021 年 7 月</small>
</sub>

</div>
</div>

[<< 第 12 天](../12_Day_Modules/12_modules.md) | [第 14 天>>](../14_Day_Higher_order_functions/14_higher_order_functions.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)

- [📘 第 13 天](#📘-第-13-天)
  - [列表推导式](#列表推导式)
  - [Lambda 函数](#lambda函数)
    - [创建 Lambda 函数](#创建-lambda-函数)
    - [Lambda 函数在另一个函数中](#lambda-函数在另一个函数中)
  - [💻 练习：第 13 天](#💻-练习第-13-天)

# 📘 第 13 天

## 列表推导式

在 Python 中，列表推导式是一种从序列中创建列表的简洁方式。它是创建新列表的简短方法。列表推导式比使用 _for_ 循环处理列表快得多。

```py
# 语法
[i for i in iterable if 表达式]
```

**例子: 1**

例如，如果你想将字符串转换为字符列表。你可以使用几种方法。我们来看看其中的一些：

```py
# 一种方法
language = 'Python'
lst = list(language)  # 将字符串转换为列表
print(type(lst))      # list
print(lst)            # ['P', 'y', 't', 'h', 'o', 'n']

# 第二种方法: 列表推导式
lst = [i for i in language]
print(type(lst))     # list
print(lst)           # ['P', 'y', 't', 'h', 'o', 'n']
```

**例子: 2**

例如，如果你想生成一个数字列表

```py
# 生成数字
numbers = [i for i in range(11)]  # 生成从0到10的数字
print(numbers)                    # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 也可以在迭代过程中进行数学运算
squares = [i * i for i in range(11)]
print(squares)                    # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# 还可以生成元组列表
numbers = [(i, i * i) for i in range(11)]
print(numbers)                    # [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

**例子: 3**

列表推导式可以与 if 表达式结合使用

```py
# 生成偶数
even_numbers = [i for i in range(21) if i % 2 == 0]  # 生成从0到21的偶数列表
print(even_numbers)                    # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# 生成奇数
odd_numbers = [i for i in range(21) if i % 2 != 0]  # 生成从0到21的奇数列表
print(odd_numbers)                      # [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]

# 过滤数字：让我们从下面的列表中过滤出正偶数
numbers = [-8, -7, -3, -1, 0, 1, 3, 4, 5, 7, 6, 8, 10]
positive_even_numbers = [i for i in range(21) if i % 2 == 0 and i > 0]
print(positive_even_numbers)           # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# 扁平化三维数组
list_of_lists = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened_list = [number for row in list_of_lists for number in row]
print(flattened_list)                  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Lambda 函数

Lambda 函数是没有名字的小匿名函数。它可以接受任意数量的参数，但只能有一个表达式。Lambda 函数类似于 JavaScript 中的匿名函数。当我们想在另一个函数中编写匿名函数时，需要它。

### 创建 Lambda 函数

要创建一个 lambda 函数，我们使用 _lambda_ 关键字，然后是一个或多个参数，再然后是一个表达式。请参阅下面的语法和示例。Lambda 函数不用 return，但它会隐式地返回表达式。

```py
# 语法
x = lambda param1, param2, param3: param1 + param2 + param3
print(x(arg1, arg2, arg3))
```

**示例:**

```py
# 命名函数
def add_two_nums(a, b):
    return a + b

print(add_two_nums(2, 3))  # 5

# 让我们将上述函数更改为 lambda 函数
add_two_nums = lambda a, b: a + b
print(add_two_nums(2, 3))  # 5

# 自调用 lambda 函数
print((lambda a, b: a + b)(2, 3))  # 5

square = lambda x: x ** 2
print(square(3))    # 9
cube = lambda x: x ** 3
print(cube(3))      # 27

# 多个变量
multiple_variable = lambda a, b, c: a ** 2 - 3 * b + 4 * c
print(multiple_variable(5, 5, 3))  # 22
```

### Lambda 函数在另一个函数中

在另一个函数中使用 lambda 函数。

```py
def power(x):
    return lambda n: x ** n

cube = power(2)(3)   # 函数 power 现在需要两个单独的括号中的参数
print(cube)          # 8
two_power_of_five = power(2)(5)
print(two_power_of_five)  # 32
```

🌕 继续保持良好的工作。保持动力，天空才是你的极限！你已经完成了第 13 天的挑战，你已经向伟大的目标迈出了 13 步。现在为你的大脑和肌肉来做一些练习。

## 💻 练习: 第 13 天

1. 使用列表推导式过滤出列表中的负数和零：
   ```py
   numbers = [-4, -3, -2, -1, 0, 2, 4, 6]
   ```
2. 将以下列表中的列表展平为一维列表：

   ```py
   list_of_lists = [[[1, 2, 3]], [[4, 5, 6]], [[7, 8, 9]]]

   输出:
   [1, 2, 3, 4, 5, 6, 7, 8, 9]
   ```

3. 使用列表推导式创建以下元组列表：
   ```py
   [(0, 1, 0, 0, 0, 0, 0),
   (1, 1, 1, 1, 1, 1, 1),
   (2, 1, 2, 4, 8, 16, 32),
   (3, 1, 3, 9, 27, 81, 243),
   (4, 1, 4, 16, 64, 256, 1024),
   (5, 1, 5, 25, 125, 625, 3125),
   (6, 1, 6, 36, 216, 1296, 7776),
   (7, 1, 7, 49, 343, 2401, 16807),
   (8, 1, 8, 64, 512, 4096, 32768),
   (9, 1, 9, 81, 729, 6561, 59049),
   (10, 1, 10, 100, 1000, 10000, 100000)]
   ```
4. 将以下列表展平成一个新列表：
   ```py
   countries = [[('芬兰', '赫尔辛基')], [('瑞典', '斯德哥尔摩')], [('挪威', '奥斯陆')]]
   输出:
   [['芬兰', '汇编', '赫尔辛基'], ['瑞典', 'SWE', '斯德哥尔摩'], ['挪威', 'NOR', '奥斯陆']]
   ```
5. 将以下列表转换为字典列表：
   ```py
   countries = [[('芬兰', '赫尔辛基')], [('瑞典', '斯德哥尔摩')], [('挪威', '奥斯陆')]]
   输出:
   [{'国家': '芬兰', '城市': '赫尔辛基'},
   {'国家': '瑞典', '城市': '斯德哥尔摩'},
   {'国家': '挪威', '城市': '奥斯陆'}]
   ```
6. 将以下列表转换为连接字符串的列表：
   ```py
   names = [[('Asabeneh', 'Yetayeh')], [('David', 'Smith')], [('Donald', 'Trump')], [('Bill', 'Gates')]]
   输出:
   ['Asabeneh Yetayeh', 'David Smith', 'Donald Trump', 'Bill Gates']
   ```
7. 编写一个 lambda 函数，可以求解线性函数的斜率或 y 截距。

🎉 祝贺你！🎉

[<< 第 12 天](../12_Day_Modules/12_modules.md) | [第 14 天>>](../14_Day_Higher_order_functions/14_higher_order_functions.md)
