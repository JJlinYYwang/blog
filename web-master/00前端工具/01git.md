### 开篇定场
你有一天忘了使用 Git 导致了无法挽回的损失时，你就 Git 有多好了。我希望你永远不会遇到那一天。

--------------------- 
### 目录:

####一：版本管理系统的历史
阶段一：VCS 出现前 
阶段二：集中式 VCS
阶段三：分布式 VCS 

####二： Git  简介

Git 作用
Git 特点
Git 诞生
####三：Git
安装Git
检查安装结果
Git文件最小配置

####四：Git 使用
建立本地Git 仓库课题 
文件变动
将本地仓库上传到 GitHub
GitHub 仓库下载到本地

####五：帮助文档

###一：版本管理系统的历史
--------------------- 
#####阶段一：VCS 出现前 
用目录拷贝区别不同版本，公共⽂文件容易被覆盖，成员沟通成本很高，代码集成效率低下

![VCS 出现前.png](https://upload-images.jianshu.io/upload_images/6299738-24a9ad81dc0f10e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/140)

#####阶段二：集中式 VCS
有集中的版本管理服务器，具备文件版本管理和分⽀管理能力，集成效率有明显地提高，但是客户端必须时刻和服务器相连

![集中式 VCS.png](https://upload-images.jianshu.io/upload_images/6299738-127ef386f52d0cc5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/240)

#####阶段三：分布式 VCS 
服务端和客户端都有完整的版本库，脱离服务端，客户端照样可以管理理版本
查看历史和版本⽐比较等多数操作，都不需 要访问服务器，⽐集中式 VCS 更更能提高版本管理效率

![分布式 VCS.png](https://upload-images.jianshu.io/upload_images/6299738-3905fa2345d89ee1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/240)

### 二： git  简介 
--------------------- 
##### 1. git作用
世界上最先进的分布式版本控制系统。

##### 2 . git特点
最优的存储能⼒
非凡的性能
开源的
很容易做备份
⽀持离线操作
很容易定制工作流程

##### 3. git诞生
Linux的创建者Linnus花费两周的时间完成的。


#####4. Git的工作流程（看不懂，等我知道的时候重新更改信息）
克隆 Git 资源作为工作目录。
在克隆的资源上添加或修改文件。
如果其他人修改了，你可以更新资源。
在提交前查看修改。
提交修改。
在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。 

##### 5.工作区、暂存区和版本库（不太懂，以后会更改信息）
工作区：就是你在电脑里能看到的目录。
暂存区：英文叫stage, 或index。一般存放在 “.git目录下” 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库

### 三：配置 Git和GitHub
--------------------- 
####1:安装Git
安装Git 详细参考网址：[安装Git](https://git-scm.com/book/zh/v2)

GitBash下载
百度网盘：链接: [https://pan.baidu.com/s/1nu99KWp](https://pan.baidu.com/s/1nu99KWp "null") 密码: jfdf

####2:检查安装结果
输入以下命检查安装结果
>git --version

![检查安装结果.png](https://upload-images.jianshu.io/upload_images/6299738-c014d9fa8a8b72c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

####3:文件最小配置
>git config --global user.name 你的英文名                                                   #此英文名不需要跟GitHub账号保持一致
git config --global user.email 你的邮箱                                                      #此邮箱不需要跟GitHub账号保持一致
git config --global push.default matching
git config --global core.quotepath false
git config --global core.editor "vim"


五句话，依次在命令行中运行（其中前两句要把中文改成对应的内容）。
一定要执行这五行！！！
一定要执行这五行！！！
一定要执行这五行！！！



### 四：Git 使用
--------------------- 
#### 1. 建立本地Git 仓库课题 

1.创建目录作为我们的项目目录：
>mkdir git-demo-1

2.进入目录>
>cd git-demo-1

3.git init，这句命令会在 git-demo-1 里创建一个 .git 目录
>git init

4.ls -la 你就会看到 .git 目录，它就是一个「仓库」
>ls -la

5.在 git-demo-1 目录里面添加任意文件，假设我们添加了两个文件，分别是 
> index.html 和 css/style.css

![image.png](https://upload-images.jianshu.io/upload_images/6299738-5eb052bce391489c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)


![生成文件.png](https://upload-images.jianshu.io/upload_images/6299738-3b24690ab570d7b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

6.运行 git status -sb 可以看到文件前面有 ?? 号
>Initial commit on master
 ?? css/
 ?? index.html

![status.png](https://upload-images.jianshu.io/upload_images/6299738-69ea162834e5063a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

这个 ?? 表示 git 一脸懵逼，不知道你要怎么对待这些变动。
7.使用 git add 将文件添加到「暂存区」
你可以一个一个地 add
>git add index.html
git add css/style.css

你也可以一次性 add
>git add . 

意思是把当前目录（.表示当前目录）里面的变动都加到「暂存区」

8.再次运行 git status -sb，可以看到 ?? 变成了 A
>  Initial commit on master
 A  css/style.css
 A  index.html

A 的意思就是添加，也就是说你告诉 git，这些文件我要加到仓库里

![add.png](https://upload-images.jianshu.io/upload_images/6299738-f10a28c9f03feb2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

9.使用 git commit -m "信息" 将你 add 过的内容「正式提交」到本地仓库（.git就是本地仓库），并添加一些注释信息，方便日后查阅
>你可以一个一个地 commit
git commit index.html -m '添加index.html'
git commit css/style.css -m "添加 css/style.css"
你也可以一次性 commit
git commit . -m "添加了几个文件"

![commit.png](https://upload-images.jianshu.io/upload_images/6299738-6ef411135ad6502d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

10.再次运行 git status -sb，发现没有文件变动了，这是因为文件的变动已经记录在仓库里了。
这时你使用 git log 就可以看到历史上的变动：

![log.png](https://upload-images.jianshu.io/upload_images/6299738-3687717d45c77da0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)


以上就是 git add / git commit 的一次完整过程，可以看到，挺复杂的。原则上，你错了任何一步，就给我从头来一遍，做到你不会再手抖为止。

####2.文件变动
1.我修改了css 当中的内容

![修改css.png](https://upload-images.jianshu.io/upload_images/6299738-dbcc27bcfe5ff3c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

1. 运行 git status -sb 发现提示中有一个 M

![status.png](https://upload-images.jianshu.io/upload_images/6299738-f6ed8fdc836b59f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

2. 此时你如果想让改动保存到仓库里，你需要先 git add css/style.css 或者也可以 git add .
3. 再次运行 git status -sb 发现 M 有红色变成了绿色

![add.png](https://upload-images.jianshu.io/upload_images/6299738-add99b00fdcea83d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

4. 运行 git commit -m "更新 css/style.css"
 
![commit.png](https://upload-images.jianshu.io/upload_images/6299738-5fa07651fd0f7c7e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

####3.将本地仓库上传到 GitHub
1. 在 GitHub 上新建一个空仓库，名称随意，一般可以跟本地目录名一致,创建的是git_learning

2. 点击ssh,点击ssh,点击ssh,点击ssh,点击ssh,点击ssh

![git_learning.png](https://upload-images.jianshu.io/upload_images/6299738-7c76ebc3f1bff05e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)

3:由于我们已经有本地仓库了，所以看图，图中下面半部分就是你需要的命令，我们一行一行拷贝过来执行
>1:复制第一行命令 并且运行 git remote add origin git@github.com:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/git-demo-1.git
2:复制第二行 git push -u origin master，运行它
3:刷新当前页面，你的仓库就上传到 GitHub 了

![remote.png](https://upload-images.jianshu.io/upload_images/6299738-96aa99ae20b5dd03.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

![github.png](https://upload-images.jianshu.io/upload_images/6299738-128ff272210cd99a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

#### 4.GitHub 仓库下载到本地

1:复制仓库连接---要确保弹出来的是ssh 链接

![下载仓库.png](https://upload-images.jianshu.io/upload_images/6299738-61db173bbfc3adc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

2:打开 Git Bash，找一个安全的目录，（比如 ~/Desktop 桌面目录就很安全：cd ~/Desktop。）运行
>git clone 你刚才得到的以git@github.com开头的地址

![git clone.png](https://upload-images.jianshu.io/upload_images/6299738-1e491a446c17b4e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

3:桌面最多出来一个文件夹，进入这个文件夹，运行 ls -la 你会看到，远程目录的所有文件都在这里出现了

![文件下载完成.png](https://upload-images.jianshu.io/upload_images/6299738-556970e5445d20b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

4.然后你就可以对文件进行操作了


### 五：帮助文档
--------------------- 
*   [廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013743256916071d599b3aed534aaab22a0db6c4e07fd0000 "null")

*   [Git 菜鸟教程](http://www.runoob.com/git/git-install-setup.html "null")
*   [Git新手学习使用总结](https://blog.csdn.net/weixin_43738731/article/details/85346457)

* [安装Git 详细参考网址](https://git-scm.com/book/zh/v2)

GitBash下载
百度网盘：链接: [https://pan.baidu.com/s/1nu99KWp](https://pan.baidu.com/s/1nu99KWp "null") 密码: jfdf





