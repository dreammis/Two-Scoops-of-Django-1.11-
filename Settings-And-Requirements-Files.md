## Django工程的settings和requirements文件

Django 11 有超过150项系统内置设置。

作者推崇遵循：
- 所有settings文件都应该被存放在版本控制系统中
- DRY 不要重复的配置，可以抽出共同的部分作为base settings
- 敏感信息足够安全 这种敏感信息不应该在版本控制系统中

### 尽量让本地settings在版本控制系统中
### 使用多种settings文件

> settings/
> ———__init__.py
> ———base.py 共同设置
> ———local.py 本地设置
> ———staging.py 准线上设置
> ———test.py 测试设置
> ———production.py 生产设置

通过附加不同的参数来达到启动不同的settings文件的目的

```
python manage.py shell --settings=twoscoops.settings.local
python manage.py runserver --settings=twoscoops.settings.local
```

---

#### 敏感信息

设置本地环境变量
```
# setting
export SOME_SECRET_KEY=1c3-cr3am-15-yummy
export AUDREY_FREEZER_KEY=y34h-r1ght-d0nt-t0uch-my-1c3-cr34m

geting
import os
os.environ['SOME_SECRET_KEY']
'1c3-cr3am-15-yummy'

```
---
设置本地配置文件
JSON, .env, Config, YAML, XML

secrets.json
```
{
"FILENAME": "secrets.json",
"SECRET_KEY": "I've got a secret!",
"DATABASES_HOST": "127.0.0.1",
"PORT": "5432"
}
```

```
import json

from django.core.exceptions import ImproperlyConfigured

with open('secrets.json') as f:
    secrets = json.loads(f.read())

def get_secret(setting, secrets=secrets):
   ''''''
   try:
       return secrets[setting]
   except KeyError:
      error_msg = 'Set the {0} environment variable'.format(setting)
      raise ImproperlyConfigured(error_msg)

SECRET_KEY = get_secret('SECRET_KEY')

```

#### 配置文件中的路径问题

不推荐使用绝对路径
```
MEDIA_ROOT = '/Users/pydanny/twoscoops_project/media'
```

使用相对路径的方式

python3.4之后的版本加入了非常好用pathlib
```
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent
MEDIA_ROOT = BASE_DIR / 'media'
STATIC_ROOT = BASE_DIR / 'static_root'
STATICFILES_DIRS = [BASE_DIR / 'static']
TEMPLATES = [
{
'BACKEND': 'django.template.backends.django.DjangoTemplates',
'DIRS': [BASE_DIR / 'templates']
},
]
```


