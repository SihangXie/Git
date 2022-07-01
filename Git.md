# Git

*谢斯航*

------

![image-20220628190544116](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628190544116.png)



# 一、 Git概述

Git 是一个免费的、开源的**分布式**版本控制系统。与之相对的，就是传统的集中式版本控制系统。



## 1.1 什么是版本控制

版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。



## 1.2 为什么需要版本控制

其实版本控制的思想在我们学习生活中随处可见，最常见的就是毕业论文，修改版1.0、修改版2.0……最终版。

![image-20220628192824543](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628192824543.png)

这样的方式称为采用副本进行版本控制，在公司团队协作的场景里，显然是不太靠谱的。

例如，小红和小蓝同时从公司服务器代码上下载了同一份代码进行修改，小红修改了第2行并首先提交了代码，小蓝修改了第4行并在小红后面提交了代码，那么小蓝的版本就会覆盖小红的版本，导致最后的结果是只有第4行被修改。但我们期望的效果是代码的第2、第4行都被修改，且不受提交的先后次序的影响。如下图所示：

![image-20220628192744450](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628192744450.png)



因此，需要一个专业且高效的版本控制工具来解决这个问题。



## 1.3 版本控制工具



### 1.3.1 集中式

集中式版本控制工具是比较传统的，包括有 CVS、SVN (Subversion) 、VSS……

**1.概念**

集中式版本控制工具都有一个单一的集中管理的服务器，保存所有文件的修订版本。而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。如下图所示：

![image-20220628193759723](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628193759723.png)

**2.优点**

* 每个人都可以在一定程度上看到项目中的其他人正在做些什么；
* 管理员也可以轻松掌控每个开发者的权限；
* 管理一个集中化的版本控制系统，要远比在各个客户端上维护本地数据库来得轻松容易。



**3.缺点**

* 集中式版本控制工具的致命缺陷是：如果单一的集中管理的服务器宕机了，那么所有人都无法提交更新，也无法协同工作。



### 1.3.2 分布式

**1.概念**

分布式版本控制工具就没有单一的中央服务器了。客户端提取的不是最新版本的文件快照，而是把代码仓库完整地镜像下来 (本地库) 。

如下图所示，每台程序员的个人电脑就是一个独立的代码仓库，可以在自己的个人电脑上做版本控制。为了保证所有程序员编写的代码的统一性，还需要一个远程库作为代码托管中心 (如 Github、Gitee 和 GitLab 等)。每个程序员在自己的个人电脑上完成版本控制后，就可以把代码推送到远程库上，以保证远程库永远是最新的。其他程序员也可以在这个远程库上克隆其他同事的代码到自己的本地库上，基于自己的本地库进行版本控制。

![image-20220628194804791](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628194804791.png)



**2.优点**

* 服务器断网的情况下也可以进行开发，因为版本控制是在本地进行的。
* 每个客户端保存的也都是整个完整的项目，包含历史记录，更加安全。



## 1.4 Git的工作机制

Git的工作机制如下图所示：

![image-20220628201545594](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628201545594.png)

**1.工作区**

工作区就是个人电脑的硬盘上，存放代码的地方。例如，每个IDEA项目都会有一个对应的文件夹，这些文件夹存放着项目的代码。工作区的代码是可以删除的。



**2.暂存区**

在工作区编写好代码后，要让Git追踪到硬盘上的代码文件。因此，要把工作区的代码文件 `add` 添加到暂存区。暂存区中的代码是临时存储的，还没有生成相应的历史版本，暂存区中的代码是也可以删除的。



**3.本地库**

当把暂存区中的代码 `commit` 提交到本地库后，就生成了相应的历史版本。注意，一旦代码 `commit` 提交到本地库后，代码就无法删除。因此，提交本地库之前，需要慎重地检查代码。



**4.远程库**

代码托管中心是基于网络服务器的远程代码仓库，简单称为远程库。主要分为局域网和互联网两大类：

* 局域网
  * GitLab
* 互联网
  * Github
  * Gitee







# 二、 Git安装



登录Git 的官网：[Git](https://git-scm.com/) 。下载Git的安装包。

![image-20220628191601127](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628191601127.png)



双击安装包文件，点击 Next。

![image-20220628203055001](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203055001.png)



选择安装路径。注意路径中不要带中文和空格：

![image-20220628203306045](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203306045.png)



保持默认不变，下一步即可：

![image-20220628203627189](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203627189.png)



直接下一步：

![image-20220628203708880](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203708880.png)



直接下一步：

![image-20220628203800498](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203800498.png)



直接下一步：

![image-20220628203855439](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628203855439.png)



选第一个：

![image-20220628204020113](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204020113.png)



直接下一步：

![image-20220628204121306](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204121306.png)



直接下一步：

![image-20220628204143779](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204143779.png)



选择如图，下一步：

![image-20220628204243864](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204243864.png)



直接下一步：

![image-20220628204326406](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204326406.png)



直接下一步：

![image-20220628204412608](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204412608.png)



直接下一步：

![image-20220628204528500](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204528500.png)



两个都选，下一步：

![image-20220628204608406](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204608406.png)



都不选，直接点击安装：

![image-20220628204709328](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204709328.png)



![image-20220628204731167](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204731167.png)



两个都不选，点击完成：

![image-20220628204819957](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204819957.png)



验证是否安装成功

在桌面点击鼠标右键，如果出现下图两项。点击 Git Bash Here，进入 Git 的命令行，以后我们的操作都在这里。

![image-20220628204927922](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204927922.png)



输入命令：

```sh
git --version
```

并回车

![image-20220628205240694](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628205240694.png)

如果出现Git的版本信息，说明Git安装成功。





# 三、 Git常用命令

|                命令                 |      作用      |
| :---------------------------------: | :------------: |
| git config –global user.name 用户名 |  设置用户签名  |
| git config –global user.email 邮箱  |  设置用户签名  |
|              git init               |  初始化本地库  |
|             git status              | 查看本地库状态 |
|           git add 文件名            |  添加到暂存区  |
|   git commit -m “日志信息” 文件名   |  提交到本地库  |
|             git reflog              |  查看历史记录  |
|       git reset –hard 版本号        |    版本穿梭    |



## 3.1 设置用户签名



### 3.1.1 设置全局用户前面

桌面，点击鼠标右键，点击 Git Bash Here，进入 Git 的命令行，输入以下代码：

```sh
git config --global user.name 用户名
```

```sh
git config --global user.email 邮箱
```

上述两条代码都必须是全英文格式。签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。Git首次安装必须设置一下用户签名，否则无法提交代码。



【注意】

* 这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系。
* 但是，我个人建议用户名和邮箱和你的 Github 用户名和邮箱保持一致。否则本地库推送到 Github 上时会出现头像和用户名对不上、不一致的问题。



【如何验证用户前面设置成功】

打开我的电脑 —> C 盘 —> 用户 (User) —> 当前账户 —> .gitconfig 文件

![image-20220628212139032](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628212139032.png)

使用记事本类工具打开，看到刚刚设置的用户签名信息，说明设置成功：

![image-20220628212238752](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628212238752.png)



### 3.1.2 设置单个项目用户签名

在该项目文件目录下点击鼠标右键，点击 Git Bash Here，进入 Git 的命令行，输入：

```sh
git show
```

能查看当前项目的用户名和用户邮箱。如果需要修改，则输入以下代码：

```sh
git config user.name 用户名
```

```sh
git config user.email 邮箱
```

来设置单个项目用户签名。

可以输入：

```sh
git config user.name
```

```sh
git config user.email
```

来查看是否设置成功。





## 3.2 初始化本地库

想让Git管理文件目录，就必须首先让Git获取文件目录的管理权限，即初始化本地库。

例如，我想让Git管理我的【Java数据结构和算法】 `JavaDSA` 这个项目。其文件目录路径如下所示：

```
F:\OneDrive - stu.ouc.edu.cn\MarkDown\2-后端开发\2-Java\1-基础阶段\5-Java数据结构与算法\JavaDSA
```

在Windows系统下，先通过“我的电脑”进入到该文件目录，再在空白处点击鼠标右键，再点击 “Git Bash Here” 。就可以进入当前文件目录的路径下了。

![image-20220628204927922](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628204927922.png)

![image-20220628213219911](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220628213219911.png)



在此命令行下，输入命令：

```sh
git init
```

就会在当前文件目录下生成一个 `.git` 的隐藏文件夹，这就是 Git 的本地库。说明 Git 已经获取到该文件目录的管理权限了。



### 3.2.1 删除本地库

要删除本地库，只需要删除本地库文件目录下的隐藏文件夹 `.git` 即可。

删除本地库前：

![image-20220630201932841](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630201932841.png)

在该项目文件目录下点击鼠标右键，点击 Git Bash Here，进入 Git 的命令行，输入删除本地库命令：

```sh
rm -rf .git
```

删除本地库后：

![image-20220630202158537](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630202158537.png)

可以看到，隐藏文件夹 `.git` 已经被删除。该项目就不能被Git识别追踪，不能进行Git版本控制了。





## 3.2 查看本地库状态

```sh
git status
```

【例子】

![image-20220630202555210](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630202555210.png)

第二行蓝色括号 `(master)` ，表示当前头指针 `HEAD` 正指向本地库的主分支 master。

下方三个红色的文件，说明本地库有3个文件目录尚未添加到暂存区，无法被Git追踪。



## 3.3 添加暂存区

```sh
git add 文件名
```

添加完成后，再次通过 `git status` 查看本地库状态：

![image-20220630203342639](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630203342639.png)

可以看到，由红色变为绿色，说明已经有15个文件成功添加到暂存区，成功被Git追踪。



## 3.4 提交本地库

```sh
git commit -m "版本日志信息" 文件名
```

【例子】

```sh
$ git commit -m "first commit" Hello.java
```

提交本地库完成后，再次通过 `git status` 查看本地库状态：

![image-20220630203913166](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630203913166.png)

提示：nothing to commit, working tree clean. 说明当前所有文件都已经提交本地库。

### 3.4.1 查看版本信息

```sh
git reflog
```

![image-20220630204148813](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630204148813.png)

能看到头指针 `HEAD` 指向 `master` 分支，且已经有了第一次提交版本 `first commit` 。而前面的 `aa4aef0` 则是版本号的前 7 位。



### 3.4.2 查看详细版本日志

```sh
git log
```

![image-20220630204510155](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630204510155.png)

第1行：完整的版本号。头指针 `HEAD` 指向 `master` 分支。

第2行：能看到提交人和提交人邮箱。

第3行：提交时间。

第4行：提交版本。



## 3.5 版本穿梭

版本穿梭前，可以先输入 `git reflog` 查看当前有哪些版本及对应的版本号。

然后再输入：

```sh
git reset --hard 版本号
```

穿梭完后， `master` 指针会指向你输入的版本号对应的版本。指针关系如图所示：

![image-20220630210036060](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630210036060.png)





# 四、 Git分支操作





# 五、 Git团队协作机制









# 六、 Github操作



## 6.1 创建远程仓库

首先，登录你的Github。网页的右上角点击 “+” 号，再点击 `New repository` 。

![image-20220630193758930](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630193758930.png)

如图所示，写好远程库名称，一般是项目文件夹的名称。

![image-20220630194350499](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630194350499.png)



下图表示你的远程仓库已经成功创建。接下来，我们需要通过远程库链接，与本地库进行绑定关联。因为我设置了SSH，所以我复制的是远程库的SSH链接，没有SSH的小伙伴也可以使用HTTPS链接。

![image-20220630194614000](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630194614000.png)



## 6.2 远程仓库操作

### 6.1.1 创建远程库链接别名

上一节我们复制了远程库的SSH链接，此链接是关联远程库与本地库的桥梁。凡是远程库与本地库之间的数据传输都需要调用该链接。但是由于该链接太长，为了方便使用，我们在Git中为该远程库链接创建一个简短易记的别名 (一般就是项目名) 。

```sh
git remote add 远程库别名 远程库链接(HTTPS/SSH)
```

【例子】

```sh
$ git remote add LeetCode git@github.com:SihangXie/LeetCode.git
```



### 6.1.2 查看当前本地库的远程库别名

为了验证当前本地库是否已经创建了远程库的别名，可以使用以下命令：

```sh
git remote -v
```

【例子】

```sh
$ git remote -v
LeetCode        git@github.com:SihangXie/LeetCode.git (fetch)
LeetCode        git@github.com:SihangXie/LeetCode.git (push)
```

可以看到，创建一个别名，但是现实两个。这是因为，第一个是拉取 (fetch) ；而第二个是推送 (push) 。



### 6.1.3 删除远程库(解除远程库与本地库绑定)

```sh
git remote rm 远程库别名
```



### 6.1.4 推送本地分支到远程仓库

因为本地库推送到远程库的最小单位是分支，所以我们要指明要推送本地库的哪个分支到远程库上。

格式：

```sh
git push 远程库别名 本地分支
```

【例子】

```sh
$ git push LeetCode master
```

推送远程库对网络要求比较高，如果没有 “科学上网” 知识，推送好几次都失败是很正常的。两个建议：一是掌握 “科学上网” 知识；二是使用码云 (Gitee) 代替 Github 。

出现下图的提示说明成功推送到远程仓库：

![image-20220630211845204](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630211845204.png)

此时刷新你的 Github 仓库页面，会发现你已经顺利推送到Github上了：

![image-20220630212028089](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630212028089.png)





### 6.2.5 拉取远程库到本地库

当远程库上的代码更新了，而你的本地却没有更新时，你就需要拉取 (pull) 远程库到本地库，从而保证本地库与远程库的代码是同步更新的。

```sh
git pull 远程库别名 远程库分支
```



### 6.2.6 克隆远程库到本地

当你的本地完全是一片空白，没有本地库，想要把别人Github上的代码下载到本地，并建立本地库时，就需要用到克隆 (clone) 操作。

```sh
git clone 远程库链接(HTTPS/SSH)
```



## 6.3 团队协作



### 6.3.1 团队内协作





### 6.3.2 跨团队协作





## 6.4 SSH免密登录

在”我的电脑“ C盘家目录下，鼠标右键打开 Git Bash：

![image-20220630214405414](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630214405414.png)

输入以下命令：

```bash
ssh-keygen -t rsa -C 账号登录邮箱
```

然后，什么都不需要输入，连续敲3次回车键。

再次回到刚刚的家目录，你会发现 `.ssh` 的文件夹：

![image-20220630214712444](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630214712444.png)

双击打开，发现有一个公钥和一个私钥：

![image-20220630214811647](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630214811647.png)

回到Git Bash，依次输入下列命令：

```bash
cd .ssh
```

```bash
cat id_rsa.pub
```

就能看到SSH公钥，选中并复制。

![image-20220630215201940](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630215201940.png)

然后登录你的Github，点击网页右上角的 `settings` ：

![image-20220630215339345](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630215339345.png)

然后如图顺序点击：创建新的SSH公钥

![image-20220630215508724](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630215508724.png)

如图按顺序操作：

![image-20220630215727493](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630215727493.png)

添加成功的画面如图所示：

![image-20220630215912458](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630215912458.png)

恭喜你，你就可以使用SSH链接了，进行Github操作再也不用输入密码验证了。

![image-20220630220124529](https://raw.githubusercontent.com/SihangXie/pic-bed/master/img/image-20220630220124529.png)







# 七、 IDEA集成Git





# 八、 IDEA集成Github





# 九、 Gitee码云





# 十、 GitLab





