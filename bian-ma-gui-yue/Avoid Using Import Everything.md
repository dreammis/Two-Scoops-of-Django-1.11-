## 一定不要使用 import*

就是类似

```
from django.forms import *
from django.db.models import *
```

不想赘述了，因为什么，因为你永远不知道这个*里面到底有多少你不知道的鬼东西在里面，天知道哪个名字重复了，冲突了，自己给自己找麻烦!

## 还有一些特殊的导入

比如Django中model的类型有CharField，而forms包中也有类似的CharField，都叫这个名字，那么请使用别名 **as**

```
from django.db.models import CharField as ModelCharField
from django.forms import CharField as FormCharField
```