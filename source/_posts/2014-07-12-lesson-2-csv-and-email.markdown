---
layout: post
title: "Lesson 2: CSV &amp; Email"
date: 2014-07-12 13:04:52 +0800
comments: true
categories: [makeitwithcode, ruby, time]
---

2 hrs

I've been waiting to jump back on my [MakeItWithCode][miwc] assignment since I'm now switching between JavaScript and Ruby.

The goal is to use the MailGun gem and write a simple script that can send emails. When I was trying to run `bundle exec ruby send_email.rb` I kept on getting the following error:

{% blockquote %}
$ bundle exec ruby send_email.rb             
                                  
/home/me/.gems/bundler/gems/mailgun-59455c20a860/lib/mailgun/base.rb:80:in `rescue in submit': Domain not found: scott@sandbox2c02f80f848447ae8c30bd6f232d1428.mailgun.org (Mailgun::Error)

from /home/me/.gems/bundler/gems/mailgun-59455c20a860/lib/mailgun/base.rb:69:in `submit'

from /home/me/.gems/bundler/gems/mailgun-59455c20a860/lib/mailgun/message.rb:18:in `send_email'

from send_email.rb:20:in `<main>' 

{% endblockquote %}


Here is my ruby script:

```ruby send_email.rb
require 'mailgun'

Mailgun.configure do |config|
  config.api_key = 'private-API-key-XXXXXXXXXXXXXXXX'
  config.domain  = 'post@sandbox2083412213.mailgun.org'
end

@mailgun = Mailgun()

parameters = {
  :to => "scott.tj.yu@gmail.com",
  :subject => "Email from a robot",
  :text => "Beep beep...beep..keep programming awesome stuff!
  			Btw, NSA is watching!!",
  :from => "scott@sandbox2083412213.mailgun.org"
}
@mailgun.messages.send_email(parameters)
```
What is with the error?

<!--more-->


I know that we're supposed to use the private API key but I tried to swap it with the public one anyway and that didn't work. After carefully examine the error message, I noticed the ```Domain not found:``` message and I noticed that I have used an email address instead of just the domain name (the domain should be the sandbox domain provided by mailugn).

E.g., "sandbox2083412213.mailgun.org". 


```ruby send_email.rb
require 'mailgun'

Mailgun.configure do |config|
  config.api_key = 'private-API-key-XXXXXXXXXXXXXXXX'
  config.domain  = 'sandbox2083412213.mailgun.org'
end
.
.
.
```

After I changed that everything went smoothly! I just sent myself an email warning about the NSA!! 


{% img center /images/emailsn.png %}


What other interesting things are you doing with emailing scripts?

[miwc]: https://www.makeitwithcode.com
