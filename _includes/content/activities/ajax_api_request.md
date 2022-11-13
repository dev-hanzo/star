### 👨‍💻 Создаем запрос на странице с помощью AJAX

На этом занятии будем использовать JavaScript для отображения ответа API на веб-странице. Для создания запроса AJAX будем использовать автоматически сгенерированный код jQuery из Postman.

- В текстовом редакторе (например, Sublime Text) создадим новый файл HTML (который содержит основные теги HTML) и вставим в него следующий скрипт:

```html
<html>
<meta charset="UTF-8">
  <head>
      <title>Sample page</title>
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
  </head>
<body>
  <h2>Sample page</h2>

</body>
</html>
```

- Сохраняем файл на ПК, с именем **weather.html**.
- Открываем Postman и переходим к конечной точке, которую вы настроили в предыдущем действии (см. «Создаем запросы в Postman»).
- Кликаем на кнопку `Code` и выбираем **JavaScript > jQuery AJAX**.

{% include image.html file="introduction-rest-api/7.png" alt="jQuery_AJAX" %}

Код AJAX должен выглядеть так:

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.openweathermap.org/data/2.5/weather?zip=95050&appid=fd4698c940c6d1da602a70ac34f0b147&units=imperial",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
    "postman-token": "e9be9756-b922-89b3-7109-66bc4cf06b17"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

- Нажимаем кнопку `Copy to Clipboard` для копирования примера кода.
- В том же шаблоне, который начали создавать на шаге 1, добавляем пару тегов `<script></script>` под ссылкой jQuery, а затем вставляем скопированный код Postman между тегов `script`.
- В коде jQuery убираем объект `headers`, вставленный Postman

```javascript
"headers": {
	"cache-control": "no-cache",
 	"postman-token": "e9be9756-b922-89b3-7109-66bc4cf06b17"
	}
```

- Убираем запятую после `"method": "GET"`.

Финальный код должен выглядеть так:

```html
<!DOCTYPE html>
<html>
   <meta charset="UTF-8">
   <head>
      <meta charset="UTF-8">
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
      <title>Sample Page</title>
      <script>
         var settings = {
           "async": true,
           "crossDomain": true,
           "url": "https://api.openweathermap.org/data/2.5/weather?zip=95050&appid=fd4698c940c6d1da602a70ac34f0b147&units=imperial",
           "method": "GET"
         }

         $.ajax(settings).done(function (response) {
           console.log(response);
         });
      </script>
   </head>
   <body>
      <h1>Sample Page</h1>
   </body>
</html>
```

> Совет: Файл можно посмотреть [по ссылке](https://idratherbewriting.com/learnapidoc/assets/files/weather-plain.html). (Добавлено несколько инструкций по открытию консоли разработчика, потому что в противном случае отображение страницы на этом этапе в учебнике было бы совершенно пустым.)

- Запускаем Chrome и открываем JavaScript Console перейдя **View > Developer > JavaScript Console.**.
- В Chrome переходим в «Файл»> «Открыть файл» и выберите файл weather.html. (Если вы не видите меню «Файл» в Chrome, нажмите Cmd + O или Ctrl + O или просто перетащите файл weather.html в окно браузера.)

Тело страницы будет пустым, но ответ о погоде должен быть записан в консоли JavaScript (из-за кода console.log (response) в запросе). Если развернуть объект, возвращенный в консоль, он будет выглядеть следующим образом:

{% include image.html file="introduction-rest-api/8.png" alt="Console" %}

Теперь эта информация доступна для интеграции на вашей странице.

Подробная информация для этого практического занятия находится по ссылкам [Изучение полезных данных JSON ответа](inspect-json.html) и [Доступ и вывод на страницу определенного значения JSON](access-print-value.html)
