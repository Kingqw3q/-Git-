 # 1、 Git常用指令和基本操作
 ## 1.1、 获取本地仓库
如果要使用Git对代码进行版本控制，那么首先要获取本地仓库
* 对本地电脑创建一个空目录例如`123.txt`，让他作为我们的本地Git仓库
* 进入目录，在文件目录内右击打开Git bash
* 执行`git init`，或者在计算机任意地方输入 `cd e:/Git`  进入123.txt所在文件位置，也可以执行get init
* 使用`ll`查看文件，就可以查看到当前文件价下的隐藏文件`.git`文件

## 1.1.1、 配置Git用户名和邮箱
配置用户名和邮箱可以让编辑有缘可查
* 配置用户名
	* `git config --global user.name"用户名"`
* 配置邮箱
	* `git config --global user.email"邮箱"`

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
* 命令：`git commit -m"提交说明"`

### 1.2.3、 为常用指令配别名(.bashrc)
* 创建`.bashrc`文件
* #用于输出git提交日志</br>
`alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'`</br>
* #用于输出当前目录所有文件及基本信息</br>
`alias ll='ls-al'`</br>
* 在Git Bash中执行`source ~/.bashrc`

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

## 1.3、分支

### 1.3.1、查看本地分支
* 命令：git branch

### 1.3.2、创建本地分支
* 命令：git branch 分支名称

### 1.3.3、切换分支(checkout)
* 命令：git checkout  分支名称
* 切换到一个不存在的分支`git checkout -b 分支名称`

### 1.3.4、合并分支(merge)
* 首先要切换到master分支`git checkout master`
* git merge `Web`，就是将“Web”分支合并到“master”分支上来

### 1.3.5、删除分支
不能删除当前分支
* git branch -d b1 删除分支，需要各种检查
* git branch -D b1 不做任何检查，强制删除

### 1.3.6、解决冲突
当两个分支上对文件的修改可能会存在冲突，例如同时修改了同一个文件的同一行，这时就需要手动解决冲突决冲突步骡如下：
* 处理文件冲突地方
* 将解决完的冲突加入暂存区
* 提交到仓库(commit)
* `<<<<<<<<hard`是本分支的内容
* `>>>>>>>> dev`被合并分支的内容

CONFLICT（content）:Merge conflict in 123.html
Automatic merge failed;fix conflicts and then commit the result.

### 1.3.7、开发中分支使用原则与流程
几乎所有版本控制系统以 某种形式支持分支。
使用分支意味着你可以把你的工作从开发主线上分离来进行重大的BUG修改、开发新功能，以免影响开发主线。

在开发中，一般有如下分支使用原则与流程：
* master（生产）分支
线上分支，主分支，中小规模项目作为线上运行应用对应的分支；

* develop（开发）分支
是master创建的分支，一般作为开发部门的主要开发分支，如果没有其他并行开发不同时期上线要求，都可以在此版本上经行开发，阶段开发完成后要合并到master上，准备上线。

* feature/xxxxx分支（不删除）
从feature创建的分支，一般是同期并行开发，但不同时期上线创建的分支，分支研发完合并到develop分支

* hotfix分支
从master派生的分支，一般作为线上BUG修复使用，修复完成需要合并到master、test、develop分支。

* 还有其他分支可删除，例如test分支（用于代码测试）、pre分支（预上线分支）等

## 1.4Git远程仓库
### 1.4.1、常用的托管服务[远程仓库]
* 注册码云
### 1.4.2、创建远程仓库
### 1.4.3、配置SSH公钥
* 生成SSH公钥
	* `ssh-keygen -t rsa`[rsa是一种非对称密钥算法]
	* 如果公钥存在则覆盖
	* 不断回车确认，确认的是SSH公钥的文件名称
* Gitee配置账户公钥
	* cat ~/.ssh/id_rsa.pub
	*将公钥置入gitee的仓库公钥中
* 验证是否配置成功
	*ssh -T git@gitee.com

### 1.4.4、查看远程仓库































