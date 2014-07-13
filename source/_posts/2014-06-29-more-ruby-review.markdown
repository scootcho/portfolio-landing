---
layout: post
title: "More Ruby Review"
date: 2014-06-29 23:30:50 +0800
comments: true
categories: [programming, ruby, review, time]
---

5 hrs

Finished reviewing Codecademy's [Ruby Track][rubytrack] today.

Here are some more snippets:

```ruby use proc and assign a variable named 'cube' that will cube an array of numbers
cube = Proc.new { |x| x ** 3 }

[1, 2, 3].collect!(&cube)
=> [1, 8, 27]

[4, 5, 6].map!(&cube)
=> [64, 125, 216]
```

<!--more-->

```ruby Create a program that will keep track of movie ratings.

movies = {
  Memento: 3,
  Primer: 4,
  Ishtar: 1
}

puts "What would you like to do?"
puts "-- Type 'add' to add a movie."
puts "-- Type 'update' to update a movie."
puts "-- Type 'display' to display all movies."
puts "-- Type 'delete' to delete a movie."

choice = gets.chomp.downcase

case choice
when 'add'
	 puts "What movie do you want to add?"

	 title = gets.chomp
	 
	 if movies[title.to_sym].nil?
	   puts "What's the rating? (Type a number 0 to 4.)"
	   rating = gets.chomp
	   movies[title.to_sym] = rating.to_i
	   puts "#{title} has been added with a rating of #{rating}."
	 else
	   puts "That movie already exists! Its rating is #{movies[title.to_sym]}."
	 end
when 'update'
	 puts "What movie do you want to update?"

	 title = gets.chomp

	 if movies[title.to_sym].nil?
	   puts "Movie not found!"
	 else
	   puts "What's the new rating? (Type a number 0 to 4.)"
	   rating = gets.chomp
	   movies[title.to_sym] = rating.to_i
	   puts "#{title} has been updated with new rating of #{rating}."
	 end
when 'display'
	 movies.each do |movie, rating|
	   puts "#{movie}: #{rating}"
	 end
when 'delete'
	 puts "What movie do you want to delete?"

	 title = gets.chomp

	 if movies[title.to_sym].nil?
	   puts "Movie not found!"
	 else
	   movies.delete(title.to_sym)
	   puts "#{title} has been removed."
	 end
else
	 puts "Sorry, I didn't understand you."
end
```

[rubytrack]: http://www.codecademy.com/tracks/ruby