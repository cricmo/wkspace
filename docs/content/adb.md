- **参数d直接进入当前USB连接的设备的shell环境**
   > adb -d shell
- **参数e 进入当前模拟器设备的shell环境：**
   > adb -e shell
- **参数s的使用：进入指定设备的shell环境**
   > adb -s udid名称 shell
- **adb devices 出现的三种状态：**
    1. offline 不能调试只能连接，有可能adb 与安卓系统不匹 配
    2. device(正常状态可调试) 
    3. unauthorized(连接后不能调试，原因是未在手机上同意调试)
- **显示设备的详细信息**
    > adb devices -l
- **查看设备日志**
   
      1. adb logcat >lg.txt
      2. adb -s udidName logcat >lg.txt
- **logcat其它用法**
    
    1. 日志筛选：
    > adb -s udid logcat |findstr packageName >test.txt
    2. 到shell里面获取：

      adb shell
      logcat |grep packageName >/data/local/tmp/text.txt
- **bugreport 命令，会将 dumpsys,dumpstate和logcat 的信息全显示出来：**
   > adb bugreport >bgtest.log
- **单独显示dumpsys 和 dumpstate的信息：**

      adb shell dumpsys>dp.log
      adb shell dumpstate >dps.log
- **pull 手机到电脑：**
    > adb pull /data/locat/tmp/xx.txt c:\test
- **push 电脑到手机**
    > adb push Desktop\bug.log /data/local/tmp
- **start-server 检查服务状态，如果没启动就启动：**
    > adb start-server
- **kill-server 命令，杀死所有 adb 进程**
- **shell命令，adb shell : 进入Android的shell环境**
- **vmstat 命令会显示服务器的状态值,包括服务器的 CPU 使用率，内存 使用，虚拟内存交换情况,IO 读写情况:**
   > adb shell vmstat
- **~~以 root 身份重启 adbd 守护进程，对于未获得 root 权限的手 机，这个命令执行时会报错的:~~**
   > ~~adb root~~
- **usb 命令，在 usb 上重启守护进程的监听:**
   > adb usb
- **tcpip <port> 命令，在特定端口上以 tcpip 协议重启守护进程的监听:**
   > adb tcpip 8787

- **#手机Wi-Fi连接电脑:**
   1. 先使用USB连接手机和电脑，获取设备号：
      > adb devices
   2. 重启守护进程：
      > adb tcpip 8787
   3. 然后查看手机设备的 ip，这里需要 保持电脑 ip 和手机 ip 能够互相 ping 通，使用 adb connect连接设备:
      > adb connect telIP
   4. 再次查看连接的设备,出现两个连接，一个USB连接，一个Wi-Fi连接，拔掉数据线，则可正常操作：
      > adb devices
- **断开Wi-Fi连接命令：**
   > adb disconnect telIP

