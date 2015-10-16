title: Evitando COUNT(*) queries com ActiveRecord::CounterCache
date: 2014-02-13 21:17
tags: [rails, active record, counter_cache, cache, ruby]
---

Gravar a informação do tamanho de um relacionamento na tabela é até uma solução trivial para evitar consultas com ```COUNT``` e o ActiveRecord traz um recurso para esta simples estratégia. Sem questionar o mérito dessa solução, vou me limitar a dizer que podemos economizar ai uns... 10 centavos em queries, alguns ```SELECT COUNT(*) whatever``` a menos no log.

Em associações ```belongs_to``` existe a opção ```:counter_cache``` trata ["pode encontrar o número de objetos pertencentes de forma mais eficiente"](http://guides.rubyonrails.org/association_basics.html#counter-cache), guardando e controlando o número de associações relacionadas. 

Considere a implementação:


	class Topic < ActiveRecord::Base

 		belongs_to :subject, counter_cache: true

	end

e

	class Subject < ActiveRecord::Base

		has_many :topics

	end


O counter cache precisa armazenar o número, assim adicionamos o campo, seguindo a convenção ```[association]_counter```, ao objeto a que ela pertence:

	class AddTopicsCountToSubject < ActiveRecord::Migration
		def up
   			add_column :subjects, :topics_count, :integer, default: 0

	    	Subject.all.pluck(:id).each do |result|
	      		Subject.reset_counters(result, :topics)
	    	end
		end

	  	def down
    		remove_column :subjects, :topics_count
  		end
	end

Quando uma associação é incluída ou removida, o [ActiveRecord::CounterCache](http://api.rubyonrails.org/classes/ActiveRecord/CounterCache/ClassMethods.html) dispara métodos como ```increment_counter``` e ```decrement_counter``` para atualizar o campo. Na migration, ```reset_counters```, bem.. parece óbvio aqui.

No console conseguimos notar uma sutil melhora de performance na chamada do método ```.size``` (o método ```.count``` sempre executa ```SELECT COUNT(*)```).

Sem o ```counter_cache```: 

	> Subject.first.topics.size
  		Subject Load (0.2ms)  SELECT "subjects".* FROM "subjects" ORDER BY "subjects"."id" ASC LIMIT 1
   		(2.3ms)  SELECT COUNT(*) FROM "topics" WHERE "topics"."subject_id" = ?  [["subject_id", 1]]
	=> 9

Com o ```counter_cache``` ele consulta diretamente pelo campo:

	Subject.first.topics.size
  		Subject Load (0.1ms)  SELECT "subjects".* FROM "subjects" ORDER BY "subjects"."id" ASC LIMIT 1
	=> 9


Quando precisamos contar o número de vários relacionamentos, essas consultas saem bem mais caras que 10 centavos e  toda ajuda aqui é bem vinda.