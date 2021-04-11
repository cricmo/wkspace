### **参数化**
1. 参数的引用方式：${}
2. 正则表达式在线测试工具: http://tool.oschina.net/regex/
3. 

https://www.cnblogs.com/imyalost/p/7062784.html

### 拉勾app
**1、实时查看接口的处理能力【3】**

    jmeter + influxDB + Grafana

**2、二次开发【4】**

    1、插件的三种方式：
        1、BeanShell
        2、自定义请求编写 java sampler
            实现Java sampler功能的两种方式：
                继承abstractJavaSamplerClient抽象类
                实现JavaSamplerClient接口
        3、自定义函数助手

**3、【5】开发性能测试平台**

**4、【8】三个性能测试场景（统称为：基石场景）**
    
    1、基准场景
        单线程或少量线程对单接口进行测试
    2、单接口负载场景
        通过模拟多线程对单接口进行负载测试
    3、混合场景负载测试
        多个接口多个线程按照一定比例进行测试

        如何控制场景比例：
        逻辑控制器--》吞吐量控制器

**5、【9】性能测试方案**

**6、【10】监控指标**

    linux指令监控：
        1、磁盘查看：iostat 
            iostat -x

        2、查看网络
            netstat

        3、统计内存使用情况
            free -m

        4、查看各个进程对资源占用状况

**7、【11】分布式服务链路监控 skywalking**

    1、
**8、【12】可视化监控屏操作**

**9、【13】容器docker示例**

**10、【14]java jvm定位cpu飙升问题**

**11、【15】jvm分析内存 可视化监控工具**

**12、【16】代码级定位工具 arthas**

**13、【18、19】 mysql性能优化**

**14、【20】全链路测试**