# FunnyCats
### Практика контейнеризации, деплоя на сервер и автоматизации деплоя (CI/CD) для проекта.

FunnyCats - социальная сеть для обмена фотографиями питомцев
Проект состоит из бэкенд-приложения на Django и фронтенд-приложения на React.
### Для неавторизованных пользователей:
- доступна главная страница со всеми питомцами;
- доступна страница отдельного питомца;
- доступна и работает форма регистрации;
- доступна и работает форма авторизации.

### Для авторизованных пользователей:
- доступна главная страница со всеми питомцами;
- доступна страница отдельного питомца;
- доступна возможность создания питомца (загрузка фото, добавление имени и даты рождения, выбор цвета питомца из предустановленных вариантов);
- доступна возможность выйти из системы.

## Как запустить проект в dev-режиме:
Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:Elllym-em/funny_cats_docker_project.git
```
```
cd funny_cats_docker_project
```
Cоздать и активировать виртуальное окружение:
```
python3 -m venv env
```
* Если у вас Linux/macOS
    ```
    source env/bin/activate
    ```
* Если у вас windows
    ```
    source env/scripts/activate
    ```
Установить зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python3 manage.py migrate
```
Запустить проект:
```
python3 manage.py runserver
```

## Примеры запросов API:
### Запрос на получение списка публикаций (GET):
```
/api/cats/
```
**Пример ответа:**
```
{
    "count": 1,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 1,
            "name": "string",
            "color": "string",
            "birth_year": year,
            "achievements": [
                {
                    "id": 1,
                    "achievement_name": "string"
                }
            ],
            "owner": 1,
            "age": 1,
            "image": "string",
            "image_url": "string"
        }
    ]
}
```
### Запрос на создание публикаций (POST):
```
/api/cats/
```
**Пример запроса:**
```
{
    "name": "string",
    "color": "string",
    "birth_year": year
}
```
**Пример ответа:**
```
{
    "id": 1,
    "name": "string",
    "color": "string",
    "birth_year": year,
    "achievements": [],
    "owner": 1,
    "age": 1,
    "image": null,
    "image_url": null
}
```
### Запрос на получение токена (POST):
```
/api/token/login/
```
**Пример запроса:**
```
{
    "username": "string",
    "password": "string"
}
```
**Пример ответа:**
```
{
    "auth_token": "string"
}
```

### Как развернуть проект локально или на сервере:
1. Установить на локальную машину или удаленный сервер 'Docker' и 'Docker Compose';
2. Создать в корневой директории файл '.env' (пример создания в файле .env.example в корневой директории);
3. Выполнить команду для запуска контейнеров
```
docker-compose up -d --build
```
4. Выполнить миграции
```
docker-compose exec backend python manage.py migrate
```
5. Собрать статику
```
docker-compose exec backend python manage.py collectstatic
```
6. Скопировать статику 
```
docker-compose exec backend cp -r /app/collected_static/. /static/static/
```
7. Создать суперпользователя
```
docker-compose exec backend python manage.py createsuperuser
```
8. Перейти в браузере по ссылке http://localhost:9000/
