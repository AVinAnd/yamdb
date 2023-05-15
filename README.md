![workflow status](https://github.com/AVinAnd/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
#  Yamdb
Проект YaMDb собирает отзывы пользователей на произведения.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Список категорий может быть расширен.
Произведению может быть присвоен жанр из списка предустановленных.
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти; из пользовательских оценок формируется усреднённая оценка произведения — рейтинг. На одно произведение пользователь может оставить только один отзыв.
Пользователи могут оставлять комментарии к отзывам.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.


### Стек технологий использованный в проекте:
* Python
* Django
* Django REST Framework
* REST API
* Postgresql
* Аутентификация по JWT-токену

## Шаблон env файла
```
SECRET_KEY=your_secret_key # секретный ключ
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
## Как запустить проект в контейнерах
1. Клонировать репозиторий 
```
git clone https://github.com/AVinAnd/infra_sp2.git
```
2. Заполнить в директории infra файл .env 

Секретный ключ можно сгенерировать командой:
```
python -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())'
```
3. В терминале перейти в директорию с docker-compose.yaml
  и выполнить команду
```
docker-compose up -d
```
4. Выполнить миграции и собрать статику
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py collectstatic --no-input
```
5. Создать суперпользователя
```
docker-compose exec web python manage.py createsuperuser
```
6. Заполнить базу данных из файла фикстур
```
docker-compose exec web python manage.py loaddata fixtures.json
```
7. Запустить проект 
```
python manage.py runserver
```
Проект доступен по адресу http://51.250.17.151
### Об авторе
Андрей Виноградов - python-developer, выпускник Яндекс Практикума по курсу Python-разработчик
