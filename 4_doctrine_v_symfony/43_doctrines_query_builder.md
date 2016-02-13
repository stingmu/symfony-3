## 4.3 Doctrine's Query Builder {#4-4-doctrine-s-query-builder}

```
$repository = $this->getDoctrine()->getRepository('...');

$query = $repository->createQueryBuilder('p')

->where('p.price>:price')

->setParameter('price','19.99')

->orderBy('p.ptice','ASC')

->getQuery();

$products = $query->getResult(); // getSingleResult(); getOneOrNullResult();
```