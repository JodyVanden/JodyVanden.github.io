---
layout: post
title:  "How to use Jekyll as a Github Blog"
date:   2017-12-04 16:26:00 +1100
categories: jekyll github newbee
---

I am writting this post as I am new to Jekyll and wanted to share how to set it
up in the Github environment. Apparently as a newbe in the code industry it is
recommanded to have a blog to show out what am I doing and what did I do during
those long months of job hunt.

this is my first post to show it

You need firstly to install on your computer the gem Jekyll
for mac `gem install jekyll bundler`
for linux `sudo gem install jekyll bundler`

there are two ways of creating a blog on Jekyll.

First is you have not repository and you can use the bundler gem jekyll to do that <br/>
`jekyll new <PATH>` <br/>
Or you already have a repo and want to install it inside <br/>
`jekyll new . --force`



To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
