---
layout: post
title:      "Many-to-Many Relationships"
date:       2018-08-29 14:52:22 -0400
permalink:  many-to-many_relationships
---


**Why do we need associations/relationships between models?**
1. Once we begin working with the data, we rely on these relationships between the tables to bring the data together in purposeful ways. 
2. They make operations within our code simpler and easier to use. 

There are many different associations/relationships within ActiveRecord, but this post will concentrate on only a few that are used often . These include, `belongs_to`, `has_many`, `belongs_to_and_has_many`, and `has_many :through`.
<br><br>
**`belongs_to`** association sets up a one-to-one relationship with another model. This indicates that each instance of the declaring model belongs to one instance of the other model. For example, a child can only have one birth mother. This model would look like
```
class Child < ActiveRecord::Base
  belongs_to :mother 
end
```

**`has_many`** association indicates a one-to-many relationship with another model. In this association, each instance of the declaring model has zero or more instances of another model. Building on the previous example, a mother can have many children. This model would look like 
```
class Mother < ActiveRecord::Base 
  has_many :children 
end
```
Most often, you will find this association on the other end of a `belongs_to` association. 
<br><br>
**`has_and_belongs_to_many`** association creates a direct many-to-many relationship with another model, without the need of a intervening third model. For example, a plane having many parts and each part appearing in (belonging to) many planes. The models would look like
```
	class Plane < ActiveRecord::Base 
	  has_and_belongs_to_many :parts
	end
	
	class Part < ActiveRecord::Base 
	  has_and_belongs_to_many :cars
	end
```
Due to the nature of this relationship, a join table is needed. For a normal `has_many` and `belongs_to` association, each model could have it’s own respective table. In this case, a `has_and_belongs_to_many` association creates a third dimension (overlapping section of a Venn diagram) and needs a connecting/join table. This join table should not have a primary key or a model associated with it. 
<br><br>
**`has_many :through`** association creates a many-to-many connection utilizing a third model. In this association, the declaring model matches with zero or more instances of another model through the third model. An example of this association is a doctor who has many patients through their appointments. This also works in the reverse, a patient has many doctors through appointments. The models would look like 
```
	class Doctor < ActiveRecord::Base
	  has_many :appointments
	  has_many :patients, through: :appointments
	end

	class Appointment < ActiveRecord::Base 
	  belongs_to :physician 
	  belongs_to :patient
	end 

	class Patient < ActiveRecord::Base
	  has_many :appointments
	  has_many :physicians, through: :appointments
	end
```
Like the above association, this one requires a join table. Unlike the above, the join table does have a model associated with it (the third model).

### Sources
[Modeling Relationships (Github)](https://github.com/wdi-hk-9/sinatra-activerecord-modeling-relationships-lesson/blob/master/readme.md) 
<br>
[ActiveRecord Associations: Join Tables (learn.co)](https://learn.co/tracks/full-stack-web-development-v6/sinatra/activerecord/activerecord-associations-join-tables )
<br>
[ActiveRecord Associations (Rails Guides)](https://guides.rubyonrails.org/association_basics.html#the-has-many-association) 
<br>
[has_and_belongs_to_many (APIdock)](https://apidock.com/rails/ActiveRecord/Associations/ClassMethods/has_and_belongs_to_many)
