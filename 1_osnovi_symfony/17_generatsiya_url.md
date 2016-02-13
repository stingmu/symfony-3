## 1.7 Генерация URL

* в контроллере

`$url = $this->generateUrl( 'blog_show', array('slug'=>'my-bkig-post') );`

* с помощью сервиса 'router'

`$url = $thi->get('router')->match('/blog/my-blog-post');`
`$url = $thi->get('router')->generate('blog_show',['name'=>$name]);`

* в js файлах

`var url = Routing.generate( 'blog_show',{"slug":'my-blog-post'} );`

Для этого необходим бандл - **FOSJsRoutingBundle**.

* в шаблонах TWIG

`<a href="{{ path( 'blog_show',{'slug':'my-blog-post'} ) }}">Read post</a>`
или абсолютный путь:
`<a href="{{ url('blog_show', {'slug': 'my-blog-post'}) }}">Read post.</a>`