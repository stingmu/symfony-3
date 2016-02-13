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

*   Отдача ответа с использованием шаблона:

`return $this->render( 'AcmeHelloBundle:Hello:index.html.twig',array( 'name'=>$name) );`

Метод **render()** создаёт объект **Response** с полученными параметрами, подключая шаблон.

Название шаблона: **BundleName:ControllerName:TemplateName**.