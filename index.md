---
title: "Курс по документированию REST API"
keywords: документирование API, technical writers, технический писатель, курс документирования
last_updated: Oct 8, 2019
sidebar: mydoc_sidebar
permalink: index.html
image: images/seo_image.png
description: Курс по документированию API. Вольный перевод курса https://idratherbewriting.comlearnapidoc/
---

Курс по документированию API. Вольный перевод курса [Documenting APIs: a guide for technical writers](https://idratherbewriting.com/learnapidoc/), составленного Томом Джонсоном, техническим писателем Amazon.

## Коротко о курсе

Тяжелых и скучных лекций об абстрактных понятиях здесь не будет.

Курс по написанию документации REST API подразумевает практический подход к документированию REST API. На этом курсе будем заниматься изучением документации API на примерах использования API сервисов прогноза погоды.

Разберем API на составные части, узнаем о конечных точках, параметрах, типах данных, аутентификации, curl, JSON, командной строке, консоли разработчика Chrome, JavaScript и прочих деталях, связанных с REST API.

Идея курса в следующем: посмотреть на реальные сценарии использования API, сделав этот курс эффективным. Изучать концепты API независимо от контекста мы не будем.

Во время прохождения курса:
- изучим стандарты, инструменты и спецификации REST API;
- узнаем о необходимых разделах в документации API;
- проанализируем примеры документации REST API различных компаний;
- узнаем, как присоединиться к опен-сорс проекту, для получения опыта;
- и многое другое.

[Начать обучение 👨‍💻](about-first-module.html)

## Модули курса

1. [**О модуле "Введение в REST API"**](about-first-module.html)

    - [**Коротко о курсе**](index.html)
    - [**Обзор курса**](course-overview.html)
    - [**Для чего этот курс**](what-for-this-course.html)
    - [**Об авторе**](about-the-author.html)
    - [**Знакомство с документацией REST API**](intro-rest-api.html)
    - [**Что такое REST API**](what-is-rest-api.html)
    - [**Видео презентации**](video-presentations.html)
    - [**Слайды курса**](course-slides.html)
    - [**Практические занятия**](workshop-activities.html)
    - [**Практика: Определение цели**](identify-goals.html)
    - [**Рынок документации REST API**](api-doc-market.html)

2. [**О модуле "Используем API как разработчики"**](about-second-module.html)

    - [**Сценарий использования API погоды**](using-api-scenario.html)
    - [**Получение ключей авторизации**](get-authorization-keys.html)
    - [**Отправка запросов в Postman**](submit-requests-postman.html)
    - [**Введение и установка curl**](curl-intro-and-instalation.html)
    - [**Создание curl запроса**](make-curl-call.html)
    - [**Понимание curl**](understand-curl.html)
    - [**Использование методов с curl**](use-methods-with-curl.html)
    - [**Анализ JSON ответов**](analyze-json-response.html)
    - [**Изучение полезных данных JSON ответа**](inspect-json.html)
    - [**Доступ и вывод на страницу определенного значения JSON**](access-print-value.html)
    - [**Погружение в точечную нотацию**](dot-notation.html)

3. [**О модуле "Документирование конечных точек"**](about-third-module.html)

    - [**Документирование новой конечной точки**](new-endpoint.html)
    - [**Обзор пошагового описания API ссылки**](api-reference-tutorial-overview.html)
    - [**Шаг 1: Описание ресурса**](step1-resourse-description.html)
    - [**Шаг 2: Конечные точки и методы**](step2-endpoints-and-methods.html)
    - [**Шаг 3: Параметры**](step3-parameters.html)
    - [**Шаг 4: Пример запроса**](step4-request-example.html)
    - [**Шаг 5: Пример и схема ответа**](step5-response-example-and-schema.html)
    - [**Собираем все вместе**](putt-all-together.html)
    - [**Практическое занятие: Что не так в разделе API?**](whats-wrong.html)
    - [**Практическое занятие: Поиск open-source проекта**](find-open-source-project.html)
    - [**Практическое занятие: Оценка ключевых элементов API документации**](evaluate-api-referense-docs.html)

4. [**Спецификация OpenAPI и Swagger**](about-fourth-module.html)

    - [**Обзор форматов спецификаций REST API**](overview-specification-formats.html)
    - [**Знакомство со спецификациями OpenAPI и Swagger**](introduction-openapi-and-swagger.html)
    - [**Работа в YAML**](working-in-YAML.html)
    - [**Обзор руководства OpenAPI**](openapi-tutorial-overview.html)
    - [**Шаг 1: Объект `openapi`**](step1-openapi-object.html)
    - [**Шаг 2: Объект `info`**](step2-info-object.html)
    - [**Шаг3: Объект `servers`**](step3-servers-object.html)
    - [**Шаг 4: Объект `paths`**](step4-paths-object.html)
    - [**Шаг 5: Объект `components`**](step5-components-object.html)
    - [**Шаг 6: Объект `security`**](step6-security-object.html)
    - [**Шаг 7: Объект `tags`**](step7-tags-object.html)
    - [**Шаг 8: Объект `externalDocs`**](step8-externalDocs-object.html)
    - [**Практическое занятие: Создание спецификации OpenAPI**](create-openapi-specification.html)
    - [**Руководство Swagger UI**](swagger-ui-tutorial.html)
    - [**Демо Swagger UI**](swagger-ui-demo.html)
    - [**Введение и руководство SwaggerHub**](swaggerhub-introduction-and-tutorial.html)
    - [**Stoplight - инструмент визуального моделирования для создания спецификаций**](stoplight.html)
    - [**Интеграция Swagger с документацией**](integrating-swagger-with-docs.html)

5. [**Тестирование документации**](about-fifth-module.html)

    - [**Обзор тестирования документации**](overview-testing.html)
    - [**Настройка тестовой среды окружения**](set-up-test-environment.html)
    - [**Самостоятельное тестирование всех инструкций**](test-instructions-yourself.html)
    - [**Тестирование предположений**](test-assumptions.html)
    - [**Практическое занятие: Тестирование документации проекта**](test-documentation.html)

6. [**Концептуальные разделы**](about-sixth-module.html)

    - [**Разделы руководства пользователя**](user-guide-topics.html)
    - [**Обзор API**](API-overview.html)
    - [**Руководство по началу работы**](getting-started.html)
    - [**Требования аутентификации и авторизации**](authentication-and-authorization.html)
    - [**Коды статусов и ошибок**](status-error-codes.html)
    - [**Ограничения скорости**](rate-limiting.html)
    - [**Описание и образцы кода**](code-samples.html)
    - [**SDK и пример приложений**](sdks-sample-apps.html)
    - [**Краткое справочное руководство**](quick-reference-guide.html)
    - [**API Глоссарий**](api-glossary.html)
    - [**Лучшие практики API**](best-practices.html)
    - [**Практическое занятие: Оценка концептуального контента в проекте**](assess-conceptual-content.html)

7. [**Публикация документации**](about-seventh-module.html)

    - [**Обзор вариантов публикации документации**](Overview-for-publishing.html)
    - [**Список из 100 сайтов с API документацией**](API-doc-sites-list.html)
    - [**Шаблоны проектирования сайтов API документации**](Design-patterns.html)
    - [**Инструменты Docs-as-code**](Doc-as-code-tools.html)
    - [**Подробнее о Markdown**](More-about-Markdown.html)
    - [**Система контроля версий (пример Git)**](Version-control-system.html)
    - [**Практическое занятие: Управляем контентом в Wiki Github**](Manage-wiki-content.html)
    - [**Практическое занятие: Используем клиент GitHub для десктопа**](Use-GitHub-Desktop.html)
    - [**Практическое занятие: процесс Pull request на GitHub**](Pull-request-workflows.html)
    - [**Генераторы статичных сайтов**](Static-site-generators.html)
    - [**Варианты хостинга и развертывания**](Hosting-and-deployment-options.html)
    - [**Возможности автономных CMS**](Headless-cms-options.html)
    - [**Рекомендации - какой инструмент документирования выбирать**](Which-tool-choose.html)
    - [**Непрерывное развертывание Jekyll и CloudCannon**](Jekyll-and-cloudCannon.html)
    - [**Кейс для изучения: Переход на Docs-as-code**](Switching-tools.html)

8. [**Работа технического писателя**](about-eigth-module.html)

    - [**Рынок вакансий для технического писателя**](job-market.html)
    - [**Необходимое количество кода, которое нужно знать**](how-much-code-to-know.html)
    - [**Лучшие локации для работы**](best-locations.html)

9. [**Нативные библиотеки API**](about-ninth-module.html)

    - [**Обзор нативных библиотек API**](Overview-of-library.html)
    - [**Получаем пример Java проекта**](Get-the-sample-Java-project.html)
    - [**Java Ускоренный курс**](Java-crash-course.html)
    - [**Практическое занятие: Генерация Javadoc из примера проекта**](Activity-Generate-Javadoc.html)
    - [**Теги Javadoc**](Javadoc-tags.html)
    - [**Изучение вывода Javadoc**](Explore-Javadoc-output.html)
    - [**Редактирование тегов Javadoc**](Make-edits-Javadocs-tags.html)
    - [**Doxygen, генератор документации для С++**](Doxygen.html)
    - [**Создание концептуальной документации при помощи исходных библиотек API**](Create-non-refsdocs-with-native-library-APIs.html)

10. [**Глоссарий API и источники**](about-tenth-module.html)

    - [**Глоссарий API документации**](Glossary-for-API-documentation.html)
    - [**Практические занятия REST API**](RESTAPI-activities.html)
    - [**Практическое занятие: Получаем информацию о событии, используя API сервиса Eventbrite**](Get-event-information-using-Eventbrite-API.html)
    - [**Практическое занятие: Извлекаем галерею, используя API сервиса Flikr**](Retrieve-gallery-using-Flickr-API.html)
    - [**Практическое занятие: Получаем скорость ветра, используя API сервиса Aeris Weather**](Get-wind-speed-using-Aeris-API.html)
    - [**Справочник RAML**](RAML-tutorial.html)
    - [**Справочник API Blueprint**](API-Blueprint-tutorial.html)
    - [**Описание ошибок**](answeres-whats-wrong.html)

11. [**Документирование кода**](about-eleventh-module.html)

    - [**Почему документирование кода так сложно?**](doc-code.html)
    - [**Исследования о документировании кода**](doc-research.html)
    - [**Пять стратегий документирования кода**](doc-strategy.html)
