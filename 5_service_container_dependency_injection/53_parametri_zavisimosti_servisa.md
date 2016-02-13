## 5.3 Параметры (зависимости) сервиса

Параметры или зависимости сервиса могут быть строковые, массивы или др. сервисы:
```
# app/config/config.yml
parameters:
    my_mailer.class: Acme\HelloBundle\Mailer
    my_mailer.transport: sendmail
    my_mailer.gateways:
        - mail1
        - mail2
        - mail3
        
services:
    my_mailer:
        class: %my_mailer.class%
        arguments: [%my_mailer.transport%]
        public: false
   newsletter:
        class: Acme\HelloBundle\Newsletter
        arguments: [@my_mailer]
```