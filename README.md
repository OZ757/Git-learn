# Git Learn

-----------------

# Git 学习笔记

学习 git 时的笔记, 记载学到的 git 命令及用法 。 

-----------------

# 学习时的参考资料:
[廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
[Git Cheat Sheet 中文版](https://github.com/flyhigher139/Git-Cheat-Sheet)

-----------------

Git Learn 
=====================

## 目录
* [基本命令](#基本命令)
* [用法实例](#用法实例)

---

### 基本命令

#### 创建

##### 创建一个新的本地仓库:
```
$ git init
```

##### 本地修改
把当前修改添加到下次提交中,(可反复多次使用，添加多个文件):
```
$ git add <file>
```

##### 提交之前已标记的变化：
```
$ git commit
```

##### 附加消息提交:
```
$ git commit -m "message here"
```

##### 显示工作路径下已修改的文件:
```
$ git status
```

##### 显示与上次提交版本文件的不同：
```
$ git diff
```

---------

#### 提交历史

##### 从最新提交开始，显示所有的提交记录（显示hash， 作者信息，提交的标题和时间）：
```
$ git log
```

##### 显示你的版本的每一次命令:
```
$ git reflog
```

#### 撤销修改

##### 放弃工作目录下的所有修改：
```
$ git reset --hard HEAD
```

##### 将HEAD重置到指定的版本, (<commit> 版本号, 版本号没必要写全，前几位就可以了):
```
$ git reset --hard <commit>
```

##### 丢弃工作区的修改：
```
$ git checkout -- <file>
```

##### 放弃某个文件的暂存区的修改：
```
$ git checkout HEAD <file>
```

---------

#### 删除文件

##### 删除文件：
```
$ git rm <file>	
```

---------

#### 关联远程仓库

##### 关联一个远程库, (<remote> 远程仓库的名称一般默认为 origin ，当然，你可以设置为其他的名称):
```
$ git remote add <remote> <url>
```

##### 第一次推送时, 推送分支的所有内容:
```
$ git push -u <remote> <branch>
```

##### 推送最新修改:
```
$ git push <remote> <branch>
```

---------

#### 分支管理

##### 创建并切换到新分支:
```
$ git checkout -b <branch>
```

##### 列出所有分支，(当前分支前面会标一个 * 号)：
```
$ git branch 
```

##### 切换分支：
```
$ git checkout <branch>
```

##### 将分支合并到当前HEAD中：
```
$ git merge <branch>
```

##### 删除本地分支:
```
$ git branch -d <branch>
```

---------

#### 标签管理

##### 给当前版本打标签：
```
$ git tag <tag-name>
```

##### 给对应的 commit id 打标签：
```
$ git tag <tag-name> <commit>
```

##### 查看所有标签：
```
$ git tag
```

##### 查看某个标签的信息：
```
$ git show <tagname>
```

##### 给当前版本打标签并附加消息：
```
$ git tag -a <tag-name> -m "message here" 
```

##### 给指定版本打标签并附加消息：
```
$ git tag -a <tag-name> -m "message here" <commit>
```

##### 删除标签：
```
$ git tag <tag-name>
```

##### 推送某个标签到远程（创建的标签都只存储在本地，不会自动推送到远程）：
```
$ git push <remote> <tag-name>
```

##### 一次性推送全部本地标签：
```
$ git push <remote> --tags
```

---------

### 用法实例

#### 创建版本库
```
$ git init 					    // 将当前目录变成一个新的本地仓库
```

#### 添加文件到Git仓库
```
$ git add file1.txt             // 把当前修改添加到下次提交中
$ git add file2.txt file3.txt   // 把当前修改添加到下次提交中
$ git commit -m "add 3 files."  // 提交之前已标记的变化, 附加消息
```

#### 查看仓库当前状态 
```
$ git status 					// 显示仓库当前状态,文件有无被修改过
$ git diff						// 显示上次怎么修改
```

#### 版本回退
```
$ git log (按 q 键退出)			// 显示从最近到最远的提交日志
$ git reset --hard HEAD			// 回退到上一个版本
$ git reset --hard 9240e23      // 指定回到某个版本
$ git reflog					// 查看命令历史, 确认版本号
```

#### 撤销修改
```
$ git checkout -- file1.txt		// 在工作区的修改撤销（git add 之前）
$ git checkout HEAD file.txt	// 把暂存区的修改撤销掉（git add 之后 git commmit之前 )
```

#### 删除文件
```
$ git rm file1.txt				// 从版本库中删除该文件
```

#### 关联远程仓库
```
$ git remote add origin git@server-name:path/repo-name.git // 添加新的远程端（GitHub的仓库）
$ git push -u origin master 	// 第一次推送时,上传 master 分支的所有内容
$ git push origin master 		// 推送 master 分支最新的修改
```

#### 分支管理
```
$ git checkout -b dev 			// 创建 dev 分支，然后切换到 dev 分支
$ git branch 					// 列出所有的分支
$ git checkout master 			// 切换回 master 分支
$ git merge dev 				// 把 dev 分支的工作成果合并到当前分支上
$ git branch -d dev 			// 删除 dev 分支
```

#### 标签管理
```
$ git tag v1.0	 				// 打一个标签
$ git tag 						// 查看标签
$ git push origin v1.0			// 推送标签 v1.0 到远程
```