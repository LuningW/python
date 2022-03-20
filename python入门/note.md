# print()
一些常见的使用
> 单双引号
```
print("we're going to do something")
print('we're going to do somthing')
```
> 内容里有'
```
print('I\'m a girl.')
print("I'm a girl.")
```
> +
```
print('apple'+'4')
```
output：apple4
> +不能连接字符串+数字，可以把数字用str()转换为字符串
```
 print('apple'+str(4))
```
output：apple4
> 输出值
```
 print(1+2) 
 print(int('1')+2)
```
output:3
```
print('1+2')
```
输出1+2
```
print(float('1.2')+2)
print(1.2+2)
```
 输出3.2
> ，使用
```
print(a,b,c)
Print('the c is',c)
```
> 输出函数
```
def fun():
     a=10
   print(a)
   return a+10
```
output:
- 10
- 20

# 基础数学运算
> +-*/
> 乘方**，x**y
> 取余%
> 取正//
```
9%2=1
9//2=4
```

# 自变量variable
```
Apple=1
Print(apple)
```
output：1
```
 apple=1+2
 print(apple)
```
Output:3
```
 a,b,c=1,2,3
Print(a,b,c)
```
输出为1 2 3

# 循环
- while
```
Condition=1
While condition <10
   print(condition)
   condition=condition+1
```
> 无限循环用ctrl C终止
- for
> 给定集合
```
example_list=[1,2,3,4,56,7,12,543,876,12,3,2,5]
for i in example_list：
    print(i)
```
> 给定区间range()
```
# 不给步长默认为1
for i in range(1,10):
     print(i)
# 给步长
for i in range(1,10,2):
    print(i)
```
output：1，3，5，7，9
# 条件
- if
```
X=1
Y=2
Z=3

if x>y:
   print('x is greater than y')

if x>y>z:
   print('x is greater than y,and y is greater than z')
```
[ python可以理解连续的逻辑关系，比如x<y>z ]
> 相等==，不相等！=
- if&else
```
If x>y:
  print('x is greater than y')
 else:
  print('x is less than y')
```
- if elif else
```
X=-2
if x>1:
  print('x>1')
elif x<-1:
  print('x<-1')
elif x<1:
 print('x<1')
else：
 print('x=1')
```
output:X<-1
> 只会满足第一个符合的语句，之后跳出整体的条件模块

# def
- 定义函数
```
 def function():
       a=1+2
       print(a)
##函数调用
function（）
```
- 函数参数
```
 def fun(a,b):
    c=a*b
   print('the c is',c)
#函数调用
 fun(2,5)
##或者fun(a=2,b=5)，必须和函数中定义的形参名保持一致
```
- 默认函数参数
```
def sale_car(price,color,brand,second_hand):  
    print('price:'price,'color:',color,'second_hand:',second_hand)

###函数调用
sale_car(1000,'red','carmy',True)
```
或者
```
 def sale_car(price,color='red',brand='carmy',second_hand=False):  
     print('price:'price,'color:',color,'second_hand:',second_hand)

###函数调用
sale_car(1000)
```
> 如果想重新定义别的形参，就   sale_car(1234,'blue')

> Ps:在def函数时，形参表中未被初始赋值的形参一定要放在赋值过的形参前，否则会被报错
```
def sale_car(price=100,color='red',brand='carmy',second_hand):
```
这样在运行时会被报错，因为second_hand这一形参未被初始赋值，却放在了一众被赋值的形参的后面。

# global/local变量
- 局部变量
def中定义一个局部变量，这个变量a中能在fun中有效，除了这个函数，a这个变量就不再是函数中局部的变量a了
- 全局变量
在外部调用一个在局部里修改了的全局变量
1.首先在外部定义一个全局变量
```
a=none
```
2.再在fun（）中声明这个a是来自外部的变量
```
  global a
```
3.在fun()中对全局变量a修改后，效果会被施加到外部的a上

# 读写文件
- \n换行符
```
Text='This is my first test.\nThis is the second line.' 
print(text)
```
Output:
> This is my first test.
> This is the second line.
- open和读文件方式
> 使用open能够打开一个文件，open的第一个参数为文件名+路径,第二个参数是要以什么方式打开它，w为可写方式,r为可读方式
> 如果说没有找到对应的文件，则将以设定的方式创建一个 新的文件，并命名
```
my_file=open('my file.txt','w') 
my_file.write(text)#该语句会写入先前定义好的text
my_file.close()#关闭文件
```
- \t  tab对齐
>使用\t能够达到tab对齐的效果(一般tab为八个空格键长度)
'''
 text='\tThis is my first test.\n\tThis is my second line.'
 print(text)
 ```
 output:
 >     This is my first test.
 >     This is my second line.
 - 给文件增加内容的文件打开方式
 ```
 append_text='\nThis is appended file.' 
 # a表示用增加内容的形式打开文件
 my_file=open('my file.txt','a')
 my.file.close()
 ```
> ps：如果是使用w方式打开，则文件中原来所有的内容将清空，文件中只有新增加的内容
- 读文件内容 .read()
> 使用file.read()能读取到文本中的所有内容
```
file=open('my file.txt','r')
Content=file.read()
print(content)
```
- 按行读取 .readline()
> file.readline()读取的内容和使用次数有关，使用第二次，读取的是文本的第二行，以此类推

- 读取所有行
> 读取所有行并使用像for一样的迭代器迭代结果
```
# 不用for循环
file = opem('my.file.txt','r')
 content=file.readlines()
 prinf(content)
```
output:
> 直接将所有行输出，并且在输出内容外面阔上  [    ]，同时连制表符和换行符等都输出
```
#使用for来迭代输出则：
for item in content
    print(item)
```
output：
> 按照正常在文件显示的样子输出
> 感觉用指针比较像，因为我尝试把两种都写在程序中，像这样
```
my_file=open('myfile.txt','r')
content=my_file.readlines()
foritemincontent:
print(item)
text=my_file.readlines()
print(text)

my_file.close()
```
output:
> 按照正常在文件显示的样子输出,并且多了一对[]

-拓展 items()
> python中字典items(),python中长使用for……in遍历字典，可以使用items（）
把字典中美对key和value组成一个元组，并把这些元组放在列表中返回
```
dict = {"name":"zhangsan","age":"30","city":"shanghai","blog":"http://www.jb51.net"} 
for key,value in dict.items():    
    print ('key=',key,'value=',value)
```
output:
> key=blog  value=http://www.jb51.net
> key=city  value=shanghai
> key=age   value=30
> key=name  value=zhangsan
#class类
-类定义
> 定义类，后面的类别首字母推荐以大写的形式定义，后面要跟冒号结尾！直接定义属性，行为用def来定义
```
Class Calculator：
        name='Good Calculator'  ##属性
        price=18                ##属性
        def add(self,x,y)
               print(self.name)
               return x+y
        def  minus(self,x,y)
                return x*y 
 ```
> 调用的时候，要：cal=Calculator（）加括号，否则无法被调用
> self这里是默认值的意思
- __init__功能（这里前后都是两个下划线!）
> _init_可以理解成初始化class的变量，在运行的时候给初始值赋值，既可以在函数定义的时候在形参中进行初始赋值，也可以在调用过程中进行初始赋值
```
classCalculation:
name='goodcalculation'
price=18
def__init__(self,name,price,height,width):
     self.name=name
     self.price=price
     self.h=height
     self.wi=width
c=Calculation('badcalculator',18,1117,45)
print(c.name)
print(c.price,c.wi,c.h)
```
output:
> bad calculator
> 18 45 1117
> 但是如果这样用：
```
c=Calculation('funny',120231)
print(c.name,c.price,c.wi,c.h)
```
则会报错：TypeError: __init__() missing 2 required positional arguments: 'height' and 'width'
> 修改为：
```
classCalculation:
name='goodcalculation'
price=18
     def__init__(self,name,price,height=1233,width=1214):
       self.name=name
       self.price=price
       self.h=height
       self.wi=width

c=Calculation('funny',120231)
print(c.name,c.price,c.wi,c.h)
```
output:funny 120231 1214 1233









 







