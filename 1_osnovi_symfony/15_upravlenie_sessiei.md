## 1.5 Управление сессией {#1-5}

```$session = $request->getSession();```

*   Установка и получение атрибутов сессий

```
$session->set('name','Albert');
$session->get('name');
```

*   Flash-сообщения - хранятся в сессии только на один доп. запрос

```
$session->getFlashBaf()->add('notice','Profile updated!');

foreach ($session->getFlashBag()->get('notice',array()) as $msg) { 
    echo '<div>'.$msg.'</div>'; 
}
```

или в шаблоне:

```
{% for flashMessage in app.session.flashbag.get('notice') %}

<div>{{ flashMessage }}</div>

{% endfor %}
```