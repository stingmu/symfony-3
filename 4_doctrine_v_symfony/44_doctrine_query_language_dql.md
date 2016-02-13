## 4.4 Doctrine Query Language (DQL)

```
$query = $em->createQuery(

'SELECT p FROM AcmeStoreBundle:Product p WHERE p.price > :price ORDER BY p.price ASC'

)->setParameter('price', '19.99');

$products = $query->getResult();
```