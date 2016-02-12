### 7.4.3 Переопределение контроллера {#7-4-3}

Теперь всё готово для вызова контроллера. Однако у нас есть еще последняя возможность переопределить контроллер с помощью события KernelEvents::CONTROLLER(kernel.controler)

        // private function handleRaw

…

$event = new FilterControllerEvent($this, $controller, $request, $type);

$this->dispatcher->dispatch(KernelEvents::CONTROLLER, $event);

$controller = $event->getController();

…

Для этого необходимо вызвать метод setController() объекта FilterControllerEvent. Сам фреймворк не имеет своих слушателей события kernel.controller. Есть только сторонние бандлы, которые слушают событие.

    Например, ControllerListener из бандла SensioFrameworkExtraBundle делает очень важную работу перед вызовом контроллера: собирает аннотации (@Template, @Cache и пр.) и сохраняет их в атрибутах запроса _template, _cache и пр.). Эти аннотации будут использоваться далее в процессе обработки запроса.

    ParamConverterListener из этого же бандла преобразует дополнительные аргументы контроллера для создания экземпляров сущностей, которые должны быть получены по id из маршрута.

 /**

 * @Route("/post/{id}")

 */

 public function showAction(Post $post)

 {

 ...

 }