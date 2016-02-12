### 7.4.4 Получение аргументов контроллера {#7-4-4}

На этом шаге уже точно определен контроллер, который будет вызван. Далее необходимо получить все аргументы, которые будут использованы:

// private function handleRaw

...

$arguments = $this->resolver->getArguments($request, $controller);

…

Controller Resolver определяет какие аргументы ему передавать, используя реверс-инжиниринг PHP ([Reflection](https://www.google.com/url?q=http://php.net/manual/ru/intro.reflection.php&sa=D&ust=1455315226864000&usg=AFQjCNGP84wrJ8r0ktzlNB9vLNc2BAIxVA)). Затем он проходит в цикле все атрибуты контроллера и использует следующие правила, чтобы понять какие значения должны быть отправлены для каждого аргумента:

1.  Если существует параметр запроса Request, совпадающий по названию с аргументом контроллера, тогда используется его значение. Например, если первый аргумент в контроллере $year и имеется параметр запроса - year.public function indexAction($year,$month,$day)
2.  Если у аргумента в контроллере указан класс Request, тогда в качестве значения передаётся объект Request.public function indexAction(Request $request)

Также можно совмещать оба варианта в одном контроллере:         public function indexAction(Request $request, $year)