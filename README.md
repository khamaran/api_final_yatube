# Проект «API для Yatube»

Yatube - это социальная сеть для обмена фотографиями . 'Api для Yatube' - полноценный интерфейс для обмена данными, 
расширяющий функционал Yatube.

## Технологии

* Django==3.2.16
* pytest==6.2.4
* pytest-pythonpath==0.7.3
* pytest-django==4.4.0
* djangorestframework==3.12.4
* djangorestframework-simplejwt==4.7.2
* Pillow==9.3.0
* PyJWT==2.1.0
* requests==2.26.0
* djoser==2.1.0

## Реализованы возможности
* Аутентифицированным пользователям разрешено изменение и удаление своего контента; 
* В остальных случаях (неаутентифицированным пользователям) доступ предоставляется только для чтения.
* Возможность подписки, отписки от авторов (в том числе, отсутствие возможности подписки на самого себя)
* Для аутентификации используйте JWT-токены.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/khamaran/api_final_yatube.git
```

```
cd yatube_api
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

```
python3 -m pip install --upgrade pip
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
## Документация

Когда вы запустите проект, по адресу  http://127.0.0.1:8000/redoc/ будет доступна документация для API Yatube. 
В документации описано, как должен работать API. Документация представлена в формате Redoc.


## Примеры запросов

### Получение публикаций

**Получить список всех публикаций. При указании параметров limit и offset выдача должна работать с пагинацией.**

*GET http://127.0.0.1:8000/api/v1/posts/*

*Пример ответа:*
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```

### Создание публикации

**Добавление новой публикации в коллекцию публикаций. Анонимные запросы запрещены.**

*POST http://127.0.0.1:8000/api/v1/posts/*
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```

*Пример ответа:*
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```

