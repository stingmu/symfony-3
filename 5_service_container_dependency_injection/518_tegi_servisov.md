## 5.18 Теги сервисов

Тег означает, что служба используется для некоторых специфических функций. Он сообщает сторонним пакетам, что ваша служба должна быть зарегистрирована или использована некоторым особым способом внутри целевого пакета. Список тегов, доступных в ядре Symfony:

*   assetic.filter
*   assetic.templating.php
*   data_collector
*   form.field_factory.guesser
*   kernel.cache_warmer
*   kernel.event_listener - использование сервиса в качестве слушателя.
    - { name: kernel.event_listener, event: xxx, method: onXxx }
*   monolog.logger
*   routing.loader
*   security.listener.factory
*   security.voter
*   templating.helper
*   twig.extension
*   translation.loader
*   validator.constraint_validator

Подробнее -[ ](https://www.google.com/url?q=http://symfony.com/doc/current/reference/dic_tags.html&sa=D&ust=1455315226817000&usg=AFQjCNEv8cFBz3hS1UhuOoSMCNfsfrmCRg)[http://symfony.com/doc/current/reference/dic_tags.html](https://www.google.com/url?q=http://symfony.com/doc/current/reference/dic_tags.html&sa=D&ust=1455315226818000&usg=AFQjCNGrqmo3bssHr3CmoZBRT1bPvtgvNw)