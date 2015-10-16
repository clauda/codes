title: Rails e Concerns
date: 2013-06-06 12:00
tags: [rails]
---

Acontece o tempo todo. 

Grandes projetos podem também trazer grandes dores de cabeça. A cada sprint de desenvolvimento, as ideias vão mudando e alterando o código, decisões são revertidas, você descobre algo que não havia previsto ou outra coisa que não era bem como você estava pensando. Ok. Nesse cenário nosso código adquire complexidades difíceis de manter, mesmo com uma boa cobertura de testes. Eu queria ter certeza de que estamos nos valendo de todas os recursos disponíveis para melhorar nosso código nesse sentido, deixando-o mais reusável, redondo e sem brechas.

## Concerns ##

A primeira intenção do Concern é remover duplicidade de código, e junto a isso, ele nos inclina a separar lógica e dados e qualquer dependência que esteja fora do domínio ou que não seja de responsabilidade dos modelos. Concerns podem ser implementados para modelos e controlers (```app/models/concerns``` e ```app/controllers/concerns```). No Rails 3 precisamos criar os diretórios, então incluí-los no ```application.rb``` para serem carregados. No Rails 4, isso será padrão e nenhuma configuração precisará ser feita.

	config.autoload_paths += %W(#{config.root}/app/models/concerns)

Implementamos um Concern criando um módulo que estende ```ActiveSupport::Concern```. Colocando a responsabilidade em um Concern, desacoplamos um trecho de código que pode ser reutilizado em outros modelos. Podemos adicionar métodos de classe ao modelo adicionando-os no módulo ```ClassMethods```, e tudo dentro do bloco ```included``` será incluído na classe que a utiliza também. Removemos o código duplicado e adicionamos a um Concern com esta estrutura:

	module OptimusPrime
		extend ActiveSupport::Concern

		included do
			# validates, scopes, relations, etc
			# tudo dentro deste bloco será incluído a classe
		end

		module ClassMethod
			# metodos de classe
		end

		# outros metodos
	end

Feito isto, um ```include``` do Concern nas classes resolvem nosso problema com o DRY.

	class class User < ActiveRecord::Base
		include OptimusPrime
		...
	end


#### Here Be Dragons ####
<br>
O uso de Concern as vezes é criticado porque um outra abordagem é tentar fazer  'remendos' com implementações específicas para um domínio, onde os concerns poderiam ficar em ```app/models/{any}/optimus_prime.rb```, por exemplo. Esse tipo de implementação tem um risco: pode não passar de uma maquiagem no seu código. Mas ainda para esse disfarce funcionar, você precisa se certificar que está extraindo métodos que fazem sentido estar em um Concern e que façam sentido entre sí, que pertençam ao mesmo domínio. Extrair código para um outro arquivo também é bem chato de manter, mas torna seu código um pouco melhor. 

O Bryan do CodeClimate, acredita que Concerns deixam a aplicação gorda, mas gordura de código é aquele trecho legado, em desuso ou que ficou depreciado e precisa ser queimado. Concerns são reusáveis, e estão no Rails para serem usados, e quando bem aplicados, até emagrece. 

O Ryan (RailsCast) também não é muito fã de módulos em geral e listou os contras em um [gist](https://gist.github.com/ryanb/4172391). São pontos interessantes discutíveis.

Achei que ia conseguir entrar em Service Objects, mas fica para o próximo post.


__Referências__
<br> [http://37signals.com/svn/posts/3372-put-chubby-models-on-a-diet-with-concerns](http://37signals.com/svn/posts/3372-put-chubby-models-on-a-diet-with-concerns)
<br>[http://api.rubyonrails.org/classes/ActiveSupport/Concern.html](http://api.rubyonrails.org/classes/ActiveSupport/Concern.html)
<br> [http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/](http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/)
<br>[http://joshsymonds.com/blog/2012/07/01/rails-concerns-i-starting-with-redcarpet/](http://joshsymonds.com/blog/2012/07/01/rails-concerns-i-starting-with-redcarpet/)