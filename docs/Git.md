# Git-Guide

![LogoMakr_50mVak](https://github.com/Pr1p/JavaRe/blob/master/asset/LogoMakr_50mVak.png)

## SVN/GIT 简介

**SVN和GIT都是一种版本控制工具。**

### 什么是版本控制？我们为什么需要它?

> 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。 除了项目源代码，你可以对任何类型的文件进行版本控制。 

有了版本控制，我们能够更为轻松与高效的进行软件开发。

为了更好的让读者理解这句话，我们用这张图做一个版本控制示例：

![LogoMakr_4KaWen](https://github.com/Pr1p/JavaRe/blob/master/asset/LogoMakr_4KaWen.png)

并不能吃辣的你一口气放了太多的辣椒，你悔不当初，希望当初放调料时能少放些辣椒。

![LogoMakr_3CqDFH](https://github.com/Pr1p/JavaRe/blob/master/asset/LogoMakr_3CqDFH.png)

在现实里，回到过去是不可能的，你只能捏着鼻子吃完这碗面。

### 在软件开发中，这是可能的，回到过去，逆转未来，这就是版本管理系统！





>SVN全称：Subversion，是一个开放源代码的**版本控制系统**
>
>Svn是一种**集中式文件版本管理系统**。集中式代码管理的**核心是服务器**，所有开发者在开始新一天的工作之前必须从服务器获取代码，然后开发，最后解决冲突，提交。



鉴于本人只使用过Eclipse-SVN插件，命令行控制方面仅是了解，若欲掌握，请见此文：

> [SVN详细操作](https://mp.weixin.qq.com/s?__biz=MzI4Njg5MDA5NA==&mid=2247483878&idx=3&sn=06a4c8258f1f1d4ccf2781c4a121e54e&chksm=ebd740e7dca0c9f1eb8e57991e701122aa61d2c94fed55aed2f0a5dff2c0e289b2120f1deb7d&scene=21###wechat_redirect)



### 什么是GIT，它和SVN的区别是什么？

+ GIT是什么？

  > [Git](http://zh.wikipedia.org/wiki/Git)是目前最流行的[版本管理系统](http://www.ruanyifeng.com/blog/2008/12/a_visual_guide_to_version_control.html)，学会Git几乎成了开发者的必备技能 .

+ 与SVN的区别？

  1.SVN是集中式版本控制系统，而GIT是分布式版本控制系统。

  2.SVN相较于GIT的分支管控能力过差。

  3.SVN极其依赖网络，GIT工作时几乎不需要网络。

+ GIT与其他版本控制系统存储方式的不同

  其他版本控制系统存储方式：

  （图源：[Java-Guide](https://snailclimb.top/JavaGuide/#/docs/tools/Git) ）

  ![img](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-3deltas.png) eg：File A（Final）= File A（Start）+Δ(Delta) 1+Δ(Delta) 2；

  

  GIT：

  （图源：[Java-Guide](https://snailclimb.top/JavaGuide/#/docs/tools/Git) ）

  ![img](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-3snapshots.png) 

  > Git 更像是把数据看作是对小型文件系统的一组快照。 每次你提交更新，或在 Git 中保存项目状态时，它主要对当时的全部文件制作一个快照并保存这个快照的索引。 为了高效，如果文件没有修改，Git 不再重新存储该文件，而是只保留一个链接指向之前存储的文件。 Git 对待数据更像是一个 **快照流**。 

### GIT操作详解

首先我们要明确GIT的结构：

![LogoMakr_9TN0kZ](https://github.com/Pr1p/JavaRe/blob/master/asset/LogoMakr_9TN0kZ.png)

> 你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 `工作目录`，它持有实际文件；第二个是 `暂存区（Index）`，它像个缓存区域，临时保存你的改动；最后是 `HEAD`，它指向你最后一次提交的结果。 
>
> 一个本地的git repo只有一个工作区和暂存区，但是有多个分支的提交区，而我们的checkout只是将HEAD指针从一个分支切换到另一个分支。 
>
> 分支切换需遵循以下方法：
>
> 1. add并且commit，再checkout，提交到当前分支 
> 2. add但不commit，可以stash，然后checkout回来之后stash apply，在commit，提交到当前分支 
> 3. add但不commit，也不stash，直接checkout，然后再commit的话，记录就在切换分支下面。 



![clipboard.png](https://segmentfault.com/img/bVkJdj) 



命令交互-（图源：[阮一峰-GIT](http://www.ruanyifeng.com/blog/2014/06/git_remote.html )）

![git](http://www.ruanyifeng.com/blogimg/asset/2014/bg2014061202.jpg) 

*仓库（本地/远程）共用*

+ git init

  ![1571050392749](https://github.com/Pr1p/JavaRe/blob/master/asset/1571050392749.png)

  ```markdown
  执行 git init
  在 /?/ 目录初始化 Git 仓库完毕。
  所有有关你的此项目的#快照数据#都存放在这里。
  ```

+ git Add/git Status

  ![1571050747147](https://github.com/Pr1p/JavaRe/blob/master/asset/1571050747147.png)![1571051099620](https://github.com/Pr1p/JavaRe/blob/master/asset/1571051099620.png)

  ```markdown
  新建测试文本test.txt 内容为this is a txt。
  执行 git add
  	git status （查看git仓库详细状态）/ git status -s(查看git仓库摘要状态)
  	可以看到test.txt文本已被添加进git仓库。
  ```

+ git diff

  ![1571051810821](https://github.com/Pr1p/JavaRe/blob/master/asset/1571051810821.png)

  ```markdown
  将测试文本test.txt 内容从this is a text->this is a text1003.
  执行 git diff/git diff --cashed
  git diff	可以看到比较的是工作区文件与暂存区文件的区别（上次git add的内容） 
  git diff --cashed    可以看到比较的是暂存区文件与仓库文件的区别(上次git commit的内容)
  ```

+ git Commit

  ![1571052254768](https://github.com/Pr1p/JavaRe/blob/master/asset/1571052254768.png)

  ![1571052277013](https://github.com/Pr1p/JavaRe/blob/master/asset/1571052277013.png)

  ```markdown
  执行 git commit -m '这里输入您想输入的备注'
  若不添加-m会强制打开一个文本编辑框
  再执行 git status 即可查看到仓库状态。
  另 git add File 
  	git commit -m '' == git commit -a m ''
  ```

+ git rm/git mv/git reset HEAD

  ![1571053584106](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053584106.png)

  ![1571053609508](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053609508.png)

  ![1571053620811](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053620811.png)

  ![1571053634378](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053634378.png)

  ```markdown
  test.txt已经提交至暂存区
  
  git rm <file> 
  从工作目录中删除文件（未提交到暂存区的文件）
  
  git rm -f <file>
  强制删除已经放到暂存区域的文件
  
  git rm --cashed <file>
  将文件从暂存区删除但保留在工作目录中。
  
  git rm -r * 
  执行此语句，会删除该目录下的所有文件和子目录。
  ```

  ![1571053886042](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053886042.png)

  ![1571053895785](https://github.com/Pr1p/JavaRe/blob/master/asset/1571053895785.png)

  ```
  在当前目录下建立一个git1目录，并创建一个git.txt文件
  使用git mv将之移动/更名（git mv 原名 改后名）
  ```

  ![1571054008299](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054008299.png)![1571054019981](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054019981.png)

  ```
  将git.txt踢出暂存区
  ```
  ---
  ```
  清除工作区（未提交到暂存区）的数据 回退到与版本库保持一致-> git checkout -- file
  清除已经提交到暂存区的数据 回退到与上次暂存区保持一致-> git reset HEAD <FileName> ->git checkout -- file
  清除已经提交到本地仓库的数据 回退到某版本-> git reset --hard <版本号> 
  ```

+ git Branch

  ```
  git branch (branchname)
  创建分支
  ```

  ![1571054301184](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054301184.png)![1571054497469](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054497469.png)

+ git Checkout

  ```
  git Checkout (branchname)
  切换到该分支
  git Checkout -b （branchname)
  创建并切换到该分支
  ```

  ![1571054435121](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054435121.png)

  ![1571054560036](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054560036.png)

+ git Merge

  ![1571054730273](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054730273.png)![1571054995880](https://github.com/Pr1p/JavaRe/blob/master/asset/1571054995880.png)

  ```
  git merge <欲合并进来的分支名>
  git branch -d <欲删除的分支名>
  删除后 仅剩master分支。
  ```

  ![1571055494756](https://github.com/Pr1p/JavaRe/blob/master/asset/1571055494756.png)

  ![1571055529019](https://github.com/Pr1p/JavaRe/blob/master/asset/1571055529019.png)

  

+ git Rebase

  ![1571055760621](https://github.com/Pr1p/JavaRe/blob/master/asset/1571055760621.png)

  ![1571055775957](https://github.com/Pr1p/JavaRe/blob/master/asset/1571055775957.png)

  ![1571057310993](https://github.com/Pr1p/JavaRe/blob/master/asset/1571057310993.png)

  ```
  git rebase <欲合并到的分支名>
  git rebase -i <欲处理的莫点的Hash>
  git rebase -i 可以对提交顺序进行处理
  注意：rebase/merge 欲将此分支合并到/欲将某分支合并进来
  ```

+  在提交树上移动的方法

>HEAD 总是指向当前分支上最近一次提交记录。 
>
>HEAD->当前分支->当前分支最近的一次提交记录

![1571056183029](https://github.com/Pr1p/JavaRe/blob/master/asset/1571056183029.png)

```
通过Git Log查看hash值
Git checkout <欲跳转的Hash>^ 
跳到欲跳转的Hash点的上一个节点
^^ 为上两个节点
git checkout <欲跳转的Hash>~?
跳到欲跳转的Hash的上？个节点 

例如git checkout HEAD~4
	git checkout HEAD^

```

+ git Cherry-pick

  ```
  命令 git cherry-pick <欲摘取节点的Hash 可为多个>
  摘取部分其他分支的提交添加到当前分支
  例如 git cherry-pick C2 C4
  ```

  ![1571056575988](https://github.com/Pr1p/JavaRe/blob/master/asset/1571056575988.png)

+ git Tag

  ```
  永远指向某个提交记录的标识，比如软件发布新的大版本，或者是修正一些重要的 Bug 或是增加了某些新特性
  
  git tag <标签名> <标记点Hash>
  ```

  ![1571057487912](https://github.com/Pr1p/JavaRe/blob/master/asset/1571057487912.png)

+ git Describe

  ```
  用来描述离你最近的锚点（也就是标签），它就是 git describe
  
  ```

  >`git describe <ref>`
  >
  >`<ref>` 可以是任何能被 Git 识别成提交记录的引用，如果你没有指定的话，Git 会以你目前所检出的位置（`HEAD`）。
  >
  >它输出的结果是这样的：
  >
  >`<tag>_<numCommits>_g<hash>`
  >
  >`tag` 表示的是离 `ref` 最近的标签， `numCommits` 是表示这个 `ref` 与 `tag` 相差有多少个提交记录， `hash` 表示的是你所给定的 `ref` 所表示的提交记录哈希值的前几位。
  >
  >当 `ref` 提交记录上有某个标签时，则只输出标签名称

  ![1571057783015](https://github.com/Pr1p/JavaRe/blob/master/asset/1571057783015.png)

  ```
  git describe
  
  result:v1_2_gC6
  ```

  

+ git stash

  [stash精简教程](https://blog.csdn.net/wh_19910525/article/details/7784901 )

  [stash详细教程](https://www.cnblogs.com/tocy/p/git-stash-reference.html )

  > `git stash`会把所有未提交的修改（包括暂存的和非暂存的）都保存起来，用于后续恢复当前工作目录。 比如下面的中间状态，通过`git stash`命令推送一个新的储藏，当前的工作目录就干净了。 
  >
  > 可以通过`git stash pop`命令恢复之前缓存的工作目录 ,这个指令将缓存堆栈中的第一个stash删除，并将对应修改应用到当前的工作目录下。 
  >
  > 你也可以使用`git stash apply`命令，将缓存堆栈中的stash多次应用到工作目录中，但并不删除stash拷贝。 
  >
  > 可以使用`git stash list`命令 查看现有stash。

*远程仓库*

+ git Clone

  ```
  从远程仓库提取一个版本库
  git clone <版本库网址>
  git clone https://github.com/jquery/jquery.git
  从远程仓库提取一个版本库并在本地生成一个指定名称的目录（若不指定则与远程仓库版本同名）
  git clone <版本库网址> <本地目录名>
  
  ```

  ![1571058034750](https://github.com/Pr1p/JavaRe/blob/master/asset/1571058034750.png)

+ git remote

  ```
  git remote 列出所有的远程主机名称
  git remote -v 列出所有远程主机的网址
  git clone -o <为远程主机命名> <远程主机网址>
  $ git clone -o jQuery https://github.com/jquery/jquery.git
  ```

  [其余讲解请查看阮一峰](http://www.ruanyifeng.com/blog/2014/06/git_remote.html )

+ git Fetch

  ```
  从远程主机拉取所有分支更新。
  git fetch <远程主机名>
  从远程主机拉取指定分支更新。
  git fetch <远程主机名> <分支名>
  git fetch origin master
  
  ```

  ![1571058422359](https://github.com/Pr1p/JavaRe/blob/master/asset/1571058422359.png)

+ git Pull

  ```
  git pull origin == git fetch origin + git merge origin/next
  如果当前分支只有一个追踪分支，可省略远程主机名。
  ```

  ![1571058565615](https://github.com/Pr1p/JavaRe/blob/master/asset/1571058565615.png)

+ git Push

```
git push origin将你负责的变更上传到远程仓库，并在远程仓库上合并你的提交记录。

上面命令表示，将当前分支推送到origin主机的对应分支。

如果当前分支只有一个追踪分支，那么主机名都可以省略。
```

![1571058774443](https://github.com/Pr1p/JavaRe/blob/master/asset/1571058774443.png)

![1571058755547](https://github.com/Pr1p/JavaRe/blob/master/asset/1571058755547.png)

推荐开发分支图：

（[图源-Cyc2018-点此访问](https://github.com/CyC2018/CS-Notes/blob/master/notes/pics/245fd2fb-209c-4ad5-bc5e-eb5664966a0e.jpg )）

![245fd2fb-209c-4ad5-bc5e-eb5664966a0e.jpg](https://github.com/CyC2018/CS-Notes/blob/master/notes/pics/245fd2fb-209c-4ad5-bc5e-eb5664966a0e.jpg?raw=true) 

Refer:

> GIT-控制台使用-在线练习：<https://learngitbranching.js.org/> 
>
> GIT-廖雪峰-小白入门教程：<https://www.liaoxuefeng.com/wiki/896043488029600> 
>
> GIT-IDEA操作参考：<https://blog.csdn.net/Tc11331144/article/details/86700107> 
>
> GIT-图解:<http://rogerdudler.github.io/git-guide/index.zh.html> 
>
> GIT-阮一峰：<http://www.ruanyifeng.com/blog/2014/06/git_remote.html> 



