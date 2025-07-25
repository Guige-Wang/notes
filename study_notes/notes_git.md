git学习笔记
==============
git命令：
--------------
# 配置全局邮箱：
## 初次配置之后即可
`git config --global user.email "you@example.com"`
`git config --global user.name "your name"`
# 版本提交命令
- `git init` 初始化。即让git帮助我们管理文件
- `git status` 检测文件夹下的文件状态
- `git add 文件名.文件拓展名` 将指定文件添加文件到暂存区（添加的文件将被git管理）
  - `git add .`添加所有文件到暂存区
- `git commit -m'v1'` 提交代码到版本库（本地仓库）
## 提交命令使用步骤
- 先使用`git status` 检测所有未被添加的文件，新增的或者修改的文件会变为红色。
- 使用`git add` 文件名.扩展名 添加指定文件，或者使用`git add .` 添加所有文件。已经被添加的文件会变为绿色。
- 使用`git commit -m'版本描述信息'` 提交文件并生成版本。提交完成之后文件，就会变为原色。
- `git log` 查看日志（版本更新记录）
# 版本回滚
- `git reset --hard 版本号` 将代码或文件退回到指定的版本
- 测试文字
- `git reflog` 查看包括回滚版本在内的日志
- 曾经被回滚的版本可以通过`git reflog`来查看日志找到版本号，然后进行回滚
# 分支
## 分支操作命令
- `git branch 分支名`创建分支
- `git branch`查询分支
- 测试文字，测试修复bug分支
- 测试文字，新功能，解决分支冲突
- `git checkout 分支名`切换分支
- `git branch -d 分支名` 删除分支
  - `git branch -D 分支名` 强制删除分支（未推送的本地分支）
- `git merge 分支名` 合并分支，将目标分支内容合并到所在的分支
## 分支的作用：
- 默认的主分支通常命名为master，开发中的分支可命名为dev
- 紧急修复线上项目bug，可创建一个新的分支然后再合并。
- 可对各个开发模块做环境隔离
## 工作流
- 创建新的项目时至少需要两个分支master 和 development/dev；master是正式环境dev则作为开发环境



GitHub学习笔记  
===========


# 新建仓库推送代码步骤
## 本地仓库为空的情况
- `echo "# notes" >> README.md`
- `git init`
- `git add README.md`
- `git commit -m "first commit"`
- `git branch -M master`
- `git remote add origin https://github.com/Guige-Wang/notes.git` 设置origin为仓库地址
- `git push -u origin master` 推送master分支到远程仓库
## 本地仓库有内容的情况
- `git remote add origin https://github.com/Guige-Wang/notes.git`
- `git branch -M master`
- `git push -u origin master`
# 由于本地缺少正确的根证书或网络环境限制导致的错误及其解决办法
      $ git push -u origin master
      fatal: unable to access 'https://github.com/Guige-Wang/notes.git/': SSL certificate problem: unable to get local issuer certificate
## Windows（使用系统自带的证书）
`git config --global http.sslBackend schannel`
## Linux/Mac（更新证书）
`sudo apt update && sudo apt install ca-certificates`  # Debian/Ubuntu
`brew update && brew install openssl`                 # Mac