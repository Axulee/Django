#1. Study Django

##1.1. Django 管理工具
django-admin 的命令介绍:

	Available subcommands:
	
	[django]
	    check
	    compilemessages
	    createcachetable
	    dbshell
	    diffsettings
	    dumpdata
	    flush
	    inspectdb
	    loaddata
	    makemessages
	    makemigrations
	    migrate
	    runserver
	    sendtestemail
	    shell
	    showmigrations
	    sqlflush
	    sqlmigrate
	    sqlsequencereset
	    squashmigrations
	    startapp
	    startproject
	    test
	    testserver
	……省略部分……

##1.2. 创建项目

使用管理工具 django-admin 来创建 wechatvideo 项目：
`django-admin startproject wechatvideo`

	$ cd wechatvideo/
	$ tree
	.
	|-- wechatvideo	#项目的容器
	|   |-- __init__.py	#一个空文件，告诉 Python 该目录是一个 Python 包
	|   |-- settings.py	#该 Django 项目的设置/配置
	|   |-- urls.py	#该 Django 项目的 URL 声明; 一份由 Django 驱动的网站"目录"
	|   `-- wsgi.py	#一个 WSGI 兼容的 Web 服务器的入口，以便运行你的项目
	`-- manage.py	#一个实用的命令行工具，可让你以各种方式与该 Django 项目进行交互

	$ django-admin
	
	Type 'django-admin help <subcommand>' for help on a specific subcommand.

##1.3. 启动服务器

启动服务器`python3 manage.py runserver 0.0.0.0:8000`  
访问服务器`127.0.0.1:8000`

这里多说两句，一般情况下，我们是将系统搭建在服务器端，挂载运行，希望其他主机都可以访问，故需要更改文件settings.py  
`ALLOWED_HOSTS = ['']`-->`ALLOWED_HOSTS = ['ip of The server', 'localhost', '0.0.0.0:8000']`  

如我的服务器的ip地址为9.134.76.160（可用`ifconfig`查询），那么：  
启动服务器`python3 manage.py runserver 0.0.0.0:8000`  
访问服务器`9.134.76.160:8000`


##1.5. 视图和 URL 配置

wechatvideo/wechatvideo/view.py 文件代码：

	from django.http import HttpResponse
	 
	def hello(request):
	    return HttpResponse("Hello world ! ")

wechatvideo/wechatvideo/urls.py 文件代码：

	from django.conf.urls import url 
	from . import view
	 
	urlpatterns = [
	    url(r'^$', view.hello),
	]

##1.6. Django 模板
在上一节中我们使用 django.http.HttpResponse() 来输出 "Hello World！"。该方式将数据与视图混合在一起，不符合 Django 的 MVC 思想。  
本节介绍 Django 模板的应用，模板说白了就是一个.html文本文件，用于分离文档的表现形式和内容，故此节需要有HTML的基础。

在项目的根目录底下创建 templates 目录并建立 hello.html文件，整个目录结构如下：

	wechatvideo/
	|-- wechatvideo
	|-- manage.py
	|-- templates
	    |-- hello.html

需要向Django说明模板文件的路径，即修改wechatvideo/settings.py，修改 TEMPLATES 中的 DIRS 为 `'DIRS': [BASE_DIR+"/templates",],`

##1.7. Django 模型

##1.8. Django 表单

###1.8.1. HTTP 请求
####GET 方法
####POST 方法

###1.8.2. Request 对象

##1.9. Django Admin 管理工具


#2. My project

##2.1. TODO

##2.2. TODO

##2.3. TODO
