title: Rails Dia-a-Dia #3
date: 2013-03-01 06:40
tags: [rails]
---

``` pluck :column_name ```

Do Active Record, ```pluck``` cria uma query direta para uma coluna específica e retorna um array com o resultado. Beauty, han!?

	Person.pluck(:id) # SELECT people.id FROM people
	Person.uniq.pluck(:role) # SELECT DISTINCT role FROM people
	Person.where(:confirmed => true).limit(5).pluck(:id)


[API](http://api.rubyonrails.org/classes/ActiveRecord/Calculations.html#method-i-pluck)