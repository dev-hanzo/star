---
title: Точечная нотация
last_updated: Oct 8, 2019
sidebar: mydoc_sidebar
permalink: dot-notation.html
folder: like-developer
---

В предыдущем разделе [Доступ и вывод на страницу определенного значения JSON](access-print-value.html) мы получили доступ и вывели на страницу определенное значение из ответа JSON. Здесь еще немного углубимся в точечную нотацию, поскольку для использования ответа необходимо понимать, как извлекать правильное значение JSON, которое мы хотим.

<a name="dotNotation"></a>
## Точечная нотация

Для доступа к свойствам объекта используется точка после имени объекта. Например, предположим, у нас есть объект с именем `data`:

```
"data": {
    "name": "Tom"
}
```

Для извлечения `Tom` нужно использовать `data.name`

Обратите внимание на различные уровни вложенности для отслеживания соответствующих объектов и получения доступа к необходимой информации.  Доступ к каждому нижнему уровню получаем после имени объекта, за которым следует точка.

<a name="brackets"></a>
## Использование квадратных скобок для получения значений в массиве

Для получения доступа к значению в массиве используются квадратные скобки, за которыми следует номер позиции. Например, предположим, есть следующий массив:

```
"data" : {
    "items": ["ball", "bat", "glove"]
}
```

Для доступа к `glove` используем `data.items[2]`.

`glove` является третьим элементом массива. Нельзя получить доступ к элементу непосредственно в массиве по имени элемента - только по его позиции. Обычно программисты перебирают массив и извлекают совпадающие значения.

{% include note.html content="Во всех языках программирования отсчет начинается с `0`, а не с `1`" %}

<a name="exercise"></a>
## 👨‍💻 Упражнение с точечной нотацией

В этом практическом занятии попрактикуемся извлекать разные значения при помощи точечной нотации.

- Создаем новый текстовый файл и вставляем в него следующий код:

```html
<!DOCTYPE html>
    <html>
        <head>
            <script src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
            <meta charset="utf-8">
            <title>JSON dot notation practice</title>
            <script>
                $( document ).ready(function() {

                    var john = {
                        "hair": "brown",
                        "eyes": "green",
                        "shoes": {
                            "brand": "nike",
                            "type": "basketball"
                        },
                        "favcolors": [
                            "azure",
                            "goldenrod"
                        ],
                        "children": [
                            {
                                "child1": "Sarah",
                                        "age": 2
                            },
                            {
                                "child2": "Jimmy",
                                        "age": 5
                            }
                        ]
                    }

                    var sarahjson = john.children[0].child1;
                    var greenjson = john.children[0].child1;
                    var nikejson = john.children[0].child1;
                    var goldenrodjson = john.children[0].child1;
                    var jimmyjson = john.children[0].child1;

                    $("#sarah").append(sarahjson);
                    $("#green").append(greenjson);
                    $("#nike").append(nikejson);
                    $("#goldenrod").append(goldenrodjson);
                    $("#jimmy").append(jimmyjson);
                });
            </script>
        </head>
        <body>
            <div id="sarah">Sarah: </div>
            <div id="green">green: </div>
            <div id="nike">nike: </div>
            <div id="goldenrod">goldenrod: </div>
            <div id="jimmy">Jimmy: </div>
        </body>
        </html>
```

Здесь у нас есть объект JSON, определенный как переменная с именем `john`. (как правило, API получают ответ через URL-запрос, но для практики мы просто определяем объект локально)

Если открыть наш файл в браузере то в каждом элементе мы увидим `Sarah` потому что мы извлекаем это значение: `john.children [0] .child1` для каждого элемента.

```javascript
var sarahjson = john.children[0].child1;
var greenjson = john.children[0].child1;
var nikejson = john.children[0].child1;
var goldenrodjson = john.children[0].child1;
var jimmyjson = john.children[0].child1;
```

- Изменим `john.children[0].child1` для отображения правильных значений для каждого элемента. Например слово `green` должно появиться в тэге ID

Корректное отображение можно посмотреть на [этой странице](https://idratherbewriting.com/learnapidoc/assets/files/dot-notation-practice.html), на ней же указаны и правильные ответы.

<a name="showOnPage"></a>
## Отображение параметров погоды на странице

В разделе [Сценарий использования API прогнозных сервисов](using-api-scenario.html) был показан пример встраивания скорости ветра и других параметров на веб-сайт. Вернемся к этому примеру кода и посмотрим, как он составлен.

```html
<html>
    <head>
        <script src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
        <link rel="stylesheet"  href='https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap.min.css' rel='stylesheet' type='text/css'>
        <title>OpenWeatherMap Integration</title>
        <style>
            #wind_direction, #wind_speed, #wind_speed_unit, #wind_degree_unit, #weather_conditions, #main_temp_unit, #main_temp {color: red; font-weight: bold;}
            body {margin:20px;}
        </style>
    </head>
    <body>
        <script>
            function checkWind() {
                var settings = {
                    "async": true,
                    "crossDomain": true,
                    "dataType": "json",
                    "url": "https://api.openweathermap.org/data/2.5/weather?zip=95050,us&appid=fd4698c940c6d1da602a70ac34f0b147&units=imperial",
                    "method": "GET"
            }

                $.ajax(settings)

                .done(function (response) {
                    console.log(response);

            $("#wind_speed").append (response.wind.speed);
            $("#wind_direction").append (response.wind.deg);
            $("#main_temp").append (response.main.temp);
            $("#weather_conditions").append (response.weather[0].main);
            $("#wind_speed_unit").append (" MPH");
            $("#wind_degree_unit").append (" degrees");
            $("#main_temp_unit").append (" F");
            });
            }
        </script>
        <button type="button" onclick="checkWind()" class="btn btn-danger weatherbutton">Check wind conditions</button>
        <h2>Wind conditions for Santa Clara</h2>
        <span><b>Temperature: </b></span><span id="main_temp"></span><span id="main_temp_unit"></span><br/>
        <span><b>Wind speed: </b></span><span id="wind_speed"></span> <span id="wind_speed_unit"></span><br/>
        <span><b>Wind direction: </b></span><span id="wind_direction"></span><span id="wind_degree_unit"></span><br/>
        <span><b>Current conditions: </b></span><span id="weather_conditions"></span>
    </body>
</html>
```

По сути это тот же код, который мы создали в разделе [Доступ и вывод на страницу определенного значения JSON](access-print-value.html), но кое-какие различия есть. Вот что отличается:

- вместо того, чтобы запускать метод `ajax` при загрузке страницы, метод `ajax` помещается в функцию с именем `checkWind`. При нажатии кнопки веб-страницы метод `onclick` запускает функцию `checkWind ()`;
- при запуске функции `checkWind` значения температуры, скорости ветра, направления ветра и текущих условий записываются в несколько тегов ID на странице.

Если загрузить страницу и нажать кнопку `Check wind conditions` то отобразиться следующее:

![](pics/9.png)

{% include image.html file="like-developer/9.png" alt="weather" %}

Результат можно посмотреть [здесь](https://idratherbewriting.com/learnapidoc/assets/files/wind-openweathermap.html)

<a name="next"></a>
## Следующий модуль

По мере выполнения практических занятий в модуле **Использование API в роли разработчика**, мы получили общее представление о том, как работают REST API, какая информация нужна разработчикам, как они могут использовать API, как они делают запросы, оценивают ответы и другие детали.

Теперь, с таким бэкграундом пришла пора топить педаль газа в пол и гнать к новым вершинам профессии "Технический писатель".

В следующем модуле [Документирование конечных точек](about-third-module.html), возьмем на себя задачу документирования новой конечной точки, которая была добавлена ​​в API погоды. Изучим основные разделы документации конечных точек, терминологию использования и соглашений о форматировании адресной информации по API.

[🔙](access-print-value.html)

[Go next ➡](about-third-module.html)
