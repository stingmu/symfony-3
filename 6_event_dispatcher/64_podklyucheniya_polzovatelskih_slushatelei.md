### 6.4 Подключения пользовательских слушателей {#6-4}

Для того чтобы подключить слушателя (listener), нужно его добавить в виде сервиса в один из конфигурационных файлов и пометить тегом "kernel.event_listener", с указанием в параметрах - наименования события и метода, который будет вызван:

services:

    kernel.listener.your_listener_name:

        class: Fully\Qualified\Listener\Class\Name

        tags:

            - { name: kernel.event_listener, event: xxx, method: onXxx }

Во многих случаях, слушателю передаётся специализированный дочерний класс Event. Это даёт слушателю доступ к информации о событии. Необходимо сверяться с документацией или реализацией каждого конкретного события для определения какой именно экземпляр Symfony\Component\EventDispatcher\Event будет передан. Так событие kernel.event передаёт экземпляр класса Symfony\Component\HttpKernel\Event\FilterResponseEvent:

use Symfony\Component\HttpKernel\Event\FilterResponseEvent

public function onKernelResponse(FilterResponseEvent $event)

{

    $response = $event->getResponse();

    $request = $event->getRequest();

}