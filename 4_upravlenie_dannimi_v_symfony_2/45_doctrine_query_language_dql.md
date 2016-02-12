### 4.5 Doctrine Query Language (DQL) {#4-5-doctrine-query-language-dql}

```
$query = $em->createQuery(

'SELECT p FROM AcmeStoreBundle:Product p WHERE p.price > :price ORDER BY p.price ASC'

)->setParameter('price', '19.99');

$products = $query->getResult();
```