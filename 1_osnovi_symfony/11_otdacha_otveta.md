## 1.1 Отдача ответа

*   Простейшая отдача ответа в контроллере:

```
use Symfony\Component\HttpFoundation\Response;

class HelloController
{
    public function indexAction($name)
    {
        return new Response('<html><body>Hello '.$name.'!</body></html>');
    }
}
```

<br />
*   Отдача ответа с использованием шаблона:

`return $this->render( 'AcmeHelloBundle:Hello:index.html.twig',array( 'name'=>$name) );`

Метод **render()** создаёт объект **Response** с полученными параметрами, подключая шаблон.

Название шаблона: **BundleName:ControllerName:TemplateName**.

Для того, чтобы использовать метод **render()** контроллер должен наследовать базовый класс **Symfony\Bundle\FrameworkBundle\Controller\Controller**.


### Объект Response

Класс **Response** - это абстракций вокруг ответа HTTP:

```
use Symfony\Component\HttpFoundation\Response;

// create a simple Response with a 200 status code (the default)
$response = new Response('Hello '.$name, Response::HTTP_OK);

// create a JSON-response with a 200 status code
$response = new Response(json_encode(array('name' => $name)));
$response->headers->set('Content-Type', 'application/json');
```

Имеется несколько специальных классов для простого создания ответов определенных типов:
* JsonResponse
* BinaryFileResponse
* StreamedResponse

Подробнее - [http://symfony.com/doc/current/components/http_foundation/introduction.html#component-http-foundation-response](http://symfony.com/doc/current/components/http_foundation/introduction.html#component-http-foundation-response)
