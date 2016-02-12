### 7.3 Метод handle() класса HttpKernel {#7-3-handle-httpkernel}

//  \Symfony\Component\HttpKernel\HttpKernel.php

public function handle(Request $request, $type = HttpKernelInterface::MASTER_REQUEST, $catch = true)

{

   try {

       return $this->handleRaw($request, $type);

   } catch (\Exception $e) {

       if (false === $catch) {

           $this->finishRequest($request, $type);

           throw $e;

       }

       return $this->handleException($e, $request, $type);

   }

}

Основную работу здесь производит приватный метод handleRaw(), находящийся в этом же классе. Если ловится Exception то вызывается соответствующий метод handleException();