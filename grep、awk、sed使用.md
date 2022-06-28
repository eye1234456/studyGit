# grep 与 awk 、sed使用
> grep 与 awk 、sed并称为linux下文本处理三剑客，grep用于过滤文本信息，sed用于动态编辑文本，awk用于格式化输出文本。

参考：  
[Linux下的文本过滤神器-grep](https://juejin.cn/post/6844904126183112717)  
[Linux 输出过滤器：grep 命令](https://learnku.com/server/wikis/36593)  
[Linux awk 命令](https://www.runoob.com/linux/linux-comm-awk.html)  
[Linux xargs 命令](https://www.runoob.com/linux/linux-comm-xargs.html)  

##管道符号`|`,用于多个命令拼接执行

##grep
第一种用法：从已存在文件中过滤并输出文本信息  
`grep [选项] [表达式] [文件路径]...`  
`grep <searchWord> <file name>  `  
grep 命令通常和管道符 `|`一起使用。  
第二种用法：过滤管道中获取到的文本信息  
`otherCommand | grep [选项] [表达式]`  
`command | grep <searchWord>  `  

```
# 过滤tmpfile1、tmpfile2中包含login字符的行
grep login tmpfile1 tmpfile2
# 实时打印以log结尾的日志文件，过滤包含关键词error的行
tail -f *.log | grep error
# 输出marks.txt文件里包含9的行
grep 9 marks.txt 
cat marks.txt | grep 9 
```

##sed内容替换
`command | sed 's/<oldWord>/<newWord>/'`    

```
echo 'helloworld' | sed 's/hello/ok/'
# 输出 okworld
```

##awk内容分割   

```
#每行按空格或TAB分割，输出文本中的1、4项  
awk '{print $1,$4}' log.txt
cat | awk '{print $1,$4}' 
```


##xargs
```
#内容单行输出，默认是echo
cat test.txt | xargs
cat test.txt | xargs echo
# 将文件内容变成用空格分割的一行，作为参数传给-n2，
cat test.txt | xargs -n2
```