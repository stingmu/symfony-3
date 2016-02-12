### 7.1 Вызов фронт-контроллера {#7-1}

Сперва вызывается фронт-контроллер /web/app.php

...

$request = Request::createFromGlobals();

$response = $kernel->handle($request);

$response->send();

...

Вся основная работа производится в методе handle(), который принимает на входе запрос ($request) и отдаёт ответ ($response);