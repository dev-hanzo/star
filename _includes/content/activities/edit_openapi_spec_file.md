### 👨‍💻 Редакция существующей спецификации API

Используем  простой [Sunrise and sunset times API](https://sunrise-sunset.org/api) для знакомства с процессом создания файла спецификации OpenAPI. [Sunrise and sunset times API](https://sunrise-sunset.org/api) не требует аутентификации с запросами, поэтому он удаляет некоторые из более сложных  процессов аутентификации (можно пропустить объект `secutity`). В этом практическом занятии отредактируем некоторые из  значений в уже написанной спецификации OpenAPI.

Для редактирования файла спецификации OPenAPI:

- Скопируем код из [pre-built OpenAPI specification](https://idratherbewriting.com/learnapidoc/assets/files/swagger-sunrise-sunset/openapi_sunrise_sunset.yml)
- Вставляем содержимое YAML в [редактор Swagger](https://editor.swagger.io/)
- Определяем каждый из объектов корневого уровня спецификации API:
  - [Шаг 1: Объект openapi](step1-openapi-object.html)
  - [Шаг 2: Объект info](step2-info-object.html)
  - [Шаг 3: Объект servers](step3-servers-object.html)
  - [Шаг 4: Объект paths](step4-paths-object.html)
  - [Шаг 5: Объект components](step5-components-object.html)
  - [Шаг 8: Объект externalDocs](step8-externalDocs-object.html)
- В объекте `info` (сверху) внесем изменения в свойство `description` и посмотрим, как обновится экран в правом столбце.
- В объекте `parameters` тоже внесем изменения в свойство `description` и посмотрим, как обновится экран в правом столбце.
- Найдем указатель `$ref` в объекте `response`. Определим, на что он указывает в компонентах.
- Добавим интервалов таким образом, чтобы сделать спецификацию недействительной (например вставим пробел перед `info`) и посмотрим на ошибку. Затем уберем лишний пробел.
- Развернем секцию `GET`, нажмем `Try it out` и посмотрим на ответ.

Подробная информация для этого практического занятия находится по ссылке [Создание спецификации OpenAPI](create-openapi-specification.html)
