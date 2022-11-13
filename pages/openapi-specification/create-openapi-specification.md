---
title: Практическое занятие "Создание спецификации OpenAPI"
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: create-openapi-specification.html
folder: openapi-specification
---

В [руководстве по OpenAPI](openapi-tutorial-overview.html) мы прошли 8 этапов создания документа в спецификации OpenAPI. Теперь стоит попрактиковаться сначала в редактировании, а затем и в создании документа спецификации OpenAPI.


<a name="edit"></a>
## 👨‍💻 Практическое занятие: редакция существующего документа в спецификации OpenAPI

Используем простой [API Sunrise and sunset times](https://sunrise-sunset.org/api), чтобы лучше ознакомиться с процессом редактирования файла спецификации OpenAPI. [API Sunrise and sunset times](https://sunrise-sunset.org/api) не требует аутентификации с запросами, поэтому здесь отсутствуют сложные рабочие процессы аутентификации (можно пропустить [объект `security`](step6-security-object.html)). В этом упражнении мы отредактируем некоторые из существующих значений в уже написанном документе спецификации OpenAPI.

Для редактирования спецификации OpenAPI:

- Копируем код из [предварительно созданной спецификации OpenAPI](https://idratherbewriting.com/learnapidoc/assets/files/swagger-sunrise-sunset/openapi_sunrise_sunset.yml)
- Вставляем содержимое YAML в [редактор Swagger](https://editor.swagger.io/).
- Определяем каждый из объектов корневого уровня спецификации OpenAPI:
  - [Шаг 1: Объект `openapi`](step1-openapi-object.html)
  - [Шаг 2: Объект `info`](step2-info-object.html)
  - [Шаг 3: Объект `servers`](step3-servers-object.html)
  - [Шаг 4: объект `paths`](step4-paths-object.html)
  - [Шаг 5: Объект `components`](step5-components-object.html)
  - [Шаг 6: Объект `security`](step6-security-object.html)
  - [Шаг 7: Объект `tags`](step7-tags-object.html)
  - [Шаг 8: Объект `externalDocs`](step8-externalDocs-object.html)
- В объекте `info`(в верхней части) внесите изменения в свойство `description` и посмотрите, как обновляется визуальный дисплей в правом столбце.
- В объекте `parameters` внесите изменения в одно из свойств описания и посмотрите, как обновляется визуальный редактор.
- Найдите указатель `$ref` в объекте `response`. Определите, на что он указывает в `components`.
- Измените несколько интервалов таким образом, чтобы сделать спецификацию недействительной (например, вставить пробел перед информацией), и посмотрите на появившуюся ошибку. Затем верните неверный пробел.
- Разверните раздел **Get** и нажмите `Try it out`. Затем нажмите `Execute` и посмотрите ответ.

<a name="create"></a>
## 👨‍💻 Создание документа в спецификации OpenAPI для выбранного API

[На практике 3 модуля мы искали опен-сорс проект API](find-open-source-project.html), которому нужна была документация. Сейчас попробуем создать спецификацию OpenAPI для этого API. В зависимости от API, с которым мы решили работать, можно будет использовать этот документ как часть своего портфолио.

Если этот опен-сорс проект не имеет API или API уже имеет спецификацию OpenAPI, можно найти другой API (возможно, из этого [списка из 100+ API](API-doc-sites-list.html)) и создать спецификацию OpenAPI.

При создании спецификации пройдем по каждому шагу руководства по спецификации OpenAPI, чтобы создать документацию API:

- [Шаг 1: Объект `openapi`](step1-openapi-object.html)
- [Шаг 2: Объект `info`](step2-info-object.html)
- [Шаг 3: Объект `servers`](step3-servers-object.html)
- [Шаг 4: объект `paths`](step4-paths-object.html)
- [Шаг 5: Объект `components`](step5-components-object.html)
- [Шаг 6: Объект `security`](step6-security-object.html)
- [Шаг 7: Объект `tags`](step7-tags-object.html)
- [Шаг 8: Объект `externalDocs`](step8-externalDocs-object.html)

После создания проверяем нашу документацию в [редакторе Swagger](https://swagger.io/tools/swagger-editor/). Выполним запрос, чтобы убедиться, что все работает верно.


[🔙](step8-externalDocs-object.html)

[Go next ➡](swagger-ui-tutorial.html)
