---
layout: post
title:      "Optimistic REACTion"
date:       2019-02-08 16:00:30 -0500
permalink:  optimistic_reaction
---


After having such a rough time with the Javascript/Rails project, I was really nervous going into this one. I was feeling a little battered after having to complete the project assessment not once, but twice due to not fully understanding the project requirements. For this project, I’ve made sure to double check with multiple people that I am hitting the requirements. I definitely didn’t want a repeat of the Javascript section. With that weight removed from my shoulders, I am incredibly happy with the product that I have made and the process of developing it. 

Like all other projects, I definitely hit my road bumps along the way. One of the biggest problems I encountered while working through my project was incorporating Redux and the `store`. I thought for a while that I had built it wrong and that’s why my Redux Chrome extension wasn’t working. So, I went along building my components manually adding my API `fetch` requests to the containers. Once I realized I worked on everything I could up to the point of **needing** to incorporate Redux, I started Googling. 

I quickly learned that I needed to include `window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()` in the creation of my store in order to use the Chrome extension. As soon as I added that, however, everything broke and again I took to Google to learn that I needed to utilize the Redux tool `compose()`. `Compose` gives you the ability to ‘write deeply nested function transformations without the rightward drift of code.’

With all of that taken care of, I realized that my store was up and running. I was so happy at that moment, because I had stressed about what I could have done wrong in my `actions` and `reducers` files for days! I was already thinking of all the things I could possibly Google to make sure I was doing this correctly within those files. 

That happiness was quickly followed up by frustration because I then realized something else wasn’t working. I kept getting an error similar to `Uncaught TypeError: this.props.data.map is not a function`. I couldn’t use `.map()` on nothing, because that is what I was passing into the component: NOTHING. Silly me!! Here is the incorrect code: 
```
import React from 'react';
import Guest from './Guest';

const GuestList = ( guestList ) =>
  <div className="guest-list">
    { guestList.map(( guest ) => {
      return <Guest
        key={ guest.id }
        name={ guest.name }
        attendees={guest.attendees}
      />
    }) }
  </div>

export default GuestList
```
Can you see what I did wrong? After 3 days of reading common mistakes made in React and Redux projects, tutorials, other projects, etc. (you name it, I looked at it) I decided to turn to the section tech lead to help me.  The problem was resolved within 5 minutes (maybe even shorter). Turns out I wasn’t passing in the prop variable correctly. A tiny little mistake. Here is the correct code: 
```
import React from 'react';
import Guest from './Guest';

const GuestList = ({ guestList }) =>
  <div className="guest-list">
    { guestList.map(( guest ) => {
      return <Guest
        key={ guest.id }
        name={ guest.name }
        attendees={guest.attendees}
      />
    }) }
  </div>

export default GuestList
```
That’s it… `({ guestList })`. All I needed was the curly braces around the prop variable. Completing my project was put off for 3 days due to that tiny mistake. I laughed so hard with the technical lead of the section when he pointed it out. I laughed so hard that I cried. It was such a relief to realize that my logic was overall correct, I just messed up one tiny thing. You could thing “You wasted 3 days, why are you feeling relief?” Well, sure that’s one way to think about it, but I **react** to it in a more optimistic way. 

Overall, the 3 days that I spent reading common mistakes, watching tutorials, and reading official documentation, really helped me gain such a deeper understanding of how React and Redux work. I feel so much more comfortable and confident in my Javascript skills, the React component lifecycle, and the Redux store. 

Bottom line: **this project has been really rewarding**. Happy coding! 

### Resources
[compose(...functions)](https://redux.js.org/api/compose)
