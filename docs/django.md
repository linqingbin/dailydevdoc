# Django
## Install
```
pip install django
```

## Admin

### Start new project
```
django-admin startproject {site name}
```

### Start new app
1. Create new app folder: `python manage.py startapp {app name} {app path}`
* Add app to `setting.py`: `setting.installed_apps`
* Create Model in `models.py`
    
        from django.db import models

        class User(models.Model):
            name = models.CharField(max_length=50, default="admin")
            email = models.EmailField(max_length=50)

* Create view in `views.py`

        from django.http import JsonResponse, HttpResponse
        def hello(request):
            return HttpResponse("Hello")

* Add route in `urls.py`

        from django.urls import path
        from newapp import views

        urlpatterns = [
            path('newapp', views.hello),
        ]

* Add urls in global `urls.py`:


        from django.conf.urls import include, url
        urlpatterns = [
            path('newapp', include('newapp.urls')),
        ]

* (Optionally) Add model to admin in `admin.py`

        from django.contrib import admin
        from newpp.models import User

        @admin.register(User)
        def UserAdmin(admin.ModelAdmin):
            pass

* Finished

### Change admin password
```
python manage.py changepassword <user_name>
```

### Two different ways to add url
* Use include
```python
from django.conf.urls import include, url
urlpatterns = [
    path('newapp', include('newapp.urls')),
]
```

* Import module
```python
from django.conf.urls import include, url
import newapp
urlpatterns = [
    path('newapp', newapp.urls),
]

```

### Frequently used moudles

| Moduel | Useage | Sample |
|:----------------:|--------------------------|--------------------------------------------------------------------------------|
| django.db | build model | from django.db import models |
| django.http | build response | from django.http import JsonResponse |
| django.urls | build route | from django.urls import path |
| django.core | core modules | from django.core import serializers|
| django.contrib | addon modules | from django.contrib import admin|
| django.shortcuts | Convenient shortcut | from django.shortcuts import render |
| django.utils | common tools | from django.utils import timezone |
| django.conf | get django config | from django.conf import settings |
| django.apps | get django app config | from django.apps import AppConfig |
| django.test | build test | from django.test import TestCase |

## Models
### Init model
```
Question(question_text="What's new?",pub_date=timezone.now())
```
### Query model
```
Question.objects.get(pk=1)
Question.objects.all()
Question.objects.filter()
Question.objects.raw({SQL})
```
### Debugging model
```
python manage.py shell
```

## Views

### Build response 
* Html
```python
from django.shortcuts import render
def hello(request)
    return render(request, '{html page path}', {data})
```
* Json
```python
from django.http import HttpResponse
def hello(request)
    return JsonResponse({data})
```
* Others
```python
from django.http import HttpResponse
def hello(request)
    return HttpResponse(status=201)
```

### Get request content
* GET: `request.GET.dict()`
* POST: `request.POST.dict()`
* PUT: `from django.http import QueryDict;QueryDict(request.body)`
* PATCH: same with put
* DELETE: same with put

## Test
Build test script
```
from django.test import TestCase
class Test1(TestCase):
    def test_get():
        result = self.client.get('user')
```
Run test
```
python manage.py test newapp
```

## Django Rest framework
### Install
```
pip install rest_framework
```

### Create new API
1. Create model as usual
* Serialize Model

        from newapp.models import User
        from rest_framework import serializers
		
		class UserSerializer(serializers.HyperlinkedModelSerializer):
            class Meta:
                User = User
                fields = ('username', 'email')

* Create API view

        from rest_framework import viewsets
        from newapp.models import User
        from newapp.serializers import UserSerializer
            
        class UserViewSet(viewsets.ModelViewSet):
            queryset = User.objects.all().order_by('-date_joined')
            serializer_class = UserSerializer

* Add urls

        from django.urls import include, path
        from rest_framework import routers
        from newapp import views

        router = routers.DefaultRouter()
        router.register('users', views.UserViewSet)

## Referral
* [Django Document](https://docs.djangoproject.com)
* [Django Rest framework quick start site](https://www.django-rest-framework.org/tutorial/quickstart/)