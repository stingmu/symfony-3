### 6.5 Таблица событий Symfony {#6-5-symfony}

| Name | KernelEvents Constant | Argument passed to the listener |
| --- | --- | --- |
| kernel.request | KernelEvents::REQUEST | [GetResponseEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseEvent.html&sa=D&ust=1455315226828000&usg=AFQjCNGTZ_zb-CMHJIx8uBUYh57U1qOFsA) |
| kernel.controller | KernelEvents::CONTROLLER | [FilterControllerEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FilterControllerEvent.html&sa=D&ust=1455315226830000&usg=AFQjCNFM1oFiJpXiY6M2zQL91ksV4bwyng) |
| kernel.view | KernelEvents::VIEW | [GetResponseForControllerResultEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseForControllerResultEvent.html&sa=D&ust=1455315226832000&usg=AFQjCNHDah8it62TJojNSKeL8GlA2ZJJFg) |
| kernel.response | KernelEvents::RESPONSE | [FilterResponseEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FilterResponseEvent.html&sa=D&ust=1455315226834000&usg=AFQjCNFQfCYqyuO6V0BNYeQ-rW6s2Vt7Uw) |
| kernel.finish_request | KernelEvents::FINISH_REQUEST | [FinishRequestEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/FinishRequestEvent.html&sa=D&ust=1455315226836000&usg=AFQjCNHFfamMAkgRmgUPAxW-2BUTYtaapQ) |
| kernel.terminate | KernelEvents::TERMINATE | [PostResponseEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/PostResponseEvent.html&sa=D&ust=1455315226838000&usg=AFQjCNHoMnABhokcSzGm3B51P5Xpvro6xw) |
| kernel.exception | KernelEvents::EXCEPTION | [GetResponseForExceptionEvent](https://www.google.com/url?q=http://api.symfony.com/3.0/Symfony/Component/HttpKernel/Event/GetResponseForExceptionEvent.html&sa=D&ust=1455315226840000&usg=AFQjCNHAIyoNZjEoDXjv1d3-BKmhSfFfYg) |