---
layout: post
title:      "ActiveRecord Scopes"
date:       2018-09-20 17:41:29 -0400
permalink:  activerecord_scopes
---


While completing my Ruby on Rails project assessment, I learned that I had not completed one tiny requirement: including an ActiveRecord scope. The reason I had not completed it was because I didn’t have a clear understanding of the topic. See, I had thought I completed the requirement, but I was wrong. I decided after learning about it and implementing it in my project, that I’d write a nice little blog post discussing what an ActiveRecord scope is and why it is used. So, let’s get started. 

**What is a scope?**

A scope is a method representing the narrowing of a database query. A scope allows a developer to pick out “commonly-used queries which can be referenced as the method calls on the association objects or models.” A scope method ultimately returns an `ActiveRecord::Relation` object that allows other methods to be called on it, which allows it to be chainable. 

**Where do I put a scope method?**

A scope method should be placed within the model. Here are two examples of how it should be formatted:

```
class Post < ActiveRecord::Base 
  scope :published, where(status: ‘published’)
  scope :draft, -> {where(status: ‘draft’) }
end
```

**Are scopes similar to class methods?**

Yes! Internally, ActiveRecord turns a scope into a class method. So, ultimately, a scope is a class method. If we were to turn one of the previously used examples into it’s mirrored class method, it would look like this:

```
def self.published 
  where(status: ‘published’)
end
```

**Why use a scope over a class method?**

From what I have read, it seems like using scopes versus class methods is all based on personal preference. I believe that scopes would be best used when the logic is small and simple, and I would use class methods when the logic is more complex. However, I do believe that the chainable quality of a scope is incredibly useful and when put in a circumstance where chaining would be needed, a scope should be used over a class method. Ultimately, as long as the code is clear, concise, consistent, and working properly, it is up to the developer which one they would prefer to use. 

### Resources
[Active Record Scopes vs Class Methods](http://blog.plataformatec.com.br/2013/02/active-record-scopes-vs-class-methods/)
<br>
[Should You Use Scopes or Class Methods?](https://www.justinweiss.com/articles/should-you-use-scopes-or-class-methods/)
<br>
[ActiveRecord Query Interface](https://guides.rubyonrails.org/active_record_querying.html)
<br>
[Scope](https://apidock.com/rails/ActiveRecord/NamedScope/ClassMethods/scope)
