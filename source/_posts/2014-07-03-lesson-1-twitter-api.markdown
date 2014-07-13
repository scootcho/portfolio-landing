---
layout: post
title: "Lesson 1: Twitter API"
date: 2014-07-03 10:38:17 +0800
comments: true
categories: [programming, ruby, makeitwithcode, time]
---

2 hrs

Today I received the first lesson from the [MakeItWithCode][miwc] team. The lesson briefly covers some basics for beginners such as linux commands and run `bundle` to install Ruby gems. But the emphasis of this course is to build things so it dives striaght into the [Twitter Ruby Gem][twgem], which I like.


You'll need to signup for a [witter Developer Account][twdev] to access the API. Once that's done, use the keys from the Twitter Developer Account in your code.  

<!--more-->

The first task is to get the first weet from a specified user, in this example, I used my own twitter handle, `scootcho`:


```ruby gets_tweets.rb
require 'twitter'

# Authentication details from twitter, your starting
# point is here: https://dev.twitter.com/apps/new
client = Twitter::REST::Client.new do |config|
  config.consumer_key    = "xxxxxxxxxxxxxxxxxx"
  config.consumer_secret = "xxxxxxxxxxxxxxxxxx"
end

# Get the first tweet of the specified user
puts client.user_timeline("scootcho").first.text
```


Next, print out the tweets to screen:

```ruby gets_tweets.rb

require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key    = "xxxxxxxxxxxxxxxxxx"
  config.consumer_secret = "xxxxxxxxxxxxxxxxxx"
end

# twitter handle to get tweets for
the_twitter_handle = "scootcho"

# go through each tweet and print out the text
client.user_timeline(the_twitter_handle).each do |tweet|
    puts tweet.text
end; nil
```


Pick a Twitter Handle and displays the 10 most recent tweets mentioning "learn to code":

```ruby gets_tweets.rb
require 'twitter'

client = Twitter::REST::Client.new do |config|
  config.consumer_key    = "xxxxxxxxxxxxxxxxxx"
  config.consumer_secret = "xxxxxxxxxxxxxxxxxx"
end
client.search("learn to code", :result_type => "recent").take(10).each do |tweet|
  puts tweet.text
end
```

There are a couple more things I would like to play with the Twitter API based on suggestions:

* Make the script tweet for you
* Try and conduct some more advanced searches using the Twitter query syntax explained <a href="https://dev.twitter.com/docs/using-search" target="_blank">here</a>:

I will follow up with the progress in the future.


[miwc]: https://www.makeitwithcode.com
[twgem]: https://github.com/sferik/twitter
[twdev]: https://dev.twitter.com/apps/new