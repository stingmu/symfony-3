### 2.3 Шаблоны,блоки, фильтры и функции {#2-3}

Наследование шаблона: {% extends "base.html.twig" %}

Дочерний шаблон может содержать только переопределяемые блоки, а использование html вне блоков вызовет ошибку.

Простая вставка шаблона: {% include 'education.html.twig' %}

Создание блока: {% block title %} Добро пожаловать на мой сайт {% endblock %}

Встроенные фильтры: date, format, replace, url_encode, json_encode, title, capitalize, upper, lower, striptags, join, reverse, length, sort, merge, default, keys, escape, e.

Встроенные функции: range, cycle, constant, random, attribute, block, parent, dump, date.