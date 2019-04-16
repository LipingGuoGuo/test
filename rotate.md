# rotate for max
* 语法基础练习-字符串，数组
```
    def max_rot(n):
        //将字符串转换为数组
        arr = list(str(n))
        //定义一个最大数
        max = n
        
        //进行n-1次循环
        for i in range(0, len(arr)-1,1):
        //取出对应的数，删除该数，并将该数插入到数组的最后一位
            num = arr[i]
            del arr[i]
            arr.append(num)
            //判断每次循环得到的数与定义的最大数进行比较，数组转换为字符串，类型强制为整数
            temp = int("".join(arr))
            if temp > max:
                max = temp
        return max
```
        