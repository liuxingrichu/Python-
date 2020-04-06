### 版本控制工具 ###
- 集中式代码库
	- CVS
	- Subversion
- 分布式版本控制系统DVCS（Distributed Version Control System）
	- Git
	- Mercurial

### 编辑器：Ubuntu python的vim配置 ###

vim $HOME/.vimrc 或 vim ~/.vimrc

	syntax on
	filetype plugin indent on

touch ~/.vim/ftplugin/python.vim
	
将Tab键换成四个空格，其为Python社区推荐的代码风格（PEP8，http://www.python.org/dev/peps/pep-0008, 即将缩进用四个空格代替）

	setl expandtab
	setl tabstop=4
	setl shiftwidth=4
	setl softtabstop=4

删除行末空格

	autocmd BufWritePre * : %s/\s\+$//ge

每行到80个字符时，自动换行（PEP8规定每行不得超过79个字符）
	
	setlocal textwidth=80

### pip ###

- pip --version
- 安装包清单
	- pip freeze

### 语法与调试工具 ###
- pep8（检查代码风格的工具）
- pyflakes（Python语法检查工具）
	- 类似有PyLint、pyChecker
- pdb（调试工具）

### Python之禅：The Zen of Python ###
"The Zen of Python"是Python开发者Tim Peter的文章，他为Python总结出19条特点。

http://www.python.org/dev/peps/pep-0020

import this

- 博客阐述(无法访问)
	- http://d/hatena.ne.jp/atsuoishimoto/20100920/1284986066