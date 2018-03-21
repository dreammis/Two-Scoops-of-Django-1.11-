## 举个栗子

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1521543304154&di=ad42d9c432b52fb6ce8bd1c60cabef06&imgtype=0&src=http%3A%2F%2Fimg.mp.sohu.com%2Fq_mini%2Cc_zoom%2Cw_640%2Fupload%2F20170708%2Fb889681e1c7e471f8f58a0799585811a.jpg)


作者举了个冰激凌(Ice Cream Ratings)评分系统的工程例子，系统给不同牌子(brands)以及口味(flavors)的冰激凌打分



![](https://i.imgur.com/rlwmACU.png)


> repository_root 目录
> 
|文件名|用途|
|:---|
|.gitignore|git生成的文件，文件列举了需要git排除的文件|
|config/|对应的上节所说的<configuration_root>目录，放置urls.py settings以及wsgi文件|
|Makefile|部署的配置文件|
|manage.py|django的启动文件|
|README.rst and docs/|说明文件额|
|requirements.txt|python库列表文件|
|icecreamratings/ |对应上节的<django_project_root>文件夹，是django项目所在的目录|



> 接下来来看django_project_root
|文件名|用途|
|:---|
|media/|用于放置用户上传的一些静态资源，诸如头像或者视频之类的，项目初期或者小型项目可以这么做，不过在国内的公司一般倾向于云存储的方式|
|products/|ice cream 的品牌以及口味的app|
|profiles/|项目中用户相关的app|
|ratings/|用户评分的app|
|static/|项目包含的静态资源文件所在|
|templates/|django自带的template目录|




2018/3/20 18:25:21 