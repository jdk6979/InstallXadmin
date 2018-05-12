# InstallXadmin
Python3 | Django后台管理框架Xadmin安装指南

> Django是python的重量级web框架,写得少,做得多,非常适合后端开发,它很大的一个亮点是,自带后台管理模块,但它自带的后台管理有点丑,而Xadmin是基于bootstrap开发的一套后台管理框架,界面非常美观,只需几步就可以替换自带的Django_admin
> 网络上能查到的都是基于python2的Xadmin安装方法,我这里提供基于Python3的Xadmin安装方法

# python3主环境django安装xadmin
##安装官网下载xadmin,
> github网址:`https://github.com/sshwsfc/xadmin`

> ![官网下载xadmin](http://upload-images.jianshu.io/upload_images/3203841-f7e521dc569f9693.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 解压`xadmin-master.zip`,将解压后文件夹内`xadmin`拷贝到项目根目录下
![解压](http://upload-images.jianshu.io/upload_images/3203841-8d1d47283f839aaf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



## 配置安装app

```python
INSTALLED_APPS = (
'xadmin'
'crispy_forms'
)
```

## 安装额外的插件

`pip install django-import-export`

## 在admin.py同级目录下建立adminx.py,配置格式如下
```python
import xadmin

from .models import *
# Register your models here.

class BigTitleAdmin(object):
    # 定义需要显示的大主题
    list_display = ['big_title_name']

xadmin.site.register(BigTitle, BigTitleAdmin)
```

## 建立与xadmin相关的表,并将表添加到数据库

`python manage.py makemigrations`
`python manage.py migrate`

## 在主目录下的urls.py中配置新的路由

```
from django.conf.urls import include, url
from django.contrib import admin
import xadmin

urlpatterns = [

    url(r'^xadmin/', xadmin.site.urls),
    url(r'^admin/', include(admin.site.urls)),

]
```

## `base.py`更改源码,换logo

> ![base.png](http://upload-images.jianshu.io/upload_images/3203841-7ad13aa97d391027.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 后台效果展示

> ![image.png](http://upload-images.jianshu.io/upload_images/3203841-8f7cf5e187584799.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
