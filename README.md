# WebAPI_1
Первая практическая работа по предмету "Основы Web API"

### Работа с протоколом HTTP через telnet

## Задание 1


Создать проект со следующей структурой:
```
myproject/
├── about
│   └── aboutme.html
└── index.html
```
В файле index.html написать 2 ссылки с прямым и абсолютным обращением к aboutme.html. В файле aboutme.html создать такие же ссылки на файл index.html.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/1.1.png?token=GHSAT0AAAAAAB7TQR75ZT7TFATEUABATQB2ZJEAXIQ)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/1.2.png?token=GHSAT0AAAAAAB7TQR74O3ZTJ4M5IAGJF3YCZJEAVAA)


## Задание 2

Подключиться по telnet к http://wikipedia.org и отправить запрос:

```
GET /wiki/страница HTTP/1.1
Host: ru.wikipedia.org
User-Agent: Mozilla/5.0 (X11; U; Linux i686; ru; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
Accept: text/html
Connection: close
(пустая строка)
```

Проанализировать ответ сервера. Описать работу HTTP протокола в данном случае.

Разрешается выбрать любой другой веб-сайт вместо http://WikiPedia.org

* GET /wiki/страница HTTP/1.1 - это запрос на получение страницы /wiki/страница с использованием версии HTTP/1.1.
* Host: ru.wikipedia.org - это заголовок, указывающий на сервер, к которому следует обратиться.
* User-Agent - это заголовок, указывающий на браузер или приложение, которое отправляет запрос.
* Accept - это заголовок, который указывает, что клиент принимает только текстовые HTML документы.
* Connection: close - это заголовок, который указывает на закрытие соединения после передачи ответа.
* Ожидаемый ответ от сервера будет содержать HTTP-статус-код, который указывает на успешность запроса, а также тело ответа, которое будет содержать запрошенную веб-страницу (если запрос успешен). Пример HTTP-статус-кода 200 означает успешный запрос, а другие коды могут указывать на различные ошибки.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/2.png?token=GHSAT0AAAAAAB7TQR75JKDDYLIUL4JTDDSUZJEAX3A)
## Задание 3
Отправить запросы на http://httpbin.org, проанализировать ответ и код состояния. Описать работу HTTP протокола в каждом запросе.

1. Запросить данные GET запросом с ресурса ip
/ip
```
GET /ip HTTP/1.1
Host: httpbin.org
Accept: */*
```

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.1.png?token=GHSAT0AAAAAAB7TQR75LO7EGXCLZGTXO4WIZJEAYEA)

2. Выполнить запрос методом GET

/get
```
GET /get?foo=bar&1=2&2/0&error=True HTTP/1.1
Host: httpbin.org
Accept: */*
```

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.2.png?token=GHSAT0AAAAAAB7TQR75YOZVHILYMUXIYPOWZJEAYLQ)

3. Выполнить запрос методом POST
/post
```
POST /post HTTP/1.1
Host: httpbin.org
Accept: */*
Content-Length: вычислить длину контента и втавить сюда число!!!
Content-Type: application/x-www-form-urlencoded

foo=bar&1=2&2%2F0=&error=True
```
Попробовать ввести неверное значение Content-Length.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.3.png?token=GHSAT0AAAAAAB7TQR74JQGDBTURPOWT4CPMZJEAYSQ)

4. Отправить запрос на установку Cookie
/cookies/set
```
GET /cookies/set?country=Ru HTTP/1.1
Host: httpbin.org
Accept: */*
```

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.4.png?token=GHSAT0AAAAAAB7TQR74CN2MA7RDKBIGD5ZSZJEAYYA)

5. Просмотреть список установленных Cookie
/cookies
```
GET /cookies HTTP/1.1
Host: httpbin.org
Accept: */*
```

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.5.png?token=GHSAT0AAAAAAB7TQR74JKSP7N7XOLQPE2OWZJEAY6A)

6. Отправить запрос на страницу с перенаправлением
/redirect
```
GET /redirect/4 HTTP/1.1
Host: httpbin.org
Accept: */*
```
Проверить глубину рекурсии в браузере, сравниь со значением опции network.http.redirection-limit из about:config в браузере FireFox.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/3.6.png?token=GHSAT0AAAAAAB7TQR74IHPTRQQB5XRPCWEEZJEAZCQ)

## Задание 4

Создать HTML форму c action="http://httpbin.org/post" method="POST" и enctype="multipart/form-data"
Добавить в форму поля firstname, lastname, group, message (textarea), myimg (file).
Проверить результат отправки данных формы.
Проанализировать ответ. Описать работу HTTP протокола в данном случае.

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/4.1.png?token=GHSAT0AAAAAAB7TQR746U6UULONGLAMGDVOZJEAZIQ)

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots/4.2.png?token=GHSAT0AAAAAAB7TQR743FLBOOBWYRJH3GFMZJEAZNQ)

Когда пользователь заполняет и отправляет HTML-форму, браузер формирует HTTP-запрос к серверу, указанному в атрибуте "action" формы (в данном случае, httpbin.org/post).
Метод HTTP запроса указан как "POST", что означает, что данные будут отправлены на сервер.
Кодировка данных:

Атрибут "enctype" формы указывает, что данные будут закодированы с использованием "multipart/form-data". Это позволяет отправлять бинарные файлы (как изображения) и текстовые данные в одном запросе.
Отправка запроса:

Когда пользователь нажимает кнопку "Отправить" на форме, браузер отправляет HTTP-запрос на сервер httpbin.org.
В этом запросе будут включены поля firstname, lastname, group, message и myimg, которые были заполнены пользователем.
Обработка запроса на сервере:

Сервер httpbin.org принимает HTTP-запрос и анализирует его содержимое.
Он распознает, что запрос использует метод POST и кодировку multipart/form-data, и начинает извлекать данные из запроса.
Формирование ответа:

Сервер анализирует данные, полученные из запроса, и создает HTTP-ответ.
Он может выполнить различные операции с данными, но в данном случае, так как это httpbin.org, сервер просто возвращает эти данные обратно в ответе.
Отправка ответа:

HTTP-ответ, содержащий данные, возвращается обратно в браузер пользователя.
Обработка ответа на клиенте:

Браузер пользователя получает HTTP-ответ и может использовать его, например, для отображения результатов на странице или для выполнения дополнительных действий на основе данных из ответа.
В данном случае, сервер httpbin.org позволяет вам проверить, какие данные были отправлены в запросе и как они были обработаны на сервере, предоставляя вам возможность анализировать результат отправки данных формы в удобном формате. Это полезный инструмент для отладки и тестирования HTTP-запросов и ответов.


### Работа с протоколом HTTPS через openssl

## Задание 1 

Подключиться по openssl к https://wikipedia.org и отправить запрос:

```
$ openssl s_client -connect wikipedia.org:443
```
```
GET /wiki/страница HTTP/1.1
Host: ru.wikipedia.org
User-Agent: Mozilla/5.0 (X11; U; Linux i686; ru; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
Accept: text/html
Connection: close
(пустая строка)
```
Проанализировать ответ сервера. Описать работу HTTP протокола в данном случае.

Разрешается выбрать любой другой веб-сайт вместо https://wikipedia.org

![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/1.1.png)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/1.2.png)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/1.3.png)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/1.4.png)

Проанализируем запрос и ответ сервера:

1. GET / HTTP/1.1: Это строка запроса. Отправляю GET-запрос к корневому каталогу (/) сайта "wikipedia.org" с использованием HTTP/1.1 протокола.

2. Host: wikipedia.org: Этот заголовок указывает на хост, к которому я обращаюсь. В данном случае, это "wikipedia.org", что позволяет серверу понять, к какому сайту нужно обратиться.

3. User-Agent: Mozilla/5.0 (X11; U; Linux i686; ru; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5: Этот заголовок содержит информацию о моем браузере и операционной системе.

4. Accept: text/html: Этот заголовок указывает, что мой браузер предпочитает получать HTML-контент.

5. Connection: close: Этот заголовок говорит серверу закрыть соединение после передачи ответа.

После отправки запроса, сервер "wikipedia.org" ответит соответствующим HTTP-ответом. В ответе содержатся заголовки HTTP (например, статусный код, тип содержимого) и сам контент страницы. 

Это пример работы с HTTP-протоколом при использовании команды openssl s_client для отправки запросов на удаленный веб-сервер.

## Задание 2

1. Создать ключ шифрования для работы по зашифрованному каналу связи
```
$ openssl req -new -x509 -keyout key.pem -out server.pem -days 365 -nodes
```
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/2.1.png)

2. Поднять веб сервер работающий по протоколу HTTPS
```python
import ssl
from http.server import HTTPServer, SimpleHTTPRequestHandler

httpd = HTTPServer(("0.0.0.0", 4443), SimpleHTTPRequestHandler)
httpd.socket = ssl.wrap_socket(
    httpd.socket,
    certfile="server.pem",
    keyfile="key.pem",
    server_side=True,
    ssl_version=ssl.PROTOCOL_TLS,
)
httpd.serve_forever()
```
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/2.2.png)
3. Отправить запрос на локальный сервер
```
$ openssl s_client -connect 127.0.0.1:4443
```
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/2.3.png)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/2.4.png)
![alt text](https://raw.githubusercontent.com/Karmatsky/WebAPI_1/main/screenshots1/2.5.png)
