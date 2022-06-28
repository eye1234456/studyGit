> 前言： 每次在更换电脑后都第一时间安装SourceTree，但是经常遇到一直提示输入密码的情况不胜其烦，经研究网上信息及周围朋友帮助，有多种解决方式，特记录之

######方式一：最简单编辑方式
`SourceTree`->`偏好设置` -> `Git` -> `Git 版本` -> `使用系统安装的Git` 详见下图
![截屏2022-02-11 下午5.31.59.png](https://upload-images.jianshu.io/upload_images/1605558-a42707b719787610.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


#####方式二：使用命令行`terminal`或`iterm`进入对应报需要输入密码的项目下，输入如下命令解决
```
1、在终端（terminal）打开你的工程目录
2、输入
git config --global credential.helper store
或者
git config --global credential.helper osxkeychain
或者
git config credential.helper store

3、拉取代码
git pull

执行完成后，再次在sourcetree里面输入一下gitlab里面的密码。注意勾选选项“store password in keychain”。

4、输入用户名密码
后面就不用再输入了。
```
#####方式三：在git路径上带上账号密码信息（不安全，不推荐）