### 1.8 Применение Assetic для CSS и JS {#1-8-assetic-css-js}

Для подключения Assetic к бандлу, необходимо изменить файл App/config/config.yml:
```
assetic:
    bundles: [BloggerBlogBundle]
```
Можно удалить строку bundles и подключить Assetic ко всем бандлам.

```
{% stylesheets

    '@BloggerBlogBundle/Resources/public/css/style.css'
    
    '@BloggerBlogBundle/Resources/public/css/blog.css'
    
    debug=false
    
    output='css/blogger.css'
    
    filter='?yui_css'

%}

    <link href="{{ asset_url }}" rel="stylesheet" media="screen" />

{% endstylesheets %}
```


Параметры:

*   **debug** - установка режима отладки
*   **output** - указания выводимого имени файла
*   **filter** - подключение фильтров (знак вопроса перед yui_css принуждает работать компрессию в DEV).

Для работы фильтра минимизации CSS, используя YUI компрессор надо обновить app/config/config.yml:

assetic:
    filters:
    yui_css:
    jar: %kernel.root_dir%/Resources/java/yuicompressor-2.4.7.jar

Фильтры в библиотеке ядра:

*   **CssMinFilter** - минимизирование CSS
*   **JpegoptimFilter** - оптимизация JPEG файлов
*   **Yui\CssCompressorFilter** - сжатие CSS с использованием YUI компрессора
*   **Yui\JsCompressorFilter** - сжатие JavaScript с использованием YUI компрессора
*   **CoffeeScriptFilter** - компиляция CoffeeScript для JavaScript

Полный список фильтров Assetic - [https://github.com/kriswallsmith/assetic/blob/master/README.md](https://github.com/kriswallsmith/assetic/blob/master/README.md).

```
{% javascripts
    'https://code.jquery.com/jquery-1.11.1.min.js'
    '@AcmeBlogBundle/Resources/public/js/scripts.js'
    output='js/scripts.js'
    filter='yui_js'
%}
    <script src="{{ asset_url }}"></script>
{% endjavascripts %}
```