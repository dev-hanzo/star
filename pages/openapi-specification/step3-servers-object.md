---
title: Руководство OpenAPI Шаг 3 Объект "servers"
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: step3-servers-object.html
folder: openapi-specification
---


| [*Шаг 1: объект* `openapi`](step1-openapi-object.html) | --> | [*Шаг 2: объект* `info`](step2-info-object.html) | --> | [**Шаг 3: объект** `servers`](step3-servers-object.html) | --> | [*Шаг 4: объект* `paths`](step4-paths-object.html) | --> | [*Шаг 5: объект* `components`](step5-components-object.html) | --> | [*Шаг 6: объект* `security`](step6-security-object.html) | --> | [*Шаг 7: объект* `tags`](step7-tags-object.html) | --> | [*Шаг 8: объект* `externalDocs`](step8-externalDocs-object.html) |

В объекте `servers` указывается базовый путь, используемый в ваших запросах API. Базовый путь - это часть URL, которая находится перед конечной точкой.

<a name="sample"></a>
## Пример объекта `servers`

Пример объекта `servers`

```
servers:
- url: https://api.openweathermap.org/data/2.5/
```

Каждая из конечных точек (называемых в спецификации `paths`) будет добавляться ​​к URL-адресу сервера, при отправке пользователями пробных запросов `Try it out`. Например, если одним из путей является` /weather`, то при отправке запроса Swagger UI представит путь к `{server URL}{path}` или [https://api.openweathermap.org/data/2.5/weather](https://api.openweathermap.org/data/2.5/weather).
<a name="options"></a>
## Опции URL сервера

Объект `servers` обладает гибкой настройкой. Можно указать несколько URL-адресов серверов, которые могут относиться к различным средам (тестовая, бета-версия, рабочая версия). При наличии нескольких URL-адресов серверов, пользователи могут выбирать среду в раскрывающемся списке серверов. Можно указать несколько URL-адресов серверов, например:

```
servers:
  - url: https://api.openweathermap.org/data/2.5/
        description: Production server
  - url: http://beta.api.openweathermap.org/data/2.5/
        description: Beta server
  - url: http://some-other.api.openweathermap.org/data/2.5/
        description: Some other server
```

В Swagger UI выбор из нескольких серверов осуществляется при помощи выпадающего списка

{% include image.html file="openapi-specification/7.png" alt="multiservers" %}

Если указан один сервер все равно будет отображаться выпадающий список, но с одним вариантом.

В URL-адрес сервера также можно включать переменные, которые будут заполняться сервером во время выполнения. Кроме того, если для разных путей (конечных точек) требуются разные URL-адреса сервера, можно добавить объект `servers` в качестве свойства в объекте операции объекта `path`. URL-адрес локально объявленных серверов переопределяет URL-адрес глобальных серверов.

См. [Overriding Servers](https://swagger.io/docs/specification/api-host-and-base-path/) в разделе «Сервер API и базовый URL» (документы Swagger) для получения дополнительной информации.

<a name="appearance"></a>
## 👨‍💻 Отображение в Swagger UI

Вставим объект `servers` (первый пример кода выше, показывающий только один URL) в редактор Swagger, добавив к имеющемуся коду. Swagger UI будет выглядеть следующим образом:

{% include image.html file="openapi-specification/8.png" alt="servers" %}

[🔙](step2-info-object.html)

[Go next ➡](step4-paths-object.html)
