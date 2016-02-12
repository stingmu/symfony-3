### 2.2 Экранирование переменных и текста: {#2-2}

{{ article.content | е }} {# переменная дважды не экранируется #}

{{ article.content | raw }} {# переменная не экранируется #}

{% autoescape true %}

    &lt;ul&gt;&lt;li&gt;Экранировать этот список&lt;/li&gt;&lt;/ul&gt;

{% endautoescape %}

{% raw %}

    &lt;ul&gt;&lt;li&gt;Оставить этот список как есть&lt;/li&gt;&lt;/ul&gt;

{% endraw %}