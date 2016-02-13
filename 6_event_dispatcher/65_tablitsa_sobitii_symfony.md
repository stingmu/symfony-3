## 6.5 Таблица событий Symfony

| **Name** | **KernelEvents Constant** | **Argument passed to the listener** |
| --- | --- | --- |
| kernel.request | KernelEvents::REQUEST | [GetResponseEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseEvent.html) |
| kernel.controller | KernelEvents::CONTROLLER | [FilterControllerEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FilterControllerEvent.html) |
| kernel.view | KernelEvents::VIEW | [GetResponseForControllerResultEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseForControllerResultEvent.html)|
| kernel.response | KernelEvents::RESPONSE | [FilterResponseEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FilterResponseEvent.html) |
| kernel.finish_request | KernelEvents::FINISH_REQUEST | [FinishRequestEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FinishRequestEvent.html) |
| kernel.terminate | KernelEvents::TERMINATE | [PostResponseEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/PostResponseEvent.html) |
| kernel.exception | KernelEvents::EXCEPTION | [GetResponseForExceptionEvent](http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseForExceptionEvent.html) |