## film-reservation-system
This project is for the final project [Capstone](https://cs50.harvard.edu/web/2020/projects/final/cap) of the online course [CS50's Web Programming with Python and JavaScript](https://cs50.harvard.edu/web/). The project replicates the basic functions of a movie theater website, where users can register for an account, see which movies is showing, select times, choose a seat, book a ticket for a movie, and see their booking history.
This project uses Django as backend and ReactJS, Javascript (ES6), Bootstrap for frontend.

### Key features:
- ReactJS for frontend UI
- JWT authentication for user
- ##### For user: 
    - Book a ticket for a movie as a user:
        1. Choose a movie
        2. Select screen date and time
        3. Select seat (Cannot choose the seat that has been taken by other user)
        4. Select ticket type
    - View your booked ticket
- ##### For administrator (Utilize Django admin):
    - Add new movie
    - Add new gernes
    - Add screen date and time for a movie
    - Add new theater (Every theater has the same 64 seats for now)
    - Manage ticket type and price for each types
    - Manage movies, genres, screens, seats, theaters, ticket types and bookings by user

## How to launch
1. Создайте виртуальную среду и активируйте ее:

```
# Create a virtual environment
python3 -m venv venv

# Activate virtual environment
	# macOS:
	source venv/bin/activate
	# Windows:
	venv/Scripts/activate.bat
```
2. Установите необходимые зависимости Python:
```
pip install -r requirements.txt
```

3. Перейдите в основную папку интерфейса:
```
cd front-end/movietheater
``` 

4. Установите необходимые зависимости Node:
```
npm install --legacy-peer-deps
```

5. Создайте приложение React:
```
npm run build
```
6. Вернитесь в основную папку проекта.
```
cd ../..
```
7. Установить django
```
pip install django
```
8. Установить Django REST Framework
```
pip install djangorestframework
```
9. Установить djangorestframework-simplejwt
```
pip install djangorestframework-simplejwt
```
10. И наконец запустите веб-сервер Django
```
python manage.py runserver
```
11. Перейдите по URL-адресу, указанному в терминале, и вы будете перенаправлены на домашнюю страницу!

## Апишки
API managed by [Django-Rest-Framework](https://www.django-rest-framework.org/)

#### АПИШКИ ВЭБ-САЙТА

###### GET MOVIES:
Возвращает массив объектов фильмов.

	'Endpoint': '/movies/',
	'method': 'GET',
	'body': None

###### GET SINGLE MOVIE:
Возвращает один объект фильма

	'Endpoint': '/movies/id',
	'method': 'GET',
	'body': None

###### GET SCREEN
Возвращает массив экранных объектов объекта фильма.

	'Endpoint': '/movies/id/screen',
	'method': 'GET',
	'body': None

###### GET SINGLE SCREEN
Возвращает один экранный объект

	'Endpoint': '/movies/id/screen/screenId',
	'method': 'GET',
	'body': None

###### GET SINGLE TICKET
Возвращает один объект ticket_type

	'Endpoint': '/ticket/ticketId',
	'method': 'GET',
	'body': None

###### CREATE SEAT & BOOKING
Создать новый объект места и новый объект бронирования

	'Endpoint': '/movies/id/screen/screenId/book',
	'method': 'POST',
	'headers': {
          "Content-Type": "application/json",
          Authorization: "Bearer " + String,
        }
	'body': {'body': {booking_object}}

###### GET TAKEN SEAT
Возвращает массив занятых мест экранного объекта, которые относятся к

	'Endpoint': '/movies/id/screen/screenId/getSeatsInfo',
	'method': 'POST',
	'headers': {
          "Content-Type": "application/json",
          Authorization: "Bearer " + String,
        }
	'body': None

###### GET TICKET TYPES
Возвращает массив типов билетов экранного объекта, которые относятся к

	'Endpoint': '/movies/id/screen/screenId/getTicketInfo',
	'method': 'POST',
	'headers': {
          "Content-Type": "application/json",
          Authorization: "Bearer " + String,
        }
	'body': None

###### GET SINGLE BOOKING
Возвращает один объект бронирования

	'Endpoint': '/movies/id/screen/screenId/booking/bookingId',
	'method': 'POST',
	'headers': {
          "Content-Type": "application/json",
          Authorization: "Bearer " + String,
        }
	'body': None

###### GET BOOKINGS
Возвращает массив объектов бронирования определенного пользователя.

	'Endpoint': '/movies/id/screen/screenId/booking/bookingId/getSeatInfo',
	'method': 'POST',
	'body': None

#### AUTHENTICATION API
Authentication with [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/) package for Django

###### РЕГИСТРАЦИЯ
Зарегистрируйте пользователя, указав его имя пользователя, адрес электронной почты, пароль, подтвердите пароль.

	'Endpoint': '/auth/register/'
	'method': 'POST'
	'body': {
		'username': String,
		'password': String,
		'confirmation': String, 
		'email': String
	}

###### ПОЛУЧИТЬ ТОКЕН (ВХОД)
Возвращает токен аутентификации, если учетные данные пользователя верны.

	'Endpoint': '/auth/token/'
	'method': 'POST'
	'body': {
		'username': String,
		'password': String
	}

###### ПОЛУЧИТЬ ОБНОВЛЯЮЩИЙ ТОКЕН
Возвращать токен обновления каждые 4 минуты

	'Endpoint': '/auth/token/refresh/'
	'method': 'POST'
	'body': {'refresh': String}

## Отличительные особенности и сложность
Для этого проекта самой большой проблемой для меня было сделать frontend и backend как два отдельных приложения, backend, использующий `Django Rest Framework` для управления и ответа на вызовы API, и frontend, использующий `ReactJS` для пользовательского интерфейса.
Это первое приложение, которое я когда-либо создавал с `ReactJS`, поэтому мне нужно много узнать о `ReactJS`, чтобы создать frontend-интерфейс для некоторых функций, таких как реализация аутентификации JWT, создание выбора даты, времени и страниц выбора места.
Backend, использующий `Django`, имеет 7 моделей, использует `Django Admin panel` для управления всеми объектами модели и использует `Django Rest Framework` для сериализации и ответа на вызовы API.

## Сноска
Я знаю, что это не «идеальный» веб-сайт для кинотеатра, ему все еще не хватает многих функций, и вы найдете его не очень удобным в использовании. Хотелось бы иметь больше времени для работы над этим проектом, я бы исправил множество проблем в приложении и сделал бы его намного лучше, но за то короткое время, что я провел над этим проектом, я узнал много нового о Django, DRF и React, и я горжусь своей работой.
Большое спасибо!
