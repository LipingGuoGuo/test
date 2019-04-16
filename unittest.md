## 单元测试
```
class Dict(dict):
	
	def __init__(self,**kw):
		super().__init__(**kw)

	def __getattr__(self,key):
		try:
			return self[key]
		except KeyError:
			raise AttrinuteError(r"'Dict' object has no attribute '%s'" % key)

	def __setattr__(self,key,value):
		self[key]=value
```
## my_dict.test
```
import unittest

from mydict import Dict

# 编写测试类，从unittest.Testcase继承
class TestDict(unittest.TestCase): 

# 以test开头的就是测试方法，每类测试都需要编写一个test_xxx()方法
# 常用的断言是assertEqual()	
	def test_init(self):
		d = Dict(a=1,b='test')
		self.assertEqual(d,a,1)
		self.assertEqual(d.b,'test')
		self.assertTrue(isinstance(d,dict))

	def test_key(self):
		d = Dict()
		d['key']= 'value'
		self.assertEqual(d.key,'value'])

	def test_attr(self):
		d = Dict()
		d.key = 'value'
		self.assertTrue('key'in d)
		self.assertEqual(d['key'],'value')

	def test_keyerror(self):
		d = Dict()
		with self.assertRaises(KeyError):
			value = d['empty']

	def test_attrerror(self):
		d = Dict()
		with self.assertRaises(AttributeError):
			value = d.empty

if __name__=='__main__':
	unittest.main()
```
### 断言
#### 1.最常用的断言就是assertEqual()
```
self.assertEqual(abs(-1),1) # 断言函数返回的结果与1相等
```
#### 2.另一种重要的断言就是期待抛出指定类型的Error,比如通过d['empty']访问不存在的key时，断言会抛出KeyError;通过d.empty访问不存在的key时，期待抛出AttributeError:
```
with self.assertRaises(AttributeError):
	value = d['empty']

with self.assertRaises(AttributeError):
	value = d.empty
```

### 运行单元测试
```
if __name__=='__main__':
	unittest.main()
```
#### 2.另一种方法是在命令行通过参数-m unittest直接运行单元测试
```
import unittest
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def get_grade(self):
        if self.score <0 or self.score >100:
            raise ValueError('invalid value')
        if self.score >= 80:
            return 'A'
        if self.score >= 60:
            return 'B'
        else:
            return 'C'
```
## 文档测试？？