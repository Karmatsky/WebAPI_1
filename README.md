# WebAPI_1
Первая практическая работа по предмету "Основы Web API"

### Задания

## Задание 1

Создать проект со следующей структурой:
myproject/
├── about
│   └── aboutme.html
└── index.html
В файле index.html написать 2 ссылки с прямым и абсолютным обращением к aboutme.html. В файле aboutme.html создать такие же ссылки на файл index.html.
## Задание 2

Подключиться по telnet к http://wikipedia.org и отправить запрос:

GET /wiki/страница HTTP/1.1
Host: ru.wikipedia.org
User-Agent: Mozilla/5.0 (X11; U; Linux i686; ru; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
Accept: text/html
Connection: close
(пустая строка)

Проанализировать ответ сервера. Описать работу HTTP протокола в данном случае.

Разрешается выбрать любой другой веб-сайт вместо http://WikiPedia.org

## Задание 3
Отправить запросы на http://httpbin.org, проанализировать ответ и код состояния. Описать работу HTTP протокола в каждом запросе.

1. Запросить данные GET запросом с ресурса ip
/ip
GET /ip HTTP/1.1
Host: httpbin.org
Accept: */*

2. Выполнить запрос методом GET
/get
GET /get?foo=bar&1=2&2/0&error=True HTTP/1.1
Host: httpbin.org
Accept: */*

3. Выполнить запрос методом POST
/post
POST /post HTTP/1.1
Host: httpbin.org
Accept: */*
Content-Length: вычислить длину контента и втавить сюда число!!!
Content-Type: application/x-www-form-urlencoded

foo=bar&1=2&2%2F0=&error=True
Попробовать ввести неверное значение Content-Length.

4. Отправить запрос на установку Cookie
/cookies/set
GET /cookies/set?country=Ru HTTP/1.1
Host: httpbin.org
Accept: */*

5. Просмотреть список установленных Cookie
/cookies
GET /cookies HTTP/1.1
Host: httpbin.org
Accept: */*

6. Отправить запрос на страницу с перенаправлением
/redirect
GET /redirect/4 HTTP/1.1
Host: httpbin.org
Accept: */*
Проверить глубину рекурсии в браузере, сравниь со значением опции network.http.redirection-limit из about:config в браузере FireFox.

## Задание 4

Создать HTML форму c action="http://httpbin.org/post" method="POST" и enctype="multipart/form-data"
Добавить в форму поля firstname, lastname, group, message (textarea), myimg (file).
Проверить результат отправки данных формы.
Проанализировать ответ. Описать работу HTTP протокола в данном случае.