## 使用@property
### 1. @property 广泛应用于类的定义中可以让调用者写出简短的代码，同时保证对参数进行必要的而检查，这样程序运行是就减少了出错的可能性
### 2.python内置的@property装饰器杜泽把一个方法变成属性调用
### 3.使用@property，把一个getter方法变成属性，只需要加上个@property即可，@property 本身又创建了另一个装饰器@score.getter,负责把一个setter()方法变成属性赋值，可拥有一个可控的而属性操作
### 4.对实例属性操作的时候，属性不是直接暴露，是通过getter和setter方法来实现；可定义只读属性，之定义getter方法，不定义setter方法就是一个只读属性
```利用@property 给一个Screen对象加上width和height属性，以及一个只读属性resolution
class Screen(object):
     @property
     def width(self):
     	return self._width

     @width.setter
     def width(self,value):
     	if isinstance(value,(int,float)):
     		raise ValueError('宽度必须是一个数')
     	if value <= 0:
     		raise ValueError('宽度值必须大于等于0')
     	self._width = value

     @property
     def height(self):
     	return self._height

     @height.setter
     def height(self,value):
     	if isinstance(value,(int,float)):
     		raise ValueError('高度必须是一个数')
     	if value <= 0:
     		raise ValueError('高度必须大于等于0')
     	self._height = value

     @resolution
     def resolution(self):
     	return self._width*self._height
     s = Scrreen()
     s.width = 1024
     s.height = 768
     print('resolution = ', s.resolution)
     if s.resolution == 786432:
     	print('测试通过')
     else:
     	print('测试失败')
```
## 多重继承
### 1.继承是面向对象重要方式，通过继承，子类可以扩展父类的功能
## __str__
### 1.定义好__str__方法，返回一个好看的字符串
```
class Student(object):
	def __init__(self,name):
		self.name = name
	def __str__(self):
		return "name:%s"%self.name
print(Student('Mary'))
```
### 2.__str__()返回用户看到的字符串，__repr__返回开发者看到的字符串，即为调试服务的
```
class Student(object):
	def __init__(self,name):
		self.name = name
	def __str__(self):
		return "name:%s"%self.name
		__repr__ = __str__
```
## __iter__??
## __getitem__??
## __call__??
## 使用元类



