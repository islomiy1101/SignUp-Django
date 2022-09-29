### Django frameworkida ro'yxatdan o'tish (Sign Up) qismini tayyorlash
___
### 1.Yangi loyiha yaratamiz  
    django-admin startproject mysite
### 2. Loyihani ichida yangi app yaratamiz 
    python manage.py startapp users
### 3. Appni loyihaga qo’shamiz
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    #======= local app =======#
    'users',
]
```
### 4. Loyihani ishga tushiramiz
     python manage.py runserver
![This is an image](https://miro.medium.com/max/854/1*n-yE8dKEeWUA7P0HvV0qeg.png)

### 5. models.py faylida yangi User nomli model yaratamiz
    from django.db import models
    from django.contrib.auth.models import AbstractUser


    class User(AbstractUser):
        confirm = models.PositiveBigIntegerField(null=True, blank=True)
        
shundan so'ng settings.py fayliga kirib quyidagi buyruqni qo'shamiz

      AUTH_USER_MODEL='users.User'
### 6. admin.py fayliga kirib quyidagicha o'zgartirish kiritamiz
    from .models import User


    class UserAdmin(admin.ModelAdmin):
        list_display=('id','username','first_name')

    admin.site.register(User,UserAdmin)
### 7. modelimizni baza bilan integratsiya qilish uchun quyidagi buyruqlar ketma-ketligini beramiz
     python manage.py makemigrations
     python manage.py migrate
     
shundan so'ng admin qismiga kirish uchun superuser yaratamiz

    python manage.py createsuperuser
    
### 8. loyiha ichida templates nomli yangi papka yaratamiz

![This is an image](https://i.ibb.co/3CzV2Mb/1.png)
    
### 9. templates ni settings.py fayliga kirib sozlaymiz

![This is an image](https://i.ibb.co/DMH8M8F/2.png)

### 10. templates papkasi ichida yangi home nomli html fayl yaratamiz

![This is an image](https://i.ibb.co/z8fTnCq/3.png)

shundan so'ng base.html fayliga getbootstrap saytidan namuna sahifa olib joylaymiz

### 11. base.html

    <!doctype html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>SignUp Loyihasi</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-iYQeCzEYFbKjA/T2uDLTpkwGzCiq6soy8tYaI1GyVh/UjpbCx/TYkiZhlZB6+fzT" crossorigin="anonymous">
      </head>
      <body>
        {% include 'navbar.html' %}

        {% block mycontent %}
        {% endblock %}

        {% include 'footer.html' %}
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-u1OknCvxWvY5kfmNBILK2hRnQC3Pr17a+RTT6rIHI7NnikvbZlHgTPOOmMi466C8" crossorigin="anonymous"></script>
      </body>
    </html>

### 12. navbar.html va footer.html sahifalarini yaratamiz

      <nav class="navbar navbar-expand-lg bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Sign In</a>
            </li>

            <li class="nav-item">
              <a class="nav-link" href="#">Sign Up</a>
            </li>
          </ul>
          </div>
        </div>
        </nav>
        
        <footer class="bg-dark text-white fixed-bottom">
          <h3 class="text-center">All rights reserved &copy; 2022</h3>
        </footer>
        
        
