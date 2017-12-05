---
layout: post
title:  "How to use Jekyll as a Github Blog"
date:   2017-12-04 16:26:00 +1100
categories: jekyll github newbee
---

I write this post to share to people starting a blog on Jekyll how to set it up. I was scrolling around the web and could not find out an easy setup Jekyll. I will try to do it here.

<h2> 1- installation of Jekyll on your computer </h2>

You need firstly to install on your computer the gem Jekyll
for mac `gem install jekyll bundler`
for linux `sudo gem install jekyll bundler`

To be able to display it on `github.io` or also called `github pages` you need
to call your folder the same as your github user. For instance for me I create
a folder `jodyvanden`. Otherwise Github pages will not work.

There are two ways of creating a blog with Jekyll.

First is you have not repository and you can use the bundler gem jekyll to do that <br/>
`jekyll new <PATH>` <br/>
Or you already have a repo and want to install it inside <br/>
`jekyll new . --force`

The jekyll install a bunch of files in this repo. Open with you prefere txt reader
and you will need to first open `./_config.yml` <br/>
change the `title`, `description`, your `email`,your `twitter` and your `github account`

To be able to display your blog on your github pages, you will need to add to your
`Gemfile`:
{% highlight ruby %}
source "https://rubygems.org"
gem 'github-pages', group: :jekyll_plugins
{% endhighlight ruby %}

<h2>2- write your first post</h2>

I am sure you saw that there is a folder `_posts` <br/>
just jump in and check out the first file in there. You will understand that a
blog post is easy and is divided in two

the first part in between the `---` contains the `title`, the type of the article
 `post` the `date` and the `categories` in which this post will be registered


So to add new post, I would suggest to copy the previous post in `_posts` and modify
 it so that you don't have to start from scratch. The convention for the title fo the
 post file is `YYYY-MM-DD-name-of-post.ext`.

<h2>3- Some Jekyll tricks</h2>

One your first blogpost I am sure you will want to find out how to do some cool tricks:
<h3>the snipped</h3>
to be able to write down some short code in a snipped `like this` simply write it down
\`like this\`

<h3>the ruby snipped</h3>
to be able to write down more code from ruby like this:
{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Simply write it in between `{ % highlight ruby %}` and `{ % endhighlight ruby %}`(without space after the curly bracket)

{ % highlight ruby %} (without space after the curly bracket)<br/>
def print_hi(name)<br/>
  puts "Hi, #{name}"<br/>
end<br/>
print_hi('Tom')<br/>
#=> prints 'Hi, Tom' to STDOUT.<br/>
{ % endhighlight %} (without space after the curly bracket)<br/>

<h3>Titles</h3>
I am sure you want to write down in between titles to help your text to be structured<br/>
for example you can write down in between \<h1>title\</h1><br/> until \<h6>title\</h6>

<h3>URL Links</h3>
To be able to write down your prefered links there is nothing easier. It works like a
constant that you define at the bottom of the blog post. <br>
for instance if I want you to check out the [Jekyll docs][jekyll-docs] for more info
I simply write down `[Jekyll docs][jekyll-docs]` <br>
the first one will be the text file which will be displayed and the second will be the
constant at the bottom which looks like this
`[jekyll-docs]: https://jekyllrb.com/docs/home`

<h1>hope this helps some people to start their blog on the Githubpages</h1>
