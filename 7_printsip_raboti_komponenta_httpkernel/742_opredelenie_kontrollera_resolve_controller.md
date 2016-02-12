### 7.4.2 Определение контроллера (Resolve Controller) {#7-4-2-resolve-controller}

Далее идёт попытка определения необходимого контроллера для текущего Request объекта с помощью объекта \Symfony\Component\HttpKernel\Controller\ControllerResolver (экземпляр интерфейса ControllerResolverInterface).

// private function handleRaw

...

if (false === $controller = $this->resolver->getController($request)) {

   throw new NotFoundHttpException(sprintf('Unable to find the controller for path "%s". The route is wrongly configured.', $request->getPathInfo()));

}

...

В методе getController() в специальный атрибут (_controller) объекта Request помещается название контроллера (строка, которая затем преобразуется в PHP-вызов).