### 4.7 Отношения метаданных (Relations) {#4-7-relations}

*   One (category) to many (products)

```
use Doctrine\Common\Collections\ArrayCollection;

class Category {

    /**
    
    * @ORM\OneToMany(targetEntity="Product", mappedBy="category")
    
    */
    
    protected $products;
    
    public function __construct() {
    
     $this->products = new ArrayCollection();
    
    }
}

```

*   Many (products) to one (category)

```
class Product

{

     /**

     * @ORM\ManyToOne(targetEntity="Category", inversedBy="products")

     * @ORM\JoinColumn(name="category_id", referencedColumnName="id")

     */

     protected $category;

}
```

*   Many (Products) to many (categories)

```
class Product {

 /**

 * @ORM\ManyToMany(targetEntity="Category", inversedBy="products")

 * @ORM\JoinTable(name="product_categories")

 */

     private $categories;

}

class Category {

 /**

 * @ORM\ManyToMany(targetEntity="Producr", mappedBy="categories")

 */

     private $products;

}
```

После указания зависимостей необходимо, чтобы доктрина сгенерировала новый аксессоры:

```php app/console doctrine:generate:entities Acme```

А также, чтобы добавила необходимые поля и ключи в таблицу БД:

```php app/console doctrine:schema:update --force```