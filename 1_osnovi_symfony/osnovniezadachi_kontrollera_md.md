### 1.4 Основные задачи контроллера

*   Redirect - перенаправление на другую страницу

```return $this->redirect(%this->generateUrl('page'),301);```

*   Forward - внутреннее перенаправление без смены URL

```return $this->forward('AcmeHelloBundle:Hello:index',array('name'=>$name));```

*   Render Templates - подстановка шаблонов

```return $this->render('AcmeHelloBundle:Hello:index.html.twig',array('name'=>$name));```

*   Accessing other services - доступ к сервисам

```$router = $this->get('router');```

*   404error response - отдача 404 ошибки

```throw $this->createNotFoundException('Not exist');```