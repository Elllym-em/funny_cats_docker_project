# Kittygram
**Kittygram - социальная сеть для обмена фотографиями любимых питомцев**
Делитесь фото и достижениями своих любимцев и наблюдайте за любимцами людей со всего мира!
Только для котиков!

Сайт доступен по адресу https://kitgram.sytes.net


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
