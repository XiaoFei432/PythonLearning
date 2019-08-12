### 1.类和对象
#### 1.1 定义和操作
- 类的定义
    >
        class MyClass:
        i = 12345
        def f(self):
            return 'hello world'
    > 包括成员变量和成员函数
- 实例化类
    >
        x = MyClass()
- 属性引用
    >
        print("MyClass 类的属性i为：", x.i)
        print("MyClass 类的方 f输出为：", x.f())
- 构造方法
    [格式]:
    >   
        def __init__(self):
        self.data = []
    [实例]:
    >
        class Complex:
            def __init__(self, realpart, imagpart):
                self.r = realpart
                self.i = imagpart
        x = Complex(3.0, -4.5)
        print(x.r, x.i)
#### 1.2 继承
我们直接介绍多继承。定义如下:
>
    class DerivedClassName(Base1, Base2, Base3):
> 需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。
>
    class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))

    #单继承示例
    class student(people):
        grade = ''
        def __init__(self,n,a,w,g):
            #调用父类的构函
            people.__init__(self,n,a,w)
            self.grade = g
        #覆写父类的方法
        def speak(self):
            print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
    
    #另一个类，多重继承之前的准备
    class speaker():
        topic = ''
        name = ''
        def __init__(self,n,t):
            self.name = n
            self.topic = t
        def speak(self):
            print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
    
    #多重继承
    class sample(speaker,student):
        a =''
        def __init__(self,n,a,w,g,t):
            student.__init__(self,n,a,w,g)
            speaker.__init__(self,n,t)
    
    test = sample("Tim",25,80,4,"Python")
    test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法

> super()可以用来调用父类

#### 1.3 私有成员
+ 类的私有属性

    __private_attrs：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 self.__private_attrs。

+ 类的方法

    在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 `self`，且为`第一个`参数，self 代表的是类的实例。

    > self 的名字并不是规定死的，也可以使用 this，但是最好还是按照约定是用 self。

+ 类的私有方法

    __private_method：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。self.__private_methods。专有私有方法如下：
    >   
        __init__ : 构造函数，在生成对象时调用
        __del__ : 析构函数，释放对象时使用
        __repr__ : 打印，转换
        __setitem__ : 按照索引赋值
        __getitem__: 按照索引获取值
        __len__: 获得长度
        __cmp__: 比较运算
        __call__: 函数调用
        __add__: 加运算
        __sub__: 减运算
        __mul__: 乘运算
        __truediv__: 除运算
        __mod__: 求余运算
        __pow__: 乘方
#### 1.4 运算符重载
>
    class Vector:
    def __init__(self, a, b):
        self.a = a
        self.b = b
    
    def __str__(self):
        return 'Vector (%d, %d)' % (self.a, self.b)
    
    def __add__(self,other):
        return Vector(self.a + other.a, self.b + other.b)
> 1.3中已有相关的运算私有函数
### 2.正则表达式
正则表达式是一个特殊的字符序列，它能帮助你方便的检查一个字符串是否与某种模式匹配。[具备相关语法规则](https://www.runoob.com/regexp/regexp-metachar.html)。在python中我们主要利用自带的re模块来实现相关功能。
### 3.re模块
+ re.match函数
re.match(pattern, string, flags=0) # flags是用于控制正则表达式的匹配方式
>
    import re
    print(re.match('www', 'www.runoob.com').span())  # 在起始位置匹配
    print(re.match('com', 'www.runoob.com'))         # 不在起始位置匹配
>
    line = "Cats are smarter than dogs"
    # .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符
    matchObj = re.match( r'(.*) are (.*?) (.*)', line, re.M|re.I)
    if matchObj:
        print("matchObj.group() : ", matchObj.group())
        print("matchObj.group(1) : ", matchObj.group(1))
        print("matchObj.group(2) : ", matchObj.group(2))
        print("matchObj.group(3) : ", matchObj.group(3))
    else:
        print("No match!!")

+ 通配符
    - 匹配任意除换行符“\n”外的字符；
    - *表示匹配前一个字符0次或无限次；
    - +或*后跟？表示非贪婪匹配，即尽可能少的匹配，如*？重复任意次，但尽可能少重复；
    - .*? 表示匹配任意数量的重复，但是在能使整个匹配成功的前提下使用最少的重复。
+ re.search函数

    re.search 扫描整个字符串并返回第一个成功的匹配。格式如下:

    re.search(pattern, string, flags=0)
+ re.match()与re.search()的区别
re.match只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回None；而re.search匹配整个字符串，直到找到一个匹配。
实例：
>
    In: line = "Cats are smarter than dogs"
        # .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符
        matchObj = re.match( r'are (.*?) than (.*?)', line, re.M|re.I)
        if matchObj:
            print("matchObj.group() : ", matchObj.group())
            print("matchObj.group(1) : ", matchObj.group(1))
            print("matchObj.group(2) : ", matchObj.group(2))
        else:
            print("No match!!")
    Out:No match!!

    In: line = "Cats are smarter than dogs"
        # .* 表示任意匹配除换行符（\n、\r）之外的任何单个或多个字符
        matchObj = re.search( r'are (.*?) than (.*?)', line, re.M|re.I)
        if matchObj:
            print("matchObj.group() : ", matchObj.group())
            print("matchObj.group(1) : ", matchObj.group(1))
            print("matchObj.group(2) : ", matchObj.group(2))
        else:
            print("No match!!")
    Out:matchObj.group() :  are smarter than dogs
        matchObj.group(1) :  smarter
        matchObj.group(2) :  dogs
> 更多[re模块方法](https://www.runoob.com/python3/python3-reg-expressions.html)
### 4.datetime模块学习
> datetime模块主要用于多方式处理日期和时间，转换日期格式等，由于其功能较为繁杂，可见[datetime相关操作](https://blog.csdn.net/cmzsteven/article/details/64906245)
### 5.http请求
+ 安装requests模块并导入
>
    import requests
+ GET请求
>
    import requests

    r = requests.get('https://www.douban.com/')
    print(r.status_code)
    print(r.text)
+ POST请求
>
    r = requests.post('https://accounts.douban.com/login', data={'form_email': 'abc@example.com', 'form_password': '123456'})
    print(r.text)
+ cookie传递
>
    cs = {'token': '12345', 'status': 'working'}
    # timeout 设置请求超时时间
    r = requests.get(url, cookies=cs, timeout=2.5)