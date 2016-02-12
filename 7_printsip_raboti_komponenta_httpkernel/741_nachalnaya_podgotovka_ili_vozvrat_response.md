### 7.4.1 Начальная подготовка или возврат Response {#7-4-1-response}

Обычно HttpKernel будет пытаться сгенерировать ответ вызывая контроллер. Но какой-либо listener, который слушает событие KernelEvents::REQUEST(kernel.request) может самостоятельно сгенерировать полностью настраиваемый ответ с помощью метода setResponse().

￼￼ //  \Symfony\Component\HttpKernel\HttpKernel.php

private function handleRaw(Request $request, $type = self::MASTER_REQUEST)

{

   $event = new GetResponseEvent($this, $request, $type);

   $this->dispatcher->dispatch(KernelEvents::REQUEST, $event);

  if ($event->hasResponse()) {

       return $this->filterResponse($event->getResponse(), $request, $type);

   }

   ...

}

Существует стандартные слушатели данного события:

*   RouteListener - берёт путь из объекта Response и пытается соонтести его с каким-либо маршрутом. И сохраняет результат в атрибутах объекта (_controller).
*   Firewall - проверяет права на посещение защищных страниц и если пользователь не авторизован - то может самостоятельно сгенерировать Response с 403 ошибкой.

Таким образом, цель события kernel.request - это либо создание и возврат ответа Response напрямую, либо добавление какой-либо информации в атрибуты объекта Request.