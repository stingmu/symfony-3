### 9.1 Что такое подзапросы {#9-1}

Подзапросы выглядят и работают подобно остальным запросам, но обычно служат для обработки небольшой части страницы, вместо всей страницы целиком.

Методу HttpKernel::handle() передаётся специальный аргумент $type:

//  \Symfony\Component\HttpKernel\HttpKernel.php

public function handle(        Request $request,         $type = HttpKernelInterface::MASTER_REQUEST,         $catch = true)

{

…

}

Существуют две константы в интерфейсе HttpKernelInterface:

1.  MASTER_REQUEST - основной запрос
2.  SUB_REQUEST - подзапрос

Для каждого запроса вашего приложение, первый запрос который обрабатывается ядром Symfony - это MASTER_REQUEST. Это задаётся неявно, так как аргумент $type не передаётся методу handle() во фронт-контроллерах.

Многие слушатели событий выполняются только для запросов типа MASTER_REQUEST. Для этог используется специальный метод Kernel:Event:isMasterRequest()  Например компонент Firewall ничего не делает, если это подзапрос:

 public function onKernelRequest(GetResponseEvent $event)

 {

    if (!$event->isMasterRequest()) {

       return;

    }

    ...

 }