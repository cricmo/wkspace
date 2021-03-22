* 查看当前终端
   > tty
* 仅显示当前用户正在使用的终端和登录时间
    > who am i
* 查看所有终端（功能最全,显示用户名，终端标记，登录时间，负载等信息）
    > w
* 查看当前目录： pwd

**列出文件**

    >ls 列出当前目录下的文件

    > ls -a 列出当前目录下的所有文件，包括隐藏文件

    > ls -l 列出当前目录下文件及文件详情

    > ls -lh 以更好的理解方式列出当前目录下的文件

    > ls -a 列出所有文件及子目录，包括以“.”开始的隐藏文件。使用l. 可以只显示隐 藏文件。

    > ls -A 列出除了“.”及“..”以外的所有项。

    > ls -h 以k字节为单位表示文件的大小，通常要配合-l使用【ls -hl】

    > ls -p  以k字节为单位表示文件的大小，通常要配合-l使用

    > ls -F  在文件或目录后面加上不同的符号来区别文件或目录的类型，其中“*”表示 可执行的普通文件;“/”表示目录;“@”表示符号链接;“=”表示套接字。

    > ls -S 根据文件大小排序。

    > ls -t  按文件修改时间排序。

    > ls -r 逆序排列。

    > ls --help 在标准输出上显示帮助信息。

    > ls --version : 在标准输出上输出ls程序的版本信息。

    > 通配符：
        > * 匹配0个或任意多个的字符  ls a*

        > ? 匹配一个任意字符。   ls a?

        > [ ] 匹配任意一个包含在括号里的单字符，如 [abc]、[a-k]、[1-5,a-i]、[ab,x-z]等。

    >ls | sed "s:^:'pwd' /:"   : 列出文件绝对路径（不包含隐藏文件）

    > tree   以树状形式显示目录结构

    > 



**创建目录：mkdir**

    1 mkdir test 当前目录下创建test目录
    2 mkdir test1 test2 创建多个目录
    3 mkdir -p test3/test4 当前目录下创建多级目录 testt3/test4
    4 mkdir -p -m 0777 test5/test6 当前目录下创建多级目录，并且多级目录的权限是777
**删除目录**

    1 rmdir test 删除teest目录，只能删除空目录
    2 rmdir -p test/test1/teest2 删除多级目录，test/test1/teest2都要删除且需要清空目录
**删除文件或目录**

    rm t.txt 删除文件t
    rm -r tt 删除 tt目录
    rm - i *.log  删除任何 .log 文件，删除前逐一询问确认
    rm -rf test 删除 test 子目录及子目录中所有档案删除，并且不用一一确认
    rm -- -f*  删除以 -f 开头的文件

**创建或编辑文件：**
    
    #方法，命令
    > vi
    > vi
    使用vi打开,默认是命令模式，需要输入a/i进入编辑模式
    按下esc键，回到命令模式
    输入  :wq!  强制保存退出
    或者  :x 保存退出
    :q  不保存退出:q! 不保存强制退出

    其它：
        1 复制当前行：非insert状态下，敲击两次yy
        2 复制多行：非insert状态下，光标开始，敲击y3y，将复制当前开始往下共3行
        3 粘贴：非insert状态下，点击p，执行粘贴
        4 跳转文件开始：非insert状态下，敲击两下g，光标跳转文件第一行
        5 跳转文件结尾：非insert状态下，shift+g 光标跳转到文件最后一行
        6 显示文件内容行号：
            非insert状态下，输入：set nu 回车
        7 删除行：
            非insert状态下，连续两次d,删除当前行
        8 删除多行
            非insert状态下，d3d,删除三行
        9 跳转第几行
            非insert状态下，输入：3 跳转到第3行
        10 查找字符串
            非insert状态下，输入/test, 则在文件中查找test字符串，按n，光标会跳转下一个，shift+n 光标跳转到上一个

**查看文件内容/日志内容**
    
    1 cat filexxx 查看文件全部内容
    2 more test.txt 分屏查看文件内容，按空格切换下屏,q 退出查看
    3 tail test.txt 查看test.txt文件倒数第10行
    4 tail -f test.txt 实时查看文件内容
    5 tail -f 200 te.txt 从te.txt文件倒数200行开始查看
    6 tail -3 tx.txt 查看文件的倒数三行
    7 head tt.txt 查看文件的前10行(默认)
    8 head -n 3 tt.txt 查看文件的前三行
    9 head -c 5 tt.txt 查看文件的前5个字节
    10 head -n -5 t.log 查看文件的最后5行
    11 ps -aux | less -N    ps查看进程信息并通过less分页显示

**移动或重命名文件**

    mv:
    移动文件或修改文件名，根据第二参数类型（如目录，则移动文件；如为文件则重命令该文件）。
    当第二个参数为目录时，第一个参数可以是多个以空格分隔的文件或目录，然后移动第一个参数指定的多个文件到第二个参数指定的目录中。

    mv t1 t2 t1命名为t2
    mv -i log.txt log2.txt : 将文件 file1 改名为 file2，如果 file2 已经存在，则询问是否覆盖

    mv * ../  : 移动当前文件夹下的所有文件到上一级目录

**复制文件**

    1 cp t.txt te/ 复制文件t.txt 到目录te下
    2 cp -r test/ tt/ 复制test目录下的文件到tt目录下
    3 cp -r test t2 复制test目录到t2目录下
**find**

    1 find / -name ios.js 全盘搜索iOS.js文件
    2 find / -type d -iname ap 全盘忽略大小写搜素ap目录
**匹配字符串grep**

    1 grep "grep" t.txt 从文件t.txt匹配grep所在的行
    2 grep -i "grep" t.txt 忽略大小写匹配
    3 grep -O "grep" t.txt 显示所有匹配到的grep字符串
  
**统计为文件行数**

    1 wc t.txt 显示统计结果13 78 333 t.txt数字分别对应行数、词数、字符数
    2 wc -l tt.txt 只显示行数
    3 wc -c t.txt 只显示字符数
    4 wc -w t.txt 只显示词数

**权限修改chmod**

    chmod参数：
        -c 当发生改变时，报告处理信息
        -R 处理指定目录以及其子目录下所有文件

    ugo:
        u ：目录或者文件的当前的用户
        g ：目录或者文件的当前的群组
        o ：除了目录或者文件的当前用户或群组之外的用户或者群组
        a ：所有的用户及群组

    r ：读权限，用数字4表示
    w ：写权限，用数字2表示
    x ：执行权限，用数字1表示
    - ：删除权限，用数字0表示
    s：特殊权限

    chmod 754 t.txt 将t文件权限修改为rwxr-xr-- r=4,w=2,x=1,每三位组成一组权限，754 分别代表三组权限的数字和，7=r+w+x,5=r+x,4=w
    r:读；w:写；x:执行

    chmod -R 777 test 修改test目录及目录下所有文件权限为777
**查看端口使用**

    netstat -ano|grep 4723 查看4723端口是否被占用
**查看进程信息 ps**

    ps -ef|grep node 查看node服务的进程信息
**杀掉进程**

     1 kill -9 56789  强制杀掉id为56789的进程
     1 killall node 杀掉所有的node进程
---

* 追加文字到文件
    > cat >>/tmp/oldboy.txt << EOF

    床前明月光

    地上鞋两双

    EOF

* Linux快捷键

    1. tab键    用于自动补全命令/文件名/目录名

    2. ctrl + l　　清理终端显示 

    3. clear/cls  清理终端显示

    4. ctrl + c 终止当前操作
* 特殊字符

   重定向符号
   > 1.>>    追加重定向，把文字追加到文件的结尾

   > 2.>     重定向符号，清空原文件所有内容，然后把文字覆盖到文件末尾

   >  echo "oldboy-python666" > /tmp/oldboy.txt

   >  echo "chaoge666" >> /tmp/oldboy.txt
------------------------------------
    把命令执行的结果信息，写入到文件中
    ip addr > /tmp/network.txt   #标准输出重定向 把命令执行结果信息，放入到文件中

* cd ~  : 进入 "home" 目录

* cd -  :进入上一次工作路径

* cd !$  :把上个命令的参数作为cd参数使用。

* tar命令
    参数：
        -c 建立新的压缩文件
        -f 指定压缩文件
        -r 添加文件到已经压缩文件包中
        -u 添加改了和现有的文件到压缩包中
        -x 从压缩包中抽取文件
        -t 显示压缩文件中的内容
        -z 支持gzip压缩
        -j 支持bzip2压缩
        -Z 支持compress解压文件
        -v 显示操作过程     
    1. tar -cvf log.* : 文件全部打成tar包
    2. tar -zcvf /tmp/etc.tar.gz /etc :将 /etc 下的所有文件及目录打包到指定目录，并使用 gz 压缩
    3. tar -ztvf /tmp/etc.tar.gz  : 查看刚打包的文件内容（一定加z，因为是使用 gzip 压缩的）
    4. 

* https://www.runoob.com/w3cnote/linux-common-command-2.html
