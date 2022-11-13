---
title: Руководство OpenAPI Шаг 1 Объект "openapi"
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: step1-openapi-object.html
folder: openapi-specification
---

| [**Шаг 1: объект** `openapi`](step1-openapi-object.html) | > | [*Шаг 2: объект* `info`](step2-info-object.html) | > | [*Шаг 3: объект* `servers`](step3-servers-object.html) | > | [*Шаг 4: объект* `paths`](step4-paths-object.html) | > | [*Шаг 5: объект* `components`](step5-components-object.html) | > | [*Шаг 6: объект* `security`](step6-security-object.html) | > | [*Шаг 7: объект* `tags`](step7-tags-object.html) | > | [*Шаг 8: объект* `externalDocs`](step8-externalDocs-object.html) |

<a name="overview"></a>
## Обзор руководства OpenAPI

Прежде чем перейти к первому шагу учебного руководства по OpenAPI, нужно прочитать [обзор руководства по OpenAPI](openapi-tutorial-overview.html) (если еще не читали), чтобы понять суть этого учебного пособия. Вкратце, это руководство по OpenAPI уникально в следующих отношениях:

- Это руководство OpenAPI показывает спецификацию в контексте API сервиса прогноза погоды, [представленного ранее](using-api-scenario.html) в этом курсе.
- В руководстве показано, как информация спецификации отображается в [интерфейсе Swagger](https://github.com/swagger-api/swagger-ui).
- Руководство OpenAPI является выдержкой из [спецификации OpenAPI](https://github.com/OAI/OpenAPI-Specification),  и из [комментариев спецификации OpenAPI](https://swagger.io/docs/specification/about/).
- В руководстве OpenAPI охвачена версия 3.0 спецификации OpenAPI, которая является последней версией.

<a name="root"></a>
## Корневые объекты в спецификации OpenAPI

{% include note.html content="Под «корневым уровнем» подразумевается первый уровень в документе OpenAPI. Этот уровень также называется глобальным уровнем, потому что некоторые свойства объекта, объявленные здесь (а именно, серверы и безопасность), применяются к каждому из объектов операции, если не переопределены на более низком уровне." %}

На верхнем уровне в спецификации OpenAPI 3.0 существует восемь объектов. Внутри этих верхнеуровневых объектов есть много вложенных объектов, но на верхнем уровне есть только следующие объекты:

- [openapi](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#oasObject)
- [info](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#infoObject)
- [servers](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#serverObject)
- [paths](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#pathsObject)
- [components](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#componentsObject)
- [security](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#securityRequirementObject)
- [tags](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#tagObject)
- [externalDocs](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#externalDocumentationObject)

Весь документ (объект, содержащий восемь объектов корневого уровня) называется документом OpenAPI. По принятому соглашению  документу присваивают имя **openapi.yml**.

{% include note.html content="«OpenAPI» относится к спецификации; «Swagger» относится к инструменту (по крайней мере от Smartbear), который поддерживает спецификацию OpenAPI. Для получения более подробной информации об условиях см. [What Is the Difference Between Swagger and OpenAPI?](https://smartbear.com/blog/develop/what-is-the-difference-between-swagger-and-openapi/)" %}

<a name="SwaggerEditor"></a>
## Редактор Swagger

Для работы над документацией со спецификацией используется [онлайн-редактор Swagger](https://swagger.io/tools/swagger-editor/). Редактор Swagger имеет разделенное представление: слева пишем код спецификации, а справа видим полнофункциональный дисплей Swagger UI. Можно даже отправлять запросы из интерфейса Swagger в этом редакторе.

Редактор Swagger проверит контент в режиме реального времени, и укажет ошибки валидации, во время кодирования документа спецификации. Не стоит беспокоиться об ошибках, если отсутствуют X-метки в коде, над которым идет работа.

Полезно хранить текстовый файл локально, (например в редакторе Atom), со спецификацией в автономном режиме, и работать с содержимым документа в онлайн-редакторе Swagger. По окончании рабочего дня копировать и сохранять содержимое в свой локальный файл. Хотя, редактор Swagger достаточно хорошо кэширует содержимое (для этого не нужно очищать кеш браузера), поэтому скорее всего, локальный файл в качестве резервной копии не понадобится.

При желании можно приобрести подписку на SwaggerHub, и хранить содержимое спецификации в облаке (SwaggerHub имеет редактор, идентичный пользовательскому интерфейсу Swagger), в своем профиле. SwaggerHub - это инструмент премиум-класса для открытого и бесплатного редактора Swagger.

<a name="addingObject"></a>
## 👨‍💻 Добавляем объект `openapi`

Переходим в [редактор Swagger](https://editor.swagger.io/) и выбираем **File > Clear editor**. Оставим эту вкладку открытой пока изучаем руководство по OpenAPI, так как будем обновлять документ спецификации с каждым шагом.

Введем первое свойство корневого уровня для документа спецификации: `openapi`. В объекте [openapi](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#oasObject) указываем версию спецификации OpenAPI для проверки. Последняя версия 3.0.2.

```yaml
openapi: "3.0.2"
```

Пока мы не добавим сюда дополнительную информацию, будут отображаться сообщения об ошибках и примечания, например:  «No operations defined in spec!». Все в порядке - на следующем шаге мы увидим дополнительную информацию.

Версия 3.0 была выпущен 2017-07-26, а 3.0.2 - 10-08-2018 (см. [«История версий»](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#appendix-a-revision-history)). Большая часть информации и примеров в Интернете, а также вспомогательные инструменты часто фокусируются только на 2.0. Даже если вы заблокированы для работы для версии 2.0, можно кодировать спецификацию в 3.0, а затем воспользоваться инструментом [APIMATIC Transformer](https://www.apimatic.io/transformer), для преобразования спецификации 3.0 в 2.0. Обратная конвертация из 2.0 в 3.0 там тоже доступна.

<a name="appearance"></a>
## Представление в Swagger UI

Объект `openapi` не такой большой, и сейчас не хватает контента для проверки спецификации. Но когда мы позже визуализируем свой документ спецификации, мы увидим, что тег «OAS3» появится справа от имени API.

{% include image.html file="openapi-specification/5.png" alt="openapi" %}

На сервере Swagger UI использует версию спецификации 3.0.2 для проверки вашего контента.

На приведенном выше снимке экрана версия 2.5 относится к версии API, а не к версии спецификации OpenAPI.

[🔙](openapi-tutorial-overview.html)

[Go next ➡](step2-info-object.html)
