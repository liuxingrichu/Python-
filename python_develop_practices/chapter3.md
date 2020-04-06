### 准备团队开发环境 ###
1. 在公共服务器上建立用户、设置权限
	1. 用户与用户组的建立

			$ sudo groupadd dev
			$ sudo adduser bpbook --ingroup dev
			$ sudo userdel -r bpbook

	2. sudoers

			$ sudo visudo
			
				%dev ALL=(ALL) ALL
				bpbook ALL=(ALL) ALL
				
				%用户组名 主机名=(权限) 命令
				用户名 主机名=(权限) 命令
	3. virtualenv
		1. 当多人共同开发项目时，不能因为某个组员添加了某个库或者变更某个版本，而影响整个团队的开发环境。
2. 问题跟踪系统（Issue Tracking System， ITS）
	1. ITS是在开发过程中创建任务、追踪状态、管理任务的系统，后面介绍的Trac和Redmine是已ticket为单位进行任务管理的系统。
	2. Trac：任务管理和缺陷管理，可同Wiki和版本管理系统等协同工作
		1. 安装
		2. 添加用户认证模块

3. 版本控制系统（管理源代码及其变更历史的系统）
	1. 版本控制管理系统（Version Control System, VCS）分类
		1. Subversion集中管理工具
		2. Mercurial、Git分布式版本控制工具
	2. Mercurial与Trac联动绑定
4. 有利于团队开发的工具
	1. Skype：团队沟通、会议纪要
	2. DropBox：团队共享文档
	3. Google Docs：多人同时编辑文档，可根据文件等级设定权限


