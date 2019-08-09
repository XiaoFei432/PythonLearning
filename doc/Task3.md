### dict字典
字典可能是Python最为重要的数据结构。它更为常⻅的名字是哈希映射或关联数组。
#### 定义
它是键值对形式的⼤⼩可变集合，键和值都是Python对象。
#### 创建
+ 使用大括号`{}`，用冒号分隔键和值。
>
    In: dictt = {'key1':5,'key2':'hello world',5:[2,3,[4,5]]}
        print(len(dictt))
        print(dictt)
    Out:3
        {'key1': 5, 'key2': 'hello world', 5: [2, 3, [4, 5]]}
+ 使用键/值列表创建
>
    In: key_list = ['key1', 'key2', 5]
        value_list = [5, 'hello world', [2, 3, [4, 5]]]
        empty_dict = {}
        print(list(zip(key_list, value_list)))
        for key , value in zip(key_list, value_list):
            empty_dict[key] = value
        print(empty_dict)
    Out:[('key1', 5), ('key2', 'hello world'), (5, [2, 3, [4, 5]])]
        {'key1': 5, 'key2': 'hello world', 5: [2, 3, [4, 5]]}
+ 使用二维元组创建
>   
    In: map_tuple = (('key1',4),('key2',5))
        map_tuple2 = [('key1',4),('key2',5)]
        map_dict = dict(map_tuple)
        map_dict2 = dict(map_tuple2)
        print(map_dict)
        print(map_dict2)
    Out:{'key1': 4, 'key2': 5}
        {'key1': 4, 'key2': 5}

#### 字典的方法

|序号|函数|描述|
|--|--|--|
|1|radiansdict.clear()|删除字典内所有元素|
|2|radiansdict.copy()|返回一个字典的浅复制|
|3|radiansdict.fromkeys()|创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值|
|4|	radiansdict.get(key, default=None)|返回指定键的值，如果值不在字典中返回default值|
|5|key in dict|如果键在字典dict里返回true，否则返回false|
|6|radiansdict.items()|以列表返回可遍历的(键, 值) 元组数组|
|7|radiansdict.keys()|返回一个迭代器，可以使用 list() 来转换为列表|
|8|radiansdict.setdefault(key, default=None)|和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default|
|9|radiansdict.update(dict2)|把字典dict2的键/值对更新到dict里|
|10|radiansdict.values()|返回一个迭代器，可以使用 list() 来转换为列表|
|11|pop(key[,default])|删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值。|
|12|popitem()|随机返回并删除字典中的一对键和值(一般删除末尾对)。|

### 集合
集合可以理解为只有键没有值的字典，没有空集这个说法和定义。
#### 特性
包含⽆序的不可重复的元素。
#### 创建
通过大括号`{}`或者set函数，如下：
>
    sett = {2,3,4,5}
    sett = set([2,3,4,5])
#### 方法

|方法|	描述|
|--|--|
|add()|	为集合添加元素|
|clear()|	移除集合中的所有元素|
|copy()|	拷贝一个集合|
|difference()|	返回多个集合的差集|
|difference_update()|移除集合中的元素，该元素在指定的集合也存在。|
|discard()|	删除集合中指定的元素|
|intersection()|	返回集合的交集|
|intersection_update()|	返回集合的交集。|
|isdisjoint()|	判断两个集合是否包含相同的元素，如果没有返回 True，否则返回 False。|
|issubset()	|判断指定集合是否为该方法参数集合的子集。|
|issuperset()|	判断该方法的参数集合是否为指定集合的子集|
|pop()	|随机移除元素|
|remove()|	移除指定元素|
|symmetric_difference()|	返回两个集合中不重复的元素集合。|
|symmetric_difference_update()	|移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。|
|union()	|返回两个集合的并集|
|update()|	给集合添加元素|
### 判断语句（要求掌握多条件判断）
多条件if判断语句格式如下:
>
    if 条件1:
        pass
    elif 条件2:
        pass
    else:
        pass
### 三目表达式
条件为真时的结果 if 判段的条件 else 条件为假时的结果 
>
    In: a = 1
        b = True if a>0 else False
        print(b)
    Out:true
### 循环语句
+ while循环，格式如下:
>  
    while 条件:
        语句1
    else:
        语句2
+ for循环，格式如下:
>
    for 索引 in 范围:
        语句
> 利用len()和range()遍历列表
>
    list = [1,2,3,4,5]
    for index in range(len(list))
        print(list[index])
        
    # 一般遍历方法
    for index in list:
        print(index)