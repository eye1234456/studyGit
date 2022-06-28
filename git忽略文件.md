# 忽略文件
参考：  
* [Git 停止追踪文件](https://www.liuin.cn/2017/11/16/Git-%E5%81%9C%E6%AD%A2%E8%BF%BD%E8%B8%AA%E6%96%87%E4%BB%B6/)  
* [git如何停止追踪未被追踪的文件和已被追踪的文件](https://blog.csdn.net/yingleiming/article/details/105691201)  
* [git 忽略文件， ‘.gitignore’ 与 ‘.git/info/exclude’配置](https://blog.csdn.net/u014259503/article/details/82775651)  
* [git update-index --assume-unchanged 找出所有被忽略的檔案的辦法](https://www.796t.com/content/1547098683.html)  

####一、配置没有追踪过的文件
1.1： 如果要多用户都一起忽略，直接配置`.gitignore`  
1.2：如果只想当前用户忽略，配置`.git/info/exclude`  
如果没有info文件夹和exclude文件就创建一个`mkdir info && touch info/exclude`  
![.gitignore+.git](https://upload-images.jianshu.io/upload_images/1605558-0f89d6aeab0ec1c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![.git/info/exclude](https://upload-images.jianshu.io/upload_images/1605558-855c002c0f4dd1b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####二、配置忽略之前追踪过的文件
###2.1 只在本地当前用户停止追踪
####停止追踪    
`git update-index --assume-unchanged xxx`  
####恢复追踪  
`git update-index --no-assume-unchange xxx`  
####查找所有被停止追踪的文件  
`git ls-files -v | grep '^h\ ' | awk '{print $2}'`
####将所有停止追踪的文件一次性全部恢复追踪  
`git ls-files -v | grep '^h\ ' | awk '{print $2}' | xargs git update-index --no-assume-unchanged `  

###2.2 将停止最终的同步到远端大家一起停止最终
`git rm --cached xxx`
然后再到.gitignore里配置对应的内容
等同于sourcetree里选择`停止最终`+`忽略`
![停止追踪](https://upload-images.jianshu.io/upload_images/1605558-7c8d5de0371a691f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![忽略g](https://upload-images.jianshu.io/upload_images/1605558-73a6f0ae22bd2ec5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-----
