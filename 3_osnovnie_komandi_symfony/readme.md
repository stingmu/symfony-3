## 3. Основные команды Symfony

* Генерирование нового бандла:

`php app/console generate:bundle --namespace=Acme/TestBundle --format=[yml,xml,php,annotation]`

* Генерирование новой сущности:php app/console doctrine:generate:entity
* Генерирование сеттеров и геттеров на основе yml, xml, php и аннотаций для сущности:

`php app/console doctrine:generate:entities Acme/StoreBundle`

*   Создание базы данных:php app/console doctrine:database:create
*   Обновление таблиц в базе данных (только DEV !!!):

`php app/console doctrine:schema:update --force`

*   Создание миграций и их внедрение:

`php app/console doctrine:migrtations:diff`
`php app/console doctrine:migrations:migrate`

*   Генерирование файла контроллера:

`php app/console generate:controller`

*   Генерирование класса форма для сущности:

`php app/console generate:doctrine:form AcmeStoreBundle:Comment`

*   Очистка кеша:

`php app/console cache:clear --env=[prod|dev|...]`

`php app/console cache:warmup --env=[prod|dev|...] --no-debug`

*   Crud генерация:
```
php app/console doctrine:generate:crud
    --entity=EnsJobeetBundle:Job
    --route-prefix=ens_job
    --with-write
    --format=yml
```
*   Загрузка данных - fixtures:

`php app/console doctrine:fixtures:load`

*   Копирование CSS и JS (при использовании стандартного Asset):

`php app/console assets:install web --symlink`

*   Копирование CSS и JS (при использовании Assetic):

`php app/console assetic:dump --env=[prod|dev|...]`

*   Генерация админа для SonataAdmin:

`app/console fos:user:create admintest admin@test.com pass --super-admin`

*   Соната админ:

`sonata:admin:list sonata registred services`
`sonata:admin:explain sonata explain some services`
`sonata:admin:generate CoreDeliveryBundle:Service`

*   Обновление библиотек в папке vendors согласно composer.json:

`php composer.phar update`