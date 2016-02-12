### 1.1 Отдача ответа {#1-1}

*   Простейшая отдача ответа в контроллере:

return new Response('&lt;html&gt;&lt;body&gt;...&lt;/body&gt;&lt;/html&gt;');

*   Отдача ответа с использованием шаблона:

return $this->render( 'AcmeHelloBundle:Hello:index.html.twig',array( 'name'=>$name) );

Метода render() создаёт объект Response с полученными параметрами, подключая шаблон.

Название шаблона: BundleName:ControllerName:TemplateName.