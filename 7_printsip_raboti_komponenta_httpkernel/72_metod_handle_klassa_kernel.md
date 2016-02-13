## 7.2 Метод handle() класса Kernel
```
//  \Symfony\Component\HttpKernel\Kernel.php
public function handle(Request $request, $type = HttpKernelInterface::MASTER_REQUEST, $catch = true)
{
   if (false === $this->booted) {
       $this->boot();
   }
   return $this->getHttpKernel()->handle($request, $type, $catch);
}
```
123В данном методе проверяется, загружено ли ядро и если нет - оно загружается: подключается все бандлы, Service Container и сервисы внутри бандлов (**$this->boot()**). Далее запроc передаётся в метод **handle()**, но уже экземпляра класса **HttpKernel**.