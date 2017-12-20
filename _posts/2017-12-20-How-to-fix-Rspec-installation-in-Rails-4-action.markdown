---
layout: post
title:  "How to fix Rspec installation in Rails 4 action"
date:   2017-12-20 16:26:00 +1100
categories: rails rspec install trouble
---

I started to read [Rails 4 in action][rails4action] and found the methodologie really good. This book shows us the mechanism of how to code properly. You are in fact in a dev's brain and see how he thinks about everything, which is perfect for people starting to code and how to get the best pratice.

I really recommend you to read this book and don't be passive. Because you will only learn if you are trying to do it by your own!

I am writting this post because I had trouble with my Rspec installation. If you are in a rush, it was because I had the wrong rspec-rails version ...
<h1>I- Rspec installation - trouble shooting</h1>

The book is from 2014 and gems versions are moving. I had an issue when I was trying to install the Rspec on my computer. I followed the infos on the gemfile .... but could not figure out what I had.

This is what I had when I was trying to install Rspec
{% highlight ruby %}
$rails g rspec:install
/Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/railties-4.2.10/lib/rails/railtie/configuration.rb:95:in `method_missing': undefined method `load_defaults' for #<Rails::Application::Configuration:0x00007fde505f7518> (NoMethodError)
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:12:in `<class:Application>'
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:10:in `<module:Ticketee>'
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:9:in `<top (required)>'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:92:in `require'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:92:in `preload'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:153:in `serve'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:141:in `block in run'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:135:in `loop'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:135:in `run'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application/boot.rb:19:in `<top (required)>'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/2.3.0/rubygems/core_ext/kernel_require.rb:55:in `require'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/2.3.0/rubygems/core_ext/kernel_require.rb:55:in `require'
  from -e:1:in `<main>'
{% endhighlight ruby %}

I tried differents ways to install it with bundle exec, because sometimes I found out that it helps if you install it in the bundle environment.
{% highlight ruby %}
$bundle exec rails g rspec:install
/Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/railties-4.2.10/lib/rails/railtie/configuration.rb:95:in `method_missing': undefined method `load_defaults' for #<Rails::Application::Configuration:0x00007fcd04c92e70> (NoMethodError)
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:12:in `<class:Application>'
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:10:in `<module:Ticketee>'
  from /Users/14buijq/Documents/code-jody/JodyVanden/ticketee/config/application.rb:9:in `<top (required)>'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:92:in `require'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:92:in `preload'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:153:in `serve'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:141:in `block in run'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:135:in `loop'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application.rb:135:in `run'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/gems/2.3.0/gems/spring-2.0.2/lib/spring/application/boot.rb:19:in `<top (required)>'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/2.3.0/rubygems/core_ext/kernel_require.rb:55:in `require'
  from /Users/14buijq/.rbenv/versions/2.3.5/lib/ruby/2.3.0/rubygems/core_ext/kernel_require.rb:55:in `require'
  from -e:1:in `<main>'
{% endhighlight ruby %}
<h1>II- How to fix the installation of Rspec in mycase</h1>

I tried to uninstall rspec and the dependencies, researching on all sorts of forums, checked if spring was not the problem... I finally tried to search other projects on Github with the same name. I found one and inspected the gemfile (because I knew this was caused by the Gemfile).
my old gemfile:
{% highlight ruby %}
source 'https://rubygems.org'

git_source(:github) do |repo_name|
  repo_name = "#{repo_name}/#{repo_name}" unless repo_name.include?("/")
  "https://github.com/#{repo_name}.git"
end


# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '~> 5.1.0'
# Use sqlite3 as the database for Active Record
gem 'sqlite3'
# Use Puma as the app server
gem 'puma', '~> 3.7'
# Use SCSS for stylesheets
gem 'sass-rails', '~> 5.0'
# Use Uglifier as compressor for JavaScript assets
gem 'uglifier', '>= 1.3.0'
# See https://github.com/rails/execjs#readme for more supported runtimes
# gem 'therubyracer', platforms: :ruby

# Use CoffeeScript for .coffee assets and views
gem 'coffee-rails', '~> 4.2'
# Turbolinks makes navigating your web application faster. Read more: https://github.com/turbolinks/turbolinks
gem 'turbolinks', '~> 5'
# Build JSON APIs with ease. Read more: https://github.com/rails/jbuilder
gem 'jbuilder', '~> 2.5'
# Use Redis adapter to run Action Cable in production
# gem 'redis', '~> 3.0'
# Use ActiveModel has_secure_password
# gem 'bcrypt', '~> 3.1.7'

# Use Capistrano for deployment
# gem 'capistrano-rails', group: :development

group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  # Adds support for Capybara system testing and selenium driver
  gem 'selenium-webdriver'
  gem 'rspec-rails', '~> 3.2.1'
end

group :test do
  gem 'capybara', '~> 2.4'
end


group :development do
  # Access an IRB console on exception pages or by using <%= console %> anywhere in the code.
  gem 'web-console', '>= 3.3.0'
  gem 'listen', '>= 3.0.5', '< 3.2'
  # Spring speeds up development by keeping your application running in the background. Read more: https://github.com/rails/spring
  gem 'spring'
  gem 'spring-watcher-listen', '~> 2.0.0'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

{% endhighlight ruby %}

I finally found out that the version of Rspec-rails was not compatible with the last rails version. Because I simply remove the version of Rpsec `gem 'rspec-rails'` and I was able to install it with `$rails g rspec:install`

I hope to help those who were in the same trouble as I.

[rails4action]: https://www.manning.com/books/rails-4-in-action
