### 7.5 Событие kernel.terminate {#7-5-kernel-terminate}

Последним событием процесса HttpKernel является KernelEvents::TERMINATE (kernel.terminate), которе возникает уже после HttpKernel метода handle() и после того как ответ был отправлен пользователю. Основной целью является выполнение “тяжелых” операций, которые не будут задерживать отдачу ответа клиенту. Вызов terminate() происходит в /web/app.php:
```
$response = $kernel->handle($request);
$response->send();$kernel->terminate($request, $response);
…
```