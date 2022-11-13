---
title: Руководство OpenAPI Шаг 8 Объект "externalDocs"
last_updated: Oct 9, 2019
sidebar: mydoc_sidebar
permalink: step8-externalDocs-object.html
folder: openapi-specification
---

| [*Шаг 1: объект* `openapi`](step1-openapi-object.html) | > | [*Шаг 2: объект* `info`](step2-info-object.html) | > | [*Шаг 3: объект* `servers`](step3-servers-object.html) | > | [*Шаг 4: объект* `paths`](step4-paths-object.html) | > | [*Шаг 5: объект* `components`](step5-components-object.html) | > | [*Шаг 6: объект* `security`](step6-security-object.html) | > | [*Шаг 7: объект* `tags`](step7-tags-object.html) | > | [**Шаг 8: объект** `externalDocs`](step8-externalDocs-object.html) |

[Объект `externalDocs`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#external-documentation-object) позволяет добавлять ссылки на внешнюю документацию. Можно добавлять ссылки на внешние документы в объекте `paths`.

<a name="example"></a>
## Пример объекта `externalDocs`

Вот пример объекта `externalDocs`:

```yaml
externalDocs:
  description: API Documentation
  url: https://openweathermap.org/api
```

Обратите внимание, что эта документация должна относиться в целом к API. Чтобы связать определенный параметр с дополнительной документацией, можно добавить объект `externalDocs` к объекту операции, как отмечено в описании [Объекта `operations`](step4-paths-object.html#%operations) в Шаге 4: Объект `paths`.

<a name="appearanse"></a>
## Отображение в Swagger UI

Добавим приведенный выше код к корневому уровню документа OpenAPI в интерфейсе Swagger.

В Swagger UI после описания API появится ссылка вместе с информацией об API:

{% include image.html file="openapi-specification/18.png" alt="externaldoc" caption="Ссылка на внешнюю документацию" %}

{% include tip.html content="На данный момент, мы можем догадаться о некоторых проблемам интеграции Swagger UI с остальной частью нашей документации. Скорее всего, будет два вывода и полуфрагментированный пользовательский опыт. Объект `externalDocs` обеспечивает предсказуемое место для ссылки [концептуальных разделов](about-sixth-module.html). См. [Интеграция Swagger UI со сторонними документами](integrating-swagger-with-docs.html) для получения дополнительной информации о стратегиях интеграции." %}

<a name="finish"></a>
## Итоговый результат

Теперь, когда мы выполнили все шаги в руководстве OpenAPI, мы закончили создание нашего документа спецификации OpenAPI. Итоговый вариант спецификации здесь: [https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml](https://idratherbewriting.com/learnapidoc/docs/rest_api_specifications/openapi_openweathermap.yml)

Вот как выглядит собранная в Swagger UI спецификация:

{% include image.html file="openapi-specification/19.png" alt="final" %}

Попробуйте выполнить запрос в вышеприведенной версии и посмотрите на результат. В результате найдите значение `temp` в объекте `main`. Затем сделайте перерыв, выйдя на улицу и оцените, соответствует ли температура снаружи реакции.

{% include note.html content="Можно вставить любой допустимый путь к документу спецификации OpenAPI в поле «Explore» в Swagger UI (при условии, что версия Swagger UI поддерживает вашу версию OpenAPI), и он отобразит документацию API. Например, вы можете вставить [https://petstore.swagger.io/v2/swagger.json](https://petstore.swagger.io/v2/swagger.json) (затем нажать «Explore»), и он отобразит API Petstore." %}

[🔙](step7-tags-object.html)

[Go next ➡](create-openapi-specification.html)
