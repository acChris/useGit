### 使用前提

* GitLab账号

* 安装好[git](https://git-scm.com/downloads)

* VSCODE && 配置GitPath

### 在vscode里配置GitPath

1. file-preferences-setting

1. 在search setting里面输入git.path，选择设置-设置为json文本

![](/images/config_gitPath.jpg)

1. 如图，Edit in setting.json,接着就可以在文本里面输入你的git路径：
比如D:\\Program Files\\Git\\bin\\git.exe（这里必须双\\）

### Git文件/文件夹基础操作

|  操作    |  输入    |
| ---- | ---- |
| 创建文件夹     | mkdir  文件名   |
|   删除文件夹   |   rm -rf 文件名/（要退出到文件名的前一个路径）   |
|进入文件夹路径|cd 文件夹名|
|退出当前路径（返回到上一路径）|cd ..|
|显示当前文件夹下的文件（包括隐藏文件）|ls（-la）|
|创建文件（某一文件夹下）|touch 文件名（文件夹名/文件名）|
|跳转至文件处|code 文件名|
</br></br>

### Git基础操作

|  操作    |  输入    |
| ---- | ---- |
|生成.git文件|git init|
|清理git当前页|clear|
|当前状态|git status|
|追踪某一文件（加入缓存区，若更改git会记录）|git add 文件名|
|追踪当前文件夹下的所有文件|git add .|
|为当前项目生成备份版本|git commit (-m/-am)|

</br></br>

### 记录操作

|  操作    |  输入    |
| ---- | ---- |
|查看历史操作记录（email和name）|git log|
|查看最近n次记录|git log -p -n|
|只显示档案号为一行记录|git log --oneline|
|用于查看分支记录|git log --graph（--oneline）|
|以样式输出log（哈希值，作者，多长时间提交，描述）| git log --pretty=format:"%h - %an, %ar : %s"|
|找到该作者commit的记录|git log --author="作者名"|

</br></br>

### 编辑操作

|  操作    |  输入    |
| ---- | ---- |
|编辑文件|vi 文件名（注意有后缀）|
|编辑状态退出|ctrl + z|
|保存文件|ctrl + c && :wq|

</br></br>

### 追踪文件

|  操作    |  输入    |
| ---- | ---- |
|查看文件的不同|git diff（--staged）|

</br></br>

### git基础知识

1. 对于git管理的当前文件，有三种状态： 被追踪、要提交

1. git commit -m ''  表示备注message为提交的信息

   git commit -am '' 仅仅只能对已add即已追踪的文件进行提交

1. 不想要文件被追踪？试试这个：

      .gitignore文件里的内容项如文件夹、文件名和*.后缀（如txt）不会被追踪。

      只有当git add .后才会都被追踪。

1. git diff 仅能看到未被add的文件变化，而git diff --staged 可以看到。   
  
1. 档案号：可以理解为每次提交自动生成的编号，图中圈中部分即为档案号。

1. git log 如果行数过多，按enter可以查看接下来的一行，还没到达end或已到达，都可以输入q退出。


![](https://img2020.cnblogs.com/blog/2191525/202012/2191525-20201205184019687-306076459.png)


</br></br>

### 文件/版本还原操作

|  操作    |  输入    |
| ---- | ---- |
|（已add进行修改）还原文件|git checkout -- 文件名|
|（未add进行修改）还原文件|git reset HEAD 文件名|
|还原到上一个版本/删除上一次提交（强制）|git reset --hard HEAD^|
|还原到之前的上上版本（以此类推）|git reset --hard HEAD^^（^...）|
|还原到某个版本的哈希值（回退到某个版本，但其之后的版本会被删除）|git reset --hard 哈希值|
|查看之前的所有版本及版本操作|git reflog|


**注意：**

* 文件未进行add修改会呈现红色，add之后修改会呈现绿色。

* 已add进行修改后，可以直接还原

* 未add进行修改后，需git reset HEAD 文件名之后再git checkout -- 文件名才可以还原

* HEAD：指针。指向当前版本的哈希值。

</br></br>


### pull文件到当前账号下的GitLab的某一仓库

//第一次创建仓库
1. git init

1. git add .

1. git commit -m 'test'

1. git remote add origin https地址

1. git push origin master

   

### 官方介绍：

#### …or create a new repository on the command line



```
echo "# useGit" >> README.md
git init
git add README.md
git commit -m "first commit"
//重命名分支main
git branch -M main
git remote add origin https://github.com/acChris/useGit.git
git push -u origin main
```

#### …or push an existing repository from the command line



```
git remote add origin https://github.com/acChris/useGit.git
git branch -M main
git push -u origin main
```

### 如果本地版本与远程版本有差异，但又要强制推送可以使用 --force 参数：

```
git push --force origin master
```

</br></br>

### 免密上传

1. 在bash里输入git config  credential.helper store
不加参数： --global  只对这个仓库生效，并非全局设置 。

1. cat .git/config

![](/images/cat_GitConfig.png)


1.  如图，最下面一行就是已配置完成。输入一次后下一次就不用输入密码了。


### 参考资料

[gitlab使用教程视频](https://www.bilibili.com/video/BV1VK4y1e7zE?p=1)

[git的官方介绍](https://try.github.io/)
