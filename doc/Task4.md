### 1 函数关键字
函数使⽤def关键字声明，⽤return关键字返回值。
>
    def	my_function(x,	y,	z=1.5):
        if	z>1:								
            return	z*(x+y)				
        else:								
            return	z/(x+y)
同时拥有多条return语句也是可以的。如果到达函数末尾时没有 遇到任何⼀条return语句，则返回None。
### 2 函数的定义
函数的定义包括`def`关键字,函数名以及函数参数构成，效果同上。
### 3 函数参数与作用域
+ 函数参数
函数可以有⼀些位置参数（positional）和⼀些关键字参数 （keyword）。关键字参数通常⽤于指定默认值或可选参数。在 上⾯的函数中，x和y是位置参数，⽽z则是关键字参数。也就是说，该函数可以下⾯这两种⽅式进⾏调⽤：
>
    my_function(5,6,z=0.7) 
    my_function(3.14,7,3.5) 
    my_function(10,20)
函数参数的主要限制在于：关键字参数必须位于位置参数（如果 有的话）之后。你可以任何顺序指定关键字参数。也就是说，你 不⽤死记硬背函数参数的顺序，只要记得它们的名字就可以了。 
>
    my_function(x=5,y=6,z=7) 
    my_function(y=6,x=5,z=7)
+ 作用域
    - 局部

    函数可以访问两种不同作⽤域中的变量：全局（global）和局部 （local）。Python有⼀种更科学的⽤于描述变量作⽤域的名称， 即命名空间（namespace）。任何在函数中赋值的变量默认都是 被分配到局部命名空间（local namespace）中的。局部命名空 间是在函数被调⽤时创建的，函数参数会⽴即填⼊该命名空间。在函数执⾏完毕之后，局部命名空间就会被销毁。
    >
        def	func():	
            a=[]			
            for i in range(5):								
                a.append(i) 
    > 调⽤func()之后，⾸先会创建出空列表a，然后添加5个元素，最 后a会在该函数退出的时候被销毁。
    - 全局
    虽然可以在函数中对全局变量进⾏赋值操作，但是那些变量必须 ⽤global关键字声明成全局的才⾏。
    >  
        a = []
        def myFunction():
            global a
            for index in range(5):
                a.append(index)
        myFunction()
        print(a)
### 4 函数返回值
python函数可以返回多个值。下⾯是⼀个简单的例⼦：
>
    def	f():				
        a = 5				
        b = 6				
        c = 7				
        return	a, b, c
    a, b, c	= f()
此外，还有⼀种⾮常具有吸引⼒的多值返回⽅式——返回字典：
>
    def	f():
        a = 5				
        b = 6				
        c = 7				
        return	{'a':a,	'b':b, 'c':c}
### 5 file
#### 5.1 打开文件方式（读写两种方式）
+ 读文件
为了打开⼀个⽂件以便读写，可以使⽤内置的open函数以及⼀个 相对或绝对的⽂件路径。
>
    In: path = 'examples/segismundo.txt'
    Out:f = open(path)
默认情况下，⽂件是以只读模式（'r'）打开的。然后，我们就可 以像处理列表那样来处理这个⽂件句柄f了，⽐如对⾏进⾏迭代。
>
    for	line in	f:			
        pass
如果使⽤open创建⽂件对象，⼀定要⽤close关闭它。关闭⽂件可以返回操作系统资源：
>
    In:	f.close() 
⽤with语句可以可以更容易地清理打开的⽂件。
> 	
    In: with open(path)	as	f:
            pass	
> 这样可以在退出代码块时，⾃动关闭⽂件。 
+ 写文件
如果输⼊`f =open(path,'w')`，就会有⼀个新⽂件被创建在 `examples/segismundo.txt`，并覆盖掉该位置原来的任何数据。
向⽂件写⼊，可以使⽤⽂件的write或writelines⽅法。例如，我们可以创建⼀个⽆空⾏版的prof_mod.py:
>   
    In:	with open('tmp.txt', 'w') as handle:			.
            handle.writelines(x	for	x in open(path))
#### 5.2 文件对象的操作方法
|模式|说明|
|--|--|
|r|只读模式|
|w|只写模式(删除同名文件)|
|a|附加到现有文件|
|r+|读写模式|
|b|附加说明某模式用于二进制文件，即'rb'或'wb'|
|U|通用换行模式。单独使用或者附加到其他读模式('rU')|

|方法|说明|
|--|--|
|read([size])|以字符串形式返回文件数据，size是读取的字节数|
|readlines([size])|将文件返回为行列表，可选参数size|
|write(str)|将字符串写入文件|
|close()|关闭句柄|
|flush()|清空I/O缓冲区，并将数据强行写回次磁盘|
|seek(pos)|移动到指定的文件位置|
|tell()|以整数形式返回当前文件位置|
|closed|如果文件已关闭，返回True|

#### 5.3 学习对excel及csv文件进行操作
pandas提供了⼀些⽤于将表格型数据读取为DataFrame对象的函数。
|函数|说明|
|--|--|
|read_csv|从文件对象中加载带分隔符的数据，默认分隔符为逗号|
|read_table|从文件对象中加载带分隔符的数据，默认分隔符为制表符|
|read_excel|从Excel或XLSX中读取表哥数据|

> 这些函数有超过50个参数，需要在python数据分析专门学习

### 6 os模块
> OS模块是python自带的关于文件和目录的模块,相关信息见[Python3 OS 文件/目录方法](https://www.runoob.com/python3/python3-os-file-methods.html)