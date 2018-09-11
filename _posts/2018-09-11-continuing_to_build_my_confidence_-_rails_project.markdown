---
layout: post
title:      "Continuing to Build my Confidence - Rails Project"
date:       2018-09-11 19:57:04 +0000
permalink:  continuing_to_build_my_confidence_-_rails_project
---

For the rails section portfolio project, I decided I would create a beer log called PintTrackr. This Ruby on Rails web application allows a user to create an account, login, and logout. It also allows a user to create an account and sign in through Facebook using the OmniAuth gem. PintTrackr gives the user the ability to add new beers that they have tried throughout the years. It also allows the user to edit these beers and delete them. 
Through the creation of a beer, the user either creates a new brewery or adds the beer to an existing brewery.  This is completed through a nested form that provides nested params. The nested params are set up as: 

```
def beer_params
  params.require(:beer).permit(
    :name,
    :beer_type,
    :ibu,
    :abv,
    :user_id,
    brewery_attributes: %i[name location]
  )
end 
```

The aspect of nested forms and nested params was something new for me and was quite difficult to get working. I was making the mistake of not passing the nested params through correctly in order to create or find the brewery. This is what I was doing:

```
def create 
  @brewery = Brewery.find_or_create_by(params[:brewery_attributes])
  …
end 
```

When I should have been doing this:

```
def create 
  @brewery = Brewery.find_or_create_by(beer_params[:brewery_attributes])
  …
end 
```

It took me a few tries to figure out exactly what I was doing incorrectly, but I finally figured it out after a lot of `pry` sessions! It always feels silly when you realize you have a spelling error, syntax error,  or you’re just passing through the wrong variable. 

**The more projects that I work on, the more excited I get about this profession.** It becomes easier and easier to discover the bugs within my projects on my own. It is becoming easier to navigate `rails console` and `pry` to discover exactly where my bugs are. It’s becoming easier to figure out the right phrases to use when googling a problem that I am having or code that I am not understanding. It is becoming easier to ask questions in Slack. And, ultimately, it is becoming easier to feel **confident** in my coding skills. 
