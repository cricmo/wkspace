- **安装app**
   > adb install apkName

   > adb install -r apkName

- **卸载app**
   > adb uninstall apk包名(com.zhihu.android)

- **参数d直接进入当前USB连接的设备的shell环境**
   > adb -d shell

- **参数e 进入当前模拟器设备的shell环境：**
   > adb -e shell

- **参数s的使用：进入指定设备的shell环境**
   > adb -s udid名称 shell

- **停止adb服务器：**
   >adb kill-server

- **adb devices 出现的三种状态：**
    1. offline 不能调试只能连接，有可能adb 与安卓系统不匹 配
    2. device(正常状态可调试) 
    3. unauthorized(连接后不能调试，原因是未在手机上同意调试)

- **显示设备的详细信息**
    > adb devices -l

- **查看手机所有的安装包**
   > adb shell pm list packages

- **查看手机安装的第三方包**
   > adb shell pm list packages -3

- **查看可用命令列表**
   > adb shell ls /system/bin

- **查看设备日志**
   
      1. adb logcat >lg.txt
      2. adb -s udidName logcat >lg.txt

- **logcat其它用法**
    
    1. 日志筛选：

      adb -s udid logcat |findstr packageName >test.txt
    2. 到shell里面获取：

      adb shell
      logcat |grep packageName >/data/local/tmp/text.txt

    3. 日志过滤:

      adb logcat *:W
      显示了优先级不低于“警告”的所有标记的所有日志消息

      优先级是以下字符值之一（按照从最低到最高优先级的顺序排列）：
      V：详细（最低优先级）
      D：调试
      I：信息
      W：警告
      E：错误
      F：严重错误
      S：静默（最高优先级，绝不会输出任何内容）

    4. 日志输出格式
   
      adb logcat -v thread
         显示了如何生成输出格式为 thread 的消息

      支持的格式：
      brief：
      显示优先级、标记以及发出消息的进程的 PID。

      long：
      显示所有元数据字段，并使用空白行分隔消息。

      process：仅显示 PID。

      raw：显示不包含其他元数据字段的原始日志消息。

      tag：仅显示优先级和标记。

      thread:：
      旧版格式，显示优先级、PID 以及发出消息的线程的 TID。

      threadtime（默认值）：
      显示日期、调用时间、优先级、标记、PID 以及发出消息的线程的 TID。

      time：
      显示日期、调用时间、优先级、标记以及发出消息的进程的 PID。

    5. 格式修饰符

      格式修饰符依据以下一个或多个修饰符的任意组合更改 Logcat 输出。如要指定格式修饰符，请使用 -v 选项，
      如下所示：
      adb logcat -b all -v color -d

      通过在命令行中输入 logcat -v --help 获取格式修饰符详细信息。

    6. 查看备用日志缓冲区

      [adb] logcat [-b <buffer>]

      使用 -b 选项运行 logcat 命令,以请求查看备用的环形缓冲区
         radio：查看包含无线装置/电话相关消息的缓冲区。

         events：查看已经过解译的二进制系统事件缓冲区消息。

         main：查看主日志缓冲区（默认），不包含系统和崩溃日志消息。

         system：查看系统日志缓冲区（默认）。

         crash：查看崩溃日志缓冲区（默认）。

         all：查看所有缓冲区。

         default：报告 main、system 和 crash 缓冲区。
      
      可以指定一个 -b 标记，后跟缓冲区逗号分隔列表:
      logcat -b main,radio,events




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

- ***截图***
   > adb shell screencap /sdcard/screen.png

- ***录制视频***

      adb shell screenrecord [options] /sdcard/demo.mp4

      [options]:

      --verbose
      	在命令行屏幕显示日志信息。如果您不设置此选项，则该实用程序在运行时不会显示任何信息。

      --size width x height
         设置视频大小：1280x720。默认值为设备的本机显示屏分辨率（如果支持）；如果不支持，则为 1280x720。为获得最佳效果，请使用设备的 Advanced Video Coding (AVC) 编码器支持的大小

      --bit-rate rate
      	设置视频的视频比特率（以 MB/秒为单位）。默认值为 4Mbps。您可以增加比特率以提升视频品质，但这样做会导致视频文件变大。
         下面的示例将录制比特率设为 6Mbps：
         screenrecord --bit-rate 6000000 /sdcard/demo.mp4

      --time-limit time
      	设置最大录制时长（以秒为单位）。默认值和最大值均为 180（3 分钟）。

- **vmstat 命令会显示服务器的状态值,包括服务器的 CPU 使用率，内存 使用，虚拟内存交换情况,IO 读写情况:**
   > adb shell vmstat

- **~~以 root 身份重启 adbd 守护进程，对于未获得 root 权限的手 机，这个命令执行时会报错的:~~**
   > ~~adb root~~

- **usb 命令，在 usb 上重启守护进程的监听:**
   > adb usb

- **tcpip <port> 命令，在特定端口上以 tcpip 协议重启守护进程的监听:**
   > adb tcpip 8787

- **端口转发**

   1. 主机端口 6100 到设备端口 7100 的转发：
      > adb forward tcp:6100 tcp:7100

   2. 主机端口 6100 到设备端口 local:logd 的转发：
      > adb forward tcp:6100 local:logd


- **#手机Wi-Fi连接电脑: Android 10 及更低版本 **
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

- **android 11 版本及以上可以Wi-Fi连接, 无需USB连接**

   > https://developer.android.google.cn/studio/command-line/adb



