### 4.2 DataBase (Doctrine) {#4-2-database-doctrine}

*   **SELECT** - получение данных

```
$em = $this->getDoctrine();
$product = $em->getRepository('AcmeStoreBundle:Product')->find($id);
```

*   **INSERT** - добавление записей

```
$product = new Product();
$product->setName('MyName');
$em = $this->getDoctrine()->getManager();
$em->persist($product);
$em->flush();
```
*   **DELETE** - удаление записей

```
$em->remove($product);
$em->flush();
```