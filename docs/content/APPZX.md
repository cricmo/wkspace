**1、app专项测试原因**

    普通功能测试无法发现的问题：
        crash问题
        设备兼容性问题
        流量过多使用问题
        app导致耗电量过快问题
        网络不稳定，如白屏、卡死等

**2、app测试考虑的方面**

    1、安装、更新、卸载测试
    2、网络测试：弱网、网络中断、网络切换
    3、中断测试：关机、重启、来电
    4、前后台切换
    5、调用第三方或被第三方调用
    6、兼容性测试
    
**3、工具**

    1、ddms
    2、jmeter
    3、postman
    4、charles
    5、adb 
    6、禅道
    7、git管理
    8、数据库可视化工具
    9、
**框架**

    1、appium + python 

**《《大话移动app》》**

    1、工具类
        网络问题定位：tcpdump + wireShark
        静态代码测试：findbugs ; lint ; 

    2、移动端性能测试
        Android原生测试框架：Instrumentation
        第三方工具：emmagee
        命令行查看内存： adb shell dumpsys meminfo packageName

    3、黑盒测试两大点：
        1、功能场景测试
        2、视觉、交互测试

    