---
title: Доступ и вывод на страницу определенного значения JSON
last_updated: Oct 8, 2019
sidebar: mydoc_sidebar
permalink: access-print-value.html
folder: like-developer
---

Этот раздел продолжает предыдущую тему: [Изучение полезных данных в JSON ответе](inspect-json.html). На [странице](https://idratherbewriting.com/learnapidoc/assets/files/weather-plain.html), где мы залоггировали ответ от сервиса погоды на консоль JS, информация ответа REST не появилась на странице. Она появилась только в консоли JS. Нам нужно использовать точечную нотацию и JavaScript для доступа к нужным значениям JSON. В этом разделе мы используем JavaScript, чтобы отобразить часть ответа на странице.

Обратите внимание, что в этом разделе будет использовать JavaScript. Может быть, в будущем этот код не пригодится при документировании, но знать его будет не лишним.

<a name="getProperty"></a>
## Получение определенного свойства из объекта JSON ответа

JSON был бы не очень полезен, если бы всегда приходилось распечатывать весь ответ. Вместо этого можно выбрать нужное свойство, и получить его через точечную запись. Точка `.` после `response` (имя полезной данной JSON, как она определена произвольно в функции JQuery AJAX) определяет доступ к нужным значениям из объекта JSON.

Допустим, мы хотим извлечь часть о скорости ветра в ответе JSON. Так выглядит точечная нотация, которую нужно использовать:

```
response.wind.speed
```

Чтобы извлечь элемент скорости ветра из ответа JSON и распечатать его в консоли JavaScript, добавляем его в пример кода (который мы создали в [предыдущем разделе](inspect-json.html)) прямо под строкой `console.log (response)`:

```
console.log("wind speed: " + response.wind.speed);
```

Код будет выглядеть так:

```javascript
$.ajax(settings).done(function (response) {
    console.log(response);
    console.log("wind speed: " + response.wind.speed);
});
```
После этого обновляем браузер и видим информацию, появившуюся в консоли.

```
wind speed: 13.87
```

<a name="printValue"></a>
## Вывод JSON значения на страницу

Допустим, нам надо вывести часть JSON (данные о скорости ветра) на страницу, а не только в консоли. (Под словом "вывести"  подразумевается отображение значения странице, а не отправка на принтер.) Для вывода значения требуется немного JavaScript (или jQuery для упрощения).

Работать будем с [тем же кодом](https://idratherbewriting.com/learnapidoc/assets/files/weather-plain.html) из [предыдущего раздела](inspect-json.html). Этот код выглядит так:

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
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

Для вывода определенного значения ответа на страницу:

- Добавим следующие строки внутрь функции `ajax`

```javascript
$.ajax(settings).done(function (response) {
console.log(response);

var content = response.wind.speed;
$("#windSpeed").append(content);

});
```

- В теле страницы (внутри тега `body`) добавим следующий тэг `div`:

```html
<body>
    <h1>Sample page</h2>
    <div id="windSpeed">Wind speed: </div>
</body>
```

Код должен получиться таким:

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
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

           var content = response.wind.speed;
           $("#windSpeed").append(content);

         });
      </script>
   </head>
   <body>
      <h1>Sample Page</h1>
      <div id="windSpeed">Wind speed: </div>
   </body>
</html>
```

- Обновляем страницу и видим отображение скорости ветра на странице Пример [здесь](https://idratherbewriting.com/learnapidoc/assets/files/weather-windspeed.html) с выведенными со скоростью ветра и погодными условиями.

Вот что мы изменили:

В теге метода `done` AJAX'а извлекли желаемое значение в переменную:

```javascript
var content = response.wind.speed;
```

И добавили названный элемент в тело страницы

```html
<div id="windSpeed">Wind speed: </div>
```

Мы использовали [метод `append` jQuery](https://api.jquery.com/append/) для добавления переменной `content` к элементу с ID `windSpeed` ​​на странице:

```javascript
$("#windSpeed").append(content);
```

Этот код говорит: найди элемент с ID `windSpeed` и добавь переменную `content` после него.

<a name="arrayValue"></a>
## Получение значения из массива

В предыдущей части мы получили значение из объекта JSON. Теперь получим значение из массива. Давайте получим свойство `main` из массива `weather` в ответе. Вот как выглядит массив JSON:

```json
{
  "weather": [
    {
      "id": 801,
      "main": "Clouds",
      "description": "few clouds",
      "icon": "02d"
    }
  ]
}
```

Помните, что квадратные скобки означают массив. Внутри массива погоды находится неназванный объект. Чтобы получить основной элемент из этого массива, нужно использовать следующую точечную нотацию:

```
response.weather[0].main
```

В то время как объекты позволяют вам получить определенное свойство, массивы требуют, чтобы вы выбрали нужную позицию в списке.

Теперь код будет выглядеть так:

```html
<!DOCTYPE html>
<html>
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

  var content = response.wind.speed;
  $("#windSpeed").append(content);

  var currentWeather = response.weather[0].main;
  $("#currentWeather").append(currentWeather);

});
</script>
</head>
<body>
<h1>Sample Page</h1>

<div id="windSpeed">Wind speed: </div>
<div id="currentWeather">Current weather conditions: </div>

</body>
</html>
```    

<a name="more"></a>
## Дополнительные упражнения

При желании можно выполнить еще несколько упражнений, которые включают вызовы API REST, доступ к определенным значениям и вывод значений на странице, см. Следующие разделы в модуле «Глоссарий и ресурсы»:

- [Получаем информацию о событии при использовании API Eventbrite](Get-event-information-using-Eventbrite-API.html)
- [Пример Flickr: извлекаем галерею Flickr](Retrieve-gallery-using-Flickr-API.html)
- [Получаем скорость ветра при использовании сервиса API Aeris Weather](Get-wind-speed-using-Aeris-API.html)


[🔙](inspect-json.html)

[Go next ➡](dot-notation.html)
