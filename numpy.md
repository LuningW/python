numpy用c语言写的，快
用矩阵运算会非常快

	• numpy属性 
  ndim:矩阵的维度n
  shape：矩阵的形状（row,colum）
  size: row*colum

Import numpy as np  
#一般会把numpy简化成np引入模块

a = np.array([  [],[]  ])
Print(a)
	• numpy的Array创建
keyword：
array：创建数组
dtype：指定数据类型
zeros：创建数据为0
ones：创建数据接近1
empty：创建数据接近0
arrage：按照指定范围创建数据
linespace：创建线段
Reshape(row,colum):重新创建矩阵

	- 创建数组array
```
 a= np.array([2,23,4])   #list 1d  1维
 print(a)
#[2,23,4]
```
	- 指定数据dtype
```
a= np.array([2,23,4],dtype=np.int)  
 print(a.dtype)
#int 64
#int 没有特殊说明默认为64位

a= np.array([2,23,4],dtype=np.int32)  
 print(a.dtype)
#int 32

a= np.array([2,23,4],dtype=np.float)  
 print(a.dtype)
#float 64
#float 没有特殊说明也默认为64位
```

|数据类型|	类型简写|		说明|
|int_|	 		默认整型64位|
|intc|	 		等价于long的整型|
|int8|	i1|	(int最小字节)	字节整型，1个字节，范围：[-128,127]|
|int16|	i2|		整型，2个字节，范围：[-32768,32767]
int32	i4		整型，4个字节，范围：[-2^31,2^31-1]
int64	i8		整型，8个字节，范围：[-2^63,2^63-1]
unit8	u1		无符号整型，1个字节，范围：[0, 255]
unit16	u2		无符号整型，2个字节，范围：[0, 65535]
unit32	u4		无符号整型，4个字节，范围：[0, 2^32-1]
unit64	u8		无符号整型，8个字节，范围：[0, 2^64-1]
bool_	 		以一个字节形式存储的布尔值（True 或者 False）
float_	 		float64简写形式
float16	F2		半精度浮点型（2字节）：1符号位+5位指数+10位的小数部分
float32	F4或者f		单精度浮点型（4字节）：1符号位+8位指数+23位的小数部分
float64	F8或者d		双精度浮点型（8字节）：1符号位+11位指数+52位小数部分
complex_	c16		complex128的简写形式
complex64	c8		复数，由两个32位的浮点数来表示
complex128	c16		复数，由两个64位的浮点数来表示
object	O		Python对象类型
String_	S		固定长度的字符串类型（每个字符1个字节），比如：要创建一个长度为8的字符串，应该使用S8
Unicode_	U		固定长度的unicode类型的字符串（每个字符串占用字节数由平台决定），长度定义类似String_类型

	- 创建特定的矩阵
	- #注意括号的使用！！！
```
#创建一般矩阵
 a= np.array([[2,23,4],[2,32,4]])   #2d,2*3
 print(a)

#[[2,23,4]
   [2,32,4]]
```

```
#创建全零矩阵
 a=np.zeros((3,4))   #数据全为0，3*4   !注意zeros()本身就有括号的，里面的行列再用一个括号括起来
 print(a)
 #
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

```
#创建全一矩阵，同时也能指定特定数据的dtype
a=np.ones((3,4),dtype=np.int64)
print(a)
print(a.dtype)

#
[[1 1 1 1]
 [1 1 1 1]
 [1 1 1 1]]
int64
```

```
#创建全空矩阵——空矩阵的意思是连续的，非常接近于0但不是0的数
 a=np.empty((3,4))
 print(a)
#
[[6.95172316e-310 6.95172317e-310 6.95172317e-310 6.95172317e-310]
 [6.95172317e-310 6.95172317e-310 6.95172317e-310 6.95172317e-310]
 [6.95172317e-310 6.95172318e-310 6.95172316e-310 6.95172316e-310]]
```
或者还可以指定数数据字节数
```
a=np.empty((3,4),dtype=np.float16)
print(a)
#
[[8.057e-03 8.057e-03 8.057e-03 8.057e-03]
 [8.057e-03 4.900e+01 1.105e+04 2.794e+03]
 [1.394e+03 8.575e-03 1.511e+04 7.296e+03]]
```

```
#使用arange创建连续数组
a = np.arange(10,20,2)    #10-19，步长为2的数组
b = np.arange(12)
print(a,b)

#[10 12 14 16 18] [ 0  1  2  3  4  5  6  7  8  9 10 11]
```

```
#reshape改变矩阵形状
```
 a= np.arrage(12).reshape((3,4))
 print(a)
# 
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
>>> 

```
#使用linspace创建线段型矩阵
```
 a= np.linspace(1,10,5)    #开始端1，结束端10，被分割成5个数据，生成线段   !注意这里的区间~  如果是arange（）,左闭右开，但是linspace（）是左闭右闭
 print(a)
 #
[ 1.    3.25  5.5   7.75 10.  ]   #(10-1)/(5-1)
```
#linspace+reshape效果
```
 a= np.linspace(1,10,6).reshape(2,3)
 print(a)
 #
[[ 1.   2.8  4.6]
 [ 6.4  8.2 10. ]]   #(10-1)/(6-1)
```

	§ Numpy基础运算
	```
	Import numpy as np
	 a= np array([10,20,30,40])
	 b= np.arange(4)
	```
	- 两个矩阵减法
	- 两个矩阵乘法
	- 两个矩阵加法
	- 矩阵乘方
	- 矩阵 数学工具
矩阵 print中的逻辑判断![image](https://user-images.githubusercontent.com/93080608/166262684-a67599f2-8a95-42a7-b026-d52a968f5bf9.png)
