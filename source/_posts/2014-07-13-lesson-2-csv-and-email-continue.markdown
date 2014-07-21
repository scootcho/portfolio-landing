---
layout: post
title: "Lesson 2: CSV &amp; Email - Continue"
date: 2014-07-12 13:51:09 +0800
comments: true
categories:  [makeitwithcode, codecademy, ruby, JavaScript, time]
---

5 hrs

I finished the [JavaScript Track][track] today. Woot! Check out my [badges][badges]! The final project was to build a cash register that can "scan" different items and quantities then calculate the total amount. It was interesting to use the ```add``` method in the ```scan``` method within the same object. A nested function:

```javascript Cash Register
var cashRegister = {
    total:0,
    lastTransactionAmount: 0,
    add: function(itemCost){
        this.total += (itemCost || 0);
        this.lastTransactionAmount = itemCost;
    },
    scan: function(item,quantity){
        switch (item){
        case "eggs": this.add(0.98 * quantity); break;
        case "milk": this.add(1.23 * quantity); break;
        case "magazine": this.add(4.99 * quantity); break;
        case "chocolate": this.add(0.45 * quantity); break;
        }
        return true;
    ),
    .
    .
    .
};

cashRegister.scan('eggs',2);
cashRegister.scan('milk',3);

// Show the total bill
//toFixed, number into a string, keeping only two decimal
console.log('Your bill is '+cashRegister.total.toFixed(2));

```

<!--more-->

<br/>
I also came back around to work on my [MakeItWithCode][miwc] assignment. [Last HW][lesson2] I used the mailgun gem to send myself an email. The goal this time is to combine powers from twitter, mailgun, and csv gems. To send myself an email attached with twitter seach results in a spreadsheet!



After figuring out how to create and send a csv file through MailGun, I was left with working out how to put them together.



Instead of sending hard-coded info like this: 

```
CSV.open("my_results.csv", "wb") do |csv|
  csv << ["firstname", "lastname", "phone", "email"]
  csv << ["scott", "yu", "888-8888", "scott@robots.com"]
end

```

I need to search the twitter feed and put the result in a CSV file. Which means, I can't just use the above example as the search results will all be put in a single row because of the ```csv << []``` iteration.

What I need is a nested iteration that will first open a CSV file and write the results line by line into the file.

```ruby 
CSV.open("tweet_result.csv", "wb") do |csv|
    client.search("learn to code", :result_type => "recent").take(10).each do |tweet|
        csv << [tweet.text]
    end
end

```

<br />

Here is the completed script :)

```ruby twitter_spreadsheet_email.rb
require 'mailgun'
require 'csv'
require 'twitter'


client = Twitter::REST::Client.new do |config|
  config.consumer_key    = "xxxxxxxxxxxxxxxxxx"
  config.consumer_secret = "xxxxxxxxxxxxxxxxxx"
end


CSV.open("tweet_result.csv", "wb") do |csv|
    client.search("learn to code", :result_type => "recent").take(10).each do |tweet|
        csv << [tweet.text]
    end
end

tweets = File.open("tweet_result.csv")


Mailgun.configure do |config|
  config.api_key = 'private-API-key-XXXXXXXXXXXXXXXX'
  config.domain  = 'sandbox12345.mailgun.org'
end

@mailgun = Mailgun()

parameters = {
  :to => "scott@robot.com",
  :subject => "Email from a robot",
  :text => "Beep beep...beep..keep programming awesome stuff! Btw, NSA is watching!!",
  :from => "scott@sandbox12345.mailgun.org',
  :attachment => File.new(tweets)
}
@mailgun.messages.send_email(parameters)

```

Woot! I got the tweets attachment in my email!

{% img center /images/posts/tweetcsv.png %}


[track]: http://www.codecademy.com/tracks/javascript
[badges]: http://www.codecademy.com/users/scottyu/achievements
[miwc]: https://www.makeitwithcode.com
[lesson2]: /blog/2014/07/12/lesson-2-csv-and-email/