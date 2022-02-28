 # 1.1获取本地仓库
如果要使用Git对代码进行版本控制，那么首先要获取本地仓库
* 对本地电脑创建一个空目录例如`123.txt`，让他作为我们的本地Git仓库
* 进入目录，在文件目录内右击打开Git bash
* 执行`git init`，或者在计算机任意地方输入 `cd e/Git`  进入123.txt所在文件位置，也可以执行get init
* 使用`ll`查看文件，就可以查看到当前文件价下的隐藏文件`.git`文件

## 1.2基础操作指令
Git工作目录对于文件的修改（增删改减）
* 工作区`workspace`，刚修改或者刚创建的文件分别是未暂存`unstaged`和未跟踪`untracked`
* 工作区通过`git add`将文件添加到暂存区`index`，现在的文件状态是已经暂存`staged`
* 仓库`respository`由暂存区`index`使用`git commit`提交
* 工作区(workspace)通过`git add`将文件添加到缓存区(staged)，缓存区(staged)通过`git commit`将文件提交到仓库(respository) 
### 查看修改状态(status)
* 作用：查看文件当前是处于工作区还是暂存区
* 命令：`git status`
### 
