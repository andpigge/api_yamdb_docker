# api_yamdb

![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

<h2 align="center">Описание</h2>
Командный проект YaMDb.
Предоставлялась готовая спроектированная документация REDOC.

API строились на основе этой документации, так же она служила как ТЗ.

Документацию можно найти по адресу: <a href="https://github.com/Rejden2000/api_yamdb/blob/master/api_yamdb/static/redoc.yaml">api_yamdb/api_yamdb/static/redoc.yaml</a>

Задача стояла разработать api для различных произведений, комментарии и отзывы к ним.
Реализовать свою систему прав доступа. Регистрацию и получения токена по коду из почты.

Команда поделила задачи:

Первый разработчик пишет всю часть, касающуюся управления пользователями (Auth и Users): систему регистрации и аутентификации, права доступа, работу с токеном, систему подтверждения через e-mail.

Второй разработчик пишет категории (Categories), жанры (Genres) и произведения (Title): модели, представления и эндпойнты для них.

Третий разработчик занимается отзывами (Review) и комментариями (Comments): описывает модели, представления, настраивает эндпойнты, определяет права доступа для запросов. Рейтинги произведений, а также реализация механизма импорта данных из csv файлов, тоже достаются третьему разработчику.

Так же помимо основного ревью, проводились ревью внутри команды, решались конфликты в git, а общие задачи решались сообща. 
Для связи использовали slug и митапы.

Много чего приходилось находить самостоятельно, а командная работа помогала.

<h2 align="center">Оглавление</h2>

1. [Установка](#установить)
2. [Стек разработки](#стек-разработки)
3. [Пользовательские роли](#пользовательские-роли)
4. [Обзор функций](#обзор-функций)
5. [Основная команда](#основная-команда)

<h2 align="center">Установить</h2>

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:Rejden2000/api_yamdb.git
```

```
cd api_yamdb
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
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

Запустить скрипт импорта данных из файлов csv в базу данных:

```
python3 manage.py importdata
```

Запустить проект:

```
python3 manage.py runserver
```

<h2 align="center">Стек разработки</h2>
<li><a href="https://www.djangoproject.com/">django 2.2</a></li>
<li><a href="https://www.django-rest-framework.org/">django rest framewor 3.12</a></li>
<li><a href="https://pypi.org/project/flake8/">flake8</a></li>
<li><a href="https://django-rest-framework-simplejwt.readthedocs.io/en/latest/">django rest framework simplejwt</a></li>
<li><a href="https://drf-yasg.readthedocs.io/en/stable/">drf-yasg</a></li>
<li><a href="https://django-filter.readthedocs.io/en/stable/">django filter</a></li>



<h2 align="center">Пользовательские роли</h2>

<li><strong>Аноним.</strong> — может просматривать описания произведений, читать отзывы и комментарии.</li><br/>

<li><strong>Аутентифицированный пользователь. (user)</strong> — может публиковать отзывы и ставить оценки произведениям (фильмам/книгам/песенкам), может комментировать отзывы; может редактировать и удалять свои отзывы и комментарии, редактировать свои оценки произведений.</li><br/>

<li><strong>Модератор (moderator).</strong> — может удалять и редактировать любые отзывы и комментарии.</li><br/>

<li><strong>Администратор (admin).</strong> — полные права на управление всем контентом проекта.</li><br/>

<li><strong>Суперпользователь.</strong> — может создавать администраторов.</li><br/>

<h2 align="center">Обзор функций</h2>

<h3>Аутентификация. Регистрация пользователей и выдача токенов:</h3>

Зарегистрировать нового пользователя. Получить код подтверждения на переданный email.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/auth/signup/
```

Получение JWT-токена. Получение JWT-токена в обмен на username и confirmation code.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/auth/token/
```

<h3>Пользователи:</h3>

Получить список всех пользователей. Добавить нового пользователя.

Права доступа: <strong>Администратор.</strong>

```
/api/v1/users/
```

Получить пользователя по username. Изменить данные пользователя по username. Удалить пользователя по username.

Права доступа: <strong>Администратор.</strong>

```
api/v1/users/{username}
```

Получить данные своей учетной записи. Изменить данные своей учетной записи.

Права доступа: <strong>Любой авторизованный пользователь.</strong>

```
api/v1/users/me/
```

<h3>Категории (типы) произведений («Фильмы», «Книги», «Музыка»):</h3>

Получить список всех категорий.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/categories/
```

Создать категорию.

Права доступа: <strong>Администратор.</strong>

```
api/v1/categories/
```

Удалить категорию.

Права доступа: <strong>Администратор.</strong>

```
api/v1/categories/{slug}/
```

<h3>Жанры произведений. Одно произведение может быть привязано к нескольким жанрам:</h3>

Получить список всех жанров.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/genres/
```

Добавить жанр.

Права доступа: <strong>Администратор.</strong>

```
api/v1/genres/
```

Удалить жанр.

Права доступа: <strong>Администратор.</strong>

```
api/v1/genres/{slug}/
```

<h3>Произведения, к которым пишут отзывы (определённый фильм, книга или песня):</h3>

Получить список всех произведений.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/genres/
```

Добавить новое произведение.

Права доступа: <strong>Администратор.</strong>

```
api/v1/genres/
```

Получить информацию о произведении.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/titles/{titles_id}/
```

Обновить информацию о произведении. Удалить произведение.

Права доступа: <strong>Администратор.</strong>

```
api/v1/titles/{titles_id}/
```

<h3>Отзывы на произведения. Отзыв привязан к определённому произведению:</h3>

Получить список всех отзывов.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/titles/{titles_id}/
```

Добавить новый отзыв. Пользователь может оставить только один отзыв на произведение.

Права доступа: <strong>Аутентифицированные пользователи.</strong>

```
api/v1/titles/{titles_id}/
```

Получить отзыв по id для указанного произведения.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/
```

Частично обновить отзыв по id. Удалить отзыв по id.

Права доступа: <strong>Автор отзыва, модератор или администратор.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/
```

<h3>Комментарии к отзывам. Комментарий привязан к определённому отзыву.</h3>

Получить список всех комментариев к отзыву по id.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

Добавить новый комментарий для отзыва.

Права доступа: <strong>Аутентифицированные пользователи.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

Получить комментарий для отзыва по id.

Права доступа: <strong>Доступно без токена.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

Частично обновить комментарий к отзыву по id. Удалить комментарий к отзыву по id.

Права доступа: <strong>Автор комментария, модератор или администратор.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

<h2 align="center">Основная команда</h2>
<table>
  <tbody>
    <tr>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://ca.slack-edge.com/TPV9DP0N4-U039Y2KLS6S-941cc7a2d585-512?s=150">
        <br>
        <a href="https://github.com/Rejden2000">Денис Стерликов</a>
        <p>Team leader</p>
        <a href="https://hh.ru/resume/e1d7db7aff085eb8050039ed1f664e786a6334?from=share_ios">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <a href="https://web.telegram.org/z/#969008307">
          <img height="30px" src="https://web.telegram.org/z/favicon.svg">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://avatars.githubusercontent.com/u/54473049?v=4?s=150">
        <br>
        <a href="https://github.com/andpigge">Рустам Рахимов</a>
        <p>Development</p>
        <a href="https://hh.ru/resume/dc361442ff07787a170039ed1f314a4e42476c">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://sun9-west.userapi.com/sun9-49/s/v1/ig2/WPfmcdC44tHUx4zU2kuFlrfK9P1dN1a30t1wB0R_OGOa40Vg2ee5y6YAS7H9AnPWcIjPpwK_bchEU4on36EyW3EI.jpg?size=2165x2160&quality=96&type=album?s=150">
        <br>
        <a href="https://github.com/RVG1995">Роман Вадимович</a>
        <p>Development</p>
        <a href="https://ekaterinburg.hh.ru/resume/446324f9ff0b4c2d310039ed1f6a5657434130">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
     </tr>
  </tbody>
</table>
