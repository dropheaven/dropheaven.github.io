---
layout: post
title:  "Rails Project"
date:   2017-08-04 20:06:21 +0000
---

   For my Rails project I decided to make a basic forum called Noteworthy. In this forum users are able to create threads on basically whatever they want and have a discussion with other users. When submitting a new thread a user is able to enter a url to link to an article that he or she wishes to share with the community and have a conversation around. 
I started out this project using Devise for authentication and adding a username attribute to the users table. Devise is an extremely helpful gem when creating an authentication interface but it comes at a price, which I learned when trying to add additional attributes to the user table. After writing a migration for the username, migrating and adding a username field in the sign up form I started running into problems. Everytime I submitted this form, I'd get a validation error stating the username field cannot be blank even though it wasn't. After rereading my code and making sure their wasn't any syntax errors I went ahead and googled 'devise adding attributes' and came across a helpful blog post with a solution. Turns out that with Rails 4, mass assignment requires us to explicitely permit parameters and with Devise's magic this is hidden. So to fix this we must add this code our ApplicationController:
```
Class ApplicationController < ActionController::Base
  before_action :configure_permitted_parameters, if: :devise_controller?
	
	protected
	
	def configure_permittted_parameters
	  devise_parameter_sanitizer.permit(:sign_up) { |u| u.permit(:username, :email, :password) }
		devise_parameter_sanitizer.permit(:account_update) { |u| u.permit(:name, :email, :password, :current_password) }
	end
end
```

   I'll admit I don't know what this exactly what this code is doing but from what I can understand is that a before_action method is being used if the devise controller is being called on and that method is adding additional attributes. After getting over this hurdle I was able to complete the authentication aspect of this application.
   My next task was to write a threads and comments migration and associate them to the user model. The associations between these three models are a has many and belongs to. After successfully writing the forms I moved onto the more complex relationship of a many to many between threads and categories. This is where I spend most of my time trying to understand how exactly to write a custom setter method to correctly find or create a category and associate it with the thread. Once I was able to work my way through this problem I spent the remainder of my time relearning bootstrap and implementing it into my app.
	 Overall I learned so much using the Rails framework throughout this section but I understand that I have only scratched the surface and that if I want to use Rails to its true extent I must continue reading up on it and writing more applications with it. 



