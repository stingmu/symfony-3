### 2.4 Макросы TWIG {#2-4-twig}

**Макрос** — это аналог функции в PHP. Они применяются для многократного повторного использования HTML тегов. Например создадим макрос в отдельном шаблоне forms.html.twig:
```
{% macro input(name, value, type, size) %}
    <input
        type="{{ type | default('text') }}"
        name="{{ name }}"
        value="{{ value | e }}"
        size="{{ size | default(20) }}" />
{% endmacro %}
```

В нужном шаблоне необходимо выполнить импорт данного файла и обратиться к макросу:
```
{% import "forms.html" as forms %}
<p>{{ forms.input('username') }}</p>
<p>{{ forms.input('password', null, 'password') }}</p>
```