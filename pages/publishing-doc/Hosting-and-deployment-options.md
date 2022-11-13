---
title: Варианты хостинга и развертывания
last_updated: Oct 10, 2019
sidebar: mydoc_sidebar
permalink: Hosting-and-deployment-options.html
folder: publishing-doc
---

[Генераторы статичных сайтов](Static-site-generators.html) занимаются разработкой контента, но не поддержкой и развертыванием. Для этого нам понадобится другая категория инструментов. Назовем эту категорию инструментов «опциями хостинга и развертывания».

Теоретически, можно опубликовать статичный веб-сайт на любом веб-сервере (например, AWS S3, Bluehost и т.д.). Но платформы хостинга с непрерывной доставкой делают нечто большее: они автоматически формируют результат при внесении изменений в репозиторий. Весь процесс сборки происходит полностью на сервере.

Платформы хостинга и развертывания обычно предлагают ряд дополнительных функций помимо простого веб-хостинга, например:

- SSL,
- CDN,
- минимизация,
- аутентификация,
- резервное копирование / резервирование
- и многое другое.

Эти платформы часто также интегрируются с определенными генераторами статичных сайтов (что является одной из причин, по которой ограничены предыдущие рассуждения о Jekyll, Hugo и Sphinx).

<a name="githubPages"></a>
## GitHub Pages

[GitHub Pages](https://pages.github.com/) предоставляет бесплатный вариант размещения и развертывания для проектов Jekyll. Загружая проект Jekyll в репозиторий GitHub, можно указать в настройках репозитория GitHub, что это проект Jekyll, и GitHub автоматически создаст его при фиксации репозитория. Эта функция - создание проектов Jekyll непосредственно из репозитория GitHub - называется GitHub Pages.

Чтобы активировать GitHub Pages для своего проекта нужно перейти на вкладку **Settings** и прокрутить страницу вниз до **GitHub Pages**

{% include image.html file="publishing-doc/49.png" alt="github pages" caption="Каждый репозиторий GitHub - это потенциальный проект Jekyll, который можно собрать автоматически после коммита" %}


Тесная интеграция Jekyll с GitHub является убедительным аргументом в пользу использования решения Jekyll-GitHub. По большей части GitHub является доминирующей платформой для проектов с открытым исходным кодом. При использовании GitHub, имеет смысл выбрать генератор статичного сайта, который интегрируется в ту же платформу для создания ваших документов.

GitHub Pages бесплатен, но имеет некоторые ограничения по объему:

- Рекомендуемое ограничение для исходных репозиториев GitHub Pages составляет 1 ГБ;
- Опубликованные сайты GitHub Pages могут быть не более 1 ГБ;
- На сайтах GitHub Pages установлен предел пропускной способности 100 ГБ в месяц;
- На сайтах GitHub Pages установлен лимит не более 10 сборок в час

[Usage limits](https://help.github.com/en/articles/what-is-github-pages#usage-limits)

В отличие от других платформ хостинга и развертывания, GitHub Pages не предлагает коммерческую версию, которая расширяет эти ограничения. Больше о GitHub Pages можно узнать [здесь](https://help.github.com/en/categories/github-pages-basics).

{% include note.html content="Оригинальный сайт этого курса и [блог Тома Джонсона](https://idratherbewriting.com/), используют Jekyll и GitHub Pages. На самом деле это отдельные проекты и репозитории Jekyll. Блог находится в репозитории GitHub под именем [`tomjoht.github.io`](https://github.com/tomjoht/tomjoht.github.io), названным по логину GitHub, но опубликованным с использованием собственного домена [`idratherbewriting.com`](https://idratherbewriting.com/). (Без кастомного домена он будет доступен по адресу [`http://tomjoht.github.com`](http://tomjoht.github.com).) Cайт API документации находится в репозитории под именем [learnapidoc](https://github.com/tomjoht/learnapidoc). Он доступен по умолчанию на [`https://idratherbewriting.com/learnapidoc`](https://idratherbewriting.com/learnapidoc). Они похожи на один и тот же сайт, но на самом деле это отдельные проекты в разных репозиториях. Довольно круто, что каждое хранилище в дополнение к первичному хранилищу (`tomjoht.github.io` отображается в виде подкаталога к первичному домену ([`idratherbewriting.com`](https://idratherbewriting.com/))." %}

<a name="cloudCannon"></a>
## CloudCannon

Предположим, мы захотели использовать Jekyll и GitHub, но останавливают ограничения GitHub и нужна более надежная платформа для проекта Jekyll. Если это так, [CloudCannon](https://cloudcannon.com/) будет хорошим решением. CloudCannon предоставляет вам множество [дополнительных функций](https://cloudcannon.com/features/files/), которых нет в GitHub, таких как:

- Аутентификация пользователей;
- Несколько сред для разных отраслей;
- Визуальный онлайн интерфейс для редактирования;
- Плагины Jekyll;
- SSL для пользовательских доменов;
- Автоматическая минификация.

И многое другое.

Основатели CloudCannon являются экспертами в Jekyll и разработали платформу специально для проектов Jekyll. Они также создали [множество учебных пособий по Jekyll](https://learn.cloudcannon.com/), чтобы обогатить знания разработчиков.

{% include tip.html content="О настройке и работе Jekyll и CloudCannon в разделе [Непрерывное развертывание Jekyll и CloudCannon](Jekyll-and-cloudCannon.html)" %}

<a name="readthedocs"></a>
## Read the Docs

Read the Docs - это платформа для онлайн-хостинга и развертывания, которая может читать проекты Sphinx (из общедоступного репозитория, такого как GitHub или Bitbucket) и автоматически создавать веб-вывод. Другими словами, это «платформа непрерывного документирования для Sphinx» (см. [An introduction to Sphinx and Read the Docs for Technical Writers](http://www.ericholscher.com/blog/2016/jul/1/sphinx-and-rtd-for-writers/)).

Введение на [главной странице Read the Docs](https://readthedocs.org/) описывает платформу следующим образом:

{% include callout.html content="Мы разместим вашу документацию бесплатно навсегда. Без всяких трюков. Мы помогаем 94 898 опен-сорс проектам делиться своей документацией. Всякий раз, когда вы отправляете код в вашу любимую систему контроля версий, будь то Git, Mercurial, Bazaar или Subversion, мы автоматически создаем ваши документы, чтобы ваш код и документация всегда были синхронизированы." type="info" %}

Read the Docs предоставляет как бесплатную версию с открытым исходным кодом ([readthedocs.org](https://readthedocs.org/)), так и коммерческую версию ([readthedocs.com](https://readthedocs.com/)). Такие уровни позволяют поднимать проект при изменении потребностей, но и не навязывают платное решение, если оно не нужно.

Read the Docs представляет темы, характерные для веб-сайтов с документацией. Позволяет использовать reStructuredText (или Markdown, в зависимости от предпочтений). reStructuredText предоставляет больше специфических для документации функций и семантики - см. раздел [Как насчет reStructuredText и Asciidoc?](More-about-Markdown.html#RST) для получения более подробной информации. Можно еще посмотреть статью [Why You Shouldn’t Use “Markdown” for Documentation](http://www.ericholscher.com/blog/2016/mar/15/dont-use-markdown-for-technical-docs/) где призывают отказаться от Markdown в пользу reStructuredText.

[В документации Read the Docs](https://docs.readthedocs.io/en/latest/intro/getting-started-with-sphinx.html) есть пример вывода.

{% include image.html file="publishing-doc/50.png" alt="Read the Docs" %}

Некоторые ключевые функции платформы:
- боковая панель с возможностью развернуть / свернуть,
- поиск,
- управление версиями,
- вывод в PDF и ePub и многое другое.

Узнать больше о платформе можно из [Read the Docs guide](https://docs.readthedocs.io/en/latest/). Read the Docs включает в себя большинство функций, которые ожидают технические писатели, особенно связанные с публикацией из единого источника. Некоторые из этих функций, отмеченные в разделе [An introduction to Sphinx and Read the Docs for Technical Writers](http://www.ericholscher.com/blog/2016/jul/1/sphinx-and-rtd-for-writers/), включают следующее:

- вывод HTML, PDF, ePub и других форматов;
- переиспользование контента при помощи "includes";
- условные включения на основе типа контента и тегов;
- множество HTML-тем, обеспечивающих удобство работы на мобильных устройствах и компьютерах;
- ссылки на страницы, документы и проекты;
- поддержка индекса и глоссария;
- поддержка интернационализации.

Платформа Read the Docs была основана [Эриком Холшером](https://www.ericholscher.com/), соучредителем [Write the Docs](http://www.writethedocs.org/). Первоначально программа Write the Docs была задумана как конференция сообщества Read the Docs, но превратилась в более общую конференцию, посвященную технической коммуникации для программных проектов. Если попасть на конференцию Write the Docs, то там можно обнаружить, что сессии фокусируются больше на передовых методах документирования, а не на обсуждении инструментов. (Можно прочитать пост [Impressions from the Write the Docs Conference](https://idratherbewriting.com/2017/05/23/write-the-docs-and-the-battle-against-vendor-evil/) или прослушать подкаст [Write the Docs podcast with the co-founders](https://idratherbewriting.com/2017/12/14/write-the-docs-founding-ideas-and-principles-podcast/)).

У Read the Docs впечатляющее количество пользователей. Платформа имеет тысячи проектов и получает миллионы просмотров страниц в месяц по этим проектам. В 2016 году программа Read the Docs имела более 77 000 проектов и получила 338 миллионов просмотров страниц и 75 миллионов уникальных посетителей). Посмотреть статистику за 2017 год можно [здесь](http://blog.readthedocs.com/read-the-docs-2017-stats/). Read the Docs является одним из самых посещаемых сайтов в сети и продолжает расти впечатляющими темпами.

<a name="netlify"></a>
## Netlify

[Netlify](https://www.netlify.com/) - это популярный сервис хостинга и развертывания для проектов статичных сайтов. В отличие от других хостинговых платформ, Netlify работает практически с любым генератором статичных сайтов, а не только с Jekyll или Sphinx.

Netlify предоставляет CD для проекта. Можно хранить контент в GitHub, GitLab или Bitbucket, связать его с Netlify, и Netlify будет пересобирать сайт всякий раз, при внесении изменений.

Netlify предлагает не только бесплатный уровень с функциями, похожими на GitHub Pages, но также позволяет переходить на уровень Pro, Business или Enterprise. С Netlify можно получить предварительный просмотр развертывания, откаты, обработку форм, распределенную сеть доставки контента (CDN), бесконечную масштабируемость, SSL, программируемый API, CLI и многое другое.

Самый впечатляющий пример сайта Netlify - [Smashing Magazine](https://www.smashingmagazine.com/). Ранее размещенный на WordPress, журнал Smashing Magazine переключился на Netlify с Hugo в качестве движка генератора статичных сайтов. [Smashing Magazine just got 10x faster](https://www.netlify.com/blog/2017/03/16/smashing-magazine-just-got-10x-faster/).

Среди других известных сайтов документации, использующих Netlify, присутствуют [Docker](https://docs.docker.com/), [Kubernetes](https://kubernetes.io/docs/home/), [React](https://reactjs.org/docs/hello-world.html), [Yarn](https://yarnpkg.com/lang/en/docs/), [Lodash](https://lodash.com/docs/), [Gatsby](https://www.gatsbyjs.org/docs/) и [Hugo](https://gohugo.io/documentation/).

Netlify CMS дополняет [Netlify CMS](Headless-cms-options.html#netlify), автономная CMS для контента (о которой будет рассказ разделе [Возможности автономных CMS (и Readme.io)](Headless-cms-options.html).)

<a name="aerobatic"></a>
## Aerobatic

[Aerobatic](https://www.aerobatic.com/) похож на Netlify тем, что он создает и публикует статический сайт. Aerobatic предоставляет мощный механизм публикации, который включает CDN, SSL, непрерывную доставку, CLI развертывания, защиту паролем и многое другое. Aerobatic могут создавать сайт, используя различные генераторы статичных сайтов, включая Jekyll, Hugo, Hexo и другие. Про Aerobatic пишут:

{% include callout.html content="Aerobatic - это специализированная платформа для эффективной доставки статических веб-страниц и ресурсов веб-сайта. Мы позаботимся о деталях конфигурации, которые обеспечат наилучший баланс производительности и удобства обслуживания. Перестаньте возиться с CDN и конфигами веб-сервера и сосредоточьтесь на кодировании отличного интерфейса. -  [Static website serving](https://www.aerobatic.com/docs/static-serving/)" type="info" %}

В целом, существует множество вариантов размещения и развертывания сайта. GitHub Pages, CloudCannon, Read Docs, Netlify и Aerobatic - это только некоторые из них. Можно изучить кастомные варианты хостинга и развертывания, доступные через существующую инфраструктуру вашей компании.

Есть еще одна категория инструментов для рассмотрения: [автономные CMS (и Readme.io)](Headless-cms-options.html). Автономная CMS часто объединяет решение для разработки и развертывания, поэтому класс инструментов тесно связан с упомянутыми здесь, но все равно она выделена в отдельную категорию на этом курсе.

[🔙](Static-site-generators.html)

[Go next ➡](Headless-cms-options.html)
