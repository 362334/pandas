# python基础
***因为自己学过，所以其实基本语法都知道，来东软学只是为了让自己学的系统一点，所以上课比较轻松而且还算认真，笔记就写一些自己不大熟或者说自己认为比较重要的点***
## 输入输出
### 输入
input输入所返回的值的字符串类型的，这就意味着假如需要对返回的值进行数字计算的时候需要改变类型
```
a=input()
int(a)+5
```
### 输出
输出有和很多种方法自己比较习惯用%这种类型的
```
name=input("请输入你的名字")
age=input("请输入你的年龄")
hight=input("请输入你的身高")
print("我叫%s,今年%d,身高%f"%(name,int(age),float(hight))))
输出 
请输入你的名字bi
请输入你的年龄18
请输入你的身高12.5
我叫bi,今年18,身高12.500000
#可以避免类型不匹配造成的报错
a='1'
b='2'
c='3'
b=f'hello{a},{b},{c}'
print(b)
输出
hello1,2,3
#formmat
s='tm{},age{}'.format(12,13)
print(s)
s='tm{1},age{0}'.format(12,13)
print(s)
s='tm{name},age{age}'.format(age=12,name=13)
print(s)
输出
tm12,age13
tm13,age12
tm13,age12
```
## 字符串
### 字符串是可以根据索引来分割的  
[开头：结尾：步数 ] markdown换行是空格+空格+回车我日
```
a='hello world'
print(a[0])
print(a[2])
print(a[1:])
print(a[:3])
print(a[2:5])
print(a[:-1])
print(a[4:0])
print(a[4:0:-2])
输出
h
l
ello world
hel
llo
hello worl
ol
```
### 字符串的一些基本函数
```
s="bishaocong"
print(s.capitalize())
print(s.lower())
print(s.upper())
print(s.swapcase())
输出：
Bishaocong
bishaocong
BISHAOCONG
BISHAOCONG
#使特殊符号或者数字隔开的字符首字母大写
s="bi,shao,cong"
print(s.title())
print(s.center(25,'*'))
print(len(s))
输出：
Bi,Shao,Cong
*******bi,shao,cong******
12
#检验邮箱合法性14242333472@qq.com
#find通过元素找索引，如果找不到返回-1  index找不到报错
s="1424233472@qq.com"
print(s.find("@"))
print(s.find("9"))
输出：
10
-1
#字符串对空格的处理
#strip(前后) rstrip（右） lstrip（左）
s='  bishaocong***    '
print(s)
print(s.strip())
输出：
 bishaocong***    
bishaocong***
#split切割，返回是一个列表
s="bi,shao,cong"
print(s.split())
输出：
['bi,shao,cong']
```
### 列表
list基本就那些函数，切片，最近知道原来list里面是可以存函数的
```
#list里面可以包含函数
list=[]
print(list,type(list))
list=[1,False,[1,2],input]
print(list)
输出：
[] <class 'list'>
[1, False, [1, 2], <bound method Kernel.raw_input of <ipykernel.ipkernel.IPythonKernel object at 0x0000026378FA9DD8>>]
list=[1,2,3]+[4,5,6]
print(list)
print(list*3)
print(1 in list)
print(min(list))
print(list.index(2))
print(list.count(1))
#del list[0]
list[0:2]='123'
print(list)
list.append(1)
print(list)
print(list.insert(1,3))
list.extend([1,2,3])
print(list)
b=list.pop(3)
print(b)
list.remove(1)
print(list)
list.reverse()
print(list)
输出：
[1, 2, 3, 4, 5, 6]
[1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6]
True
1
1
1
['1', '2', '3', 3, 4, 5, 6]
['1', '2', '3', 3, 4, 5, 6, 1]
None
['1', 3, '2', '3', 3, 4, 5, 6, 1, 1, 2, 3]
3
['1', 3, '2', 3, 4, 5, 6, 1, 2, 3]
[3, 2, 1, 6, 5, 4, 3, '2', 3, '1']
```
### 元组
自己简单的认为就是不能修改的List  
一些稍微需要注意的地方
```
a=10,元组单独一个数的时候要加，
print(type(a))
输出：
<class 'tuple'> 
#但我们操作元组的时候，如果元组非空，我们可以省略括号
a=1,2,3
print(type(a))
print(a)
输出：
<class 'tuple'>
(1, 2, 3)
#元素解包
a,b,c,d=10,20,30,40
print(a,b,c,d)
输出：
10 20 30 40
#*代表剩下的所有
a,b,*c=10,20,30,40
print(a,b,c)
输出：
10 20 [30, 40]
#元组儿子元素不能改，孙子元素可以改
a=(1,2,3,[4,5,6])
a[3][1]=7
print(a)
输出：
(1, 2, 3, [4, 7, 6])
```
### 字典
```
#字典 dict，key不能重复切不可变（int str bool tuple...），如果重复，后面会替换前面的
d=dict([('name','zhangsan'),('age',10)])
print(d)
d=dict(name='zhangsan',age=10)
print(d)
输出：
{'name': 'zhangsan', 'age': 10}
{'name': 'zhangsan', 'age': 10}
#长度
print(len(d))
print(d.get('name'))
输出：
2
zhangsan
#setdefault 如果key已经存在返回key值 返回key的value值，如果不存在，则添加Key设置value
a={1:2,2:3,3:4}
b=a.setdefault(1,'helloworld')
print(b)
print(d.setdefault('name','helloworld'))
d={'a':1,'b':2,'c':3}
d1={'d':4,'e':5,'f':6}
print(d.update(d1))
print(d)
输出：
2
helloworld
None
{'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5, 'f': 6}
#pop第二个属性值为假如没有键则返回的值
a=d1.popitem()
print(a)
c=d.pop('a1','moone')
print(c)
输出：
('e', 5)
moone
print(d.keys(),type(d.keys()))
print(d.values(),type(d.values()))
输出：
dict_keys(['a', 'b', 'c', 'd', 'e', 'f']) <class 'dict_keys'>
dict_values([1, 2, 3, 4, 5, 6]) <class 'dict_values'>
同时输出键值对
for a,b in d.items():
    print(a,b)
a 1
b 2
c 3
d 4
e 5
f 6
```
### set
```
#set 无序，不重复，与列表相似，只能储存不可变对象
s={1,2,3,3,6,2,9,8,7}
print(s)
s.add(10)
print(s)
a=s.pop()#删除第一个
print(a)
print(s)
a={1,2,3,4,5}
b={3,4,5,6,7,8}
print(a & b)
print(a | b)
print(a-b)
print(a^b)
输出：
{1, 2, 3, 6, 7, 8, 9}
{1, 2, 3, 6, 7, 8, 9, 10}
1
{2, 3, 6, 7, 8, 9, 10}
{3, 4, 5}
{1, 2, 3, 4, 5, 6, 7, 8}
{1, 2}
{1, 2, 6, 7, 8}
```
### 操作文件
```
#文件操作  1)文件的路径   2）操作文件的编码方式   3）操作方式
#1）打开文件 2）文件读写保存 3）文件关闭
a=open('2/2.1.txt')
print(a.read(3))
print(a.read(3))#从光标位置开始继续读
a.close()
输出：
hel
lo
#with as 语句 with语句结束时自动关闭
try:
    with open('2/2.11.txt') as f:
        print(f.read())
except FileNotFoundError:
    print('file not found')
输出：
file not found
with open('2/2.1.txt') as f:
    t=100
    while True:
        a=f.read(t)
        print(a)#read()里面可以填写读多少个字符
        if not a:
            break#大文件读取
输出：
hello
#open方式打开时，默认是文本打开的，但是open方法飞编码是None，所以我们在处理文本的时候，必要制定文本的编码方式
with open('2/2.1.txt') as f:
    a=f.readlines()#readlines() 方法用于读取所有行(直到结束符 EOF)并返回列表，该列表可以由 Python 的 for... in ... 结构进行处理。如果碰到结束符 EOF 则返回空字符串。
    print(len(a))
    for i in a:
        print(i)
输出：
3
hello

123

321
f=open('2/2.1.txt',mode='r+',encoding='utf-8')
print(f.read())
f.write('nihao')
输出：
hello
123
321nihaonihao
#open方法读取的是问呢文件的时候，read(size)读的是字符，读取的是二进制文件的时候，read(size)读取的是字节
#seek()调整光标
f=open('2/2.1.txt',mode='r+',encoding='utf-8')
f.write('nihao')
print(f.tell())
f.seek(0)
print(f.tell())
print(f.read())
输出：
5
0
nihao
123
321nihaonihaonihao
#使用文件的方式存储用户名，密码
#第一步 注册 二 while<3
print("注册")
zh=input("账号:")
mm=input("密码:")
with open('123.txt','a+',encoding='utf-8') as f:
    f.write(zh)
    f.write(mm)
    f.seek(0)
    m=f.read()
print("登录")
i=0
while i<3:
    zh1=input('账号:')
    mm1=input('密码:')
    with open('123.txt','a+',encoding='utf-8') as f:
        if i>=3:
            break
        elif zh1 and mm1 in m:
            print("登陆成功")
            break
        else:
            print("账号或密码错误")
            i+=1
输出：
注册
账号:123
密码:123
登录
账号:1232
密码:1232
登陆成功
```
### 异常
```
'''try:
    代码块（可能发生错误的语句）
except 异常的类型 as 异常的别名:
    代码块（提醒性信息）
except Exception(剩下的所有异常) as 异常的别名:
    代码块（提醒性信息）
else:
    代码块
finally:
    代码块（总会执行的）'''
print("helloworld")
a=int(input('请输入数字'))
try:
    print(10/a)
except ZeroDivisionError as chuf:
    print('0不能作为除数')
输出：
helloworld
请输入数字0
0不能作为除数
def add(a,b):#(自己定义如果a<0则抛出异常)
    if a<0:
        raise Exception
if __name__ =='__main__':
    add(-1,-2)
Exception                                 Traceback (most recent call last)
<ipython-input-10-9d877eede2b2> in <module>()
      3         raise Exception
      4 if __name__ =='__main__':
----> 5     add(-1,-2)

<ipython-input-10-9d877eede2b2> in add(a, b)
      1 def add(a,b):
      2     if a<0:
----> 3         raise Exception
      4 if __name__ =='__main__':
      5     add(-1,-2)

Exception:
```
### 函数
```
def test():
    print('A')
    print('B')
test()
`

print(test)#输出函数发现有地址，所以test属于函数对象，test()调用对象
输出：
A
B
<function test at 0x0000027B2A8309D8>
#默认参数是针对形参的,位置参数
def fn(a=1,b=2,c=3):
    print('a',a)
    print('b',b)
    print('c',c)
fn(1,2)
输出：
a 1
b 2
c 3
#关键字传参
def fn(a=1,b=2,c=3):
    print('a',a)
    print('b',b)
    print('c',c)
fn(1,c=22)
#当我们把位置参数和关键字参数混合使用，必须将位置参数写到前面
输出：
a 1
b 2
c 22
#不定长参数 可变参数
def sum(*num):#装箱
    print(type(num))#元组类型
sum(1,2)
输出：
<class 'tuple'>
def sum(*num):
    c=0
    for i in num:
        c+=i
    print(c)
sum(1,2)
输出：
3
def sum(a,b,*num):
    print(a)
    print(b)
    c=0
    for i in num:
        c+=i
    print(c)
sum(1,2,3,4,5,6)
输出：
1
2
18
def sum(a,*num,b):
    print(a)
    print(b)
    c=0
    for i in num:
        c+=i
    print(c)
sum(1,2,3,4,5,b=6)#假如放中间的话需要确认
输出：
1
6
14
def sum(a,b,**c):
    print('a',a)
    print('b',b)
    print('c',c,type(c))
sum(1,2,d=3)
输出：
a 1
b 2
c {'d': 3} <class 'dict'>
def fn(a=1,b=2,c=3):
    print('a',a)
    print('b',b)
    print('c',c)
t=(1,2,3)
fn(*t)#(拆箱)
输出：
a 1
b 2
c 3
def sum(**c):
    print('c',c,type(c))
d={
    'k':1,
    'm':2
}
sum(**d)
输出：
c {'k': 1, 'm': 2} <class 'dict'>
def fn():
    print(1,2)
    return 1,2#返回是元组
a=fn()
print(a)
输出：
1 2
(1, 2)



