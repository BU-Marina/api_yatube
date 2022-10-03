# API для проекта Yatube
Yatube - социальная сеть, в которой можно создать учетную запись, публиковать посты, подписываться на любимых авторов и комментировать их записи.

## Технологии

    Python 3.7.9
    Django==2.2.16
    pytest==6.2.4
    pytest-pythonpath==0.7.3
    pytest-django==4.4.0
    djangorestframework==3.12.4
    djoser==2.1.0
    djangorestframework-simplejwt==4.7.2
    Pillow==8.3.1
    PyJWT==2.1.0
    requests==2.26.0

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Marina-ui/api_final_yatube
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции из директории yatube_api:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```

### Получить токен для авторизации:

Создать суперпользователя

```
python manage.py createsuperuser
```

или обычного пользователя через админку ../admin (войти через созданного суперпользователя)

Отправить на эндпоинт ../api/v1/jwt/create/ имя и пароль созданного пользователя/суперпользователя в теле запроса. Ожидаемый ответ:

```
{
  "refresh": "string",
  "access": "string"
}
```

Токен access передавать в заголовке каждого запроса, в поле Authorization, иначе вернётся *HTTP 401 Unauthorized*. Перед самим токеном должно стоять ключевое слово Bearer и пробел.

### Примеры запросов:

Просмотр доступных эндпоинтов:

```
http://127.0.0.1:8000/api/v1/
```

Подробнее о возможностях api yatube:

```
http://127.0.0.1:8000/redoc/
```
