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

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/1.1.png?token=GHSAT0AAAAAAB7TQR74XQJX7VUT52ED26VAZI62JXQ)

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

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/2.png?token=GHSAT0AAAAAAB7TQR74M7T2D7LQIQFDP4VQZI62KLA)
## Задание 3
Отправить запросы на http://httpbin.org, проанализировать ответ и код состояния. Описать работу HTTP протокола в каждом запросе.

1. Запросить данные GET запросом с ресурса ip
/ip
GET /ip HTTP/1.1
Host: httpbin.org
Accept: */*

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.1.png?token=GHSAT0AAAAAAB7TQR7435YMBAS2IF5V44T2ZI62KQQ)

2. Выполнить запрос методом GET
/get
GET /get?foo=bar&1=2&2/0&error=True HTTP/1.1
Host: httpbin.org
Accept: */*

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.2.png?token=GHSAT0AAAAAAB7TQR74ZHKEQDSIAP6GVN3EZI62KYA)

3. Выполнить запрос методом POST
/post
POST /post HTTP/1.1
Host: httpbin.org
Accept: */*
Content-Length: вычислить длину контента и втавить сюда число!!!
Content-Type: application/x-www-form-urlencoded

foo=bar&1=2&2%2F0=&error=True
Попробовать ввести неверное значение Content-Length.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.3.png?token=GHSAT0AAAAAAB7TQR75QS4RQGWOQEVDJS7AZI62K6A)

4. Отправить запрос на установку Cookie
/cookies/set
GET /cookies/set?country=Ru HTTP/1.1
Host: httpbin.org
Accept: */*

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.4.png?token=GHSAT0AAAAAAB7TQR74QGNHO6MIO6LDH3VOZI62LCQ)

5. Просмотреть список установленных Cookie
/cookies
GET /cookies HTTP/1.1
Host: httpbin.org
Accept: */*

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.5.png?token=GHSAT0AAAAAAB7TQR74WAMG7TBLUA76KATGZI62LJA)

6. Отправить запрос на страницу с перенаправлением
/redirect
GET /redirect/4 HTTP/1.1
Host: httpbin.org
Accept: */*
Проверить глубину рекурсии в браузере, сравниь со значением опции network.http.redirection-limit из about:config в браузере FireFox.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.6.png?token=GHSAT0AAAAAAB7TQR75LR2CTYOM3H442QUWZI62LNA)

## Задание 4

Создать HTML форму c action="http://httpbin.org/post" method="POST" и enctype="multipart/form-data"
Добавить в форму поля firstname, lastname, group, message (textarea), myimg (file).
Проверить результат отправки данных формы.
Проанализировать ответ. Описать работу HTTP протокола в данном случае.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/4.1.png?token=GHSAT0AAAAAAB7TQR74Y3F7YPURG33GP4LIZI62LTQ)

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/4.2.png?token=GHSAT0AAAAAAB7TQR75GNE4ELJO6DKF5HNKZI62L2Q)