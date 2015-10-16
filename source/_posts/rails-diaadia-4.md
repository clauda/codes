title: Rails Dia-a-Dia #4
date: 2013-09-24 15:05 
tags: [rails]
---

*Esta série bem poderia ser chamada 'Rails mês-a-mês' para fazer jus a frequência de posts. Estou deixando muitas dicas passarem, mas tenha blogar com três projetos! Vamos lá.*

### warn ###
Antes de remover definitivamente um método, com cobertura de testes ou não, podemos ir refatorando gradualmente o código até termos a certeza de que ele poderá ser expurgado do seu código com o build verde. Aplicando um `warn` ao método, lembramos que ele, em breve, não estará mais disponível.

	def your_method
		warn 'message says: this will be deprecated'
		... 
	end


[api](http://api.rubyonrails.org/classes/ActiveSupport/Deprecation/Reporting.html#method-i-warn)