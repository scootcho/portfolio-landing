---
layout: post
title: "Meteor Learning Lesson2"
date: 2014-07-26 13:08:43 +0800
comments: true
categories: [agile code camp, meteorjs, javascript, code, time]
---

Completed Lesson 2 of the [Meteor Learning Playlist][playlist]. Below were some of the challenges I encountered and work arounds.


Problem: views did not render properly, instead of the views, it was rendering "[object Object]" in its place. After some digging around and help from people, it turns out that `Meteor.Router` is deprecated.

So instead of 

`mrt add router`

do

`mrt add iron-router`

<!--more-->

Also replace the code associated with the old router:


Instead of 

```javascript
Meteor.Router.add({
    '/':'homepage',
    '/calendar':'calendar'
})
```

use this

```javascript
Router.map( function () {
  this.route('homepage', {
  	path: '/'
  });
  this.route('calendar');
});
```

Views were rendering fine after the above update.

There is also issue with the Modal, when the calendar is clicked, there were no popups. I'll update when I resolve this issue.

Cheers!





[playlist]: https://www.youtube.com/playlist?list=PLKfAG4yMwKkRT4SVt_j04AnZSKcdYPFgx