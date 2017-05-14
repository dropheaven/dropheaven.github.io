---
layout: post
title:  BookFinder - My First Ruby Gem
date:   2017-05-12 16:23:49 -0400
---


 Today I completed my first Ruby Gem. It was definitely less stressful than I had anticipated. Leading up to the CLI Data Gem Project I was nervous that I did not have enough knowledge of the structure of a Gem and that this would become a tough roadblock. But thankfully, it wasn’t because Learn provides us with a ton of resources to fall back when starting a project from scratch. After watching the “CLI Data Gem Walkthrough” video I gained some confidence and told myself this was something I could definitely do. 
  
So the obvious first step was to come up with an idea of what I wanted my Gem to accomplish. At first I was coming up blank and couldn’t think of something interesting. So I went on StumbleUpon, hoping I’d come across something. And I did! I stumbled onto a booklist and I thought it would be cool if I could find a Top 100 Booklist and display that on the CLI. Now all I needed was a website that offered a list of the best 100 novels. This is when I came across Times Magazine’s All Time 100 Novels on GoodReads.com, and I knew this would be a great place to start scraping. I wrote two class methods in my Scraper class. The first would handle scraping the entire list and passing each book, author, and a book-link into an array of hashes. Once I was able to find the correct selectors for the first title I was able to get the intended result right away. The second class method would use the book-link to scrape the description of an individual book and this too, worked out relatively fast. 
   
After getting my Scraper class working I moved onto the Book class. Originally, I was thinking of writing an additional Author class but decided it would be of no use in this model as each author would most likely only appear once in the list. The Book class relied on much of the methods learned in Object Oriented Ruby so I won’t go over most of them. The actual method that displays the list in the CLI gave me somewhat of a hard time. I was unable to get my list from displaying duplicates every time the function was called. To fix this I added an if statement to break out of of the method once the index exceeded 99. This worked and allowed me to display the books and authors properly.

Other than the duplicity bug I encountered, the remaining project was enjoyable and something I’d like to do again. Here’s a link to the Ruby Gem if anyone is interested: 

https://github.com/dropheaven/book_finder
 
