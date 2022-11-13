---
title: Получаем ключ авторизации
last_updated: Oct 8, 2019
sidebar: mydoc_sidebar
permalink: get-authorization-keys.html
folder: like-developer
---

Почти каждый сайт API имеет метод для аутентификации запросов. Обычно мы предоставляем ключ API в своих запросах для получения ответа. Сейчас нам нужно получить ключи API, чтобы отправлять запросы нашему API погоды, а позже изучим [аутентификацию и авторизацию](authentication-and-authorization.html) подробнее.

<a name="auth"></a>
## Зачем запросу нужна авторизация

Требование авторизации позволяет издателям API делать следующее:

- лицензированный доступ к API;
- оценка лимита количества запросов;
- Контроль доступа определенных функций в API и многое другое.

Для запуска примеров кода в этом курсе нам нужно будет использовать свои собственные ключи API, поскольку эти ключи обычно обрабатываются как пароли и не выдаются или не публикуются открыто на веб-странице.

{% include tip.html content="Если вы хотите позаимствовать ключи API автора курса, вы можете получить их [здесь](https://idratherbewriting.com/learnapidoc/assets/files/apikeys.txt). Иногда бывает, участники семинара зацикливаются на попытках получить ключи API, поэтому автор опубликовал свои ключи здесь, чтобы избежать задержек в работе." %}

<a name="key"></a>
## 👨‍💻 Практика: Получаем ключ авторизации OpenWeatherMap API

- Переходим на страницу [https://openweathermap.org](https://openweathermap.org/)
- Нажимаем `Sign Up` в навигационной панели и создать аккаунт
- После создания аккаунта вернуться на страницу [https://openweathermap.org](https://openweathermap.org/) и кликнуть `Sign in`
- После входа попадаем в панель разработчика. Кликаем на плашку `API key`  
- Сохраняем сгенерированный ключ в удобном месте.

<a name="idAeris"></a>
## Получаем секретный код и ID Aeris Weather API

И для контраста, давайте получим ключи для Aeris Weather API. Aeris Weather API требует секретного кода и идентификатора для отправки запросов.

- Открываем сайт [http://www.aerisweather.com](https://www.aerisweather.com/) и нажимаем кнопку `Get started for free` (бесплатная версия ограничивает количество запросов, которые можно сделать).
- Вводим username, email и пароль, после чего нажимаем `Sign up for free` для создания аккаунта в сервисе Aeris. После этого входим в аккаунт.
- После входа в аккаунт нажимаем `Account` в правом верхнем углу.
- Нажимаем `Apps`(во втором навигационном ряду справа от `Usage`) и там выбираем `New Application`

{% include image.html file="like-developer/5.png" alt="aeris" %}

- В диалоговом окне **Add a New Application** вводим следующее:
  - **Application Name**: My biking app (или что-то в этом духе)
  - **Application Namespace**: localhost
- Нажимаем `Save App`.

После регистрации приложения мы должны увидеть его идентификатор, секретный код и пространство имен. Скопируем эту информацию в место, к которому можем легко получить доступ, так как оно понадобится вам для отправки запросов.

{% include tip.html content="Помните, то как пользователи авторизуют вызовы с помощью API - это то, что вы обычно описываете в документации API. Далее в курсе мы более подробно рассмотрим [методы авторизации](authentication-and-authorization.html)." %}

<a name="editor"></a>
## Текстовый редактор

В предстоящих практических занятиях мы будем работать с кодом в текстовом файле. Для работы с кодом, мы используем текстовый редактор plain text вместо редактора WYSIWYG). Вот несколько вариантов для текстовых редакторов:

- [Sublime Text (Mac or PC)](http://www.sublimetext.com/)
- [TextWrangler](http://www.barebones.com/products/textwrangler/) or [BBEdit](http://www.barebones.com/products/bbedit/) (Mac)
- [WebStorm (Mac or PC)](https://www.jetbrains.com/webstorm/)
- [Notepad++ (PC)](https://notepad-plus-plus.org/)
- [Atom (Mac or Windows)](https://atom.io/)
- [Komodo Edit (Mac or PC)](https://www.activestate.com/products/komodo-edit/)
- [Coda (Mac)](https://panic.com/coda/)

Эти редакторы предоставляют функции, которые позволяют вам лучше управлять текстом. Выберите тот, который вы хотите. Избегайте использования TextEdit, так как он добавляет скрытое форматирование, которое может повредить ваш контент.


[🔙](using-api-scenario.html)

[Go next ➡](submit-requests-postman.html)
