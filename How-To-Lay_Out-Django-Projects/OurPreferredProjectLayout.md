## 作者推崇的工程结构


```
<repository_root> -- 
|--<configuration_root> -- 
|--<django_project_root> -- 

``` 
### 第一梯队： repository_root

repository_root 作为工程的根目录
包含 django_project_root & configuration_root 以及其他一些诸如README.rst, doc/ manage.py, .gitignore, requirements.txt以及部署或者启动项目的一些高级别的文件

### 第二梯队：
1. django_project_root

> 项目核心代码所在目录喽

2. configuration_root

> 故名思意项目配置文件目录， 注入urls.py， settings.py啦等等
> <font color=red>因为这个目录应该是一个python package所以，必须包含\_\_init\_\_.py </font>
