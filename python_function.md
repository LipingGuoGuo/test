# python笔记之函数
## 函数-定义函数
### 1.可变参数：定义可变参数和定义一个list或tuple参数相比，仅仅在参数前面加了一个 * 号；（*args是可变参数，args接收的是一个tuple)
### 2.关键字参数可以扩展函数的功能；** extra表示把extra这个dict的所有key-value用于关键字参数传入到**kw参数，kw将获得一个dict(注：kw获取的dict是extra的一份拷贝，对kw的改动不会影响到函数外的extra)(**kw是关键字参数，kw接收的是一个dict)
### 3.命名关键字参数：使用命名关键字参数时，如果没有可变参数，必须加一个*作为特殊分隔符，* 后面的参数被视为命名关键字参数；缺少分隔解释器会无法识别位置参数和命名关键字参数；命名关键字参数必须传入参数名，这和位置参数不同，如果没有传入参数名，调用将报错
### 4.位置参数
### 5.默认参数：默认参数可以简化函数的调用；必选参数在前，默认参数在后，否则python解释器会报错；设置默认参数：函数多个参数时，变化大的参数放前（降低调用函数的难度）；默认参数一定要用不可变对象，如果是可变对象，程序运行时会有逻辑错误

## 函数-递归函数
### 1.递归函数的优点是定义简单，逻辑清晰；使用递归函数需要注意防止栈溢出（函数调用是通过栈这种数据结构实现的，递归调用的次数过多，会导致栈溢出）
### 2. 尾递归：解决递归调用栈溢出的方法；函数返回时，调用自身本身，return语句不包含表达式
### 3.汉诺塔递归算法：
```
def move(n,a,b,c):
	if n == 1:
		print(a,'-->',c)
	else:
		move(n-1,a,c,b)
		move(1,a,b,c)
		move(n-1,b,a,c)
move(3,a,b,c)
```

## 高级特性-切片
## 高级特性-列表生成式
### 1.列表生成式可以用来创建list的生成式
#### 生成[1x1,2x2,...,10x10]
#### 方法一：利用循环
```
L = []
  for i in range(1,11)
  L.append(i*i)
```
#### 方法二：利用列表生成式
```
[i*i for i in range(1,11)]
```

#### list中既包含字符串，又包含整数，非字符串类型没有lower（）方法，使用内建的isinstance函数可以判断一个变量是否为字符串
```
L1 = ['hello', 17, 'An', None]
L2 = [s.lower() for s in range L1 if isinstance(s,str)]
```
### 运用列表生成式，可以快速生成list,可以通过一个list推导另一个list,代码简单
## 高级特性-生成器
### 1.创建列表和生成器的区别仅在于最外层的[],()
### 2.generator保存的是算法，每次调用next(),计算下一个元素值，直到计算到最后一个值，咩有元素时，抛出StopIteration错误
#### 函数斐波拉契数列
、、、
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
       print(b)
       a, b = b, a+b //t=(b,a+b);a=t[0];b=t[1]  t是一个tuple
       n = n +1
    return 'done'
、、、
#### generator
、、、
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b,a+b
    return 'done'
、、、
### 3.函数中包含yield关键字，不是普通函数，而是generator
### 4.函数是顺序执行，遇到return语句或者最后一行函数语句返回
### 5.generator函数，每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行
### ？？？6.for循环调用generator时，要拿到返回值，必须捕获StopIteration错误
## 高级特性-迭代器
### 1.凡是可作用于for循环的对象都是Iterable类型
### 2.凡是可作用于next()函数的对象都是Iterable类型，他们表示一个惰性计算的序列？？？
## 函数式编程:函数式编程就是一种抽象程度很高的编程语言，纯粹的函数式编程语言编写的函数没有变量
函数式编程的特点：允许把函数本身作为参数传入另一个函数，还允许返回一个函数（python允许使用变量，python不是纯函数式编程语言）
## 高阶函数
### 1.函数本身也可以赋值给变量；即变量可以指向函数
```变量f已经指向函数本身，直接调用abs()函数和调用变量f完全相同
f=abs
f(-10)
```
### 2.函数名也是变量（函数名指向函数的变量）
### 3.传入函数：变量可以指向函数，函数的参数能接收变量，那么一个函数恶意接收另一个函数作为参数，这种函数称之为高阶函数
```
def add(x,y,f):
	return f(x)+f(y)
print(add()-4,5,abs)
```
## map/reduce
### map()函数
```利用map函数，把用户输入不规范的英文名字，变为首字母大写，其他字母小写
def normalize(name):
	name = name[0].upper()+name[1:].lower()
	return name
L1 = ['adam','LISA','barT']
L2 = list(map(normalize,L1))
print(L2)
```
### reduce()函数
```sum()函数可以接收一个list并求和，编写prod()函数，可以接收一个list并利用reduce()求积
from functools import reduce
def prod(L):
	def f(x,y):
		return x*y
	reduce(f,L)
print('3*5*7*9=', prod([3,5,7,9]))
if prod([3,5,7,9])== 945:
	print('测试成功')
else：
	print('测试失败')
```
### map()和reduce()函数
```
from functools import reduce
def str2float(s):
	for i in range(len(s)):
	if s[i]=='.':
		break
	L=s[:i]+s[i+1:]  #把小数点去掉
	m= len(s)-i-1   #m为小数点后面几位数
	dic = {'0':0,'1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9}  #字典的含义不明白
	def f(x,y)
		return x*10+y 
	def char2num(s):
		return dic[s]
	return reduce(f,map(char2num,L))/10**m
print(str2float('123.456'))
if abs(str2float('123.456')-123.456)<0.00001:
	print('测试成功')
else：
	print('测试失败')
```
### filter函数
### sorted函数
## 返回函数
## 匿名函数
## 装饰器
## 偏函数
## 模块
### 特点：1.提高代码的可维护性；2.使用模块可以避免函数名和变量名冲突；3.自己创建模块时要注意命名，不能和python自带的模块名冲突，检查交互环境下import abc,若成功则说明系统存在此模块；4.模块名要遵循python变量命名规范，不要使用中文/特殊字符；5.使用模块
### 使用模块
#### 作用域：1.正常的函数和变量名是公开的(public),可以被直接引用，比如abc,PI 等；2.类似_xxx_这样的变量是特殊变量，可以被直接引用，但是有特殊用途，比如_author_,_name_就是特殊变量，hello模块定义的文档注释也可以用特殊变量_doc_访问，自己变量一般不要用这种变量名；类似_xxx和__xxx这样的函数或变量是非公开的(private),不应该被直接引用，比如_abc等
## python内置函数
##类class和实例instance
### 1.类是创建实例的模板，实例是一个个具体对象，各个实例拥有的数据互相独立，互不影响；类是抽象的模板；2.定义类是通过关键字class；3.类可以起到模板作用，定义特殊的_init_方法
```
class Student(object):
	def _init_(self,name,score):
		self.name =name
		self.score =score
```
### 数据封装
```
class Student(object):
	def _init_(self,name,score):
		self.name = name
		self.score = score
	def print_score(self):
		print("%s:%s"%(self.name,self.score))
	def get_grade(self):
		if self.score>90:
			return 'A'
		elif self.score>=69:
			return 'B'
		else:
			return 'C'
```
## 访问限制
```内部属性不被外部访问，可以在属性的名称前加两个下划线__
class Student(object):
	def __init__(self,name,score):
		self.__name = name
		self.__score = score

	def print_score(self):
		print("%s:%s"%(self.__name,self.__score))

	#获取name和score
	def get_name(self):
		return self.__name

	def get_score(self):
		return self.__score
	
	# 允许外部代码修改score，Student类增加set_score方法
	def set_score(self):
		self.__score = score
```
### 访问限制练习:Student对象的gender字段对外隐藏，用get_gender()和set_gender()代替，并检查参数有效性
```
class Student(object):
	def __init__(self,name,gender):
		self.name = name
		self.__gender = gender

	def get_gender(self):
		return self.__gender

	def set_gender(self,gender):
		if gender == "female" or "male":
			self.__gender = gender 
		else:
			raise ValueError("Input Error")

	bart = Student('Bart', male)
	if bart.get_gender()!='male':
		print("测试失败")
	else：
		bart.set_gender("female")
		if bart.set_gender ！='female':
			print("测试失败")
		else：
			print("测试成功")
```
## 继承和多态
## 实例属性和类属性
``` 统计学生人数，可以给Student类增加一个类属性，没创建一个实例，该属性自动增加
class Student(object):
	count = 0

	def __init__(self,name):
		self.name = name
		Student.count += 1

```
### 1.判断一个变量是否是某个类型可以用isinstance()判断
```
isinstance(a,list)
True
```
### 继承：可以把弗雷的所有功能直接拿过来，不必从零开始，子类只需新增自己特有的方法，也可以覆盖重写父类不合适的方法
### 多态：调用方只管调用，不管细节  著名的开闭原则：对扩展开放（允许新增Animal子类）；对修改封闭（不需要修改依赖Animal类型的run_teice()等函数
### 静态语言vs动态语言：动态语言的鸭子类型特点决定了继承不像静态语言那样必须
## 获取对象信息
### 使用type():判断对象类型，使用type函数；如果一个变量只想函数或者类，也可以用type函数（）判断
### 使用isinstance():isinstance()判断的是一个对象是否是该类型本身，或者位于该类型的父继承链上
### 使用dir():获得一个对象的所有属性和方法们可以使用dir()函数
 