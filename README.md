# 1. Название проекта

__*yamdb_final*__

![example workflow](https://github.com/Skrad20/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg)

# 2. Краткое описание

Проект для собра и хранения отзывов пользователей на произведения различных категорий, таких как *Книги, Фильмы, Музыка*.

# 3. Технологии в проекте

* Python 3.7
* Django 2.2.19
* Gunicorn 20.1.0
* PostgreSQL
* Docker
* Docker-compose
* NGINX

# 4. Инструкции по запуску

* Клонируйте репозиторий

```bash
git clone git@github.com:Skrad20/yamdb_final.git
```

* Установите и активируйте виртуальное окружение:

```bash
python -m venv venv
source venv/Scripts/activate
```

* Установите зависимости из файла requirements.txt

```bash
pip install -r requirements.txt
```

* Установите Docker desktop

[Ссылка на скачивание](https://www.docker.com/products/docker-desktop)
[Ссылка на инструкцию по установке](https://docs.docker.com/desktop/windows/wsl/)

* Заполните [переменные окружения](/.env)
Укажите параметры подключения к базе данных (DB_ENGINE, DB_NAME, POSTGRES_USER, POSTGRES_PASSWORD, DB_HOST, DB_PORT)

* В папке с проектом запустите сборку контейнеров и их запуск

```bash
docker-compose up --build
```

* Проект должен быть доступен по [адресу](http://localhost/admin/login/?next=/admin/)

* Выполните миграции для успешно работы с базой данных

```bash
docker-compose exec web python manage.py migrate --noinput
```

* Создайте аккаунт суперпользователя для доступа к панели администратора

```bash
docker-compose exec web python manage.py createsuperuser
```

* Соберите статические файлы для удоства работы

```bash
docker-compose exec web python manage.py collectstatic --no-input 
```

* Добавьте имеющиеся данные в базу данных

```bash
docker-compose exec web python manage.py loaddata fixtures.json 
```

* Проверьте правильность исполнения кода

```bash
docker-compose exec pytest
```

* Сохраните данные в json

```bash
docker-compose exec web python manage.py dumpdata --indent 2 > fixtures.json
```

# 5. Инструкции по остановке

* Остановить работу всех образов

```bash
docker-compose down
```

* Удалить неиспользуемые образы, контейнеры, тома.

```bash
docker system prune
```

# 6. Автор
Yandex.Practicum, Евдокимов Е.Г.

# 7. Посмотреть проект

[Можно тут](http://130.193.54.156/admin/login/?next=/admin/)