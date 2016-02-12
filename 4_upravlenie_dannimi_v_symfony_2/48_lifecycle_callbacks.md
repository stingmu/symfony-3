### 4.8 Lifecycle Callbacks {#4-8-lifecycle-callbacks}

Методы, которые необходимо выполнить во время различных стадий жизни сущности.

*   **preRemove (postRemove)** - перед/после удаления
*   **prePersist (postPersist)**
*   **preUpdate (postUpdate)** - перед/после обновления
*   **postLoad** - загрузка или обновление
*   **loadClassMetadata** - после загрузки аннотаций

Методы выполняются только через EntityManager.