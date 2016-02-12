### 5.10 Класс Configuration {#5-10-configuration}

Для определения всех возможных конфигураций бандла используется класс Configuration, находящийся в файле /AcmeBundle/DependencyInjection/Configuration.php. Название класса на самом деле может быть любым, главное чтобы класс реализовывал интерфейс ConfigurationInterface.

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

В нём имеется один публичный метод: getConfigTreeBuilder(). Этот метод должен возвращать экземпляр класса TreeBuilder, который помогает вам в построении описания всех опций конфигурации, включая правила их валидаций. Создание дерева настроек начинается с определения корневого узла:

$rootNode = $treeBuilder->root('name_of_bundle');

Название корневого узла должно быть названием бандла без “bundle” и в нижнем индексе с нижними подчеркиваниями. Корневой узел - это массив узлов.