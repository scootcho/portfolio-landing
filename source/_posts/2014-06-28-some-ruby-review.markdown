---
layout: post
title: "Some Ruby Review"
date: 2014-06-28 21:35:24 +0800
comments: true
categories: [programming, ruby, review, time]
---

2.5 hrs

I have signed up for a new online Ruby curriculum which will start next week. We'll be building 10 projects in 10 weeks. I figure I'd review some materials from Codecademy's [Ruby Track][rubytrack] I've completed [last month][badges].


I spent about 2.5 hours review part of the material and will continue the review tomorrow.

Here are some review snipets:


```ruby How do you sort a word by individual character?
"sortme".chars.sort
=> ["e", "m", "o", "r", "s", "t"]
```

<!--more-->

```ruby Split name to firstname and lastname with one-line %}
name = "Scott Yu"

firstname, lastname = name.split
=> ["Scott", "Yu"]
firstname
=> "Scott"
lastname
=> "Yu"
name
=> "Scott Yu"
```

```ruby true or false %}
1.eql?(1.0)

=> false.

#True if the receiver and argument have both
#the same numeric type and equal values.
```

```ruby set default hash value %}
hash = Hash.new("notnil")

hash
=> {}

hash[5]
=> "notnil"
```

[rubytrack]: http://www.codecademy.com/tracks/ruby
[badges]: http://www.codecademy.com/users/scottyu/achievements