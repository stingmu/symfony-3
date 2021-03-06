## 1.6 Маршрутизация

### Указание маршрутов в YAML

Настройки маршрутизации указываются в файле **/app/config/routing.yml**. Пример роутинга для блога:
```
article_show:
    path: /articles/{lang}/{year}/{title}.{_format}
    defaults: { _controller: AcmeBundle:Article:show, _format: html }
    methods:  [GET]
    requirements:
        lang: en|fr|ru
        _format: html|rss
        _locale: ru
        year: \d+
```

Подключение внешнего файла роутинга с добавлением префикса:

```
acme_hello:
    prefix: /admin
    resource: "@AcmeBundle/Resources/config/routing.yml"
```

### Указание маршрута в PHP аннотациях 

Также имеется возможность указывать маршруты в аннотациях к контроллерам:

```
/**
 * @Route("/hello/{name}", name="hello")
 */
public function indexAction($name)
{
    return new Response('<html><body>Hello '.$name.'!</body></html>');
}
````

### Просмотр и отладки маршрутов в консоли

* Просмотр всех маршрутов приложения:

`php bin/console debug:router`

* Просмотр информации о маршруте по его названию:

`php bin/console debug:router homepage`

* Определение маршрута по URL:

`php bin/console router:match /blog/my-latest-post`

