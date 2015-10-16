title: Turbolinks do Rails 4
date: 2012-11-28 12:31
tags: [rails]
---

[Turbolinks](https://github.com/rails/turbolinks) é um nome sugestivo, novidade que será integrado ao Rails 4, não vou explicar a p* toda.

Ele faz a requisição de forma assíncrona e carrega o conteúdo apenas do corpo (body), ao invés da página inteira, e isso tudo sem jQuery ou nada além que poucas linhas de js. 

Uma vez na sua aplicação todos os links irão seguir o comportamento do Turbolinks por padrão. Para 'desabilitá-lo' do link basta adicionar um atributo chamado de  ```data-no-turbolink ``` setado para  ```true ``` à sua âncora. 

Ele usa um recurso chamado pushState para alterar a URL e simular um click normal e tem outros recursos interessantes como eventos de página.

Isso me lembrou o velho PrototypeHelper do rails 2.3, o ```update_html```, ```remote_function```, aqueles ```page.call```, ```page.insert_html```, uma seboseira, mas escutei muito choro de dev.

Pro do Turbolinks: carregar conteúdo duas a três vezes mais rápido.
Contra: o navegador precisa dar suporte ao recurso.

Mais...<br>
[Railscast #390](http://railscasts.com/episodes/390-turbolinks)<br>
[Rails 4: A Look at Turbolinks](http://blog.teamtreehouse.com/rails-4-a-look-at-turbolinks)