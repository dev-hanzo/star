### 👨‍💻 Наполняем интерфейс Swagger

В этом упражнении создадим отображение пользовательского интерфейса Swagger для спецификации OpenAPI. Если используется один из предварительно созданных файлов OpenAPI, можно увидеть демо того, что мы создадим здесь:
[OpenWeatherMap Swagger UI](https://idratherbewriting.com/learnapidoc/assets/files/swagger/) или [Sunrise/sunset Swagger UI](https://idratherbewriting.com/learnapidoc/assets/files/swagger-sunrise-sunset/index.html)

{% include image.html file="introduction-rest-api/14.png" alt="OpenWeatherMap API" caption="Демо визуализации интерфейса Swagger спецификации OpenAPI OpenWeatherMap" %}

Для интеграции спецификации OpenAPI в Swagger UI:

- Подготовим действительный документ спецификации OpenAPI:
  - инструкции по созданию документа спецификации OpenAPI с нуля [в руководстве по OpenAPI](openapi-tutorial-overview.html);
  - для использования предварительно созданной спецификации OpenAPI можно воспользоваться файлом спецификации [OpenWeatherMap](https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml) или [Sunrise/sunset API](https://idratherbewriting.com/learnapidoc/assets/files/swagger-sunrise-sunset/openapi_sunrise_sunset.yml) (правой кнопкой кликаем ссылку и сохраняем YAML на рабочем столе);
- Удостоверяемся в правильности нашей спецификации. Вставляем нашу спецификацию OpenAPI в [Swagger online editor](https://editor.swagger.io/) и удостоверимся в отсутствии ошибок. В правой части отображается функциональный дисплей Swagger UI.
- Переходим по ссылке [Swagger UI GitHub project](https://github.com/swagger-api/swagger-ui).
- Нажимаем `Clone` или `Download` и затем нажимаем `Download ZIP`. Сохраняем архив на компьютер и извлекаем файлы.
  - Единственная папка, с которой будем работать в загруженном zip-архиве, - это папка `dist` (сокращение от дистрибутива). Все остальное используется только при компиляции файлов Swagger, что выходит за рамки этого руководства.
- Перетащим папку `dist` из папки `swagger-ui-master`. (Затем при необходимости удалите папку swagger-ui-master и zip-файл.)
- Перетащим файл спецификации OpenAPI (из шага 1) в папку dist. (Если вы используете предварительно созданные файлы OpenAPI, файл называется либо "openapi_openweathermap.yml", либо "openapi_sunrise_sunset.yml".) Файловая структура должна выглядеть следующим образом:

```
├── dist
│   ├── favicon-16x16.png
│   ├── favicon-32x32.png
│   ├── index.html
│   ├── oauth2-redirect.html
│   ├── swagger-ui-bundle.js
│   ├── swagger-ui-bundle.js.map
│   ├── swagger-ui-standalone-preset.js
│   ├── swagger-ui-standalone-preset.js.map
│   ├── swagger-ui.css
│   ├── swagger-ui.css.map
│   ├── swagger-ui.js
│   ├── swagger-ui.js.map
│   ├── swagger30.yml
│   └── [your openapi specification file]
```

- В папке `dist` открываем файл index.html в редакторе [Atom](https://atom.io/) или [Sublime Text](https://www.sublimetext.com/)

- Ищем следующий код:

```
url: "http://petstore.swagger.io/v2/swagger.json",
```

- Меняем значение `url` из [http://petstore.swagger.io/v2/swagger.json](http://petstore.swagger.io/v2/swagger.json) на относительный путь к файлу YAML и сохраняем файл. Пример:

```
url: "openapi_openweathermap.yml",
```

или

```
url: "openapi_sunrise_sunset.yml",
```

- Рассмотрим файл index.html локально в вашем браузере. Обратите внимание, что ограничения безопасности Chrome (CORS objections) не позволяют просматривать файл пользовательского интерфейса Swagger локально, но есть несколько обходных путей:

  - Просмотр файла локально с помощью [Firefox](https://www.mozilla.org/en-US/firefox/new/) (это самый простой способ);
  - Используйте размещенный в Интернете URL-адрес для [openapi_openweathermap.yml](https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml) или [openapi_sunrise_sunset.yml](https://idratherbewriting.com/learnapidoc/assets/files/swagger-sunrise-sunset/openapi_sunrise_sunset.yml). (Клик правой кнопкой мыши и выбор "Копировать адрес ссылки".);
  - Загружаем папку `dist` на веб-сервер и смотрим на нее там;
  - Размещаем файл YAML на публичном [GitHub Gist](https://gist.github.com/) и затем нажимаем `Raw`. Используем URL для этого Gist;
  - Используем локальный сервер, например [простой локальный HTTP сервер](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server)

По готовности публиковать Swagger файл просто загружаем папку на веб-сервер и переходим в файл `index.html`. Если папку не переименовали и оставили `dist` то переходим по адресу [http://myserver.com/dist/](http://myserver.com/dist/). Переименовать папку можно в любой момент.   

> Подробные инструкции работы в Swagger по ссылке [ Swagger.io docs](https://swagger.io/docs/open-source-tools/swagger-ui/usage/installation/)  		 

Подробная информация для этого практического занятия находится по ссылке [Руководство Swagger UI](swagger-ui-tutorial.html)
