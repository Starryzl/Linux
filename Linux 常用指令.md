# Linux 常用指令



# 一、目录操作

## 1.1访问目录

```
pwd				查看当前工作目录
clear 			清除屏幕
cd ~			当前用户目录
cd /			根目录
cd -			上一次访问的目录
cd ..			上一级目录
```

## 1.2**查看目录内信息**

```
ll				查看当前目录下内容（LL的小写）
```

## 1.3**创建目录**

```
mkdir aaa		在当前目录下创建aaa目录，相对路径；
mkdir ./bbb		在当前目录下创建bbb目录，相对路径；
mkdir /ccc		在根目录下创建ccc目录，绝对路径；

mkdir -p temp/nginx  递归创建目录（会创建里面没有的目录文件夹）
```

## 1.4**搜索命令**

```
find / -name 'b'		查询根目录下（包括子目录），名以b的目录和文件；
find / -name 'b*'		查询根目录下（包括子目录），名以b开头的目录和文件； 
find . -name 'b'		查询当前目录下（包括子目录），名以b的目录和文件；
```

## 1.5重命名

```
mv 原先目录 文件的名称   mv tomcat001 tomcat 
```

## 1.6移动目录

**剪切命令(有目录剪切到制定目录下，没有的话剪切为指定目录）**

```
mv	/aaa /bbb		    将根目录下的aaa目录，移动到bbb目录下(假如没有bbb目录，则重命名为bbb)；
mv	bbbb usr/bbb		将当前目录下的bbbb目录，移动到usr目录下，并且修改名称为bbb；
mv	bbb usr/aaa			将当前目录下的bbbb目录，移动到usr目录下，并且修改名称为aaa；
```

## 1.7**复制目录**

```
cp -r /aaa /bbb			将/目录下的aaa目录复制到/bbb目录下，在/bbb目录下的名称为aaa
cp -r /aaa /bbb/aaa		将/目录下的aa目录复制到/bbb目录下，且修改名为aaa;
```

## 1.8**删除目录**

```
rm -r /bbb			普通删除。会询问你是否删除每一个文件
rmdir test01		目录的删除

rm -rf /bbb			强制删除/目录下的bbb目录。如果bbb目录中还有子目录，也会被强制删除，不会提示
```

## 1.9查看树状目录结构

```
tree test01/
```

<img src="https://img-blog.csdnimg.cn/50cfc9a5d07a410d8a49cabe470b288f.png" alt="img" style="zoom:67%;" />

## 1.10批量操作

需要采用`{}`进行参数的传入了。

```
mkdir {dirA,dirB}  # 批量创建测试目录
touch dirA/{A1,A2,A3}     # dirA创建三个文件dirA/A1,dirA/A2,dirA/A3

```

# 二、文件操作

## 2.1删除文件

```
rm -r a.java		删除当前目录下的a.java文件（每次回询问是否删除y：同意）

rm -rf a.java		强制删除当前目录下的a.java文件
rm -rf ./a*			强制删除当前目录下以a开头的所有文件；
rm -rf ./*			强制删除当前目录下所有文件（慎用）；

find . -name '*.pyc' -exec rm -rf {} \;		递归删除.pyc格式的文件

find . -name "*" -size 145800c -exec rm -rf {} \;	递归删除指定大小的文件(145800)
find . -name "*" -size 145800c -print -exec rm -rf {} \;	递归删除指定大小的文件，并打印出来


```

## 2.2创建文件

```
touch testFile
```

## 2.3打印当前文件夹下指定大小的文件

```
find . -name "*" -size 145800c -print
```

```
"." 表示从当前目录开始递归查找
“ -name '*.exe' "根据名称来查找，要查找所有以.exe结尾的文件夹或者文件
" -type f "查找的类型为文件
"-print" 输出查找的文件目录名
-size 145800c 指定文件的大小
-exec rm -rf {} \; 递归删除（前面查询出来的结果）
```

