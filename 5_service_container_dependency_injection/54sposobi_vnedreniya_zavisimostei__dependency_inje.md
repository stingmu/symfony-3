## 5.4 Способы внедрения зависимостей (Dependency Injection)

Есть 2 способа внедрения зависимостей:

1. Типичный способ удостовериться в том, что сервис получил свои зависимости - это прописать зависимости в качестве аргументов конструктора.
```
class SomeService
{
    private $container;
    public function __construct(ContainerInterface $container)
    {
        $this->container = $container;
    }
}
```
2. В некоторых случаях требуется не переопределять конструктор или не добавлять к нему дополнительные обязательные аргументы. Или какие-либо зависимости еще не определены в момент создания сервиса. В этих случаях можно добавить в класс сервиса метод-сеттер, позволив таким образом внедрять зависимость сразу после создания сервиса. Но в таком случае необходимо позаботиться, чтобы сеттер был обязательно вызван.
```
class SomeService
{
    private $container;
    
    public function setContainer(ContainerInterface $storage)
    {
        $this->container = $container;
    }
    
    public function getContainer()
    {
        return $this->container;
    }
}
```
    * Преимущество использования сеттеров в том, что не требуется иметь аргумент в конструкторе для каждой зависимости. Иногда это означает что нет необходимости создавать конструктор вообще, или что можно оставить текущий конструктор без изменений.

    * Единственный недостаток данного подхода в том, что можно забыть вызвать сеттер и получить ошибку из-за отсутствия необходимой зависимости. Для избежания данной ошибки можно обернуть вызовы зависимостей проверкой на их существование.


```
...
public function getContainer()
    {
           if (!($this->container instanceof ContainerInterface)) {
                throw new \RuntimeException(‘Service container is missing’);
           }
        return $this->container;
    }
...
```

Компонент Symfony Dependency Injection включает в себя интерфейс ContainerAwareInterface и трейт ContainerAwareTrait (\Symfony\Component\DependencyInjection\ContainerAwareTrait), который уже содержит приватное свойство $container и его сеттер. Классы, в которые передаётся трейт ContainerAwareTrait автоматически получают контейнер через сеттер setContainer(). Стандартный класс Controller из бандла FrameworkBundle использует как раз ContainerAwareTrait.

Однако такой подход вызовет большое количество дублирующего кода в конфигурациях сервиса. Дабы избежать это, можно создать абстракный сервис, в который добавить вызов setContainer(). И уже этот сервис наследовать всеми остальными.

```
abstract_container_aware:
    abstract:  true    calls:        - [setContainer, ['@service_container]]
        some_service:
            class: AcmeBundle\Service\SomeService
            parent: abstract_container_aware
```

Родительский сервис не обязательно делать абстрактным. Если он будет использоваться напрямую - можно опустить параметр abstract.