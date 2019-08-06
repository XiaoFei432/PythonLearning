- [1 列表](#1-列表)    
    - [1.1 标志](#11-标志)    
    - [1.2 基本操作(创建，append( )，pop( ) ,del( ), 拷贝）](#12-基本操作创建append-pop--del--拷贝)    
    - [1.3 列表相关方法](#13-列表相关方法)
- [2 元组](#2-元组)    
    - [2.1 标志](#21-标志)    
    - [2.2 基本操作（创建及不可变性）](#22-基本操作创建及不可变性)
- [3 string字符串](#3-string字符串)    
    - [3.1 定义及基本操作（+，*，读取方式）](#31-定义及基本操作读取方式)    
    - [3.2 字符串相关方法](#32-字符串相关方法)
- [4 字符串格式化问题](#4-字符串格式化问题)
## Task2
### 1 列表
列表(list)是一种有序的集合，可以随时添加，删除和更改其中的元素，元素类型可各不相同。
#### 1.1 标志
列表的标志是`[]`,建立方式如下:
>
    array = [1,2,3,'hello']
    array = [1,2,[3,4,5]]  #列表的列表
#### 1.2 基本操作(创建，append( )，pop( ) ,del( ), 拷贝）
+ 创建
>
    array = [1,2,3]
+ append()用于在列表末尾追加元素，参数为要追加的末尾的元素值且只能有一个参数
>
    In[1]:  array = [1,2,3]
            array.append(6)
            print(array)
    Out[1]: [1,2,3,6]
+ pop()用于删除列表中的元素，分为有参和无参两种情况
> 无参默认删除列表末尾的元素

> 有参数为要删除的元素的索引，从0开始
>
    In[1]:  array = [1,2,3,4,5,6]
            array.pop()  #无参
            print(array)
    In[2]:  array.pop(2) #有参
            print(array)
    Out[1]: [1,2,3,4,5]
    Out[2]: [1,2,4,5]
+ del 在python3中用于释放变量内存，可利用此性质删除列表中的元素，如下所示:
>
    In[1]:  array = [1,2,3,4,5]
            del array[0]
            print(array,array[0])
    Out[1]: [2, 3, 4, 5] 2
+ 拷贝
    - 非拷贝，直接赋值
>
    In[1]:  old = [1,2,3,4,5]
            new = old
            old[2] = [3,5]
            print('old:',old)
            print('new:',new)
    Out[1]: old: [1, 2, [3, 5], 4, 5]
            new: [1, 2, [3, 5], 4, 5]
> old与new对象的内存空间是一致的
    - 浅拷贝
>   
    In[1]:  old = [1,[1,2,3],3]
            new = old.copy()
            print('Before:')
            print(old)
            print(new)
            new[0] = 3
            new[1][0] =3
            print('After:')
            print(old)
            print(new)
    Out[1]: Before:
            [1, [1, 2, 3], 3]
            [1, [1, 2, 3], 3]
            After:
            [1, [3, 2, 3], 3]
            [3, [3, 2, 3], 3]
> 第一层list实现了深拷贝，即新列表与旧列表无关，而由于内层子列表保存的是地址，故在拷贝过程中发生了浅拷贝。
    - 深拷贝
>
    In[1]:  import copy
            old = [1,[1,2,3],3]
            new = copy.deepcopy(old)
            print('Before:')
            print(old)
            print(new)
            new[0] = 3
            new[1][0] = 3
            print('After:')
            print(old)
            print(new)
    Out[1]: Before:
            [1, [1, 2, 3], 3]
            [1, [1, 2, 3], 3]
            After:
            [1, [1, 2, 3], 3]
            [3, [3, 2, 3], 3]
> 无论有几层列表，拷贝后的列表均与原列表无关
    
#### 1.3 列表相关方法

|序号|	函数|介绍|
|--|--|--|
|1|	cmp(list1, list2) |比较两个列表的元
|2|len(list)|列表元素个数|
|3|max(list)|返回列表元素最大值|
|4|min(list)|返回列表元素最小值|
|5|list(seq)|将元组转换为列表|
|6|	list.append(obj)|在列表末尾添加新的对象|
|7|	list.count(obj)|统计某个元素在列表中出现的次数|
|8|	list.extend(seq)|在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）|
|9|	list.index(obj)|从列表中找出某个值第一个匹配项的索引位置|
|10|list.insert(index, obj)|将对象插入列表|
|11|list.pop([index=-1])|移除列表中的一个元素（默认最后一个元素），并且返回该元素的值|
|12|list.remove(obj)|移除列表中某个值的第一个匹配项|
|13|list.reverse()|反向列表中元素|
|14|list.sort(cmp=None, key=None, reverse=False)|对原列表进行排序|
### 2 元组
元组(tuple)与列表类似，但是其内元素可以使不同种类型，但是不能被修改。
#### 2.1 标志
列表的标志是`()`,建立方式如下:
>
    array = (1,2,3,'hello')
    array = (1,2,(3,4,5))  #元组的元组
#### 2.2 基本操作（创建及不可变性）
>
    In[1]:  tup = (2,3,'hello',(3,4))
            print(tup[2])
            tup[2] = 4
    Out[1]: hello
            Error:XXXX
> 可以根据索引访问tuple的元素，但是该元素的内存空间地址不能被改变，而不是单纯的数值
### 3 string字符串
#### 3.1 定义及基本操作（+，*，读取方式）
- 定义
Python中的字符串用单引号 ' 或双引号 " 括起来，同时使用反斜杠 \ 转义特殊字符。
>
    str = 'hello world'
- 基本操作
    + 加号`+是字符串连接符,中间无空格
    + 星号`*`表示复制当前字符串，紧跟的数字为复制的次数
>
    In[1]:  string = 'hello python'
            string += string
            print(string) 
            string = 'hello python'
            print(string*3)
    Out[1]: hello pythonhello python
            hello pythonhello pythonhello python
- 读取方式
    + 按索引读取
    + 分片读取
>
    In[1]:  str = 'Runoob'
            print (str)          # 输出字符串
            print (str[0:-1])    # 输出第一个到倒数第二个的所有字符
            print (str[0])       # 输出字符串第一个字符
            print (str[2:5])     # 输出从第三个开始到第五个的字符
            print (str[2:])      # 输出从第三个开始的后的所有字符
    Out[1]: Runoob
            Runoo
            R
            noo
            noob
#### 3.2 字符串相关方法
|序号|函数|介绍|
|--|--|--|
|1|string.count(str,beg=0,end=len(string))|返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数|
|2|string.decode(encoding='UTF-8', errors='strict')|以 encoding 指定的编码格式解码 string，如果出错默认报一个 ValueError 的 异 常 ， 除非 errors 指 定 的 是 'ignore' 或 者'replace'|
|3|string.encode(encoding='UTF-8', errors='strict')|以 encoding 指定的编码格式编码 string，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace'|
|4|string.find(str, beg=0, end=len(string))|检测 str 是否包含在 string 中，如果 beg 和 end 指定范围，则检查是否包含在指定范围内，如果是返回开始的索引值，否则返回-1|
|5|string.split(str="", num=string.count(str))|以 str 为分隔符切片 string，如果 num 有指定值，则仅分隔 num+ 个子字符串|
### 4 字符串格式化问题
见Task1的print用法部分的格式化输出(format方法)