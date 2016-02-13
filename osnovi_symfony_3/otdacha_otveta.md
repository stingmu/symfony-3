## Отдача ответа {#1-1}

*   Простейшая отдача ответа в контроллере:

`return new Response('<html><body>...</body></html>');`

*   Отдача ответа с использованием шаблона:

`return $this->render( 'AcmeHelloBundle:Hello:index.html.twig',array( 'name'=>$name) );`

Метод **render()** создаёт объект Response с полученными параметрами, подключая шаблон.

Название шаблона: **BundleName:ControllerName:TemplateName**.