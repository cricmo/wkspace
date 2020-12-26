**1、git安装. 略**

**2、本地创建新仓库：**

- 创建新文件夹，打开，然后执行:
- >git init

**3、检出仓库：**
- 执行如下命令以创建一个本地仓库的克隆版本：
- >git clone /path/to/repository
- 克隆远端服务器上的仓库:
- >git clone username@host:/path/to/repository
---
**4、日常工作用到的：**
#### 基本命令：
 1. *拉取工程下所有更新的内容:*
- >git pull

 2. 查看本地状态:
- >git status

3. 输入完命令后选取修改文件添加，如果要添加所有修改文件用“git add * ”
- >git add .
- >git add * （所有文件提交）

4. 提交add选取的文档
- >git commit -m "提交的描述信息"

5. 把文件push到服务器
- >git push origin HEAD:refs/for/master 

or
- >git push origin master

6. 创建分支
- >git checkout -b 分支名称 

7. 切回主线
- >git checkout master  

8. 删除分支
- >git branch -D   分支名称

#### 未入库文件自己aboand后的处理方法：
1.  查看提交记录
- >git log
2. 本地退回到想要退回节点的提交记录
- >git reset --soft + 要退回到节点的commit ID
3. 之前更新的记录是绿色的
- >git status 
4. 此时本地之前的更新记录是红色的了，就可以再修改之前提交的文件，也可以本地直接删除,修改完成后重新走提交流程
- >git reset

---
#### 注意事项：
push文件最好切换到分支上去操作，具体方法：

创建一个分支：
- >git checkout -b 分支名称

然后在分支上进行add，commit等操作。

commit完成后再执行push操作，
- >git push origin HEAD:refs/for/master

---
Ps.

git commit 进入输入comment框后按“a”进入编辑框，

输入完comment后按esc后按shift + ：，

然后输入wq后回车，回到主界面后Git push即可。

---
如果被退回修改后重新提交，

则再Git add后执行git commit --amend后再push

（此方法也适用于在审核前想修改文件或二次提交审核前想修改文件）

---
<a href="https://rogerdudler.github.io/git-guide/index.zh.html">可查看网上的《git 简明指南》快速熟悉</a>

<a href="https://www.despairyoke.com/2019/04/18/2019/2019-04-18-git-basecommand/">网上看到的一个博客：git 基础命令记录</a>


