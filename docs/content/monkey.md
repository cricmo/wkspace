    

- https://blog.csdn.net/qq_30993595/article/details/80748559

    公司客户端示例：

      adb shell monkey -p com.quanmincai.caipiao --ignore-crashes -s 123123 --throttle 300 -v -v 20
- 参数v:
- -v 默认值，仅提供启动提示，操作结果等少量信息 比如adb shell monkey -p  xxx.xxx.xxx -v 1 ；
- -v -v 提供比较详细信息，比如启动的每个activity信息 ，比如adb shell monkey -p xxx.xxx.xxx -v -v 1 ；
- -v -v -v 提供最详细的信息 ，比如adb shell monkey -p xxx.xxx.xxx -v -v -v 1 

- --ignore-crashes 忽略异常崩溃，如果不指定，那么在monkey测试的时候，应用发生崩溃时就会停止运行；
- 如果加上了这个参数，monkey就会运行到指定事件数才停止。比如adb shell monkey -p xxx.xxx.xxx -v -v -v  --ignore-crashes 10 

- -s:指定伪随机数生成器的seed值  seed值相同，则两次monkey测试产生的事件序列也相同

**查看设备中的包 data/data**
> adb shell dumpsys activity | grep mFocusedActivity

> ~~dumpsys activity | grep mFocusedActivity~~

**命令中用到的参数**

    --throttle  
    设定两个事件之间一个固定延迟，可以减缓monkey的执行速度。
    如果不指定，monkey将不会被延迟，事件将尽可能快地生成和发送消息。
    单位：毫秒
    eg:adb shell monkey  --throttle  3000  -p com.tencent.news  100    
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。

    --pct-touch  
    （空格后加数字）设定触屏事件生成的百分比。
    触屏事件是一个有手指按下，抬起事件的手势。
    eg:  adb shell monkey   --throttle  3000   --pct-touch  50  -p  com.tencent.news  100 
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。
    其中设定触屏的事件占比为50%。

    --pct-motion  
    设定滑动事件生成的百分比。
    滑动事件是一个先在某一个位置手指按下，滑动一段距离后再抬起手指的手势。
    eg:  adb shell monkey   --throttle  3000 --pct-motion  50  -p  com.tencent.news  100 
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。
    其中设定滑动的事件占比为50%。

    --pct-trackball  
    设定轨迹球事件生成的百分比。
    轨迹球事件是包含一系列随机移动和单击事件的事件
    eg:adb shell monkey --throttle  3000 --pct-trackball  50  -p  com.tencent.news  100
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。
    其中设定轨迹球的事件占比为50%。

    --pct-nav  
    设定基本导航事件生成的百分比。
    基本导航事件是模拟方向性在设备上输入向上、向下、向左、向右的事件。
    eg:adb shell monkey --throttle  3000 --pct-nav  40  -p  com.tencent.news  100 
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。
    其中设定基本导航事件的占比为40%。

    --pct-majornav  
    设定主要导航事件生成的百分比。
    主要导航事件通常会导致UI产生回馈信息，如单击Back键、Home键、Menu键等、
    eg: adb shell monkey  --throttle  3000   --pct-majornav  40  -p  com.tencent.news  100 
    向腾讯新闻发送1000次随机事件，每次事件间隔为3秒。
    其中设定主要导航事件的占比为40%。

    --hprof
    指定了该参数，Monkey会在发送事件序列的前、后，生成性能分析报告。
    通常会在data/misc目录下生成一个5MB左右大小的文件

    --ignore-crashes
    通常情况下，monkey会在测试应用程序崩溃或者发生异常后停止运行，若指定了该参数，则monkey将会在产生异常后，继续向系统发送事件，直到指定事件全部运行完毕。

    --ignore-timeouts
    通常情况下，当应用程序发生任何超时错误（application  not  responding）时，monkey将停止运行。
    若指定了该参数，则monkey将会在产生错误信息后，继续向系统发送事件，直到指定事件全部运行完毕

    --ignore-security-exceptions    : 忽略安全异常
    通常情况下，指定应用程序发生许可错误时（如证书许可，网络许可等），monkey将停止运行。
    若指定了该参数，即使应用程序发生许可错误，monkey会继续向系统发送事件，直到指定事件全部运行完毕。
    eg：adb shell monkey  --throttle  3000 --pct-trackball  50  -p  com.tencent.news  --ignore-security-exceptions  100 
 
    --kill-process-after-error：发生错误后直接杀掉进程

    --monitor-native-crashes：跟踪本地方法的崩溃问题

    --wait-dbg：直到连接了调试器才执行monkey测试。

    eg:
    adb shell monkey -p com.xy.android.junit -s 500 --ignore-crashes --ignore-timeouts --monitor-native-crashes -v -v 10000 > E:\monkey_log\java_monkey_log.txt
    产生时间序列的种子值：500
    忽略程序崩溃 、 忽略超时 、 监视本地程序崩溃 、 详细信息级别为2 ， 产生 10000个事件 。


**随机点击一个app n次，python脚本简单编写**
    
    import os

    def os_command(command):
        os.system(command)

    def monkey_click_n(package_name,click_num):
        os_command("adb shell monkey -p " + package_name + " -v -v " + str(click_num) +" > result01.txt")


    def monkey_click2(package_name,click_num):
        os_command("adb shell monkey -p " + package_name + " -v -v -s 34521 -- throttle 300 " + str(click_num) + " > result02.txt"


    def get_apkName(file_apk):
        os_command("aapt d badging " + file_apk + ">> apkName.txt")
        

    if __name__ == "__main__":
        monkey_click_n("com.xybaby.lucky",8000)
    # monkey_click_n("com.quanmincai.caipiao",5000)

**monkey日志初步分析**

    初步分析法： monkey出现错误后，一般的分析步骤

    1）先找到出现错误的位置

    2）查看出现错误之前2个switch之间的activity

    3）手动执行事件，复现问题

    4）若以上步骤还不能找出，产生错误时，有会seed值，输入相同的seed值，重新按照之前命令跑monkey

日志详细分析：http://www.cocoachina.com/articles/34914
    
**Event percentages（事件百分比）:**

    0：触摸事件百分比，参数--pct-touch

    1：滑动事件百分比，参数--pct-motion

    2：缩放事件百分比，参数--pct-pinchzoom

    3：轨迹球事件百分比，参数--pct-trackball

    4：屏幕旋转事件百分比，参数--pct-rotation

    5：暂时不知道这个是什么

    6：基本导航事件百分比，参数--pct-nav

    7：主要导航事件百分比，参数--pct-majornav

    8：系统事件百分比，参数--pct-syskeys

    9：Activity启动事件百分比，参数--pct-appswitch

    10：键盘翻转事件百分比，参数--pct-flip

    11：其他事件百分比，参数--pct-anyevent



   
