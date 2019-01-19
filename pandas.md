# pandas
##  series
```
import pandas as pd
a=pd.Series([9,8,7,6])#产生了自动索引从0开始
print(a)
b=pd.Series([9,8,7,6],index=['a','b','c','d'])#自定义索引，如果放在第二列，可以省略Index
print(b)
输出：
0    9
1    8
2    7
3    6
dtype: int64
a    9
b    8
c    7
d    6
dtype: int64
#2从字典创建
d=pd.Series({'a':1,'b':2})
print(d)

a    1
b    2
dtype: int64

e=pd.Series({'a':9,'b':8,'c':7},index={'c','a','b','d'})#index从字典中选取确定值
print(e)

b    8.0
d    NaN
a    9.0
c    7.0
dtype: float64

#从发ndarray创建类型
import numpy as np
n=pd.Series(np.arange(5))
print(n)

0    0
1    1
2    2
3    3
4    4
dtype: int32

m=pd.Series(np.arange(5),index=np.arange(9,4,-1))#index的值需要和arange数量相对应，不然报错
print(m)

9    0
8    1
7    2
6    3
5    4
dtype: int32
```
### 基本操作
```
b=pd.Series([9,8,7,6],index=['a','b','c','d'])
print(b.index)
print(b.values,type(b.values))#$是ndarray类型

Index(['a', 'b', 'c', 'd'], dtype='object')
[9 8 7 6] <class 'numpy.ndarray'>

print(b['b'])
print(b[1])#可以理解为自己创造的索引和自动索引都存在
print(b[['c','d',0]])#如果是混用索引就自动认为是自定索引，在这里注意是两层[]，索引又是一个列表

8
8
c    7.0
d    6.0
0    NaN
dtype: float64

b=pd.Series([9,8,7,6],index=['a','b','c','d'])
b[:3]
print([b>7])
print(b[b>7])#切片和运算都是生成Serise,如果只是选择一个值就只返回一个值
np.exp(b)

[a     True
b     True
c    False
d    False
dtype: bool]
a    9
b    8
dtype: int64
a    8103.083928
b    2980.957987
c    1096.633158
d     403.428793
dtype: float64

'c' in b#判断的自定义索引，不会判断自动索引

True

b.get('f',100)#如果有f则返回f，否则返回100

100

#Series对齐问题
a=pd.Series([1,2,3],['c','d','e'])
b=pd.Series([9,8,7,6],['a','b','c','d'])#会自动对齐不同索引的数
print(a+b)

a    NaN
b    NaN
c    8.0
d    8.0
e    NaN
dtype: float64

#对象和索引都可以有名字
b.name="对象"
b.index.name="索引表"
print(b)

索引表
a    9
b    8
c    7
d    6
Name: 对象, dtype: int64

#datafreame(多维)多列数据公用一个索引
#纵向：index(axis=0) 横向：column(axis=1)
#1二维ndarray对象创建
d=pd.DataFrame(np.arange(10).reshape(2,5))
print(d)

   0  1  2  3  4
0  0  1  2  3  4
1  5  6  7  8  9

#2从字典创建
dt={'one':pd.Series([1,2,3],index=['a','b','c']),
    'two':pd.Series([9,8,7,6],index=['a','b','c','d'])}
d=pd.DataFrame(dt)#键自动成为列索引
print(d)
c=pd.DataFrame(dt,index=['b','c','d'],columns=['two','three'])
print(c)

   one  two
a  1.0    9
b  2.0    8
c  3.0    7
d  NaN    6
   two three
b    8   NaN
c    7   NaN
d    6   NaN

#从列表类型的字典创建
d1={'one':[1,2,3,4],'two':[4,5,6,7]}
d=pd.DataFrame(d1,index=['a','b','c','d'])
print(d)

   one  two
a    1    4
b    2    5
c    3    6
d    4    7

d1={'one':[1,2,3,4],'two':[4,5,6,7]}
d=pd.DataFrame(d1,index=['a','b','c','d'])
print(d)
d.index=(1,2,3,4)
print(d)
d.columns=(1,2)#单纯改名字
print(d)

   one  two
a    1    4
b    2    5
c    3    6
d    4    7
   one  two
1    1    4
2    2    5
3    3    6
4    4    7
   1  2
1  1  4
2  2  5
3  3  6
4  4  7

d1={'one':[1,2,3,4],'two':[4,5,6,7]}
d=pd.DataFrame(d1,index=['a','b','c','d'])
print(d)
d2=d.reindex(index=['1','2','3','4'])#返回一个新的dataframe假如是新的数，Index和colunms都可以用
print(d2)

   one  two
a    1    4
b    2    5
c    3    6
d    4    7
   one  two
1  NaN  NaN
2  NaN  NaN
3  NaN  NaN
4  NaN  NaN
```
### 插入
```col=d.columns.insert(3,'新增')
print(col)
d3=d.reindex(columns=col,fill_value=200)#让columns等于col而且让空的值等于二百
print(d3)


Index(['one', 'two', '新增'], dtype='object')
   one  two   新增
a    1    4  200
b    2    5  200
c    3    6  200
d    4    7  200
```
### 删除
```d4=d.drop('a')#初始自动删除index
print(d4)
d5=d.drop('one',axis=1)#设置axis可以删除columns
print(d5)

   one  two
b    2    5
c    3    6
d    4    7
   two
a    4
b    5
c    6
d    7

```
```重新索引
.reindex(index=None,columns=None,...)


参数	说明
index, columns	新的行列自定义索引
fill_value	重新索引中，用于填充缺失位置的值
method	填充方法，ffill当前值向前填充，bfill向后填充
limit	最大填充量
copy	默认True，生成新的对象，False时，新旧相等不复制
索引类型
Series和DataFrame的索引是Index类型，
Index对象是不可修改对象类型


方法	说明
.append(idx)	连接另一个Index对象，产生新的Index对象
.diff(idx)	计算差集，产生新的Index对象
.intersection(idx)	计算交集
union(idx)	计算并集
delete(loc)	删除loc位置处的元素
insert(loc,e)	在loc位置上增加一个元素e
.drop方法能够删除Series和DataFrame指定行或列索引
```
### 计算
```
a=pd.DataFrame(np.arange(12).reshape(3,4))
print(a)
b=pd.DataFrame(np.arange(20).reshape(4,5))
print(b)
print(a+b)#只对同时都有值的地方进行运算
print(a*b)
c=a+b

   0  1   2   3
0  0  1   2   3
1  4  5   6   7
2  8  9  10  11
    0   1   2   3   4
0   0   1   2   3   4
1   5   6   7   8   9
2  10  11  12  13  14
3  15  16  17  18  19
      0     1     2     3   4
0   0.0   2.0   4.0   6.0 NaN
1   9.0  11.0  13.0  15.0 NaN
2  18.0  20.0  22.0  24.0 NaN
3   NaN   NaN   NaN   NaN NaN
      0     1      2      3   4
0   0.0   1.0    4.0    9.0 NaN
1  20.0  30.0   42.0   56.0 NaN
2  80.0  99.0  120.0  143.0 NaN
3   NaN   NaN    NaN    NaN NaN
one	two
a	True	True
b	True	False
c	True	False
d	True	False

a.add(b)

	0	1	2	3	4
0	0.0	2.0	4.0	6.0	NaN
1	9.0	11.0	13.0	15.0	NaN
2	18.0	20.0	22.0	24.0	NaN
3	NaN	NaN	NaN	NaN	NaN

b.add(a,fill_value=0)#add,sub,mul,div加减乘除

	0	1	2	3	4
0	0.0	2.0	4.0	6.0	4.0
1	9.0	11.0	13.0	15.0	9.0
2	18.0	20.0	22.0	24.0	14.0
3	15.0	16.0	17.0	18.0	19.0

方法 	说明
.add(d,**argws)	类型间加法运算，可选参数
.sub(d,**argws)	类型间减法运算，可选参数
.mul(d,**argws)	类型间乘法运算，可选参数
.div(d,**argws)	类型间除法运算，可选参数
```