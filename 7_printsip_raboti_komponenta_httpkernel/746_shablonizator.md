### 7.4.6 Шаблонизатор

Контроллер на предыдущем шаге должен был::1) Либо сразу отдать напрямую объект Response2) Либо отдать что-то еще, например массив шаблонизатора, который уже будет преобразован в объект. Для того, чтобы шаблонизаторы могли “вклиниться” на данном этапе имеется событие KernelEvents::VIEW (kernel.view).

...if (!$response instanceof Response) {

    $event = new GetResponseForControllerResultEvent($this, $request, $type, $response);

    $this->dispatcher->dispatch(KernelEvents::VIEW, $event);

    if ($event->hasResponse()) {

        $response = $event->getResponse();

    }

    if (!$response instanceof Response) {

        // Ошибка, так как не получен Response и отдача Exception

    }

 }

...

Слушатели данного события могут вызывать метод setResponse() для установки своего ответа.