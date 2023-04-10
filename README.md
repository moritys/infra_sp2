

# API Yamdb

Данный проект содержит в себе ревью, рейтинг и комментарии на фильмы, книги и музыку. Похож на IMDb, но обширнее.

#### Шаблон наполнения env-файла

    SECRET_KEY  =  'yoursecretdjangokey'
    
    DB_ENGINE = django.db.backends.postgresql # указываем, что работаем с postgresql
    
    DB_NAME = postgres_name # имя базы данных
    
    POSTGRES_USER = postgres_user # логин для подключения к базе данных
    
    POSTGRES_PASSWORD = password1234! # пароль для подключения к БД
    
    DB_HOST = db # название сервиса (контейнера)
    
    DB_PORT = 5432 # порт для подключения к БД
---

#### Запуск приложения в контейнерах
После запуска контейнера с приложением необходимо выполнить следующие команды в терминале:

    docker-compose exec web python manage.py migrate 
    docker-compose exec web python manage.py createsuperuser 
    docker-compose exec web python manage.py collectstatic --no-input
---
#### Заполнение базы данными

Резервные данные сохранены в dump.json в контейнере. Чтобы их использовать, необходимо выполнить в терминале следующее:
    
    docker-compose exec web python manage.py shell 
    # выполнить в открывшемся терминале: 
    >>> from django.contrib.contenttypes.models import ContentType 
    >>> ContentType.objects.all().delete() 
    >>> quit() 
    docker-compose exec web python manage.py loaddata dump.json
