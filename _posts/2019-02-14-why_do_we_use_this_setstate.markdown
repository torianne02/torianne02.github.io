---
layout: post
title:      "Why Do We Use `this.setState()`?"
date:       2019-02-14 22:56:06 +0000
permalink:  why_do_we_use_this_setstate
---


During my React assessment I was asked the question why we should use `this.setState()` and not just `this.state.KEY = VALUE`. This question stumped me. In my mind I thought that we were supposed to use `this.setState()` because it actually updates the state, meanwhile `this.state.KEY = VALUE` doesn’t. That just isn’t the case. 

I was also thinking that we should never try to update the state by utilizing `this.state.KEY = VALUE` because we should consider `this.state` immutable. I had read that somewhere, but I never even bothered to look deeper into it, to find out why we should consider it to be immutable. I couldn’t explain my ‘why’ to the instructor because I didn’t even know. 

So, here I am writing a blog post about it so that hopefully this can help myself, as well as someone else, gain a better understanding of the topic! Here we go!

According to the official React.js documentation, “Treat `this.state` as if it were immutable.” See, I knew I had seen it somewhere. So, let’s dive deeper into why this is the case. 

The most important ‘why’ that I could find on this topic, at least in my opinion, is that when we use `this.state.KEY = VALUE`, while it may update the state, it does not re-render the component. Here is an example:

Let’s say you wanted to add a button to a site and every time it was clicked you wanted the counter that is displayed to increase. 

```
import React, { Component } from 'react';

class Count extends Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 0
    }
  }

  handleOnClick = event => {
    let num = this.state.counter + 1

    this.state = {
      counter: num
    }
  }

  render() {
    return (
      <div>
              <button onClick={this.handleOnClick}>Like</button>
              { this.state.counter }
      </div>
    )
  }
}

export default Count
```

Every time this button is clicked, the state will increase every time, the only problem is, the user wouldn’t see it. They would think that the button is broken because what is displayed will remain 0. This is because the component isn’t re-rendering every time the button is clicked.

Now, if we were to write our code using `this.setState()`, the counter displayed on the page will actually change every time it is clicked. 

```
  handleOnClick = event => {
    let num = this.state.counter + 1

    this.setState = {
      counter: num
    }
  }
```

Why is this, you may ask? It’s because `this.setState()` synchronously updates `this.state` and re-renders the component. According to the official React documentation, “`setState()` enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state.” 

Another great thing to keep in mind in regards to this topic is that if you utilize the `this.state.KEY = VALUE` and then use `setState()` afterwards, it “may replace the mutation you made.” This would mean you lost what you were trying to store into state and that isn’t something any of us wants to happen to our code! 

I don’t know about you, but I now feel like I have a much better understanding of why we should be using `setState()` and not `this.state.KEY = VALUE`. There are other reasons as to why this is the case, but I’ll leave that up to you to explore! 

### Resources
[React.Component](https://reactjs.org/docs/react-component.html#setstate)
<br><br>
[State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

