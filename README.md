# API Yatube

### Технологии

* Python 3.9
* Django 3.2.16
* Django REST framework 3.12.4
* djangorestframework-simplejwt 4.7.2
# API социальной сети Yatube

1.Неаутентифицированные пользователи могут получить посты пользователей соцсети,  комментарии к постам, а также информацию о группах.

2.Аутентифицированные пользователи могут добавлять посты и комментарии, подписываться на авторов, а также они имеют возможность изменять и удалять свои посты.

### Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:
```
 git clone https://github.com/Mikhail2690/api_final_yatube
```
```
 cd yatube_api
```
Cоздать и активировать виртуальное окружение:
```
 python -m venv venv
```
Для Windows
```
 source venv/Scripts/activate
```
Для Mac
```
 source env/bin/activate
```
Установить зависимости из файла requirements.txt:
```
 python -m pip install --upgrade pip
```
```
 pip install -r requirements.txt
```
Выполнить миграции:
```
 python manage.py migrate
```
Запустить проект:
```
 python manage.py runserver
```
### Доступные эндпоинты:

* api/v1/posts/ : получаем список всех постов или создаём новый пост;
* api/v1/posts/{post_id}/ : получаем, редактируем или удаляем пост по id;
* api/v1/posts/{post_id}/comments/ : получаем список всех комментариев поста с id=post_id или создаём новый, указав id поста, который хотим прокомментировать;
* api/v1/posts/{post_id}/comments/{comment_id}/ : получаем, редактируем или удаляем комментарий по id у поста с id=post_id;
* api/v1/groups/ : получаем список всех групп;
* api/v1/groups/{group_id}/ : получаем информацию о группе по id;
* api/v1/follow/ : получаем все подписки пользователя, сделавшего запрос, или подписываемся на пользователя, переданного в теле запроса;

### Примеры запросов:

Пример POST-запроса с токеном Антона Чехова: добавление нового поста.
POST .../api/v1/posts/
```
{
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре. Проект Шехтеля всем нравится.",
    "group": 1
}
```

Пример ответа:
```
{
    "id": 14,
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре. Проект Шехтеля всем нравится.",
    "author": "anton",
    "image": null,
    "group": 1,
    "pub_date": "2021-06-01T08:47:11.084589Z"
}
```

Пример POST-запроса с токеном Антона Чехова: отправляем новый комментарий к посту с id=14.
POST .../api/v1/posts/14/comments/
```
{
    "text": "тест тест"
}
```

Пример ответа:
```
{
    "id": 4,
    "author": "anton",
    "post": 14,
    "text": "тест тест",
    "created": "2021-06-01T10:14:51.388932Z"
}
```

Пример GET-запроса с токеном Антона Чехова: получаем информацию о группе.
GET .../api/v1/groups/2/
Пример ответа:
```
{
    "id": 2,
    "title": "Математика",
    "slug": "math",
    "description": "Посты на тему математики"
}
```
Автор: [Федоренко Михаил](https://github.com/Mikhail2690/)
