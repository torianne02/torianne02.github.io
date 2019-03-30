---
layout: post
title:      "Protecting Your API Keys - Rails"
date:       2019-03-30 17:30:34 +0000
permalink:  protecting_your_api_keys_-_rails
---


From needing to hide API keys to app authorization keys and secrets, dotenv is the gem you want to use in order to protect your projects credentials. As a developer, you don’t want your personal project credentials to be used by those who fork or clone your project. 

API keys are vulnerable, as most API’s require them to allow access for each request they receive. Here are a few reasons to protect API keys:

* Some API’s only allow you to make so many API calls a day/month/year before making you pay money to continue to use the API. 

* There are API’s that limit the amount of calls you can make in a specific time period.

* API keys can be suspended due to use outside of their terms of service.

This is where dotenv comes into play. What does dotenv do exactly? As a gem, “dotenv loads variables from a .env file into ENV when the environment is bootstrapped.” In layman’s terms, dotenv takes variables that we place in a .env file and makes them accessible by calling `ENV[‘’]`. We protect this .env file and the keys inside it by placing it in our .gitignore file. Now, let’s get into the installation and usage instructions for dotenv.

## Installation 

Add this line to your application’s Gemfile:

`gem ‘dotenv-rails’`

And then run `bundle install` in your terminal.

Create your .env file in the root of your project directory. You could do this manually or by running `touch .env` in your terminal.

## Usage

Write your credentials in .env

`EXAMPLE_API_KEY=YOURAPIKEYHERE`

Upon your application loading, the variables in this file will be available in ENV. You can call them by using:

`ENV[“EXAMPLE_API_KEY”]`

Lastly, you don’t want to forget to protect those API keys. Make sure to include .env in your .gitignore file!!!!

There you go, you are all set to protect your API keys by using the dotenv gem.

Happy coding!

### Resources

[API Key Protection](https://www.approov.io/api-key-protection.html)

[The Simplest and Powerful Ruby Gem — Dotenv](https://medium.com/coffee-and-codes/the-simplest-and-powerful-ruby-gem-dotenv-74d64cbc5d5d)

[Dotenv Documentation](https://github.com/bkeepers/dotenv)



