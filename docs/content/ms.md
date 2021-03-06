**项目介绍**

略

**软件测试四个阶段**
    

    单元测试--》集成测试--》系统测试--》验收测试

**python的元组和列表**


    1 相同：
        1 两者都是一个可以放任意数据类型的有序集合，可以是数字、字符串、对象等。
        2 都支持负索引
        3 都支持切片操作
        4 都可以随意嵌套
    
    2 区别：
        1 列表是动态的，长度大小不固定，可以随意增加、删除、修改元素；
        2 元组是静态的，长度在初始化的时候就已经确定不能更改，也无法增加、删除、修改元素
    
    如果数据发生变更的可能性不大，就用元组存储，如果数据是需要频繁的进行数据的修改增加，就使用列表


**web测试和app测试区别**

    单从功能上来说，两者没什么区别
    区别：
    1 系统架构方面
        1 web项目是b/s架构，基于浏览器的；只要web服务器有更新，客户端就会同步更新
        2 app项目c/s架构，必须有客户端；app修改了服户端，那app所有版本的功能都要重新进行一遍测试
    
    2 性能方面
        1 web项目 需检测 响应时间、cpu、memory
        2 app项目 除了检测响应时间、cpu、memory外，还需检测流量、电量等
    
    3 兼容性方面
        web项目：
            1 浏览器（火狐、谷歌、IE等）
            2 操作系统(win7，win10，Linux等)
        app项目：
            1 设备系统： iOS（iPad、iPhone）、android（不同牌手机）
            2 手机设备根据手机型号、分辨率不同进行测试
    
    4 相对于web项目，app有专项测试：
        1 干扰测试：中断、来电、短信、关机、重启等
        2 弱网测试（模拟Wi-Fi、移动网络状态及丢包情况）；网络切换测试（网络断开后重连、3g切换到4g/wifi等）
        3 安装、更新、卸载
            安装：考虑安装时的中断、弱网、安装后删除安装文件等情况
            卸载：需考虑卸载后是否删除app相关文件
            更新：分强制更新、非强制更新、增量包更新、断点续传、弱网状态下更新
    
    5 测试工具方面：
        自动化工具：app一般使用appium; web一般使用selenium
        性能测试工具：app一般使用jmeter; web一般使用jmeter
    
    6 界面操作
        关于手机端测试，需注意手势，横竖屏切换，多点触控，前后台切换
    
    7 安全测试
        安装包是否可反编译代码、安装包是否签名、权限设置，例如访问通讯录等
    
    8 边界测试
        可用存储空间少、没有sd卡/双sd卡、飞行模式、系统时间有误、第三方依赖（QQ\微信登录）等
    
    9 权限测试
        设置某个app是否可以获取该权限，例如是否可以访问通讯录、相册、照相机等。


**H5 页面测试**

    测试要点：
    1. 业务逻辑测试
        - 业务逻辑相关测试，视具体需求而定
    2. 页面元素UI测试
        - 主要包括文字、图片及页面布局等测试
            - 文字：风格是否一致，错别字、标点符号统一、换行是否正常、一行文字是否有省略还是全显示、图片与文字是否一致、页面刷新是否展示文字
            - 图片：
                - 静态：大小、风格
                - 动态： 大小、风格、准确性动态图、转场动画，loading动画，动画点击等
                - 页面刷新是否正常展示
                - 图片适配：不同屏幕和分辨率进行适配；
                - 是否内嵌链接；链接是否正常跳转
    3. 页面操作
        - 页面刷新是否正常
        -  页面跳转是否正常
        - 页面返回链接是否正确返回，点击手机物理返回键是否正常
        - 页面滑动是否正常，数据是否正确加载
        - 快速连续点击功能按钮，是否发生重复提交数据
        - 吐司或弹框提示是否正常显示
        - 弹框中各操作功能是否正常，弹框内操作是否会穿透，影响到弹框底部页面操作
        - 弱网情况下，数据加载时是否有加载提示；页面刷新或加载内容时是否出现抖动；数据获取不到，提示是否合理
        - 停留在某一页面，手机锁屏 或 将应用在后台运行，再次进入，是否正常展示当前页面
        - 是否需要用户登录：
            - 客户端未登录，进入页面，是否出现登录入口或登录提示；取消登录提示，再次进入页面，是否需要再次出现；页面成功登录后，退出H5页面，客户端是否登录
            - 客户端已经登录：进入H5，是否是登录状态；
        -  关于金额：
            - H5消费金额或充值金额后，账户余额是否正常；回到客户端，账户余额是否显示正常
            - 支付过程中，余额不足时，是否有充值连贯支付功能
    
    4. 接口测试
        - 接口返回处理：
            - 接口入参等边界值校验
            - 传输数据类型不符要求(小数、中英文、特殊符号等)，是否有正确提示
            - 请求成功，data内容为空时，如何处理
        - 接口性能；
            - 页面加载时间：接口返回数据时间过长影响用户体验
            - 资源相关：页面中图片应尽量小；资源应压缩
            - 服务端并发：用户量过多时，服务器性能影响
            - 内存： 反复访问，是否会占用大量内存
            - 流量消耗：一些比较固定等图片或其它资源，是否可本地缓存；数据量大时，是否设置量分页加载
    5. 网络测试
        - 网络环境：Wi-Fi，手机网络、热点
        - 网络异常：弱网测试、断网测试、网络间切换
    6. 适配测试
        - 图片高清适配；字体大小适配；页面布局宽度适配
        - 横竖屏适配
        - 不同平台适配
        - 如是iOS13及以上系统，深浅色适配
    7. 页面数据埋点测试
        - 埋点数据是否正确


​    
**红包测试**

    1. 功能测试
        1.发给指定人
            1 金额正确+无留言+无表情
            2 金额错误+无留言+无表情
            3 金额正确+有留言+无表情
            4 金额错误+有留言+无表情
            5 金额正确+有留言+有表情
            6 金额错误+有留言+有表情
            7 金额正确+无留言+有表情
            8 金额错误+无留言+有表情
        2. 金额额度测试：
            1> 数字：输入0，0.009，0.01，01，1，199.9，199.99，200，200.01测试边界值
            2> 输入中英文、特殊字符
            3> 是否可复制粘贴
            4> 输入字符有空格
        3. 留言测试
            1 输入数字、中英文、特殊字符、表情或各种组合
            2 输入大段文本，是否有文本长度限制
            3 输入空格
            4 是否可复制粘贴
        4. 表情测试
            1 录制的表情发送
            2 收藏的表情发送（动图/静图）
            3 下载的表情发送（动图/静图）
            4 增删改查
        5. 设置红包额度：
            1 零钱账户余额 < 额度值
            2、零钱账户余额 = 额度值
            3、零钱账户余额 > 额度值
            4、已绑定的银行卡付款：<额度；  >额度；=额度；
            5、新绑卡支付：<额度；  >额度；=额度；
        6. 红包支付
            1 密码付款：正确、错误
            2 指纹付款：正确、错误
            3 成功发送，账户余额是否正常；
            4 发送者/接收者看到的红包额度、留言、表情是否正常
            5 接收者成功领取，其账户余额是否正常；再次点击领取，只能查看红包信息
            6 红包超过24小时未领取，是否原路退回；账户金额是否正常更新；接收者此时点击红包是否提示过期
        7. 红包记录是否正常展示
        8. 群发红包
            1 其它和单发类似
            2 不同点：
                1 拼手气红包，每个人收到的金额随机，但其之和是发送的红包金额额度。普通红包，每个人收到的金额相同
                2 红包个数：
                    输入0是否有提示；
                    输入的个数小于群内人数，=群内人数，大于群内人数，超出最大红包个数
                3 红包未抢完时，未抢过红包的人点击时可成功领取，已抢过的再次点击时，只能查看信息；
                4 红包抢完后，所有人点击后只能查看红包信息
                5 24小时内，红包抢完，显示运气王昵称；未抢完的到24小时后，则不显示最佳手气，余额原路返回
                6 设置红包个数为3，金额为1时的场景
        
    2. 兼容性测试
        1 android和iOS
        2 iOS不同版本
        3 android不同版本
        4 不同分辨率
    3. 性能测试
        1 红包的打开响应时间
        2 耗电量
        3 流量消耗
        4 占用内存等
    4. UI测试
        1 界面的设计风格是否统一
        2 界面中文字是否简洁，有无错字
        3 是否易操作
    5. 中断测试
        1 网络异常
        2 切换到后台，再次切回
        3  手机锁屏再次进入
        4 低电量
        5 来电
        6 其它消息等
    6. 网络测试
        1 网络环境：Wi-Fi，手机网络、热点
        2 网络异常：弱网测试、断网测试、网络间切换

**测试六大特性以及在工作中的运用**

    1、六大特性：
        1 功能性---产品功能准备，安全满足
            功能性；
            准确性；
            互操作性（界面等）
            保密安全性（支付安全、登录安全等）
            功能的依从性（国际标准、国家标准、行业标准）
        2 易用性--产品便于学习操作
            易学性
            易理解性
            易操作性
            吸引性
            易用的依从性
        3 效率--软件性能
            时间特征
            资源利用性
            效率依从性
        4 可靠性--产品功能发生错误失效的能力
            成熟性（针对内部错误）
            容错性（针对外部错误）
            易恢复性
            可靠性的依从性
        5 可移植性--产品环境迁移的能力
            适应性
            易安装性
            易替换性
            可移植性的依存性
        6 可维护性---产品可修改的能力，修正、改进等
            易分析性
            稳定性
            易测试性
            可维护性的依存性

**测试用例的6大特性**

    1 一致性    
        1 主要包括用例模版一致；
        2 用例细粒度一致
        3 每个人编写手法一致
    2 覆盖率
        1 对需求对覆盖，包括隐含需求
        2 新需求对先有功能是否有影响
        3 不同场景覆盖
    3 易用性(可执行性)
        1 步骤易于理解
        2 信息描述准确
    4 准确性
        1 用例的执行准确度
    5 持续更新
        1 需求有变更，用例要及时更新
    6 复用性
        1 主要用例可以复用，减少维护成本

**http请求头包含得内容（请求行、请求头、请求体）**

    1 请求报文(请求行/请求头/请求数据/空行)
        1 请求行
            请求方法字段、URL和http协议版本
              例如：GET /index.html HTTP/1.1
                get方法将数据拼接在url后面，传递参数受限
            请求方法：get,post,head,put。。
        2 请求头：key value 形式
            user-agent:产生请求的浏览器类型
            accept：客户端可识别的内容类型列表
            host：主机地址
        3 请求数据
            post方法中，会把数据以key value形式发送请求
        4 空行
            发送回车符和换行符，通知服务器不再有请求头
    2 响应报文
        1 状态行；
        2 消息报头
        3 响应正文
**http响应包含内容；**

    1、状态行
    2、 响应头
        包含服务器类型、日期、长度、内容类型等
    3、响应正文

**http请求流程**

    1 域名解析
    2 建立tcp连接
    3 发送http请求，传输数据
    4 服务器返回数据
    5 浏览器解析数据，页面渲染
    6 关闭连接

一次完整的Http请求过程：
https://www.cnblogs.com/engeng/articles/5959335.html


**常见状态码**

    100:Informational 处理请求
    200:success 请求成功
    202: 已经接受请求，还未处理
    204: 服务器成功处理了请求，但还未返回内容
    301:重定向，链接发生变化
    404:请求失败，资源没有或不存在
    500；服务器遇到未知错误，无法完成请求
    503:由于临时服务器过载或维护，无法解决当前请求


    1xx: Informational（信息性状态码）接受的请求正在处理
    2xx: Success（成功状态码）请求正常处理完毕
    3xx: Redirection（重定向）需要进行附加操作完成请求
    4xx: Client error（客户端错误）客户端请求出错，服务器无法处理
    5xx:Server Error（服务器错误） 服务器处理请求出错

**性能指标**
https://zhuanlan.zhihu.com/p/38253500

    1 响应时间
    2 吞吐量（每秒事务数）
    3 错误率：一段时间内出错的请求在总请求数中的占比
    4 90%平均响应时间
        从计算平均响应时间的那些请求里去掉最慢的10%之后重新计算平均响应时间
        使用90%平均响应时间，因为去掉了出错超时的那些请求，使得得到的数据更加接近真实值。

**性能测试工具以及具体工具得操作【具体到哪个控件要说出】**

**工作中怎么定性能指标**

**电梯测试**

    1 功能测试 单个功能
        1 楼层键是否正常
        2 开关门是否正常
        3 上下键是否正常
        4 报警键是否正常
        5 通话功能是否正常
        6 楼层显示屏是否正常
    2 模块交互
        1 上行状态，有人在某楼层按下上升/下降，电梯是否会停止
        2 下行状态，有人在某楼层按下上升/下降，是否会停止
        3 满员状态，有人在某楼层按下上升/下降，是否停止
        4 电梯刚关上门，又立即按下上升/下降，是否会停止
    3 界面测试
        1 电梯的外观
        2 按钮的图标大小、显示
        3 电梯内部张贴的说明，如满载数量、报警装置说明等
    4 接口测试
        1 电梯和大楼层对应
        2 电梯和摄像头
        3 电梯和空调
        4 电梯和对讲机
        5 电梯和显示屏
        6 多个电梯间的协作能力
    5 易用性测试
        1 楼层按键高度
        2 电梯内是否有地毯、是否有空调、通风条件、照明条件、手机信号是否畅通
        3 电梯内是否有扶手，是否有针对残疾人的扶手等
    6 安全性测试
        1 下坠时是否有制动装置
        2 暴力破坏是否会报警
        3 超重是否会报警
        4 超时自动开门
        5 火灾报警后，是否可就近停靠
        6 停电情况下，是否有应急电源装置
    7 兼容性测试
        1 不同类型的电梯电压是否兼容
        2 电梯的整体和其它设备的兼容性，与大楼的兼容性，与海底隧道的兼容性等
    8 性能测试
        1 负载单人时的运行情况【基准测试】
        2 多人时的运行情况【负载测试】
        3 一定人数下较长时间的运作【稳定性测试】
        4 长时间运作时的运行情况【疲劳测试】
        5 不断增加人数导致电梯报警【拐点压力测试】
    9 场景验收测试
        1 多人从1楼上电梯，去不同楼层
        2 多人从不同楼层上电梯，一起到一楼

**微信视频测试**

    1 功能测试
        1 视频连接是否正常
        2 声音和画面是否正常，是否能同步
        3 挂断功能是否正常
        4 单人视频和多人视频是否正常
    2 性能测试
        1 压力测试：长时间视频是否正常，cpu、内存消耗情况等
        2  稳定测试：频繁进行视频和其它操作等
        3 前后台切换，突然来电或其它信息等
        4 安装卸载测试
        5 网络测试
        6 发热量测试、耗电量测试
    3 界面测试
        1 软件界面是否显示正常
        2 文字、图片和logo是否正常显示
        3 操作过程中各种提示是否正确
    4 易用性测试
        1 操作流程是否符合用户习惯，是否容易上手
        2 操作出现异常提示是否清晰易懂
    5 兼容性测试
        1 android手机测试
        2 iOS手机测试
        3 不同机性、不同版本、不同分辨率进行测试

**用例设计的方法**

    1 等价类划分
    2 边界值分析
    3 错误推测法
    4 判定表：
        该方法适合于逻辑判断复杂的场景，通过穷举条件获得结果，对结果再进行优化合并，会得到一个判断清晰的策略表。

**测试流程**

    1 需求分析
    2 指定测试计划
    3 测试用例编写
    4 测试执行
    5 测试bug提交
    6 bug验证
    7 测试报告汇总

**商品订单查询页面得用例现场编写【搜索框、日期控件、订单列表、查询条件、订单操作按钮】**

    1 搜索框：
        搜索框布局是否符合要求
        是否默认文字，如有是否正常显示
        点击搜索框，是否展示输入光标
        输入的订单号不符合规则，是否提示
        订单号符合规则
        是否会记录上次查询的订单号
        是否能完整显示订单号
        是否包含搜索图标
    
    2 日期控件
        控件布局是否符合要求
        默认是否展示当前日期
        日期格式是否符合要求：年月日/年月日时分秒
        点击日期控件，是否出现日期选择弹框
        日期弹框内是否可正常选择任意日期
        选好日期后，不确定，直接取消日期弹框，日期栏显示
        选好日期后，确定并取消日期弹框，日期栏显示
    
    3 订单列表
        默认订单列表展示样式
        需要查询的字段是否都正常显示
        是否有分页功能
        查询都条件无订单，订单列表展示
        查询都条件有订单，订单列表展示
        订单列表未占满当前屏幕，列表展示
        订单列表数据超出当前屏幕，是否可正常上下滑动页面
        订单列表查询字段过多，左右是否可正常滑动
        点击下一页，如有数据，是否正常加载新数据
        点击下一页，如已没有数据，是否有合理提示
        点击上一页，是否可正常返回
    
    4 查询条件
        输入不存在记录的查询条件
        输入有记录的查询条件
        单个查询条件搜索
        多个查询条件组合搜索
        条件下拉框是否可正常展示
        下拉框内条件是否点击是否正常
        选择下拉框内条件后，下拉框是否自动消失
        查询条件显示的内容是否是下拉框内选择的条件
        查询条件是可手动输入还是只能在下拉框中进行选择
    5 订单操作按钮
        发货操作
        退货操作
        退款操作
        快递选择

**前后端问题定位**
https://www.cnblogs.com/cookietxt/p/13495745.html

    1 前端bug：
        1 界面问题：如图标错误、样式错误等
        2 功能js兼容（android、iOS、h5）等
    2 后台bug：
        逻辑、性能、安全、数据错误、排序、提示语看接口返回
    3 常见bug:
        日期的处理转换
        极限值（数据库字段）
        前后端对接字段
        类型保持一致性
    4 接口信息
        1 500 服务器问题
        2 404 考虑接口是否发生变更
        3 200 后台返回错误信息，前端未处理
        4 前后端对接问题，状态未明确

**弱网测试**
https://www.jianshu.com/p/bb169ae18bca

    1 charles工具模拟弱网
        proxy--throttle setting 中设置
**抓包工具的使用 ，修改参数， 要说出具体的操作**
http://www.bubuko.com/infodetail-3580392.html

    Charles工具
        1 tools--rewrite，弹出改写设置弹框
        2 点击左侧add，右侧出现地址和参数相关信息窗
        3 右侧 name栏输入便于识别的名称
        4 location区点击 add输入URL
        5 参数区 点击add 输入参数值
        6 保存即可，下次请求时，将会自动加上修改的参数
**jmeter 接口关联怎么做**
https://zhuanlan.zhihu.com/p/143894465

    正则表达式提取器
        1 在请求后面，添加一个后置处理器- -正则表达式提取器
        将上一个请求结果通过正则表达式提取出来，放到下一个请求里面的参数中

**集成自动化测试得流程**

    1 编写测试用例
    2 执行测试用例，查找最新测试用例，自动发送报告
    3 定时执行用例【持续集成】
    4 成果验收

**接口测试流程**

    1 阅读接口说明/设计文档
    2 设计接口测试方案，如使用的接口测试工具
    3 编写接口测试用例
    4 执行测试
    5 收集测试结果，提交测试报告
    
    1 需求评审，熟悉业务和需求
    2 开发提供接口文档
    3 编写接口测试用例
    4 用例评审
    5 执行测试
    6 提交测试报告

**用java 写json 字符串提取**

    //将字符串转化json来提取
    JSONObject js = jSON.parseObject(str);  
    //获取key对应的value值
    String  s1 = js.getString("as");

**数据驱动原理**

    测试脚本读取数据源中的一行数据，赋值给相应的变量，执行用例。然后再继续读取下一行数据，继续执行，直至读取完所有的数据，测试结束。

**如何制定驱动测试**

    1 熟悉测试对象
    2 构建测试模型
    3 识别测试用例
    4 选择测试数据

**testNg 的属性**

**testNg 参数**

**编写testNg测试用例步骤**

    1 生成testng的测试框架
    2 在生成的框架中，编写测试代码逻辑
    3 根据测试代码逻辑，插入testng注解标签
    4 配置testng.xml文件，设定测试类、测试方法、测试分组的执行信息
    5 执行测试程序
**testNg常用注解**

    1 、@BeforeSuite: 标示此注解的方法会在当前测试集合(suite)中的任一测试用例开始运行之前执行。
    2、 @AfterSuite: 标示此注解的方法会在当前测试集合(suite)中的所有测试程序运行结束之后执行。
    3、 @BeforeTest:标示此注解的方法会在Test中任一测试用例开始运行前执行。
    4、 @AfterTest:标示此注解的方法会在Test中所有测试用例运行结束后执行。
    5、 @BeforeGroups: 标示此注解的方法会在分组测试用例的任一测试用例开始运行前执行。
    6、 @AfterGroups: 标示此注解的方法会在分组测试用例的所有测试用例运行结束后执行。
    7、 @BeforeClass: 标示此注解的方法会在当前测试类的任一测试用例开始运行前执行。
    8、 @AfterClass: 标示此注解的方法会在当前测试类的所有测试用例运行结束后执行。
    9、 @BeforeMethod: 标示此注解的方法会在每个测试方法开始运行前执行。
    10、 @AfterMethod:: 标示此注解的方法会在每个测试方法运行结束后执行。
    11、 @Test: 标示此注解的方法会被认为是一个测试方法,即一个测试用例