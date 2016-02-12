### 1.6 Маршрутизация {#1-6}

article_show:

    path: /articles/{lang}/{year}/{title}.{_format}

    defaults: { _controller: AcmeBundle:Article:show, _format: html }

    requirements:

        lang: en|fr|ru

        _format: html|rss

        year: \d+

Подключение внешнего файла роутинг с добавлением префикса:

acme_hello:

   prefix: /admin

resource: "@AcmeBundle/Resources/config/routing.yml"