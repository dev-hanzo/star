### 👨‍💻 Создаем запросы в curl

1. Открыть Postman
2. В любом запросе кликаем на кнопку `Code` под кнопкой `Save`
3. В диалоговом окне "Generate Code Snippets" выбираем cURL из выпадающего списка и нажимаем на кнопку `Copy to Clipboard`

{% include image.html file="introduction-rest-api/6.png" alt="Generate_code_snippets" %}

Код Postman для запроса прогноза погоды OpenWeatherMap выглядит в формате cURL следующим образом:

```javascript
curl -X GET \
      'https://api.openweathermap.org/data/2.5/weather?lat=37.3565982&lon=-121.9689848&units=imperial&appid=fd4698c940c6d1da602a70ac34f0b147' \
      -H 'Postman-Token: dcf3c17f-ef3f-4711-85e1-c2d928e1ea1a' \
      -H 'cache-control: no-cache'
```

Postman добавил свою информацию о хедере (обозначено -Н) Тэги добавленного заголовка можно удалить. Также можно удалить знаки `\`, они добавлены для читаемости текста.

Кроме того, обратите внимание, что в Windows нужно изменить одинарные кавычки на двойные, потому что одинарные кавычки не поддерживаются в терминале Windows по умолчанию.

Вот запрос curl с удаленными символами -H и обратной косой чертой, а одинарные кавычки преобразованы в двойные кавычки:

```
curl -X GET "https://api.openweathermap.org/data/2.5/weather?lat=37.3565982&lon=-121.9689848&units=imperial&appid=fd4698c940c6d1da602a70ac34f0b147"
```

4. Curl доступен на MacOS по умолчанию. Если на Windows curl еще не установлен, то инструкции по установке по [ссылке](http://www.confusedbycode.com/curl/#downloads), нужно выбрать одну из бесплатных версий с правами Администратора.
5. Открываем терминал
 - на OS Windows нажимаем `ctrl+R` и вводим команду `cmd`, Правой кнопкой мыши вызываем меню и выбираем `Paste` для вставки запроса.
 - на MacOS открываем [iTerm](https://www.iterm2.com/) или терминал, нажимая `cmd+Пробел` и вводим команду `Terminal` Вставляем запрос в командную строку и жмем кнопку `Enter`  

Ответ от OpenWeatherMap на наш запрос будет выглядеть так:

```javascript
{"coord":{"lon":-121.96,"lat":37.35},"weather":[{"id":801,"main":"Clouds","description":"few clouds","icon":"02d"}],"base":"stations","main":{"temp":65.59,"pressure":1014,"humidity":46,"temp_min":60.8,"temp_max":69.8},"visibility":16093,"wind":{"speed":4.7,"deg":270},"clouds":{"all":20},"dt":1522608960,"sys":{"type":1,"id":479,"message":0.1642,"country":"US","sunrise":1522590719,"sunset":1522636280},"id":420006397,"name":"Santa Clara","cod":200}
```

Этот запрос минимизирован. Вы можете развернуть его, например на сайте [JSON pretty print](http://jsonprettyprint.com/) или, на MacOS с установленным Python добавив `| python -m json.tool` в конец cURL запроса, чтобы минимизировать JSON в ответе.

Для подробностей можно посмотреть ветку [Stack Overflow](https://stackoverflow.com/questions/352098/how-can-i-pretty-print-json-in-a-shell-script) по этой теме.

6. Самостоятельно сделаем curl запрос на 5-дневный прогноз, сохраненный в Postman.

Подробная информация для этого практического занятия находится по ссылке [Создание curl запроса](make-curl-call.html).
