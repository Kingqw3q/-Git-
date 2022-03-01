 # 1、 Git常用指令和基本操作
 ## 1.1.1、 获取本地仓库
如果要使用Git对代码进行版本控制，那么首先要获取本地仓库
* 对本地电脑创建一个空目录例如`123.txt`，让他作为我们的本地Git仓库
* 进入目录，在文件目录内右击打开Git bash
* 执行`git init`，或者在计算机任意地方输入 `cd e:/Git`  进入123.txt所在文件位置，也可以执行get init
* 使用`ll`查看文件，就可以查看到当前文件价下的隐藏文件`.git`文件

## 1.2、 基础操作指令
Git工作目录对于文件的修改（增删改减）
* 工作区`workspace`，刚修改或者刚创建的文件分别是未暂存`unstaged`和未跟踪`untracked`
* 工作区通过`git add`将文件添加到暂存区`index`，现在的文件状态是已经暂存`staged`
* 仓库`respository`由暂存区`index`使用`git commit`提交
* 工作区(workspace)通过`git add`将文件添加到缓存区(staged)，缓存区(staged)通过`git commit`将文件提交到仓库(respository) 

### 1.2.1、 查看修改状态(status)
* 作用：查看文件当前是处于工作区还是暂存区
* 命令：`git status`

### 1.2.2、 添加工作区至暂存区
* 作用：将工作区文件添加到暂存区
* 命令：`git add "file.file"`
 * 通配符：将文件目录下的所有文件都加入暂存区`git add .`

### 1.2.3、 添加暂存区文件到工作区
* 作用：提交文件到仓库
* 命令：`git commit -m""`

### 1.2.3、 为常用指令配别名
#用于输出git提交日志</br>
`alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'`</br>
#用于输出当前目录所有文件及基本信息</br>
`alias ll='ls-al'`</br>

### 1.2.4、 查看提交日志
* 作用：查看提交记录
* 命令：git log[option]
 * option
   * `--all` 显示所有分支
   * `--pretty=oneline`将提交信息显示为一行
   * `--abbrev-commit`使得输出的commited更加简短
   * `--graphy`以图的形式显示
   * `--decorate`在Mac本上有时会不显示装饰，这个可以让其显示

### 1.2.5、 版本回退
* 作用：版本切换
* 命令：`git reset --hard commit ID`
   * commit ID可以使用`git-log`或者`git log`指令查看 
* 如何查看已经删除的记录
   * git reflog
   * 可以查看已经删除的提交记录
* 如何让某一类文件不进行提交到缓存区
   * 创建`.gitignore`文件
   * 使用VI编辑器，`vi .gitignore`
   * 输入`*.a`，将.a后置的文件都不存入缓存区



