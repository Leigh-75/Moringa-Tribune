### Moringa-Tribune
Walkthrough
1. Create the folder you want to store your django project in 
   ```
   mkdir Jango-Project cd Jango-Project
   ```
2. Create your virtual environment
```
python3.6 -m venv nameofvirtual
```
3. Activate your virtual environment
```
source nameofvirtual/bin/activate
```
3. Install django
```
pip install django
```
4. Create a requirements file
```
touch requirements.txt
```
5. Create a django project name it tribune
```
django-admin startproject tribune
```
6. CD into tribune and at the same level as the  ````manage.py```` file create a django app called news.
```
cd tribune 
  django-admin startapp news
```
7. Register the new app inside ````tribune/settings.py```` file in the INSTALLED APPS array. 
```
INSTALLED_APPS = [
    'news.apps.NewsConfig'
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
8. Creating a basic View. Inside ````news/views.py```` 
```
from django.http  import HttpResponse

# Create your views here.
def welcome(request):
    return HttpResponse('Welcome to the Moringa Tribune')
```   
9. Inside the news app create a ```urls.py``` file add the url list
```
from django.urls import path

from . import views

urlpatterns = [
    path('', views.welcome, name='welcome'),
]
```
10. Register these inside the main app Tribune inside ````tribune/urls.py````.
```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('news/', include('news.urls')),
    path('admin/', admin.site.urls),
]
```

11. To see the page run 
```
python manage.py runserver
```
Then go to port```127.0.0.1:8000/news```
