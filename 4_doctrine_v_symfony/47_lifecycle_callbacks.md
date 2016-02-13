## 4.7 Lifecycle Callbacks

Методы, которые необходимо выполнить во время различных стадий жизни сущности.

*   **preRemove (postRemove)** - перед/после удаления
*   **prePersist (postPersist)**
*   **preUpdate (postUpdate)** - перед/после обновления
*   **postLoad** - загрузка или обновление
*   **loadClassMetadata** - после загрузки аннотаций

Методы выполняются только через **EntityManager**.