- [Task1](#task1)    
    - [1 环境搭建](#1-环境搭建)        
        - [1.1 anaconda环境配置](#11-anaconda环境配置)    
        - [1.2 解释器](#12-解释器)    
    - [2 python初体验](#2-python初体验)       
        - [2.1 print](#21-print)        
        - [2.2 input](#22-input)    
    - [3 python基础讲解](#3-python基础讲解)        
        - [3.1 python变量特性+命名规则](#31-python变量特性命名规则)        
        - [3.2 注释方法](#32-注释方法)        
        - [3.3 python中“：”作用](#33-python中作用)        
        - [3.4 学会使用dir()及和help()](#34-学会使用dir及和help)        
        - [3.5 import使用](#35-import使用)        
        - [3.6 pep8介绍](#36-pep8介绍)    
    - [4 python数值基本知识](#4-python数值基本知识)        
        - [4.1 python中数值类型](#41-python中数值类型)        
        - [4.2 算数运算符](#42-算数运算符)        
        - [4.3 逻辑运算符](#43-逻辑运算符)        
        - [4.4 成员运算符](#44-成员运算符)        
        - [4.5 身份运算符](#45-身份运算符)        
        - [4.6 运算符优先级](#46-运算符优先级)
## Task1 
### 1 环境搭建
#### 1.1 anaconda环境配置
+ 从[anaconda官网](https://www.anaconda.com/)下载Anaconda3-2019.07-MacOSX-x86_64.pkg安装包
+ 安装后新建环境变量到anaconda的安装目录和其下的Script目录
> 主要为了方便使用python3解释器，conda以及pip包管理工具 
### 1.2 解释器
+ 安装anaconda并配置好环境变量后，就可以在cmd下输入python，可由如下效果：
>
    Python 3.7.3 (default, Mar 27 2019, 17:13:21) [MSC v.1915 64 bit (AMD64):: Anaconda, Inc. on win32
    Warning:
    This Python interpreter is in a conda environment, but the environment has not been activated.  Libraries may fail to load.  To activate this environment
    please see https://conda.io/activation
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

### 2 python初体验
#### 2.1 print
+ 输出字符串
> print()会依次打印每个字符串，遇到逗号“,”会输出一个空格
>
    In:  print(字符串1,字符串2,...)
    Out: 字符串1 字符串2 ...
+ 输出数字/算数表达式
>
    In[1]:  print(100)
    Out[1]: 100
    In[2]:  pirnt(50+50)
    Out[2]: 100
+ 输出真值/逻辑表达式
>
    In[1]:  a = true
            print(a)
    Out[1]: ture
    In[2]:  pirnt(true or false)
    Out[2]: true
+ 混合输出(考虑用户体验)
>
    In:  a=5 
            print('a的值为',a)
    Out: a的值为5
+ 格式化输出
> 利用format函数+占位符
1. 不带编号，即“{}”
2. 带数字编号，可调换顺序，即“{1}”、“{2}”
3. 带关键字，即“{a}”、“{tom}”
>

    >>> print('{} {}'.format('hello','world'))  # 不带字段
        hello world
    >>> print('{0} {1}'.format('hello','world'))  # 带数字编号
        hello world
    >>> print('{0} {1} {0}'.format('hello','world'))  # 打乱顺序
        hello world hello
    >>> print('{1} {1} {0}'.format('hello','world'))
        world world hello
    >>> print('{a} {tom} {a}'.format(tom='hello',a='world'))  # 带关键字
        world hello world

#### 2.2 input
格式： a = input([提示内容])
> input函数可以接受字符串,数字,列表等
>

    >>> a = input('请输入你的值')
        请输入你的值:5
    >>> print(a)
        5
### 3 python基础讲解
#### 3.1 python变量特性+命名规则
变量特性
+ 变量不用提前声明
+ 变量没有固定的类型

命名规则
+ 变量名只能包含字母、数字和下划线。变量名可以字母或下划线打头，但不能以数字打头，例如，可将变量命名为message_1，但不能将其命名为1_message。
+ 变量名不能包含空格，但可使用下划线来分隔其中的单词。例如，变量名greeting_message可行，但变量名greeting message会引发错误。
+ 不要将Python关键字和函数名用作变量名，即不要使用Python保留用于特殊用途的单词，如print。
+ 变量名应既简短又具有描述性。例如， name比n好， student_name比s_n好， name_length比length_of_persons_name好。
+ 慎用小写字母l和大写字母O，因为它们可能被人错看成数字1和0。
#### 3.2 注释方法
+ 单行注释样式: #[注释内容]
+ 多行注释样式: '''[注释内容]'''
>
    #我是一行注释
    print("helloworld")
    '''
    多行的第一行注释
    多行的第二行注释
    '''
#### 3.3 python中“：”作用
用于定义分片、步长，如
>
    list1[:3:2]，tul1[3:6:2]
>（注意3:6是索引第3至5 ,不包含6)
#### 3.4 学会使用dir()及和help()
+ dir() 函数不带参数时，返回当前范围内的变量、方法和定义的类型列表；带参数时，返回参数的属性、方法列表
+ help() 函数用于查看函数或模块用途的详细说明和帮助信息。

#### 3.5 import使用
若python项目下可找到名为AA.py的python模块，则在另一个python文件中可用以下方式导入
+ `import AA`  导入AA包
+ `from AA import c` 导入AA包里的c成员，使用时AA.c
+ `from AA import *`  导入AA包里的全部成员
#### 3.6 pep8介绍
PEP8为python编码规范，具体内容见[PEP8规范中文版](https://blog.csdn.net/ratsniper/article/details/78954852#introduction-%E4%BB%8B%E7%BB%8D)

### 4 python数值基本知识
#### 4.1 python中数值类型
python的主要数值类型是**int**,**float**,**bool**,**e计法**,python数值类型均为**不可变对象**(底层内存空间)。
+ int类型
> 
int可以存储`任意大小的数`，包括负数，没有类似C/C++的数值上限和下限。
>
int还支持不同进制的整数，用法如下
>
|  进制  |  实例  |
|  --  |  --  |
|  2  |  0b1234,0B1234  |
|  8  |  0o1234,0O1234  |
|  10  |  1234，-12,0  |
|  16  |  0x1234,0X1234  |
+ float类型
>
float即浮点数，每个数都是双精度(64位)的值。
+ bool类型
>
Python中的布尔值有两个，True和False。⽐较和其它条件表达 式可以⽤True和False判断。布尔值可以与and和or结合使⽤： 
>
    In[89]:	True and True 
    Out[89]: True
    In[90]:	False or True 
    Out[90]: True
+ e记法
> 
e记法即科学计数法。按照科学记数法表示时，一个浮点数的小数点位置是可变的，比如，1.23x109和12.3x108是完全相等的。浮点数可以用数学写法，如1.23，3.14，-9.01，等等。但是对于很大或很小的浮点数，就必须用科学计数法表示，把10用e替代，1.23x109就是`1.23e9`，或者`12.3e8`，0.000012可以写成`1.2e-5`，等等。
#### 4.2 算数运算符
>
|运算符|描述|实例|
|--|--|--|
|+|加 - 两个对象相加|	a + b 输出结果 30|
|-	|减 - 得到负数或是一个数减去另一个数|	a - b 输出结果 -10|
|*|	乘 - 两个数相乘或是返回一个被重复若干次的字符串|	a * b 输出结果 200|
|/|	除 - x除以y|	b / a 输出结果 2|
|%|	取模 - 返回除法的余数|	b % a 输出结果 0|
|**|	幂 - 返回x的y次幂|	a**b 为10的20次方， 输出结果 10000000000000000000|
|//|	取整除 - 返回商的整数部分（向下取整）	|9//2输出结果为4| 
     
#### 4.3 逻辑运算符
|运算符|	逻辑表达式|	描述|	实例|
|--|--|--|--|
|and|	x and y	|布尔"与" - 如果 x 为 False，x and y 返回 False，否则它返回 y 的计算值。|	(a and b) 返回 20。
|or|	x or y|	布尔"或"	- 如果 x 是非 0，它返回 x 的值，否则它返回 y 的计算值。	|(a or b) 返回 10。
|not|	not x	|布尔"非" - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。	|not(a and b) 返回 False
#### 4.4 成员运算符
|运算符|	描述|	实例|
|--|--|--|
|in	|如果在指定的序列中找到值返回 True，否则返回 False。|	x 在 y 序列中 , 如果 x 在 y 序列中返回 True。
|not in|	如果在指定的序列中没有找到值返回 True，否则返回 False。	|x 不在 y 序列中 , 如果 x 不在 y 序列中返回 True。
#### 4.5 身份运算符
|运算符|	描述|	实例|
|--|--|--|
|is|	is 是判断两个标识符是不是引用自一个对象|	x is y, 类似 id(x) == id(y) , 如果引用的是同一个对象则返回 True，否则返回 False|
|is not|	is not 是判断两个标识符是不是引用自不同对象|	x is not y ， 类似 id(a) != id(b)。如果引用的不是同一个对象则返回结果 True，否则返回 False。|
#### 4.6 运算符优先级
>
以下表格列出了从最高到最低优先级的所有运算符：
>
|运算符	|描述|
|--|--|
|**	|指数 (最高优先级)|
|~ + -|	按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@)|
|* / % //	|乘，除，取模和取整除|
|+ -	|加法减法|
|>> <<	|右移，左移运算符|
|&	|位 'AND'|
|^ |	位运算符|
|<= < > >=|比较运算符|
|<> == !=	|等于运算符|
|= %= /= //= -= += *= **=	|赋值运算符|
|is is not	|身份运算符|
|in not in	|成员运算符|
|not and or	|逻辑运算符|