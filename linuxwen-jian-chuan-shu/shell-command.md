# 

## 开头

```
#!/bin/sh
```

脚本以.sh结尾, 并且要使用```chmod +x filename.sh```来使文件为可执行脚本


## 注释

注释以" # " 来开始, 占据一行

## 变量


1. 定义变量时,变量名不加美元符号($)
``` 
a="shell" 
```
变量名和等号之间不能有空格, 除了显式赋值, 还可以用语句赋值
```
for file in 'ls /etc'
```

2. 使用变量用${}表示(花括号虽然可以不用, 但尽量使用)
```
echo "a is ${a}"
```

## 字符串

单引号的变量和转义字符是无效的, 只会原样输出

双引号可以有变量和转义字符, 比如:   
```
your_name='qinjx'
str="Hello, I know your are \"$your_name\"! \n"
```


## 环境变量

使用export导入环境变量, 命令可以直接使用

```
# 运行命令的两种方法

/usr/bin/python /XXX/xx.py

export

```

## shell流程控制

1. if语句
```
if condition
then
    comamnd1
    command2
    command3
elif condition2
    command4
else
    command5
fi
```

2. for
```
for var in item1 item2... itemn
do
    command1
    ...
    commandn
done
```

3. while
```
while condition
do 
    command
done
```

## 并行运行多个命令

& 
```
#!/bin/sh
# 启动爬虫
/usr/bin/python3 /home/ec2-user/crawler/baemin/baeminApp3.0.py 0 >/dev/null 2>&1 &
/usr/bin/python3 /home/ec2-user/crawler/baemin/baeminApp3.0.py 1 >/dev/null 2>&1 &
```
**解释**:
- 最后的 `&`符号可以使命令并行运行
- `>`重定向符号
- `/dev/null`  # 代表空设备文件
- `2>`  # 代表stderr标准错误
- `&1` # 中的&表示等同,就是2的输出等同于标准输出
- `1`  # 表示系统标准输出  `>/dev/null`等同于`1>/dev/null`


## sh样本

```
#!/bin/sh
# 切换到目录下
cd /home/ec2-user/uber/crawler/python/zomato/
# 启动爬虫
/usr/bin/python3 zomato_apac.py
```

```
#!/bin/sh
# 启动爬虫
/usr/bin/python3 /home/ec2-user/crawler/baemin/baeminApp3.0.py 0 >/dev/null 2>&1 &
/usr/bin/python3 /home/ec2-user/crawler/baemin/baeminApp3.0.py 1 >/dev/null 2>&1 &

```

