## 2.3 Шаблоны,блоки, фильтры и функции

Наследование шаблона: `{% extends "base.html.twig" %}`

Дочерний шаблон может содержать только переопределяемые блоки, а использование html вне блоков вызовет ошибку.

Простая вставка шаблона: `{% include 'education.html.twig' %}`

Создание блока: `{% block title %} Добро пожаловать на мой сайт {% endblock %}`

Вставка контроллера:

```
<div>
    {{ render(controller(
        'AppBundle:Article:recentArticles',
        { 'max': 3 }
    )) }}
</div>
```

---

Применение фильтров: `{{ title|upper }}`

Встроенные фильтры: **date, format, replace, url_encode, json_encode, title, capitalize, upper, lower, striptags, join, reverse, length, sort, merge, default, keys, escape, e**
([полный список](http://twig.sensiolabs.org/doc/filters/index.html))

---

Применение функций: `{{ cycle(['odd', 'even'], i) }}`

Встроенные функции: **range, cycle, constant, random, attribute, block, parent, dump, date.**
([полный список](http://twig.sensiolabs.org/doc/functions/index.html))