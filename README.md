# reverse and rotate(排序及旋转)
* 语法练习-字符串，数组，数组转字符串
```
	def revrot(string, sz):
 	//判断return 返回为空的情况
    	if (sz <= 0) or (string == "") or (len(string) < sz):
        	return ""
 	//建立新的数组（list）,对输入的数字进行模块的划分及插入进新的数组中
    	chunk = []
    	chunkNew = []
    	while len(string) >= sz:
	//通过一个while循环将数字分块，并将等于sz部分的模块插入到新数组
        	chunk.append(string[:sz])
	//由于字符串中的元素不可修改，所以将剩余模块继续传给string
        	string = string[sz:]
	//定义一个新的字符串str2,传入chunk数组中
    	for str2 in chunk:
	//根据已知条件，定义sum并赋值
        	sum = 0
        	for i in str2:
	/for循环得到字符串中每一位数，计算位数的立方和，通过现有的pow(x,y),表示x^y
        		sum += pow(int(i), 3)
        	if sum % 2 == 0:
	//将str2中逆序的新字符串传入新的字符串中
            	strNew = str2[::-1]
        	else：
	//将str2中的首元素置于尾部，重新进行拼接
            	strNew = str2[1:] + str2[0]
	//将判断中得到的新字符串元素插入定义的数组中
    		chunkNew.append(strNew)
	//数组转字符串
    	return "".join(chunkNew)
```
