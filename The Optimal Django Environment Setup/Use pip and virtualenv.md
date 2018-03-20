## 使用pip以及Virtualenv

这俩就不说那么多了，我也没管作者说的，自己一些有用的，或者一些见解随便聊聊


---

pip 安装包文件，可以指定镜像

```
sudo pip install -i http://pypi.douban.com/simple/ requests
```

当然还有阿里的源什么乱七八糟源

virtualenv
环境管理工具

virtualenvwrapper
可以自由切换版本的一个工具


貌似近一段时间pipenv这个库，是结合两者在一起的一个库，还有一个好处是pip uninstall一些库，它实质上是只删除requests库，而不去理睬当初安装它的时候关联的一些其他库。

而pipenv可以避免这个问题

具体想了解的话 [pipenv](https://github.com/pypa/pipenv)