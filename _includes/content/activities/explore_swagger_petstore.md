### 👨‍💻 Знакомство со Swagger при помощи Petstore Demo

- Переходим по ссылке [Swagger Pet Store Demo](https://petstore.swagger.io)

Как и в большинстве основанных на Swagger'е инструментов, в интерфейсе Swagger есть кнопка «Try it out». Для работы необходима авторизация в Swagger. Авторизация по нажатии на  кнопку `Authorize`, в появившемся окне нужно вставить корректную информацию. При желании авторизоваться можно добавив любой номер в поле `api_key` и нажав `Authorize`. Окно авторизации Petstore предназначено только для демонстрации, так что окно можно просто закрыть.

{% include image.html file="introduction-rest-api/10.png" alt="auth" caption="Окно авторизации в Swagger UI" %}

- Разворачиваем конечную точку **Pet**
- Нажимаем на кнопку `Try it out`. После нажатие пример значения в поле "Тело запроса" станет редактируемым.

{% include image.html file="introduction-rest-api/11.png" alt="auth" caption="Кнопка `Try it out` в Swagger UI" %}

- В примере заменяем значение `id` на другое целое (не повторяющееся) число. Далее меняем значение `value` на какое-нибудь узнаваемое (имя щенка - `Puppy`).
- Нажимаем  `Execute`

{% include image.html file="introduction-rest-api/12.png" alt="Execute" caption="Выполнение примера Petstore запроса" %}

Swagger UI отправляет запрос и показывает отправленный curl.
В примере был отправлен curl:

```js
curl -X POST "https://petstore.swagger.io/v2/pet" -H "accept: application/xml" -H "Content-Type: application/json" -d "{ \"id\": 1000, \"category\": { \"id\": 0, \"name\": \"string\" }, \"name\": \"Bentley\", \"photoUrls\": [ \"string\" ], \"tags\": [ { \"id\": 0, \"name\": \"string\" } ], \"status\": \"available\"}"
```

Обратите внимание, что с параметром -d (data) параметр тела запроса экранируется и добавляется непосредственно в команду curl, а не загружается из файла (как описано в разделе: [Общие команды curl, связанные с REST](understand-curl.html#curlCommands)).

В разделе "Ответы" Swagger UI выдает ответ сервера. По умолчанию ответ возвращает XML:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
  <Pet>
    <category>
      <id>0</id>
      <name>string</name>
    </category>
    <id>1000</id>
    <name>Bentley</name>
    <photoUrls>
      <photoUrl>string</photoUrl>
    </photoUrls>
    <status>available</status>
    <tags>
      <tag>
        <id>0</id>
        <name>string</name>
      </tag>
    </tags>
  </Pet>
```

Если выбрать в выпадающем списке "Response content type" JSON, то в ответе вернется JSON вместо XML.

{% include image.html file="introduction-rest-api/13.png" alt="JSON" %}

- "Petstore" - является действующим API, питомец фактически создан. Для забавы развернем конечную точку GET / pet / {petId}, нажимаем `Try it out`, вводим идентификатор питомца, который использовали в предыдущей операции, а затем выполняем запрос. В ответе видим имя питомца, которое совпадает с тем, что ввели в предыдущем примере.

Подробная информация для этого практического занятия находится по ссылке [Знакомство со спецификациями OpenAPI и Swagger](introduction-openapi-and-swagger.html)
