### 编写单元测试之unittest模块 ###
Python中，可使用unittest标准模块，编写单元测试。

测试的执行可以使用nose，其是一个可以自动找出所有测试单元并自动执行的实用工具，还提供了丰富的插件功能。

- unittest模块
	- unittest是从unit以及sunit派生出来的基于xunit测试工具类库。主要使用的是其中的unittest.TestCase类。用户通过继承该类，将各个测试用例在该类的成员方法中体现出来。
	- 在类方法名前加上test前缀，表示测试用例的名称。

			import unittest
			
			class TestIt(unittest.TestCase):
				
				def test_it(self):
					"""This method is one of the test case"""
			
				def test_one(self):
					"""Another test case"""

	- TestCase类中，提供了用来配置环境的测试配置器和判断测试结果的断言方法。
	- 测试配置器是在测试前用来准备测试的前提条件以及在测试后清理测试环境的一组功能。在unittest中，每一个类均有setUp、tearDown方法分别在测试前和测试后被调用，可在其方法内编写在测试执行前处理测试环境的相关功能代码。
	- 每一个类都有的配置器：

			class TestIt(unittest.TestCase):
				
				def setUp(self):
					"""Prepare the test environment"""
				
				def tearDown(self):
					"""Clear the test environment"""
	- 每一个模块的配置器：
			
			def setUpModule():
				"""Prepare the test environment"""
			
			def tearDownModule():
				"""Clear the test environment"""
	- setUpModule在每一个测试模块开始前都会调用执行一次，*tearDownModule会在所有测试结束后调用一次*。
	- Python中可以使用assert断言来判断测试结果。

			a = 1
			b = 2
			c = a+b
			assert c==3, "%d != %d" % (c, 3)

	- 最常用的断言方法是assertEqual。

			def test_it(self):
				a = 1
				b = 2
				c = a + b
				self.assertEqual(c, 3)
