**appium 安装总体分为两种形式，两种最好都进行安装：**

* 第一种是命令行安装方式，参照第一、第二步，命令行方式安装的，appium 没有界面不能录制
* 第二种是安装界面版，参照第三大步(也请完成第一、二(1-8)步的公用软件安装)，界面版可以支持录制



#### 一、windows 下安装 appium 
**1. 公用软件安装**
* 1.1 安装 jdk1.8

  请根据自己的 windows 配置下载相应的版本 下载后安装，一路下一步即可完成安装
* 1.2 sdk安装

  网盘内下载 sdk 压缩包，下载后解压即可使用
* 1.3 node安装
  
  网盘内下载 node 安装包，一路下一步即可，安装完成后一般会自动默认配上环境变量
* 1.4 Java的环境变量配置 ： 略 
* 1.5 Android环境变量配置 ：略
* 1.6 appium的安装：
    
      npm -g install appium@1.15.1 
* 1.7 安装 appium-doctor 检查命令
      
      npm -g install appium-doctor 
* 1.8 分别执行 appium-doctor 和 appium，验证是否安装成功
#### 二、Mac下环境搭建
**先安装 xcode，并且启动一次 xcode，再执行以下步骤:** 
* 1、安装 brew，在终端下执行
> /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 

* 2、 安装 libimobiledevice，在终端下执行:
> brew install libimobiledevice --HEAD 
* 3、 安装 ideviceinstaller
> brew install ideviceinstaller
* 4、 安装 carthage，在终端下执行:
> brew install carthage
* 5、安装ios-webkit-debug-proxy
> brew install ios-webkit-debug-proxy
* 6、安装 node，在终端下执行: 
> brew install node
* 7、安装 ios-deploy
> npm install -g ios-deploy
* 8、安装 jdk

  在网盘中下载 jdk 文件，一路下一步安装
* 9、安装 sdk
  
  在网盘中下载 sdk 压缩包，下载后解压即可
* 10、配置环境变量，在终端下编辑/etc/profile 文件
> vi /etc/profile
  
  如果没有权限请先执行:
> sudo chmod 777 /etc/profile

内容如下:

    export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home 
    export ANDROID_HOME=/Users/lixionggang/Desktop/android-sdk-macosx
    export NODE_PATH=/usr/local/lib/node_module
    export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$ANDROID_HOME/tools:$ANDROID_HO ME/platform-tools:$PATH

然后保存，保存后在终端下再输入:
> source /etc/profile 
* 11、安装 appium-doctor，在终端下执行:
> npm install -g appium-doctor 
* 12、安装 appium，在终端下执行:
> npm install -g appium@1.15.1
* 13、检查环境，在终端下分别执行以下命令:
> adb deivces 

可以正常操作 
> appium-doctor 

检查无误appium 可以正常启动 appium服务

 
 