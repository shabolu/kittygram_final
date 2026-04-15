# Kittygram

Kittygram - сервис для публикации котиков. Пользователи могут
регистрироваться, авторизоваться, добавлять карточки котов, указывать их цвет,
год рождения, достижения и загружать изображения.

Цель проекта - подготовить приложение к запуску в контейнерах, подключить
PostgreSQL, настроить Nginx gateway для раздачи frontend, static и media, а
также автоматизировать проверку и публикацию Docker-образов через GitHub
Actions.

## Функции

- регистрация и авторизация пользователей;
- просмотр списка котов;
- добавление, редактирование и удаление карточек котов;
- загрузка изображений;
- хранение данных в PostgreSQL;
- раздача пользовательских файлов и статики через Nginx;
- автоматическая проверка проекта и сборка Docker-образов.

## Стек технологий

- Python 3.9;
- Django 3.2;
- Django REST Framework;
- Djoser;
- PostgreSQL 13;
- Gunicorn;
- React;
- Node.js 18;
- Nginx;
- Docker;
- Docker Compose;
- GitHub Actions;
- Ruff.

## Запуск проекта

Создайте файл `.env` в корне проекта:

```bash
cp .env.example .env
```

Заполните переменные окружения:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=change_me
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432

SECRET_KEY=change_me
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,your-domain.example
CSRF_TRUSTED_ORIGINS=https://your-domain.example

DOCKERHUB_USERNAME=username
```

Назначение переменных:

- `POSTGRES_DB` - имя базы данных;
- `POSTGRES_USER` - пользователь базы данных;
- `POSTGRES_PASSWORD` - пароль пользователя базы данных;
- `DB_HOST` - хост базы данных, для Docker Compose должен быть `db`;
- `DB_PORT` - порт PostgreSQL;
- `SECRET_KEY` - секретный ключ Django;
- `DEBUG` - режим отладки;
- `ALLOWED_HOSTS` - разрешённые хосты через запятую;
- `CSRF_TRUSTED_ORIGINS` - доверенные источники для CSRF через запятую;
- `DOCKERHUB_USERNAME` - имя пользователя Docker Hub.

Соберите и запустите контейнеры:

```bash
docker compose build
docker compose up -d
```

Проверьте состояние контейнеров:

```bash
docker compose ps
```

Приложение будет доступно по адресу:

```text
http://localhost:9000/
```

Остановить проект:

```bash
docker compose down
```