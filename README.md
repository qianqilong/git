### 1.基本配置
1. 命令行
```js
ll 显示显示详细列表
mkdir 创建目录
pwd 当前文件夹
cd 进入目录
rm-rf 删除文件
```
2. 配置全局身份信息
```js
git config --global user.name ""
git config --global user.email ""
```
3. 配置局部身份信息
```js
进入.git文件
打开config文件
添加下面内容
[user]
    name=
    email=
```
### 2.基本使用
1. 常用命令
```js
git init初始化新仓库 
git clone ...克隆代码 
git clone -b dev ... 克隆指定分支 

git status 查看状态 

git add index.js 提交单个文件 
git add . 提交所有文件
git reset 撤销上次提交到暂存区

git commit -m '提示信息' 提交到仓库中 
git commit -a -m '提交信息' 提交已经跟踪过的文件，不需要执行 
```
2. 忽略文件```.gitignore```
```js
node_modules
*.log
dist
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
```
3. 移除仓库的文件
```js
git rm home/index.js 移除本地和仓库文件 
git rm --cached home/index.js 移除仓库文件 
```
4. 修改仓库中文件名
```js
git mv home/index.js home/index.ts 本地也会修改
```
5. 修改提交仓库的提交信息
```js
git commit --amend

按Esc退出输入模式进入命令行模式
:wq保存修改并且退出 。
:w回车后底行会提示写入操作结果，并保持停留在命令模式。
:q! 回车后放弃修改并退出。
:e! ，回车后回到命令模式。
```
### 3.日志和自定义命令
1. 查看log日志
```js
git log 查看日志
git log -p  查看日志并显示文件差异
git log -p -2 查看最近2次日志并显示文件差异 
git log --name-only 显示已修改的文件清单
```
2. 自定义命令
```js
git config --global alias.a add a命名add
git a .
/*
git的全局配置文件在用户文件夹下.gitconfig
[alias]
	a = add
*/
可以直接在全局配置中添加快捷命令
[alias]
	a = add .
  c = commit -m
  l = log
  s = status
```
### 4.分支管理
1. 创建分支的操作
```js
(1)创建了主分支,并进行了提交
(2)git branch home 创建分支
```
2. 切换分支
```js
(1)git branch 查看分支 
(2)git checkout home 切换分支
(3)书写功能不影响主分支
快捷命令:git checkout -b home 创建并切换
```
3. 合并分支
```js
(1)git checkout master  切换到master分支
(2)git merge home 合并分支的代码
(3)git branch --merged 查看已经合并的分支
(4)git branch --no-merged 查看没有合并的分支
```
4. 分支冲突
```js
<<<<<<< HEAD
// 首页的身份认证
=======
// 首页功能的开发
>>>>>>> home

使用编辑器修改冲突的文件
添加暂存区 表示已经解决冲突
git commit 提交完成
```
5. 删除分支
```js
普通删除:git branch -d home  
强制删除:git branch -D home
```
### 5.临时暂存stash
1. 问题出现
```js
当你在一个分支工作时,代码并没有完成,无法提交,
这时你着急去其他分支处理问题,可以使用暂存区
```
2. 暂存区
```js
(1)git stash 储藏工作 
(2)git stash apply 恢复暂存区
```
3. 删除暂存区
```js
(1)git stash list 查看储藏列表
(2)git stash drop stash@{0} 删除储藏
快捷操作:git stash pop 应用并删除储藏
```
### 6.版本标签tag
1. 添加标签
```js
一个版本的总结
git tag v1.0 
```
2. 列出标签
```js
git tag
```
3. 版本打包压缩
```js
在window终端可能报错,建议在git的命令行界面
git archive main --prefix='Git' --format=zip > git.zip
```
### 7.定义PowerShell命令
1. 注意事项
```js
(1)定义的命令只可以在PowerShell中使用
(2)定义完成之后,关闭vscode终端输入命令
```
2. 初始化命令文件
```js
echo $profile
输出对应目录
如果有对应目录文件添加下面命令
无则添加目录文件
```
3. 快捷命令文件
```js
function gs{git status}
function gl{git log}
function ga{git add .}
function gp{git push}
function gii{git init}
function gim() {
  param([string] $pkg)
  git commit -m $pkg
}
function go() {
  param([string] $pkg)
  git checkout $pkg
}
function gb() {
  param([string] $pkg)
  git branch $pkg
}
```
### 8.rabase合理分支合并
1. 问题的引出
```js
创建的分支的主分支状态和当前的主分支状态的差异
主分支向前走了,改变子分支的创建点
```
2. 改变子分支的创建点
```js
(1)确认在子分支中
(2)git rebase master
(3)git checkout master
(4)git merger home
```
### 9.SSH密钥链接
1. 生成密钥
```js
ssh-keygen -t rsa
```
2. 远程填写密钥
![对象和函数的原型链](D:\workCode\FrontEndCode\Git\ssh.png)
### 10.连接远程仓库
1. 连接远程仓库
```js
(1)初始化了仓库
(2)git remote add origin [链接]
```
2. 查看远程仓库
```js
(1)git remote -v 查看远程仓库连接
(2)git branch -a 查看远程分支本地分支
```
3. 同步远程分支
```js
(1)
```