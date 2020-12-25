#### 1、hugo的安装(二进制安装，源码安装另寻他方)：
    brew install hugo
#### 2、站点生成：
假设生成站点到 /path/mysite:

    hugo new site /path/mysit

进入生成的站点：

    cd /path/mysite

#### 3、创建一个about页面：
    hugo new about.md
   创建的about.md在content下。创建一篇文章在post目录下，方便以后页面聚合：
   
    huto new post/first.md

   打开post/first.md进行文章编辑

#### 4、主题安装（具体主题可查看），下面以hyde主题示例：：
	cd themes git clone https://github.com/spf13/hyde.git
#### 5、运行Hugo，在站点根目录下进行调试：
	hugo server --theme=hyde --buildDrafts
   浏览器里打开查看： http://localhost:1313
#### 6、部署在github pages，GitHub上创建一个repository，命名为：个人github用户名.github.io.
   进入站点根目录执行Hugo生成最终页面:
   (注意，以上命令并不会生成草稿页面，如果未生成任何文章，请去掉文章头部的 draft=true 再重新生成)：

    hugo --theme=hyde --baseUrl="https://个人github用户名.github.io/"

#### 7、如果一切顺利，所有静态页面都会生成到 public 目录，将pubilc目录里所有文件 push 到刚创建的Repository的 master 分支。
    $ cd public
    $ git init
    $ git remote add origin https://github.com/gitHub用户名/gitHub用户名.github.io.git
    $ git add -A
    $ git commit -m "first commit"
    $ git push -u origin master 
#### 8、浏览器里访问：https://gitHub用户名.github.io/