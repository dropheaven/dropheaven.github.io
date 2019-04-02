---
layout: post
title:      "Rails JS Project"
date:       2019-04-02 01:30:10 +0000
permalink:  rails_js_project
---


I had a great time working on adding JavaScript to my existing Rails app, and I now feel much more comfortable traversing and manipulating the DOM with JS after completing this project. I ended up using vanilla JavaScript instead of jQuery as I didn’t want to rely on a library before understanding how to achieve similar results without one. 

Most of the requirements for this project were met without too much of a struggle, but I did run into a wall when trying to create a resource and submitting it through JS. My application has a comment section and I was trying to post comments dynamically but every time I’d submit a comment, Rails would return this error message:

```
ActionController::InvalidAuthenticityToken (ActionController::InvalidAuthenticityToken)
```

The error message is clear enough,  Rails is expecting an authenticity token and I had no clue how to produce one. Form_for and form_tag spoiled me by providing this and now without them I was lost. Here’s my fetch request that kept producing this error:

```
fetch('/comments', {
  method: 'post',
  body: JSON.stringify({ id: userId, book_id: bookId, content: commentContent })
})
.then ....

```

So, I starting googling around and thankfully came across this Medium post: [Sending POST requests in Rails 5.1 without jQuery – Actualize – Medium](https://medium.com/actualize-network/sending-post-requests-in-rails-5-1-without-jquery-ff89f6f80487) I could not have gotten this to work without this resource. In this post, the author explains that if you’re using the fetch API, then you’re responsible for providing the authenticity token. Thankfully, Rails provides a helper function Rails.csrfToken() that can grab the token. Heres’ my working fetch request using this method:

```
fetch('/comments', {
  method: 'post',
  body: JSON.stringify({ id: userId, book_id: bookId, content: commentContent }),
  headers: {
    'Content-Type': 'application/json',
    'X-CSRF-Token': Rails.csrfToken()
  }
})
```

And that's about it. All in all, this was a great learning experience and I look forward to going back to this app and adding more features as well as refactoring parts of it. On to React!
