# matplotlib
matplotlib是Python优秀的数据可视化第三方库  
matplotlib库的效果可参考  
http://matplotlib.org/gallery.html  
matplotlib的使用 由各种可视化类构成，内部结构复杂，受matlab库启发，matplotlab.pyplot是绘制种类可视化图形的命令子库，相当于快捷方式  
import matplotlib.pyplot as plt
```
plt.subplot(2,1,1)#可在一个区域中绘制a根横轴，y根竖轴，的c位置绘图
plt.plot([2,3,4,5,1,6])#plot只有一组数的时候默认Y轴
plt.ylabel("Y")#给X,Y轴命名
plt.xlabel("X")
plt.show()
plt.subplot(2,1,2)
plt.plot([0,2,4,6,8,10],[2,3,4,5,1,6])
plt.axis([-5,16,0,7])#修改坐标长度，一二个数字代表X轴，后代表Y轴
plt.savefig('test',dpi=600)#图片保存的名字和清晰度
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/TIM图片20190118220412.png)
### plot
```a=np.arange(10)
plt.plot([a,a+10],[a*1.5,a+10],a,a*2.5,a,a*3.5,a,a*4.5)
```
![avatar](C:/Users/毕少聪大王/Desktop/1.png)
plt.plot(x,y,format_string,**kwargs)
x:x轴数据，列表或数组，可选
y:y轴数据，列表或数组
format_string: 控制曲线的格式字符串，可迁
**kwargs: 第二组或更多的(x,y,format_string)
注意：当绘制多条曲线时，各条曲线的x不能省略
```
 format_string：由颜色字符、风格字符和标记字符组成
颜色字符	说明	颜色字符	说明
'b'	blue	'm'	magenta洋红色
'g'	green	'y'	黄色
'r'	red	'k'	黑色
'c'	cyan青绿色	'w'	白色
'#008000'	RGB某颜色	'0.8'	灰度值字符串


风格字符	说明
'-'	实线
'--'	破折线
'-.'	点划线
':'	虚线
' '	无线条


标记字符	说明	标记字符	说明	标记字符	说明
'.'	点标记	'1'	下花三角标记	'h'	竖六边形标记
','	像素标记(极小点)	'2'	上花三角标记	'H'	横六边形标记
'o'	实心圏标记	'3'	左花三角标记	'+'	十字形标记
'v'	倒三角标记	'4'	右花三角标记	'x'	x标记
'^'	上三角标记	's'	实心方形标记	'D'	菱形标记
'>'	右三角标记	'p'	实心五角标记	'd'	瘦菱形标记
'<'	左三角标记	'*'	星形标记	'|'	垂直线标记

**kwargs: 第二组或更多(x,y,format_string)
color: 控制颜色 如color='green'
linestyle:线条控制 如linestyle='dashed'
marker:标记风格，marker='o'
markerfacecolor:标记颜色，markerfacecolor='blue'
markersize:标记尺寸，markersize=20
...
```
#### pyplot的中文显示
```
import matplotlib
import matplotlib.pyplot as plt 
matplotlib.rcParams['font.family']='SimHei'
plt.plot([3,1,4,5,2])
plt.ylabel('纵轴值')
plt.savefig('test',dpi=600)
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/2.png)
```
属性	说明
'font.family'	用于显示字体的名字
'font.style'	字体风格，正常'normal'或斜体'italic'
'font.size'	字体大小，整数字号或者'large','x-small'

rcParams['font.family']
中文字体	说明
'SimHei'	中文黑体
'Kaiti'	中文楷体
'LiSu'	中文隶书
'FangSong'	中文仿宋
'YouYuan'	中文幼圆
STSong	华文宋体
```
```
import matplotlib
import matplotlib.pyplot as plt 
import numpy as np
matplotlib.rcParams['font.family']='STSong'
matplotlib.rcParams['font.size']=20
a = np.arange(0.0,5.0,0.02)
plt.xlabel('纵轴： 振幅')
plt.ylabel('横轴： 时间')
plt.plot(a,np.cos(2*np.pi*a),'r--')
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/4.png)
```
pyplot的文本显示
 

函数	说明
plt.xlabel()	对x轴增加文本标签
plt.ylabel()	对y轴增加文本标签
plt.title()	对图形本整体增加文本标签
plt.text()	在任意位置增加文本
plt.annotate()	在图形中增加带箭头的注释
```
```
import matplotlib.pyplot as plt 
import numpy as np
a = np.arange(0.0,5.0,0.02)
plt.plot(a,np.cos(2*np.pi*a),'r--')
plt.xlabel('纵轴： 振幅', fontproperties='SimHei', fontsize=20, color = 'green')
plt.ylabel('横轴： 时间', fontproperties='SimHei', fontsize=20)
plt.title(r'正弦波实例$y=cos(2\pi x)$',fontproperties='SimHei',fontsize=25)
plt.annotate(r'$\mu=100$',xy=(2,1),xytext=(3,1.5),
	arrowprops=dict(facecolor='black',shrink=0.1,width=2))
plt.axis([-1,6,-2,2])
plt.grid()
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/5.png)
```
函数	说明
plt.plot(x,y,fmt,...)	绘制一个坐标图
plt.boxplot(data,notch,position)	绘制一个箱形图
plt.bar(left,height,width,bottom)	绘制一个条形图
plt.barh(width,bottom,left,heitht)	绘制一个横向条形图
plt.polar(theta,r)	绘制极坐标图
plt.pie(data,explode)	绘制饼图
plt.psd(x,NFFT=256,pad_to,Fs)	绘制功率谱密度图
plt.specgram(x,NFFT=256,pad_to,F)	绘制谱图
plt.cohere(x,y,NTTF=256,Fs)	绘制X-Y相关性函数
plt.scatter(x,y)	绘制散点图，其中x,y长度相同
plt.step(x,y,where)	绘制步阶图
plt.hist(x,bins,normed)	绘制直方图
plt.contour(X,Y,Z,N)	绘制等值图
plt.vlines()	绘制垂直图
plt.stem(x,y,linefmt,markerfmt)	绘制柴火图
plt.plot_date()	绘制数据日期
```
## 饼图
```
import matplotlib.pyplot as plt 
labels = 'Frogs','Hogs','Dogs','Logs'
sizes = [15,30,45,10]
explode = [0,0.1,0,0]
plt.pie(sizes, explode = explode,labels = labels, autopct = '%1.1f%%',
	shadow = True,startangle = 180)#旋转角度
plt.axis('equal')#让平面图变成竖直
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/6.png)
## 直方图
```
import matplotlib.pyplot as plt 
import numpy as np
np.random.seed(0)
a = np.random.normal(2,10,size=100)#均值，标准差，数量
plt.hist(a,20,normed=1,histtype='bar',facecolor='b',alpha=0.75)
plt.title('Hitogram')
plt.show()
```
![avatar](C:/Users/毕少聪大王/Desktop/7.png)
```
# 直方图
# n, bins, patches = plt.hist(arr, bins=10, normed=0, facecolor='black', edgecolor='black',alpha=1，histtype='bar')
# hist的参数非常多，但常用的就这六个，只有第一个是必须的，后面四个可选

# arr: 需要计算直方图的一维数组

# bins: 直方图的柱数，可选项，默认为10

# normed: 是否将得到的直方图向量归一化。默认为0

# facecolor: 直方图颜色

# edgecolor: 直方图边框颜色

# alpha: 透明度

# histtype: 直方图类型，‘bar’, ‘barstacked’, ‘step’, ‘stepfilled’

# 返回值 ：

# n: 直方图向量，是否归一化由参数normed设定

# bins: 返回各个bin的区间范围

# patches: 返回每个bin里面包含的数据，是一个list
```