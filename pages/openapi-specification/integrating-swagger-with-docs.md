---
title: Интеграция Swagger с документацией
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: integrating-swagger-with-docs.html
folder: openapi-specification
---

Всякий раз, когда обсуждаются Swagger и другие спецификации REST API, технические писатели неизменно спрашивают, как можно интегрировать выходные данные Swagger в свою документацию. Когда речь идет о Swagger, этот вопрос обсуждается среди технических писателей гораздо чаще других.

<a name="truth"></a>
## Единственный источник истины

Когда мы помещаем документацию в другой исходный файл - в данном случае в файл YAML или JSON, включенный в набор файлов Swagger UI, в конечном итоге разбиваем свой единственный источник истины на несколько источников. Конечные точки и параметры уже определены в обычной документации, и теперь их нужно перенести в спецификацию OpenAPI . Вы копируете и вставляете одинаковые параметры и другую информацию на обоих сайтах? Вы как-то генерируете описания из одного и того же источника?

Эта головоломка обычно кристально ясна для технических авторов. Документация API состоит не только из адресного материала об API. Также имеется информация о получении ключей API, установке и настройке сервисов, или другие сведения, которые не соответствуют спецификации. Все это будем рассматривать в разделе [Концептуальные разделы](about-sixth-module.html). Концептуальными разделами считают следующие:

- [Обзор API](API-overview.html)
- [Начало работы](getting-started.html)
- [Требования к аутентификации и авторизации](authentication-and-authorization.html)
- [Коды статусов и ошибок](status-error-codes.html)
- [Ограничения скорости](rate-limiting.html)
- [Примеры кода](code-samples.html)
- [SDK и примеры приложений](sdks-sample-apps.html)
- [Глоссарий](api-glossary.html)
- [Лучшие практики API](best-practices.html)

Бывает, имеется больше данных, которые нужно сообщить пользователю, но которые не вписываются в спецификацию. Например, в конечной точке `weather` в [примере API OpenWeatherMap](https://idratherbewriting.com/learnapidoc/assets/files/swagger/), который мы использовали в этом курсе, есть некоторые подробности об идентификаторах городов, которые требуют некоторого объяснения.

```json
...
},
"id": 420006397,
"name": "Santa Clara",
"cod": 200
}
```

Что означает `"cod": 200`? Если перейти в раздел [«Идентификатор города» в документации OpenWeatherMap](https://openweathermap.org/current#cityid), увидим ссылку для загрузки списка кодов городов файлов.

Может быть сложной задачей добавить описания всех параметров, выделенных в спецификации OpenAPI, если таких данных очень много в адресных разделах документации. К сожалению, простого решения для создания единого источника истины не существует . Вот несколько вариантов:

- [Вариант 1. Встроить Swagger UI в свои документы](#embed)
- [Вариант 2: Разместить всю информацию в спецификацию в сворачиваемых разделах](#put)
- [Вариант 3: Парсить документ в спецификации OpenAPI](#parse)
- [Вариант 4. Хранить содержимое в YAML формате](#yaml)
- [Вариант 5: Использовать инструмент, импортирующий Swagger и позволяющий работать с другой документацией](#multitool)
- [Вариант 6: изменить перспективы - наличие двух сайтов не так уж плохо](#breake)

<a name="embed"></a>
## Вариант 1. Встраиваем Swagger UI в свои документы

Одним из решений является внедрение Swagger UI непосредственно в документацию. Пример этого здесь: [Swagger UI Demo](swagger-ui-demo.html). Вставить Swagger в HTML-страницу довольно легко. Последняя версия Swagger имеет более отзывчивый, гибкий дизайн. Так и просится быть встроенным в другой сайт.

Единственная проблема с вариантом встраивания состоит в том, что некоторые из моделей не ограничены в своем контейнере, поэтому они расширяются за пределы контейнера. Попробуйте расширить раздел «Модель» в демоверсии - будет понятно, о чем речь.

Может быть джедай стилей и смог бы изменить такое поведение. Возможно, но падаван, который не силен в стилях, не может решить такую проблему. В [Swagger UI Demo](swagger-ui-demo.html) добавлены несколько пользовательских стилей, для внесения изменений в интерфейс Swagger в разных местах. Если просмотреть исходный код этой страницы и изучить второй блок `<style>`, можно увидеть добавленные стили.

Итак что-же сделал падаван в лице переводчика курса?

Пришлось попотеть. Опишу свои действия step-by-step:

- перешел в [Swagger UI](https://github.com/swagger-api/swagger-ui) сохранил себе на ПК папку `dist`;
- из папки `dist` извлек файл `swagger-ui.css` и поместил его в папку `css` проекта;
- из папки `dist` извлек файлы `swagger-ui-bundle.js` и `swagger-ui-standalone-preset.js` и вставил их в папку `js` проекта;
- в `pages/openapi-specification` где лежат исходники модуля "Спецификация OpenAPI и Swagger" добавил файл `openapi-weathermap.yml` вот с [этим кодом](https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml);
- в файле `swagger-ui-demo.md` вставил код из оригинала курса:

```html
{% if site.format == "pdf" or site.format == "kindle" %}
<p>This page can only be viewed online in your computer's web browser{% if site.format == "kindle" %} (not through Kindle's browser){% endif %}. Go to <a href="https://idratherbewriting.com/learnapidoc/pubapis_swagger_demo.html">https://idratherbewriting.com/learnapidoc/pubapis_swagger_demo.html</a> to view it.</p>
{% else %}

<link rel="stylesheet" type="text/css" href="css/swagger-ui.css" >
<style>
  html
  {
    box-sizing: border-box;
    overflow: -moz-scrollbars-vertical;
    overflow-y: scroll;
  }
  *,
  *:before,
  *:after
  {
    box-sizing: inherit;
  }
  body {
    margin:0;
    background: #fafafa;
  }
</style>

<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="position:absolute;width:0;height:0">
  <defs>
    <symbol viewBox="0 0 20 20" id="unlocked">
          <path d="M15.8 8H14V5.6C14 2.703 12.665 1 10 1 7.334 1 6 2.703 6 5.6V6h2v-.801C8 3.754 8.797 3 10 3c1.203 0 2 .754 2 2.199V8H4c-.553 0-1 .646-1 1.199V17c0 .549.428 1.139.951 1.307l1.197.387C5.672 18.861 6.55 19 7.1 19h5.8c.549 0 1.428-.139 1.951-.307l1.196-.387c.524-.167.953-.757.953-1.306V9.199C17 8.646 16.352 8 15.8 8z"></path>
    </symbol>

    <symbol viewBox="0 0 20 20" id="locked">
      <path d="M15.8 8H14V5.6C14 2.703 12.665 1 10 1 7.334 1 6 2.703 6 5.6V8H4c-.553 0-1 .646-1 1.199V17c0 .549.428 1.139.951 1.307l1.197.387C5.672 18.861 6.55 19 7.1 19h5.8c.549 0 1.428-.139 1.951-.307l1.196-.387c.524-.167.953-.757.953-1.306V9.199C17 8.646 16.352 8 15.8 8zM12 8H8V5.199C8 3.754 8.797 3 10 3c1.203 0 2 .754 2 2.199V8z"/>
    </symbol>

    <symbol viewBox="0 0 20 20" id="close">
      <path d="M14.348 14.849c-.469.469-1.229.469-1.697 0L10 11.819l-2.651 3.029c-.469.469-1.229.469-1.697 0-.469-.469-.469-1.229 0-1.697l2.758-3.15-2.759-3.152c-.469-.469-.469-1.228 0-1.697.469-.469 1.228-.469 1.697 0L10 8.183l2.651-3.031c.469-.469 1.228-.469 1.697 0 .469.469.469 1.229 0 1.697l-2.758 3.152 2.758 3.15c.469.469.469 1.229 0 1.698z"/>
    </symbol>

    <symbol viewBox="0 0 20 20" id="large-arrow">
      <path d="M13.25 10L6.109 2.58c-.268-.27-.268-.707 0-.979.268-.27.701-.27.969 0l7.83 7.908c.268.271.268.709 0 .979l-7.83 7.908c-.268.271-.701.27-.969 0-.268-.269-.268-.707 0-.979L13.25 10z"/>
    </symbol>

    <symbol viewBox="0 0 20 20" id="large-arrow-down">
      <path d="M17.418 6.109c.272-.268.709-.268.979 0s.271.701 0 .969l-7.908 7.83c-.27.268-.707.268-.979 0l-7.908-7.83c-.27-.268-.27-.701 0-.969.271-.268.709-.268.979 0L10 13.25l7.418-7.141z"/>
    </symbol>


    <symbol viewBox="0 0 24 24" id="jump-to">
      <path d="M19 7v4H5.83l3.58-3.59L8 6l-6 6 6 6 1.41-1.41L5.83 13H21V7z"/>
    </symbol>

    <symbol viewBox="0 0 24 24" id="expand">
      <path d="M10 18h4v-2h-4v2zM3 6v2h18V6H3zm3 7h12v-2H6v2z"/>
    </symbol>

  </defs>
</svg>

<div id="swagger-ui"></div>

<script src="{{ "js/swagger-ui-bundle.js" }}"> </script>
<script src="{{ "js/swagger-ui-standalone-preset.js" }}"> </script>
<script>
window.onload = function() {
  // Build a system
  const ui = SwaggerUIBundle({
    url: "pages/openapi-specification/openapi_weathermap.yml",
    // url: "http://petstore.swagger.io/v2/swagger.json",
    dom_id: '#swagger-ui',
    defaultModelsExpandDepth: -1,
    docExpansion: "full",
    deepLinking: true,
    presets: [
      SwaggerUIBundle.presets.apis,
      SwaggerUIStandalonePreset
    ],
    plugins: [
      SwaggerUIBundle.plugins.DownloadUrl
    ],
    layout: "StandaloneLayout"
  })
  window.ui = ui
}
</script>

<style>
.swagger-ui .info .title small pre {
	padding: 1px;
	background-color: #444;
}
.swagger-ui .info .title small {
    font-size: 10px;
    position: relative;
    top: -5px;
    display: inline-block;
    margin: 0 0 0 5px;
    padding: 4px;
    vertical-align: super;
    border-radius: 57px !important;
    background: #89bf04 !important;
}
.swagger-ui .info .title small pre.version {
    background-color: #89bf04;
    border: 0px;
  }
.swagger-ui pre.version {
      padding: 0px;
      max-width: 60px;
      border: 0px;
  }
.swagger-ui .info .title small pre {
      padding:0px;
  }
.swagger-ui .info .title small {
      background-color: rgb(137, 191, 4);
  }
  .swagger-ui table th, .swagger-ui table td {
      padding: 10px !important;
  }
  .swagger-ui table th {
    color: white;
    font-size:16px;
}
.swagger-ui .col_header {
    color: white !important;
}
div#swagger-ui {
    border: 1px solid #dedede;
}
.swagger-ui .info .title small pre {
	padding: 1px;
	background-color: #444;
}
.swagger-ui .info .title small {
    font-size: 10px;
    position: relative;
    top: -5px;
    display: inline-block;
    margin: 0 0 0 5px;
    padding: 4px;
    vertical-align: super;
    border-radius: 57px !important;
    background: #89bf04 !important;
}
.swagger-ui .info .title small pre.version {
    background-color: #89bf04;
  }
.swagger-ui li.tabitem {
    list-style: none !important;
}
.swagger-ui .response-col_description__inner p {
  color: white;
  font-style: normal;
  font-size: 12px;
}
.swagger-ui pre.version {
    padding: 0px;
}
.swagger-ui .info .title small pre {
    padding:0px;
}
.swagger-ui .info .title small {
    background-color: rgb(137, 191, 4);
}
.swagger-ui a.tablinks {
    margin-right: 20px;
}
.swagger-ui td.col.response-col_status {
    padding: 10px !important;
}
.swagger-ui .opblock .opblock-section-header h4 {
  font-size: 18px !important;
  font-weight: bold;
  padding: 0px;
}
.swagger-ui td.col, .swagger-ui td.col.col_header.response-col_description {
    padding: 10px;
}
.swagger-ui h4.opblock-title_normal {
    font-size: 16px;
    font-style: italic;
}
.swagger-ui h4.opblock-title_normal[id] {
    padding-bottom: 15px;
    font-style: italic;
  }
.swagger-ui {
  border: 1px solid #dedede;
}
.swagger-ui select {
    font-weight: normal !important;
    font-family: monospace;
}
.swagger-ui table {
  table-layout: auto !important;
}
.swagger-ui .scheme-container {
  padding: 0px 0px 15px 0px;
}
.swagger-ui .renderedMarkdown p {
    font-size: 14px;
}
.swagger-ui tr.response p {
  font-style: italic;
}
.swagger-ui table.model tbody tr td {
  padding: 1em !important;
}
.response-content-type.controls-accept-header small code {
    font-size: 12px;
  }
.swagger-ui .opblock-summary-path a.nostyle {
    font-family: monospace;
}
.swagger-ui .info {
  /* margin: -25px 0px !important; */
}
.swagger-ui .main span.url {
    display: none;
}
.swagger-ui span.opblock-summary-path a.nostyle {
    font-family: Monospace !important;
    size: 16px;
}
.swagger-ui .opblock-description-wrapper, .swagger-ui .opblock-external-docs-wrapper, .swagger-ui .opblock-title_normal {
    padding: 15px 20px 5px 20px;
}
.swagger-ui h1[id], .swagger-ui h2[id], .swagger-ui h3[id], .swagger-ui h4[id], .swagger-ui h5[id] {
    margin: 0px;
    padding: 0px;
}
.swagger-ui pre {
    font-family: Monaco, Monospace !important;
    font-size: 11px;
  }
h6, h6 code.highlighter-rouge {
    font-size: 16px;
}
.swagger-ui .responses-inner h4, .swagger-ui .responses-inner h5 {
  font-size: 16px;
}
.swagger-ui code {
    font-size: 12px;
}
/* disable the try it out buttons
button.btn.try-out__btn {
    display: none;
}
*/
</style>

{% endif %}

{% include random_ad.html %}


{% include random_ad2.html %}
```

*После сборки в этом примере кода не отображается код Jekyll, нужно иметь ввиду тем, кто будет копировать код со страницы сайта: лучше зайти в репозиторий и скопировать непосредственно из исходника.*

- изменил ссылки к файлам `swagger-ui.css`, `swagger-ui-bundle.js`, `swagger-ui-standalone-preset.js` и `openapi_weathermap.yml` (в примере кода ссылки уже изменены);
- НИЧЕГО НЕ ПОЛУЧИЛОСЬ!;
- посмотрел логи сборки jekyll, вычитал, что в `_includes` он не видит файлы `random_ad.html` и `random_ad2.html`;
- скопировал их из оригинала курса в свою папку `_includes`;
- ЗАРАБОТАЛО!!! этот коммит написан капслоком от радости. © That's how winning is done!

Благодаря встроенному параметру все равно можно использовать официальный инструментарий Swagger UI для чтения спецификации, и включать вывод Swagger UI в основную документацию. Swagger UI читает последнюю версию спецификации OpenAPI, которую многие инструменты еще не поддерживают. Кроме того, интерфейс Swagger имеет знакомый интерфейс, с которым разработчики API, уже знакомы. Но, если стилистика уродливым образом пересекается в разделах модели, можно не использовать  подхода встраивания документации .

<a name="put"></a>
## Вариант 2: Размещаем всю информацию в спецификацию в сворачиваемых разделах

Этот вариант предполагает попытку поместить всю информацию в сам документ спецификации. Удивительно, сколько информации можно включить в спецификацию. Любой элемент `description` (не только свойство `description` в объекте `info`) позволяет использовать Markdown и HTML. Например, вот объект `info` в спецификации OpenAPI, где появляется описание. (При желании можно набрать `>`, для перевода на следующую строку, а затем сделать отступ в два пробела. Можно добавить много содержимого в элементах `description`.)

```yaml
info:
  title: OpenWeatherMap API
  description: 'Get the current weather, daily forecast for 16 days, and a three-hour-interval forecast for 5 days for your city. Helpful stats, graphics, and this day in history charts are available for your reference. Interactive maps show precipitation, clouds, pressure, wind around your location. Data is available in JSON, XML, or HTML format. **Note**: This sample Swagger file covers the `weather` endpoint only from the OpenWeatherMap API. <br/><br/> **Tip**: We recommend that you call the API by city ID (using the `id` parameter) to get unambiguous results for your city.'
  version: '2.5'
```

Можно делать ссылки на Bootstrap CSS и JS в заголовке `index.html` проекта Swagger UI, и затем включать предупреждения Bootstrap и кнопки раскрытия / свертывания в элементе `description`. Вот пример:

```yaml
info:
  description: >
    ACME offers a lot of configuration options...
    <div class="alert alert-success" role="alert"><i class="fa fa-info-circle"></i> <b>Tip: </b>See the resources available in the portal for more detail.</div>
    <div class="alert alert-warning" role="alert"><i class="fa fa-info-circle"></i> <b>Note: </b>The  network includes a firewall that protects your access to the resources...</div>

    <div class="container">
    <div class="apiConfigDetails">
    <button type="button" class="btn btn-warning" data-toggle="collapse" data-target="#demo">
    <span class="glyphicon glyphicon-collapse-down"></span> See API Configuration Details
    </button>
    <div id="demo" class="collapse">

    <h2>Identifiers Allowed</h2>

    <p>Based on this configuration, ACME will accept any of the following identifiers in requests.</p>

    <table class="table">
    <thead>
    <tr>
    <th>Request Codes</th>
    <th>Data Type</th>
    <th>Comparison Method</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    ...
```

Результатом будет сжатие большей части информации в одну кнопку, которая при нажатии разворачивалась, выдавая более подробную информацию. Включая разделы «развернуть/ свернуть» из Bootstrap, можно добавить массу информации в объект `description`. (Для необходимого JavaScript надо добавить теги `<script>` в заголовок или футер того же файла `index.html`, где мы ссылались на файл `openapi.yaml`)

Кроме того, можно включить модальные окна, которые появляются при нажатии. Модальные окна - это диалоговые окна, которые затемняют фон за пределами диалогового окна. Опять же, весь необходимый JavaScript-код можно включать в файл `index.html` проекта Swagger UI.

Если включить Bootstrap, вероятно, потребуется ограничить пространство имен, чтобы оно не влияло на другие элементы в отображении Swagger UI. (Подробнее о том, как это сделать, см. В разделе [«How to Isolate Bootstrap CSS to Avoid Conflicts»](https://formden.com/blog/isolate-bootstrap).)

В целом, если документация API относительно невелика, можно сначала попытаться поместить всю свою информацию в спецификации. Если есть сложный API или просто API, который содержит много дополнительной информации, не относящейся к спецификации, надо искать альтернативные подходы. Но попробуйте сначала вписать его в спецификацию. Это сохранит информацию в одном месте.

В использовании спецификации много преимуществ, которые легко упустить, если выбрать другой подход. Многие инструменты могут анализировать спецификацию и генерировать интерактивные дисплеи если сохранять информацию в спецификации.

Например, [Spectacle](https://github.com/sourcey/spectacle) - это проект, который создает вывод из файла Swagger - он практически не требует программирования или технических знаний. Появляется все больше и больше инструментов, которые позволяют импортировать вашу спецификацию OpenAPI: [Lucybot](https://lucybot.com/), [Restlet Studio](https://studio.restlet.com/), [адаптивная тема Swagger UI](https://github.com/jensoleg/swagger-ui), [пользовательский интерфейс Material Swagger](https://github.com/legendecas/material-swagger-ui), [DynamicAPIs](https://www.dynamicapis.com/), [Run in Postman](https://learning.getpostman.com/docs/postman_for_publishers/run_button/creating_run_button/), [SwaggerHub](swaggerhub-introduction-and-tutorial.html#editor) и многое другое. Все они читают спецификацию OpenAPI.

Перевод контента в формат спецификации OpenAPI позволяет  отделять контент от уровня представления, мгновенно используя преимущества любого нового инструментария API или платформы, которые могут анализировать спецификацию.

<a name="parse"></a>
## Вариант 3: Парсим (анализируем) документ в спецификации OpenAPI

Если используется инструмент, такой как Jekyll, включающий язык под названием Liquid, можно использовать инстанс Liquid для Jekyll, для чтения документации спецификации OpenAPI (который, в конце концов, просто синтаксис YAML). Например, можно использовать [цикл `for`](https://learn.cloudcannon.com/jekyll/looping-in-liquid/) для итерации значений спецификации OpenAPI. В примере ниже файл `swagger.yml` хранится в каталоге `_data` Jekyll.

```html
<table>
    <thead>
    <tr><th>Name</th><th>Type</th><th>Description</th><th>Required?</th></tr>
    </thead>
    {% for parameter in site.data.swagger.paths.get.parameters %}
        {% if parameter.in == "query" %}
        <tr>
            <td><code>{{ parameter.name }}</code></td>
            <td><code>{{ parameter.type }}</code></td>
            <td>
            {% assign found = false %}
            {% for param in site.data.swagger.paths.get.parameters %}
                {% if parameter.name == param.name %}
                    {{ param.description }}
                    {% assign found = true %}
                {% endif %}
            {% endfor %}
            {% if found == false %}
                ** New parameter **
            {% endif %}
            </td>
            <td><code>{{ parameter.required }}</code></td>
        </tr>
        {% endif %}
    {% endfor %}
</table>
```

Особая благодарность Питеру Хендерсону за то, что он поделился этой техникой и кодом. При таком подходе, возможно, придется выяснить правильный синтаксис Liquid для итерации вашей спецификации OpenAPI, и это может занять некоторое время. Но это может сработать в поиске тесной интеграции с авторским инструментом. (Стоит обратить внимание, что многие [генераторы статических сайтов](Static-site-generators.html) могут анализировать YAML, а не только Jekyll.)

Дополнительная информация об этом подходе в статью Питера Хендерсону в разделе [«Интеграция автоматически сгенерированного контента в ваш сайт документации с использованием Swagger и Jekyll»](https://www.enigma.com/blog/integrating-autogenerated-content-into-your-documentation-site-using-swagger-and-jekyll) и этот [пример кода GitHub](https://github.com/peterhend/documentation-theme-jekyll).

<a name="yaml"></a>
## Вариант 4. Храним содержимое в YAML формате

Другой подход к интеграции выходных данных Swagger с другими документами может состоять в том, чтобы хранить описания и другую информацию в файлах данных YAML в проекте, а затем включать ссылки на данные в документ спецификации. Рассмотрим пример с использованием Jekyll (но аналогичные методы существуют для других генераторов статических сайтов).


Jekyll позволяет хранить содержимое в файлах YAML в папке `_data`. Допустим, внутри `_data` есть файл `parameters.yml` со следующим содержимым:

```yaml
acme_parameter: >
  This is a description of my parameter ...
```

Затем можно обернуть эту ссылку в такие теги:

```
{{site.data.parameters.acme_parameter}}
```

В проекте Jekyll ссылка на спецификацию выглядела бы следующим образом:

```yaml
info:
  description: >
    {{site.data.parameters.acme_parameter}}
```

После берем вывод из Jekyll, который содержит контент, вставленный в каждое свойство спецификации. В этой модели происходит генерация спецификацию OpenAPI из проекта Jekyll.


Не плохой вариант, но трудно гарантировать, что спецификация OpenAPI останется действительной, пока пишется контент. При наличии подобных ссылок в содержании спецификации (`{{site.data.parameters.acme_parameter}}`), не получится воспользоваться проверкой спецификации в реальном времени в [Swagger](https://swagger.io/tools/swagger-editor/).

Скорее всего, придется подключить весь проект Swagger UI к сайту Jekyll. Вверху файла `Swagger.yml` нужно добавить frontmatter с `layout: null`, чтобы Jekyll обработал файл:

```yaml
---
layout: null
---
```

В команде `jekyll serve` конфигурируем место назначения (`destination`), чтобы преобразовать выходные данные в папку `htdocs`, в которой работает [простой локальный HTTP-сервер](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server). С каждой сборкой, нужно проверять наличие ошибок.

Сохраняя значения в файлах данных, можно затем включить их в другое место в документе. Например, в документе может быть раздел параметров, в котором также включено описание `{{site.data.parameters.acme_parameter}}`.

Недостаток этого подхода в отсутствии возможности проверки спецификации. Сложно отслеживать виновников ошибок валидации.

<a name="multitool"></a>
## Вариант 5: Используем инструмент, импортирующий Swagger и позволяющий работать с другой документацией

еще один подход заключается в использовании таких инструментов, как [Readme.io](https://readme.io/) или [Stoplight](https://stoplight.io/), которые позволяют как импортировать спецификации OpenAPI, так и добавлять собственные страницы документации. [Readme.io](https://readme.io/) предоставляет один из наиболее привлекательных результатов и полностью включает в себя практически все функции документации, которые могут понадобиться. Более подробно изучим Readme в разделе [Headless CMS option]() (и Readme.io). [Readme.io](https://readme.io/) требует сторонний хостинг, но некоторые другие инструментальные документы позволяют также включить Swagger. Подробно изучали Stoplight в теме: [Stoplight - инструменты визуального моделирования для создания вашей спецификации OpenAPI](stoplight.html).

Такие сайты, как [Apiary](https://apiary.io/) и [Mulesoft](https://www.mulesoft.com/), позволяют импортировать спецификации OpenAPI, и добавлять пользовательские страницы документации. Эти сайты предлагают полное управление API-интерфейсами, поэтому, если разработчики уже используют одну из этих платформ, имеет смысл также хранить документацию в этих инструментах.


У Cherryleaf есть интересная статья под названием [«Пример портала документации API с использованием MadCap Flare»](https://www.cherryleaf.com/2017/06/example-api-documentation-portal-using-madcap-flare/). В этом посте Эллис Пратт демонстрирует концепцию проекта Flare, который читает спецификацию OpenAPI и генерирует из нее статический контент HTML. Если интересен Flare, возможно, стоит изучить статью.

<a name="breake"></a>
## Вариант 6: Меняем перспективы - наличие двух сайтов не так уж плохо

Наконец, спросим себя, что плохого в наличии двух разных сайтов? Один сайт с описанием адресных разделов, а другой для [концептуальной документации](about-sixth-module.html). Программисты могут посчитать справочную информацию на основе Swagger удобной, потому что она перерабатывает и упрощает объем информации. Вместо огромного сайта для навигации, вывод Swagger предоставляет базовую справочную информацию, которая им нужна. Когда им нужна не справочная информация, они могут обратиться к сопроводительному руководству. Можно рассматривать вывод Swagger UI как [краткий справочник API](quick-reference-guide.html).

Правда в том, что программисты годами работают с [Javadocs](Activity-Generate-Javadoc.html), [Doxygen](Doxygen.html) и другими [инструментами генерации документов](https://en.wikipedia.org/wiki/Comparison_of_documentation_generators), которые генерируют документацию из Java, C++, C#, Python, Ruby и других языков программирования. Автоматическое создание справочной информации из исходного кода в автономном режиме является чрезвычайно распространенным явлением и не должно восприниматься программистами как фрагментарная информация.

В конце концов, вместо того, чтобы чувствовать, что наличие двух выводов фрагментировано или разъединено, можно переосмыслить свою точку зрения. Вывод Swagger предоставляет четкий источник перехода к справочной информации о конечных точках, параметрах, запросах и ответах. Остальные документы предоставляют справочную информацию. Два этих результата просто стали организационной стратегией для документации.

<a name="nextSteps"></a>
## Следующие шаги

Итак, мы разобрались со адресной документацией API, пришло время погрузиться в тестирование. Поскольку мы работаем с конечными точками API и кодом, нам нужно будет самостоятельно тестировать конечные точки, чтобы собрать и проверить информацию, содержащуюся в документации. Тестирование - не всегда просто. Поэтому ему посвящен целый раздел. Переходим к [модулю тестирования документации](about-fifth-module.html).


[🔙](stoplight.html)

[Go next ➡](about-fifth-module.html)
