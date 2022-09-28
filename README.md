# Api_final_yatube

## Описание проекта:
### Социальная сеть для публикации личных дневников.
Это сайт, на котором можно создать свою страницу. Если на нее зайти, то можно посмотреть все записи автора.
Пользователи смогут заходить на чужие страницы, подписываться на авторов и комментировать их записи.
Автор может выбрать имя и уникальный адрес для своей страницы.
Записи можно отправить в сообщество и посмотреть там записи разных авторов.

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:DianaKab/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```
В Windows:
```
source venv/Scripts/activate
```
В macOS или Linux:
```
source venv/bin/activate
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

## Примеры запросов:

Пример POST-запроса с токеном Антона Чехова: добавление нового поста.

*POST .../api/v1/posts/*

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
*POST .../api/v1/posts/14/comments/*

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

*GET .../api/v1/groups/2/*

Пример ответа:

```
{
    "id": 2,
    "title": "Математика",
    "slug": "math",
    "description": "Посты на тему математики"
}
```

Пример GET-запроса с возвращением всех подписки пользователя Антона Чехова.

*GET .../api/v1/follow/*

Пример ответа:

```
{
    "user": "Антон Чехов",
    "following": "Максим горький"
}
```
