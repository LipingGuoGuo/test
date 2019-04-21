##### datetime
> *datetime是模块，datetime模块包含一个datetime类，from datetime import datetime导入的是datetime这个类，仅导入import datetime，必须引用全名datetime.datetime
###### str转换为datetime
> *转换方法通过datetime.strtime()实现，需要一个日期和时间的格式化字符串
```
from datetime import datetime
cday =datetime.strptime("2019-4-20","%Y-%m-%d %H:%M:%S")
print(cday)
```
> *转换后的datetime没有时区信息
###### datetime转换为str
> *转换方法是通过strtime()实现的，同样需要一个日期个时间的格式化字符串
```
from datetime import datetime
now = datetime.now()
print(now,.strtime("%a,%d,%H:%M"))
```
###### collections
> *nametuple tuple可以表示不变集合
```
from collections import nametuple
Point = nametuple("Point",['x','y'])
p = Point(1,2)
p.x
p.y
```
> *nametuole是一个函数，用来创建一个自定义的tuple对象，并且规定tuple元素的个数，并可以用属性而不是索引来引用tuple的某个元素
> *deque 使用list存储数据，按索引访问元素很快，插入和删除慢，list是线性存储；deque是为了高效实现插入和删除的双向列表，适用于队列和栈
> *defaultdict 使用dict时，如果引用的Key不存在，抛出KeyError;Key不存在时，返回一个默认值，可以用defaultdict
> *OrderedDict 使用dict时，Key是无序的，要保持Key的顺序，可以用OrderedDict
