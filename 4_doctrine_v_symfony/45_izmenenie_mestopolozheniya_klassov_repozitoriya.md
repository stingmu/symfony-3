## 4.5 Изменение местоположения классов репозитория

Чтобы файл с классами репозиториев не лежал в одной директории со стандартными классами сеттеров и геттеров сущностей, необходимо указать перед объявлением соответствующего класса сущности в аннотациях следующее:

```
/**
* @ORM\Entity(repositoryClass="Acme\StoreBundle\Entity\Repository\ProductRepository")
*/
```

Сам файл репозитория выглядит следующим образом:

```
// src/Acme/StoreBundle/Entity/Repository/ProductRepository.php

namespace Acme\StoreBundle\Entity\Repository;

use Doctrine\ORM\EntityRepository;

class ProductRepository extends EntityRepository {

    public function findOneProductById($id) {
        $query = $this->getEntityManager()->createQuery(
            'SELECT p FROM AcmeStoreBundle:Product p WHERE p.id = :id'
        )->setParameter('id',$id);

        try {
            return $query->getSingleResult();
        } catch(\Doctrine\ORM\NoResultExcetion $e) {
            return null;
        }
    }
}
```

Теперь данный метод доступен в контроллерах:

`$products = $em->getRepository('AcmeStoreBundle:Product')->findAllOrderedByName();`

Также в классах репозитория имеется связка с UnitOfWork.

`$this->matching(Criteria ::create()->where());`