## 使用相对导入

不废话了贴代码

```
不好的导入
# cones/views.py
from django.views.generic import CreateView

# DON'T DO THIS!
# Hardcoding of the 'cones' package
# with implicit relative imports
from cones.models import WaffleCone
from cones.forms import WaffleConeForm
from core.views import FoodMixin

class WaffleConeCreateView(FoodMixin, CreateView):
	model = WaffleCone
	form_class = WaffleConeForm
```

```
推荐的导入
# cones/views.py
from django.views.generic import CreateView

# Relative imports of the 'cones' package
from .models import WaffleCone
from .forms import WaffleConeForm
from core.views import FoodMixin

class WaffleConeCreateView(FoodMixin, CreateView):
	model = WaffleCone
	form_class = WaffleConeForm
```


|Code|导入类型|用途|
|:----|
|from core.views import FoodMixin        |absolute import           |使用外部项目时这么导入，如core是Django中其他app  |
|from .models import WaffleCone        |explicit relative         |使用当前项目/app的某个模块  |
|from models import WaffleCone| implicit relative| 经常被用在同一个项目/app 中导入其他模块（其实这是作者不推荐的做法）|