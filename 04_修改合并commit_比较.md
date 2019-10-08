## 分离头指针-detached HEAD

*实际功能与分支类似，用于可随时丢弃的情况*

**实际使用方法**

使用git checkout + commit 在不创建分支的情况下返回这个版本

进入后的git add / git commit 等命令可以正常使用

但是**在这个状态下再次切换branch的时候git在过一段时间后会清除你的这次提交**

这时如果想要保存你的更改应生成一个新的branch

git branch <new branch name>  commit标识 为当前提交生成一个新的分支

---



**HEAD-->指向使用的分支（一般为新分支的最后一次提交，除分离头状态）**

---

命令：

git diff commit1 commit2 比较两次提交的不同

比较分支和父分支的不同

git diff HEAD HEAD^



#### 修改最近一次提交的备注

git commit --amend



#### 修改之前的某次提交的备注

git rebase -i 父亲commit(前一次)

进入文件后将 pick=>r 修改备注



#### 合并commit

git rebase -i 父亲commit

进入后将需要被合并的pick->s

wq!退出



#### 比较暂存区和commit之间的区别

git diff --cached



#### 比较工作区域和暂存区

git diff 

*默认比较工作区和暂存区*

只对某一个文件或者几个文件感兴趣

git diff <文件名>







