**allure的几个特性**

	1. @allure.feature # 用于描述被测试产品需求2. @allure.story # 用于描述feature的用户场景，即测试需求
	3. with allure.step # 用于描述测试步骤，将会输出到报告中
	4. allure.attach # 用于向测试报告中输入一些附加的信息，通常是一些测试数据，截图等
	5. @pytest.allure.step # 用于将一些通用的函数作为测试步骤输出到报告，调用此函数的地方会向报告中输出步骤
	----
	https://blog.csdn.net/liuchunming033/article/details/79624474






