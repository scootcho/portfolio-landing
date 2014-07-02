---
layout: post
title: "Codecademy JavaScript"
date: 2014-07-02 22:38:09 +0800
comments: true
categories: [javascript, codecademy, time]
---

4 hrs

Knowing that JavaScript will be extremely useful in combination with Ruby on Rails. I Codecademy's <a href="http://www.codecademy.com/tracks/javascript" target="_blank">JavaScript Track</a> today. It was especially fun building the rock, paper and scissors game.

Scottbot vs Computer, who will win!?

<!-- more -->

```ruby rock, paper scissors game

var scottbotChoice = prompt("Do you choose rock, paper or scissors?");

var computerChoice = Math.random();
if (computerChoice < 0.34) {
 computerChoice = "rock";
} else if(computerChoice <= 0.67) {
 computerChoice = "paper";
} else {
 computerChoice = "scissors";
} console.log("Computer: " + computerChoice);

var compare = function(choice1, choice2){
    if(choice1 === choice2){
        return "The result is a tie!"
    }
    if(choice1 === "rock"){
        if(choice2 === "scissors"){
            return("rock wins!");
        }
        else if (choice2 === "paper"){
            return "paper wins!";
        }
    }
    if(choice1 === "paper"){
        if(choice2 === "scissors"){
            return"scissors wins!";
        }
        else if (choice2 === "scissors"){
            return "scissors wins!";
        }
    }
    if(choice1 === "scissors"){
        if(choice2 === "rock"){
            return"rock wins!";
        }
        else if (choice2 === "paper"){
            return "scissors wins!";
        }
    }    
}

compare(scottbotChoice, computerChoice)

```