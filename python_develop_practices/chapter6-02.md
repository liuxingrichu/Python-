### 模块的分割设计###
#### 组件设计 ####
将子功能分割到一个个组件中去。

- 根据输入信息设计View
	- 输入功能
	- 数据来源：用户输入、既存数据、外部系统
	- 用户输入数据和向用户展示数据，都是通过View。
	- 由于View不会保存状态，大多数需要通过函数（后面提到的View函数）进行封装。
- 设计View关联的ApplicationModel
	- View函数可以根据输入参数返回输出结果。而且，一个函数只能关联一种Model类型。
	- 在不考虑DomainModel情况下，可以将每一个View函数对应一个ApplicationModel。View函数、ApplicationModel的名字可以根据实现的子功能名来命名，可以是{功能名}_view，{功能名}Model这样的形式。
- DomainModel的设计
	- 这里DomainModel以类的形式定义状态信息。
	- 定义DomainModel之后，就可以定义其方法。在该步骤中，需要明确各个方法会进行怎样的状态变化，并定义每一个状态变化的属性。除此之外，还需要根据方法的调用，将业务逻辑同其他的DomainModel状态变化相关联，定义变化的DomainModel的相关方法，使之可以被调用。要注意，不能直接修改其他DomainModel的状态。
- 将ApplicationModel和DomainModel相关联
	- 从ApplicationModel的方法触发并定义应该被调用的DomainModel，然后再确认功能输入输出是否满足条件。
- 整理ApplicationModel
	- 删除那些只和一个DomainModel对应的ApplicationModel，通过View直接调用DomainModel。在ApplicationModel中，作为对象的DomainModel通过一个类进行统一，然后，探索类的命名。
- 从组建设计到实现
	- 到此为止，已经讲子功能按组件进行了分割，这样就可以使用Python的模块、包进行封装整理，付诸实践了。

#### 模块与包 ####
对应Web应用程序而言，可以将每一个功能都分成一个包，在一个功能中用到的组件（View或者Model）可以分别使用模块来封装。Python中通过类和函数来实现每一个组件的功能。

基于MVC架构，一个实际的项目工程文件构成如下：

	project/
		__init__.py
		views.py
		models.py
		services/
			__init__.py
			twitter.py
			twitpic.py
		utils.py
		templates/
		tests/
			__init__.py
			test_models.py
			test_views.py
			test_services.py
			test_utils.py


	project/__init__.py的用途

		该文件需要编写WSGI应用的入口,或应用程序启动时必要进行的一些处理过程。
		还有Model模块导入、初始化数据库的连接、读取配置文件等操作。

- project/views.py及project/utils.py
	- 分别实现View与Utility
- project/models.py
	- 实现DomainModel和ApplicationModel，以及导入数据库连接的模块。
- project/services
	- services在多数时，通过包来整理。
- project/templates
	- 放置HTML模板。
- project/tests/
	- 存放单元测试。

在更大规模的项目中，会将多个project合并成一个站点。例如根据用户的不同（终端用户与提供服务的用户）、DomainModel的分离情况而建立不同的project进行合并。