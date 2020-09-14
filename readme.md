# Git Submodule Demo
## Instructions
各个子模块实际上是独立的项目，它们和父项目仅仅存在引用关系。

### create a submodule
- create parent repo first
```shell script
mkdir GitSubmodule
cd GitSubmodule
git init
# edit readme here, such as readme.md
git add .
git commit -m "init commit"
# manual creates the remote repo,then run the following commands
git branch -M master
git remote add origin https://github.com/TTcheng/GitSubmodule.git
git push -u origin master
```
- create a submodule in the existed parent repo.
```shell script
cd GitSubmodule
mkdir GitSubmodule1
cd GitSubmodule1
git init
# edit any file here
git add .
git commit -m "sub initial commit"
# manual creates the remote repo,then run the following commands
git branch -M master
git remote add origin https://github.com/TTcheng/GitSubmodule1.git
git push -u origin master
# --important-- 添加子模块到父仓库(子模块应该有一次提交，并且已经推到远程分支)
cd ..
git submodule add https://github.com/TTcheng/GitSubmodule1.git GitSubmodule1
git add .
# 注意,这里提交的文件应该有子模块的目录，而不包括该目录下的文件
git commit -m "add submodule 1"
git push origin master
```
### clone with submodule
 - 全部项目 
```shell script
git clone --recursive https://github.com/TTcheng/GitSubmodule.git
git submodule foreach 'git checkout master'
git submodule update --init --recursive
```
 - 单个子模块
```shell script
git submodule update --init GitSubmodule1 
```