#### 清除暂存区恢复为HEAD

***add后 撤销***

*恢复所有文件*

git reset HEAD

*某文件恢复到HEAD*

git reset HEAD -- <file> <file> ....



#### 变更工作区为暂存区内容

***修改工作区后 撤销***

git checkout -- <file> <-文件名

---

*ps: file前都有空格*

---



#### 消除最近几次commit

***commit之后后悔***

git reset --hard commit_hash

彻底恢复成这个commit

**后果严重谨慎使用**



#### 对比两次commit的不同

git diff branch1 branch2 -- <file>    or    git diff commit_hash1 commit_hash2



#### 删除文件的正确姿势

git rm filename



#### 暂存手头的工作

*应用场景：暂存手头工作，使用git暂存当前工作空间和缓存空间，去解决新的任务*

git stash  # 暂存当前状态

git stash list # 查看暂存列表

git stash apply  # 返回stash状态不删除stash列表

git stash pop  # 返回stash状态删除这个stash

git stash clear  # 默认清除所有stash

git stash drop [-q | --quiet] [<stash>]

从存储条目列表中删除单个存储条目。如果没有`<stash>`给出，则删除最新的一个。即`stash@{0}`，否则`<stash>`必须是表单的有效存储日志引用`stash@{<revision>}`。

**在使用git stah命令的时候暂存区间必须有文件未commit**



*当有多个git stash的时候*

git stash pop/apply@{num}

num数字越大说明贮藏时间越早

git stash pop == git stash pop@{0}



#### 某些文件不需要加入git管控

将不需要git管理的添加到.gitignore里，可以参考github中的.gitignore的写法

其中写法

*.后置名 # 不管某类文件

doc # 不管文件夹和文件

doc/ # 不管文件夹，管文件



quection：想要管文件夹，不管文件

doc

!doc/*



#### git仓库备份到本地

传输协议：

| 常用协议       | 语法格式                                                     | 说明                               |
| -------------- | ------------------------------------------------------------ | ---------------------------------- |
| 本地协议(1)    | /path/to/repo.git                                            | 哑协议                             |
| 本地协议(2)    | file:///path/to/repo.git                                     | 智能协议<br />(常用，能显示进度条) |
| http/https协议 | http://git-server.com:port/path/to/repo.git<br />https://git-server.com:port/path/to/repo.git | 平时接触到的都是智能协议           |
| ssh协议        | user@git-server.com:path/to/repo.git                         | 工作中最常用的智能协议             |

*在备份的文件夹下*

---

哑协议

git clone --bare {git仓库的pwd}.git pathName  # 不带工作空间的裸仓库



智能协议

git clone --bare file:///{git仓库的pwd}.git pathName # 智能协议的裸仓库



在工作空间中

---

同步到远端

git remote -v add pathName file:///{备份位置的pwd}  # 添加备份文件夹位置

git push pathName # 备份到远端

*git pash --set-upstream pathName branchName* #提示































