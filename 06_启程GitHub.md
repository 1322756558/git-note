#### 建立公私匙

---

检查本地是否存在公私匙

cd ~/.ssh

ls -al

---

生成公私钥

ssh-keygen -t rsa -b 4096 -C "lijunhui000123@gmail.com"

此时

13227 ~ $ cd .ssh
13227 .ssh ​$ ls -al
total 28
drwxr-xr-x 1 13227 197609    0 2月  10 23:52 ./
drwxr-xr-x 1 13227 197609    0 2月  10 23:52 ../
-rw-r--r-- 1 13227 197609 3243 2月  10 23:52 id_rsa # 私钥
-rw-r--r-- 1 13227 197609  750 2月  10 23:52 id_rsa.pub # 公钥

然后将公钥添加GitHub中：在设置中key



#### 创建仓库

常规的创建仓库，唯一需要注意的是是否生成  .gitignore文件

这是一个很棒的功能，会自动创建一个文件，让git选择性的屏蔽某些文件

通过选择语言来生成不同的.gitignore文件

在后面选择项目协议可以选择将仓库设置为MIT，对外公开

若还没有建立本地项目建议点选readme



#### 本地git推至GitHub

1. 建立git与GitHub的链接，类似于建立本地备份  
   命令：git remote add  <project name> githubSSH(从项目处复制)

*git remote -v 查看建立链接的仓库（本地或GitHub）*

*git remote remove <name>  # 删除链接，不再推送更新*

![1549878900966](C:\Users\13227\AppData\Roaming\Typora\typora-user-images\1549878900966.png)



2. 此时可以通过fetch拉到本地 或者push推送过去
   *git push <name> --all # 将所有分支push过去*
   当远端和本地不同时需要优先将远端的fetch下来然后才能进行提交会报错
   这时建议将报错的分支fetch下来
   *git fetch <name> <branch name>*

   

3. fetch下来后将GitHub/master与本地master两个分支合并然后才能重新上传文件
   *git merge --allow-unrelated-histories github/master*



```
总结：
	在使用git向GitHub提交的时
	1. 首先需要有公私钥
	2. 通过git remote add <name> githubSSH 将本地git绑定github仓库
	3. 这时候可以通过git push <name> 将所有分支push过去，这时其他分支大多数是没问题的
	   这时候如果github/master下如果有东西 master分支是无法提交的
	如果github/master下是有东西的那么直接提交这样就没问题了
	如果有东西（比如设置为MIT协议的文件）：
		4. 通过 git fetch <name> <branch name> 将github的分支从远端拉下来
		5. 通过 git merge 或者 git rebase 将两个不在同一个主干的合并
		   git merge 合并后不是一个连贯的线条 git rebase是在一个线条中
		使用 git merge --allow-unrelated-histories github/master
		将两个分支合并
		6. git push <name> master 将合并后的master push过去
	
```





