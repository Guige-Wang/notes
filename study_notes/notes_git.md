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
## 命令使用步骤
- 先使用`git status` 检测所有未被添加的文件，新增的或者修改的文件会变为红色。
- 使用`git add` 文件名.扩展名 添加指定文件，或者使用`git add .` 添加所有文件。已经被添加的文件会变为绿色。
- 使用`git commit -m'版本描述信息'` 提交文件并生成版本。提交完成之后文件，就会变为原色。
- `git log` 查看日志（版本更新记录）
# 版本回滚
- `git reset --hard 版本号` 将代码或文件退回到指定的版本
- 测试文字
- `git reflog` 查看包括回滚版本在内的日志
- 曾经被回滚的版本可以通过`git reflog`来查看日志找到版本号，然后进行回滚