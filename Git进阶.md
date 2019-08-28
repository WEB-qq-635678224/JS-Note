---
title: Git进阶
date: 2018-07-05 11:56:25
tags: Git
comment: true
categories: Essay
img: /img/Git.jpg
preview: /img/Git.jpg
---
Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。<!--more-->



## Git 与 SVN 区别

   GIT不仅仅是个版本控制系统，它也是个内容管理系统(CMS),工作管理系统等。如果你是一个具有使用SVN背景的人，你需要做一定的思想转换，来适应GIT提供的一些概念和特征。


### Git 与 SVN 区别点：

* 1、GIT是分布式的，SVN不是：这是GIT和其它非分布式的版本控制系统，例如SVN，CVS等，最核心的区别。

+ 2、GIT把内容按元数据方式存储，而SVN是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似.svn,.cvs等的文件夹里。        

* 3、GIT分支和SVN的分支不同：分支在SVN中一点不特别，就是版本库中的另外的一个目录。

+ 4、GIT没有一个全局的版本号，而SVN有：目前为止这是跟SVN相比GIT缺少的最大的一个特征。

* 5、GIT的内容完整性要优于SVN：GIT的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。      



## Git命令

### 我们先来预览一下Git命令

```
{
    mkdir：         XX (创建一个空目录 XX指目录名)

    pwd：          显示当前目录的路径。

    git init          把当前的目录变成可以管理的git仓库，生成隐藏.git文件。

    git add XX       把xx文件添加到暂存区去。

    git reset --mixed 把上次add文件撤销但修改保留。

    git commit –m “XX”  提交文件 –m 后面的是注释。

    git status        查看仓库状态

    git diff  XX      查看XX文件修改了那些内容

    git log          查看历史记录

    git cherry-pick [<options>] <commit-ish>...   选择其他分支commit在当前分支提交

    git reset HEAD 撤销git add 上次所有文件

    git reset HEAD xxx.js 撤销git add 上次某个文件

    git reset  –-hard HEAD^ 或者 git reset  –-hard HEAD~ 回退到上一个版本

                            (如果想回退到100个版本，使用git reset –-hard HEAD~100 )

    cat XX         查看XX文件内容

    git reflog       查看历史记录的版本号id

    git checkout — XX  把XX文件在工作区的修改全部撤销。

    git rm XX          删除XX文件

    git rm *         删除所有文件

    git remote add origin https://github.com/tugenhua0707/testgit 关联一个远程库

    git push –u(第一次要用-u 以后不需要) origin master 把当前master分支推送到远程库

    git clone https://github.com/tugenhua0707/testgit  从远程库中克隆

    git checkout –b dev  创建dev分支 并切换到dev分支上

    git branch  查看当前所有的分支

    git checkout master 切换回master分支

    git merge dev    在当前的分支上合并dev分支

    git branch –d dev 删除dev分支

    git branch name  创建分支

    git stash 把当前的工作隐藏起来 等以后恢复现场后继续工作

    git stash list 查看所有被隐藏的文件列表

    git stash apply 恢复被隐藏的文件，但是内容不删除

    git stash drop 删除文件

    git stash pop 恢复文件的同时 也删除文件

    git remote 查看远程库的信息

    git remote –v 查看远程库的详细信息

    git push origin master  Git会把master分支推送到远程库对应的远程分支上
}
```

### Git深度理解
```
{
    1.git进入vim界面 输入Ctrl+Z 即可退出 ////////Esc Shift+:

    2.查看git所有已配置项 $ git config --list

    3.Git撤销commit的操作命令  git reset --hard HEAD^       git reset --hard commitID    git reset --hard HEAD@{n}

    4.git 撤销初始化 删除 .git 文件即可 或者执行命令 rm -rf .git

    5.git add . 出现以下报错
        ---------- warning: LF will be replaced by CRLF in XXXXXXXXXXXXXX.
        ---解决方案：执行命令git config core.autocrlf false

    6. 查看git本机 用户名： $ git config --global user.name
                    邮箱： $ git config --global user.email
        更改本机配置 用户名： $ git config --global user.name "Lee"
                    邮箱： $ git config --global user.email "Jack2244057555@gmail.com"
        修改git全局初始化的用户名 $ git config --global --replace-all user.email "输入你的邮箱"
                                 $ git config --global --replace-all user.name "输入你的用户名"
   7. 查看全局配置  $  git config --list 
}
```

```
{   
    一.Git命令解析
    1、git基本命令

    1）git add 将想要快照的内容写入缓存区

    2）git status -s "AM" 状态的意思是，这个文件在我们将它添加到缓存之后又有改动

    3）git commit -m '第一次版本提交' -m选项添加备注信息

    4）git clone url 使用 git clone 拷贝一个 Git 仓库到本地

    5）git diff 查看执行 git status 的结果的详细信息
    　　尚未缓存的改动：git diff
    　　查看已缓存的改动： git diff --cached
    　　查看已缓存的与未缓存的所有改动：git diff HEAD
    　　显示摘要而非整个 diff：git diff --stat

    6）git commit -a 跳过git add 提交缓存的流程

    7）git reset HEAD 用于取消已缓存的内容

    8）git rm file
    　　git rm 会将条目从缓存区中移除。这与 git reset HEAD 将条目取消缓存是有区别的。
    　　"取消缓存"的意思就是将缓存区恢复为我们做出修改之前的样子。
    　　默认情况下，git rm file 会将文件从缓存区和你的硬盘中（工作目录）删除。

    9）git mv 重命名磁盘上的文件 如 git mv README README.md

    10）git push -u origin master 提交代码

    2、git 分支管理
    1）创建分支命令 git branch (branchname) 列出分支 git branch
    2）切换分支命令 git checkout (branchname)
    3）合并分支 git merge (branchname)
    4）创建新分支并立即切换到该分支下 git checkout -b (branchname)
    5）删除分支命令 git branch -d (branchname)
    ps:状态 uu 表示冲突未解决 可以用 git add 要告诉 Git 文件冲突已经解决

    3、查看日志版本
    git log 命令列出历史提交记录
    git log --oneline 查看历史记录的简洁的版本
    git log --oneline --graph 查看历史中什么时候出现了分支、合并

    4、标签
    为软件发布创建标签是推荐的。这个概念早已存在，在 SVN 中也有。你可以执行如下命令创建一个叫做 1.0.0 的标签：
    git tag 1.0.0 1b2e1d63ff
    1b2e1d63ff 是你想要标记的提交 ID 的前 10 位字符。可以使用下列命令获取提交 ID：
    git log
    你也可以使用少一点的提交 ID 前几位，只要它的指向具有唯一性

    5、提取远程仓库代码

    1）git fetch　　从远程仓库下载新分支与数据

    2)）git pull　　从远端仓库提取数据并尝试合并到当前分支

    6、git分支

    git-flow主要有5中分支：master、hotfix、release、develop、feature

    feature分支开始于develop分支，完成以后合并到develop分支。
    当完成一定数量feature分支以后，从develop再开一个release分支出来，这些特性将被更行到下一个发布的版本中，
    之后的feature将不会被合并到release中。
    之后在release分支中，只修改bug，然后完成release分支。完成release分支会完成以下三个操作：
    1、合并release分支到master；
    2、给master打上版本的标签
    3、release回归到develop分支。
    当发现master上有bug时，开一个hotfix，完成后合并到master分支。


    初次安装git配置用户名和邮箱

    初次安装git需要配置用户名和邮箱，否则git会提示：please tell me who you are.



    你需要运行命令来配置你的用户名和邮箱：

    $ git config --global user.name "superGG1990"

    $ git config --global user.email "superGG1990@163.com"

    注意：（引号内请输入你自己设置的名字，和你自己的邮箱）此用户名和邮箱是git提交代码时用来显示你身份和联系方式的，并不是github用户名和邮箱
    git使用ssh密钥

    git支持https和git两种传输协议，github分享链接时会有两种协议可选：

    git协议链接图例 : ↓



    https协议链接图例：↓



    git使用https协议，每次pull, push都会提示要输入密码，使用git协议，然后使用ssh密钥，这样免去每次都输密码的麻烦

    初次使用git的用户要使用git协议大概需要三个步骤：
    一、生成密钥对
    二、设置远程仓库（本文以github为例）上的公钥
    三、把git的 remote url 修改为git协议（以上两个步骤初次设置过以后，以后使用都不需要再次设置，此步骤视以后项目的remote url而定，如果以后其他项目的协议为https则需要此步骤）
    一、生成密钥对
    大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个。生成公钥的过程在所有操作系统上都差不多。首先你要确认一下本机是否已经有一个公钥。

    SSH 公钥默认储存在账户的主目录下的 ~/.ssh 目录。进去看看：

    $ cd ~/.ssh
    $ ls
    authorized_keys2  id_dsa       known_hosts config            id_dsa.pub
    看一下有没有id_rsa和id_rsa.pub(或者是id_dsa和id_dsa.pub之类成对的文件)，有 .pub 后缀的文件就是公钥，另一个文件则是密钥。

    假如没有这些文件，甚至连 .ssh 目录都没有，可以用 ssh-keygen 来创建。该程序在 Linux/Mac 系统上由 SSH 包提供，而在 Windows 上则包含在 MSysGit 包里：

    $ ssh-keygen -t rsa -C "your_email@youremail.com"

    Creates a new ssh key using the provided email # Generating public/private rsa key pair.

    Enter file in which to save the key (/home/you/.ssh/id_rsa):
    直接按Enter就行。然后，会提示你输入密码，如下(建议输一个，安全一点，当然不输也行，应该不会有人闲的无聊冒充你去修改你的代码)：

    Enter same passphrase again: [Type passphrase again]
    完了之后，大概是这样：

    Your public key has been saved in /home/you/.ssh/id_rsa.pub.
    The key fingerprint is: # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@youremail.com
    到此为止，你本地的密钥对就生成了。

    二、添加公钥到你的远程仓库（github）


    1、查看你生成的公钥：

    $ cat ~/.ssh/id_rsa.pub

    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0X6L1zLL4VHuvGb8aJH3ippTozmReSUzgntvk434aJ/v7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8vR3c8E7CjZN733f5AL8uEYJA+YZevY5UCvEg+umT7PHghKYaJwaCxV7sjYP7Z6V79OMCEAGDNXC26IBMdMgOluQjp6o6j2KAdtRBdCDS/QIU5THQDxJ9lBXjk1fiq9tITo/aXBvjZeD+gH/Apkh/0GbO8VQLiYYmNfqqAHHeXdltORn8N7C9lOa/UW3KM7QdXo6J0GFlBVQeTE/IGqhMS5PMln3 admin@admin-PC
    2、登陆你的github帐户。点击你的头像，然后 Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key

    3、然后你复制上面的公钥内容，粘贴进“Key”文本域内。 title域，自己随便起个名字。

    4、点击 Add key。

    完成以后，验证下这个key是不是正常工作：

    $ ssh -T git@github.com

    Attempts to ssh to github
    如果，看到：

    Hi xxx! You've successfully authenticated, but GitHub does not # provide shell access.
    恭喜你，你的设置已经成功了。

    三、修改git的remote url


    使用命令 git remote -v 查看你当前的 remote url

    $ git remote -v
    origin https://github.com/someaccount/someproject.git (fetch)
    origin https://github.com/someaccount/someproject.git (push)
    如果是以上的结果那么说明此项目是使用https协议进行访问的（如果地址是git开头则表示是git协议）

    你可以登陆你的github，就像本文开头的图例，你在上面可以看到你的ssh协议相应的url，类似：



    复制此ssh链接，然后使用命令 git remote set-url 来调整你的url。

    git remote set-url origin git@github.com:someaccount/someproject.git

    然后你可以再用命令 git remote -v 查看一下，url是否已经变成了ssh地址。

    然后你就可以愉快的使用git fetch, git pull , git push，再也不用输入烦人的密码了
}
```
