## 5.17 Подключение файлов

Для подключения некоторого файла прямо перед загрузкой сервиса имеется директива "file":
```
services:
    foo:
        class: Acme\HelloBundle\Foo\Bar
        file: %kernel.root_dir%/src/path/to/file/foo.php
```