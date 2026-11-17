# Каталог курсов

Учебное веб-приложение на Django (урок 42-43): каталог курсов через ModelForm — добавление и редактирование.

Модель Course: title (до 100 символов), description, seats (места, от 1 до 30 — проверка в clean_seats()).

Форма CourseForm — ModelForm, в Meta модель Course и три поля title/description/seats; clean_seats() отклоняет значения вне 1..30, ошибка показывается рядом с полем.

Страницы:

- /courses/ — список курсов
- /courses/add/ — добавление курса
- /courses/<pk>/edit/ — редактирование курса (instance передается и при GET, и при POST)

При POST вызывается is_valid(): корректные данные сохраняются и редирект на список, при ошибке форма показывается снова с введенными данными. {% csrf_token %} в шаблоне формы.

Проверка: seats=0 и seats=31 дают ошибку, 1 и 30 сохраняются, редактирование обновляет запись.

Запуск:

    pip install -r requirements.txt
    python manage.py makemigrations courses
    python manage.py migrate
    python manage.py runserver

Сайт: http://127.0.0.1:8000/courses/
