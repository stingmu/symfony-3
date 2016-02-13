## 8\. Обработка исключений (Exceptions) {#8-exceptions}

Немаловероятно, что в процессе прохождения длинного пути от запроса до ответа будут появляться какие-либо ошибки. По-умолчанию Symfony ловитя любые исключения и пытается найти соответствующий ответ для них. В методе handle() класса HttpKernel вся обработка запроса обёрнут в блок try/catch:

```
//  \Symfony\Component\HttpKernel\HttpKernel.php
...
try {
   return $this->handleRaw($request, $type);
} catch (\Exception $e) {
   if (false === $catch) {
       $this->finishRequest($request, $type);
       throw $e;
   }
   return $this->handleException($e, $request, $type);
}
…
```

Если $catch установлена в true, то в случае выявления ошибки вызывается метод handleException(). Этот метод вызывает событие KarnelEvents::EXCEPTION (kernel.exception), которому передаётся объект GetResponseForExceptionEvent.
```
//  \Symfony\Component\HttpKernel\HttpKernel.php
private function handleException(\Exception $e, $request, $type)
{
   $event = new GetResponseForExceptionEvent($this, $request, $type, $e);
   $this->dispatcher->dispatch(KernelEvents::EXCEPTION, $event);

   // a listener might have replaced the exception
   $e = $event->getException();
   if (!$event->hasResponse()) {
       $this->finishRequest($request, $type);
       throw $e;
   }
   $response = $event->getResponse();
   ...
}
```
###Возможно 2 варианта:

1.  Один из слушателей данного события установил надлежащий объект Response для специфичного исключения и заменил оригинальный объект Exception ($e).

    В данном случае HttpKernel проверяет новый объект Response для установки правильного статус-кода ответа. Если мы не установили свой код, то по-умолчанию будет отдаваться “500 - Internal server error”.

1.  Если ни один слушатель не вызвал метод setResponse(), исключение будет выброшено повторно, но уже без автометической обработкой Symfony. В том случае если в настройках PHP включена директива display_errors - PHP выведет ошибку “как есть”.