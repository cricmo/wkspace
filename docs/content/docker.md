**1.获取镜像；**
> docker pull ubuntu

**1. 启动容器：**
> docker run -it ubuntu /bin/basn

参数解析：
1.  -t: 在新容器内指定一个伪终端或终端
1. -i: 交互式操作
1. ubuntu: ubuntu 镜像
1. /bin/bash：放在镜像名后的是命令，这里我们希望有个交互式 Shell，因此用的是 /bin/bash

1. 退出容器终端：exit

**2. 查看所有的容器:**
> docker ps -a

**3. 启动一个已经停止的容器:**
> docker start containerID

**4.后台运行：-d指定容器的运行模式**
> docker run -itd --name ubuntu-test ubuntu /bin/bash

**5.停止容器：**
> docker stop containerIDs

**6.重启一个容器：**
> docker restart <容器 id>

**7.进入容器：**
> 1. docker attach <容器 id> // 使用该命令进入容器，退出容器时，会导致容器停止
> 2. docker exec -it  <容器 id> /bin/bash // 推荐使用此方式。 使用该命令进入容器，退出容器时，不会导致容器停止
> 3. 查看exec参数说明：docker exec --help

**8.导出 <容器 id> 快照到本地文件ubuntu.tar:**
> docker export  <容器 id> > ./docker/ubuntu.tar

**9.导入容器快照：(将快照文件 ubuntu.tar 导入到镜像 test/ubuntu:v1:)**
> 1. cat docker/ubuntu.tar | docker import - test/ubuntu:v1
> 1. docker import http://example.com/exampleimage.tgz example/imagerepo // 指定URL或某一目录导入

**10.删除指定容器：**
> docker rm -f <容器 ID>

**11.清除所有处于终止状态的容器：**
> docker container prune

**web相关：**

1.查看指定容器的网络端口：
> docker port <容器ID>
2. 查看web应用程序日志：
> docker logs -f <容器ID>
3. 查看web应用程序容器的进程：
> docker top <容器ID>
4. 检查web程序. 返回一个json文件，记录docker容器的配置和状态信息
> docker inspect <容器ID>

5. 停止web应用
> docker stop <容器ID>
6. 查询最后一次创建的容器：
> docker ps -l
7. 移除web应用容器(容器必须是停止状态)：
> docker rm <容器ID>

**docker镜像**

1. 列出镜像：
> docker images
2. 查找镜像：两种方式：
> docker search 镜像名称

    结果参数解析：
    NAME: 镜像仓库源的名称
    DESCRIPTION: 镜像的描述
    OFFICIAL: 是否 docker 官方发布
    stars: 类似 Github 里面的 star，表示点赞、喜欢的意思。
    AUTOMATED: 自动构建。

> docker网址：https://hub.docker.com/
3. 删除镜像：
> docker rmi 镜像名称
4. 创建镜像，两种方式更改：
    1.更新：
    2.创建：
    > https://www.runoob.com/docker/docker-image-usage.html
5. 设置镜像标签：
> docker tag <容器id> userName/镜像源:nerTagNamee

**容器连接**

1.网络端口映射：
> docker run -d -P training/webapp python app.py

> docker run -d -p 127.0.0.1:5002:5000 training/webapp python app.py  //默认是绑定tcp端口
 
> docker run -d -p 127.0.0.1:5003:5000udp training/webapp python app.py  // 绑定udp端口

2.查看端口的绑定情况：
> docker port <容器名称/id> 5000

3.docker 容器互联
1. 容器命名：--name
> docker run -d -P --name cric training/webapp python app.py

2. 新建一个docker网络：
> docker network create -d bridge test-net

    参数说明：
    -d：参数指定 Docker 网络类型，有 bridge、overlay。
    其中 overlay 网络类型用于 Swarm mode

3. 运行一个容器，并链接到新建到test-net网络：
> docker run -itd --name test1 --network test-net ubuntu /bin/bash

4. 另开一终端，运行一容器链接到新建到test-net网络：
> docker run -itd --name test2 --network test-net uubuntu /bin/bash

5. 容器内安装ping: 进入容器终端：
> apt-get update
> apt install iputills-ping

4.dns配置：

1. 查看容器dns信息：
    > docker run -it --rm ubuntu cat etc/resolv.conf

2. 手动指定容器配置；
> docker run -it --rm host_ubuntu --dns=114.114.114.114 --dns-search=test.com ubuntu

    参数说明：
    -h HOSTNAME 或者 --hostname=HOSTNAME： 设定容器的主机名，它会被写到容器内的 /etc/hostname 和 /etc/hosts。
    --dns=IP_ADDRESS： 添加 DNS 服务器到容器的 /etc/resolv.conf 中，让容器用这个服务器来解析所有不在 /etc/hosts 中的主机名。
    --dns-search=DOMAIN： 设定容器的搜索域，当设定搜索域为 .example.com 时，在搜索一个名为 host 的主机时，DNS 不仅搜索 host，还会搜索 host.example.com。
**docker 仓库管理：**
1.  登录：
> docker login

2. 退出：
> docker logout

3. 推送镜像：
> docker tag ubuntu:18.04 dockerUser/ubuntu:18.04
> docker push dockerUser/ubuntu:18.04
> docker search dockerUser/ubuntu

**-- 删除镜像：----**

    1. 删除所有已停止的容器 docker rm $(docker ps -a -q)
    2. 删除所有镜像 docker rmi $(docker images -q)
    3. 强制删除所有镜像 docker rmi -f $(docker images -q)

**dockerfile的使用：**

1.定制镜像：
**https://www.runoob.com/docker/docker-dockerfile.html**

2.**Compose 运行多容器的工具**
https://www.runoob.com/docker/docker-compose.html

3.** 的 **
