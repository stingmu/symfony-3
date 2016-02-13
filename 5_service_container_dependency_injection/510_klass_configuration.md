## 5.10 Класс Configuration

Для определения всех возможных конфигураций бандла используется класс **Configuration**, находящийся в файле **/AcmeBundle/DependencyInjection/Configuration.php**. Название класса на самом деле может быть любым, главное чтобы класс реализовывал интерфейс **ConfigurationInterface**.

```
class Configuration implements ConfigurationInterface
{
   public function getConfigTreeBuilder()
   {
       $treeBuilder = new TreeBuilder();
       $rootNode = $treeBuilder->root('name_of_bundle');
       $rootNode
        ->children()
            // Определение узлов конфигураций
        ->end()
       ;
       return $treeBuilder;
   }
}
```

В нём имеется один публичный метод: **getConfigTreeBuilder()**. Этот метод должен возвращать экземпляр класса **TreeBuilder**, который помогает вам в построении описания всех опций конфигурации, включая правила их валидаций.

Создание дерева настроек начинается с определения корневого узла:

`$rootNode = $treeBuilder->root('name_of_bundle');`

Название корневого узла должно быть названием бандла без “bundle” и в нижнем индексе с нижними подчеркиваниями. Корневой узел - это массив узлов. Узлов может быть сколько угодно:

```
$rootNode
    ->children()
        ->booleanNode('auto_connect')
            ->defaultTrue()
        ->end()
        ->scalarNode('default_connection')
            ->defaultValue('default')
        ->end()
->end()
```

Подробноее - [http://symfony.com/doc/current/components/config/definition.html](http://symfony.com/doc/current/components/config/definition.html)

Обычно объект класс Configuration используется внутри класса **BundlenameExtension**, которыйрасширяет  базовый класс **Extension**, и располагается в файле **/src/AcmeBundle/DependencyInjection/AcmeExtension.php**. Его назначение - получение массивов конфигураций, которые также получает ядро Symfony из соответствующих конфигурационных YAML файлов.

```
class MatthiasAccountExtension extends Extension
{
    public function load(array $configs, ContainerBuilder $container)
    {
        $processedConfig = $this->processConfiguration(
            new Configuration(),
            $configs
        );
    }
}
```

Метод **processConfiguration()** получает дерево конфигураций из объекта **Configuration** и обрабатывает полученные массивы.