## Import

PEP8中规定了import导入的相关规则

1. 标准库导入  **Standard library imports**
2. 相关第三方库导入  **Related third-party imports**
3. 自定义或者一些特殊导入  **Local application or library specific imports**

``` python
    # Stdlib imports
    from math import sqrt
    from os.path import abspath
    # Core Django imports
    from django.db import models
    from django.utils.translation import ugettext_lazy as _
    # Third-party app imports
	from django_extensions.db.models import TimeStampedModel
	# Imports from your apps
	from splits.models import BananaSplit
```

