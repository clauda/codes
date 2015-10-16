title: Rails Dia-a-Dia #2
date: 2013-01-04 05:07:00
tags: [rails, serializer]
---

```serialize(attr_name, class_name = Object) ```

"Se você tem um atributo que precisa ser salvo no banco como um objeto, especifique o nome do atributo usando o método ```serialize``` para fazê-lo automaticamente. A serialização é feita através de YAML"


	class User < ActiveRecord::Base
  		serialize :preferences
	end


```class_name``` é opcional.


[api](http://api.rubyonrails.org/classes/ActiveRecord/AttributeMethods/Serialization/ClassMethods.html#method-i-serialize)