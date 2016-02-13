## 1.6 Маршрутизация

Настройки маршрутизации указываются в файле **/app/config/routing.yml**. Пример роутинга для блога:
```
article_show:
    path: /articles/{lang}/{year}/{title}.{_format}
    defaults: { _controller: AcmeBundle:Article:show, _format: html }
    requirements:
        lang: en|fr|ru
        _format: html|rss
        yeaыr: \d+
```

Подключение внешнего файла роутинг с добавлением префикса:

```
acme_hello:
    prefix: /admin
    resource: "@AcmeBundle/Resources/config/routing.yml"
```