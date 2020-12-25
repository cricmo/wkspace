    

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
    



   
