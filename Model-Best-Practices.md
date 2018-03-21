# Model Best Practices

不要随随便便就搞一个model出来，否则你会后悔的！

作者列举了几个常用的库用于models

- django-model-utils 常用的TimeStampedModel,顾名思义，常用于存放时间戳的字段
- django-extensions 一个非常强大的django management 扩展，非常强大，但是我没用过

## 一句话
建议每一个app配备不超过5个models，如果太多意味着，你的app过于太重

## 小心那些model Inheritance（model 继承）

**Django Abstract Base Classes <> Python Abstract Base Classes**

- 如果两个models重叠的部分特别小，比如只有一两个字段是相同的，那么步入直接分别加入同一个fileds在俩不同的models
- 如果两个models重叠的部分足够大，（这个足够大是字面意思，原文就是enough），并且会导致冲突和不经意的疏忽，那么高一个abstract base models出来，两个其他models继承它
- Proxy models 是一种偶尔有用的的models， 它和其他的继承models完全不同（作者这里没说怎么不同）
- 尽量不要使用多重继承，很容易出错误。这里说的多重继承，指的应该是，一个models层层继承很多model， 作者建议使用ToOneFields以及ForeignKeys。

举例抽象类

```
from django.db import models

class TimeStampedModel(models.Model):
	"""
	An abstract base class model that provides self-
	updating ``created`` and ``modified`` fields.
	"""
	created = models.DateTimeField(auto_now_add=True)
	modified = models.DateTimeField(auto_now=True)
class Meta:
	abstract = True #这里定义了这个model类是抽象类
```

应用
```
from django.db import models

from core.models import TimeStampedModel

class Flavor(TimeStampedModel):
	title = models.CharField(max_length=200)
```

## Database Migrations

从django1.7开始，内置的migrations就被替换成South library了

- 一有新的app或者model创建，花上几分钟去migrate
- migrate之前要检查一下migration的代码，尤其是关联的部分
- 使用MIGRATION_MODULES去定义自己想要的migrations方式，第三方的
- 不要担心有很多migrations创建，可以使用squashmigrations将其带回到开始的部分（重置migrations的number）
- 运行migrations的时候记得备份你的数据


在migrations中可以加入自己想要的逻辑和sql文

具体可以参照
> https://docs.djangoproject.com/en/1.11/ref/migration-operations/#runpython
> https://docs.djangoproject.com/en/1.11/ref/migration-operations/#runsql


## Django Model 设计

2018/3/21 20:33:12 