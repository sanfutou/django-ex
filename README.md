# django-ex
django xuexi

这个是我学django的一个记录

1、关于Django的版本

    python -m django --version   #可以查看Django的版本，我用的是2.0
2、建立一个项目

    我在m-py下建立了mysite
    django-admin startproject mysite  #在m-py下建立mysite目录
3、启用服务器

    python manage.py runserver
    浏览器打开 http://127.0.0.1:8000/可以看到启动页面
4、设置第一个view

 （1）python manage.py startapp polls    #在mysite下建立 polls目录
    编辑polls/views.py 添加如下代码
    from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
  （2）编辑polls/urls.py添加如下代码
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
  （3）返回上一级目录编辑mysite/urls.py添加如下代码
    from django.urls import include, path
from django.contrib import admin

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
  （4）启动服务器python manage.py runserver 进入 http://localhost:8000/polls
