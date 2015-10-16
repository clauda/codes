title: URL Amiga
date: 2012-02-24 12:31:00
tags: [rails]
---

overwrite ```to_param``` method on model ...

	def to_param
		"#{self.id}-#{self.title.parameterize}"
	end
