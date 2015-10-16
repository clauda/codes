title: Rails Dia-a-Dia #1
date: 2012-11-08 12:19:00
tags: [rails]
---

Métodos obscuros...


```record.toggle :boolean_attribute``` <br>
troca chave true/false de um campo booleano  [api] [1]


```record.clone``` <br>
cria um novo registro de com os mesmos valores do objeto clonado #damn! [api] [2]


```record.touch``` <br>
atualiza o campo update_at/on com a data/hora atual  [api] [3]


```record.reload``` <br>
atualiza os campos de acordo com o banco  [api] [4]

[1]: http://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-toggle
[2]: http://api.rubyonrails.org/classes/ActiveResource/Base.html#method-i-clone
[3]: http://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-touch
[4]:  http://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-reload
