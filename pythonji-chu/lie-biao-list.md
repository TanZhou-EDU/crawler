#列表

	一组有序数据的组合就是列表

#列表的操作

##创建列表

1.创建空列表

	列表变量 = []

2.创建单个数据的列表

	列表变量 = [值]

3.创建多个数据的列表

	列表变量 = [值,值,值....]

##列表的普通操作

###列表的特征

1.列表是序列的一种，并且是由序的序列，可以使用有序序列访问方式

2.列表是可以修改的序列

3.列表的数据组成可以是任意一种数据


###列表的访问操作

	列表变量[索引位置]

###添加列表操作

不可以使用索引方式添加

###修改列表操作

	列表变量[索引位置] = 新值

###删除列表操作

	del 列表变量[索引位置]



##列表的序列操作

序列操作包括：索引，分片，序列相加，序列相乘，成员检测，最大值，最小值，长度计算

1.索引操作

	列表 = [值,值，值....]

	格式： 列表变量[索引]

	作用:获取列表中指定位置的值

2.分片操作

	列表 = [值,值,值...]

	方法1：

		列表[:] 

		表示获取列表的所有数据

	方法2：

		列表[开始索引：]

		表示丛开始索引位置截取到列表的最后

	方法3：

		列表[:结束索引]

		表示从列表的开头截取到结束索引位置之前，不包含结束位置

	方法4：

		列表[开始索引:结束索引]

		表示从列表的开始索引位置截取到结束索引位置之前，，不包含结束位置

	方法5：

		列表[开始索引:结束索引:跳步值]

		表示从开始索引位置到结束索引位置之间，不包含索引位置，并且获取数据时索引每次+跳步值来获取，默认跳步值为1

3.序列相加

	格式：列表 = 列表1 + 列表2
	结果：2个列表组成的新列表

	注意: + 两边必须都是列表才可以运算

4.列表相乘

	格式： 列表 = 列表1 * 整数
	
	结果：将列表重复N分组成新的列表

	注意： 数字必须为整数

5.成员资格运算


	格式：数据  in 列表

	作用：检测数据是否在列表当中

	返回值：布尔值



	格式：数据  not in 列表

	作用：检测数据是不是不再列表当中

	返回值：布尔值

##列表的遍历

1.for ... in 遍历
	
	for i in 列表:
   		 print(i)

2.while循环遍历

	length = len(列表)
	i = 0
	
	while i < length:
	    print(列表[i])
	    i += 1

3.双层列表循环

	列表 = [[值1,值2],[值1,值2]，[值1,值2]...]


	格式： for 变量1,变量2 in 列表：

				可以使用变量1和变量2

4.列表内涵： list content

	简单的列表内涵：

		格式：[[变量 for [变量 in 列表]
		作用：遍历列表中的数据并且组成新的列表，如果需要改变原有数据，在最开始i处修改即可
		结果：新的列表

	带有判断的列表内涵

		格式 [变量 for 变量 in 列表 判断条件]	
		作用：遍历列表中的数据，根据判断条件取出符合条件的数据组成新的列表
		结果:新的列表

	多循环带判断的列表内涵

		格式：[[变量1+变量2 for 变量1 in 列表1 for 变量2 in 列表2]
		作用：将列表1中的每个数据和列表2的每个数据进行相加操作，此处可以使用别的操作（变量1+变量2 仅为参考）

		结果：新的列表

		
		格式：[[变量1+变量2 for 变量1 in 列表1 for 变量2 in 列表2 判断条件]
		作用：将列表1中和列表2中每个数据进行操作，但是必须在符合判断条件的前提下进行。
		结果：新的列表

		作用：一行代码  99乘法表

##序列函数
	
len()  获取列表的数据长度
	
	格式：len(列表)
	返回值：整型

max() 获取列表中的最大值

	格式：max(列表)
	返回值：列表中的最大值

min() 获取列表的最小值

	格式：min(列表)
	返回值：列表中的最小值

list() 将其他序列类型转化为列表

	格式：list(序列)
	返回值：列表

##列表专用函数

append() 在列表的最后追加新数据

	格式： 列表.append(数据)
	返回值：无
	注意：该操作直接改变原有列表

insert() 在列表指定的位置插入数据

	格式：列表.insert（索引,数据）
	返回值：无
	注意：该操作直接改变原有列表

pop() 在列表中移除一个元素

	格式：列表.pop()
	返回值:移除掉的元素
	注意：移除列表最后的元素

	格式：列表.pop(索引)
	返回值：:移除掉的元素
	注意：移除列表中指定索引的元素

	无论哪种格式都直接改变原有列表

remove() 在列表中移除指定的值的元素
	
	格式:列表.remove(值)
	返回值：无
	
	注意：该操作直接改变原有列表

clear() 清空列表

	格式：列表.clear()
	返回值：无

	
	注意：该操作直接改变原有列表

reverse() 列表反转

	格式：列表.reverse（）
	返回值：无

	注意：该操作直接改变原有列表


extend() 在原有列表最后追加新的序列

	格式:列表.extend(序列类型)
	返回值：	无

	注意：该操作直接改变原有列表

count() 计算指定值在列表中出现的次数

	格式: 列表.count(值)
	返回值：整数

copy() 复制原有列表

	格式: 列表.copy()
	返回值：新的列表

#列表函数

|函数 | 作用 |返回值| 示例  |
| :--------| :-----:|:----: |:----: |
| append|在列表最后追加数据|无|[].append(数据)|
|insert|在列表指定位置插入数据|无|[].insert(索引，数据)|
|pop|在列表中移除一个元素<br>默认移除掉最后一个|移除掉的元素|[].pop(索引）|
|remove|在列表中移除指定值元素|无|[].remove('foo')|
|clear|清空列表|无|[].clear()|
|reverse|列表反转|无|[].reverse()|
|extend|扩展原有列表|无|[].extend(序列类型)|
|count|计算指定值在列表中出现次数|整数|[].count(值)|
|copy或[:]|复制原有列表|新的列表|[].copy()|
