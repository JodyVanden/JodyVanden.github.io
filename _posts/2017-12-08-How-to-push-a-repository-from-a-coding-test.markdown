---
layout: post
title:  "How to push to your repo a repository from a coding test"
date:   2017-12-08 11:57:00 +1100
categories: github newbee
---

Who never had a coding test to do from a big company to be able to check out if you are able to code? I had to do that for a big company. My problem was that they send me a repository per email with all git and github already initialized. Meaning I was not able to send it out to my own repository on Github and show to the world what I was able to do.

I will show you how to do change that, and don't worry it's really simple.

<h1>1- What is my problem</h1>

When I was on my folder and tried to push it to my repository on Github with the command `git push origin master` I got the response

{% highlight ruby %}
$ git push origin master
ssh: connect to host git.rea*** port 22: Operation timed out
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
{% endhighlight ruby %}

This meant that my folder was still connected to the previous owner.

<h1>2- How to check that?</h1>

To check the owner of the repository simple check it out with this command <br>
`$ git remote -v` <br>

here is my result:
{% highlight ruby %}
origin  git@git.rea***:recruiting/toy-robot.git (fetch)
origin  git@git.rea***:recruiting/toy-robot.git (push)
{% endhighlight ruby %}

<h3>3- how to fix this?</h3>
  <h3>3-1 Trouble to fix it!</h3>
I tried to fix it by simple adding my repo on the remote like this: <br>
{% highlight ruby %}
$ git remote set-url origin git@github.com:JodyVanden/toyrobot.git

$ git remote -v
origin  git@github.com:JodyVanden/toyrobot.git (fetch)
origin  git@github.com:JodyVanden/toyrobot.git (push)
{% endhighlight %}

Then I created the repository on Github with <br>
`$ hub create` <br>

but this did not really worked out for me with an error: <br>
{% highlight ruby %}
$ git push origin master
ERROR: Repository not found.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
{% endhighlight %}

<h3>3-2 How I did to fix it</h3>

I finally found out that I had to remove the previous remote with this command line: <br>
`$ git remove rm origin`<br>

and then add my remote with creating a folder on github <br>
`hub create`<br>

You can then double check if everything is ok <br>
`$ git remote -v`

{% highlight ruby %}
$ git remote -v
origin  git@github.com:JodyVanden/toyrobot.git (fetch)
origin  git@github.com:JodyVanden/toyrobot.git (push)
{% endhighlight %}

Everything is looking good. <br>

I just need to push it to my Github with <br>
`git push origin master`

{% highlight ruby %}
Counting objects: 375, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (333/333), done.
Writing objects: 100% (375/375), 39.99 KiB | 356.00 KiB/s, done.
Total 375 (delta 140), reused 21 (delta 5)
remote: Resolving deltas: 100% (140/140), done.
To github.com:JodyVanden/toy-robot.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
{% endhighlight %}

some links where I found the infos:
[Stackoverflow][stackoverflow] / [Stackoverflow 2][stackoverflow 2] / [Githubhelp][github help]

[stackoverflow]: https://stackoverflow.com/questions/18200248/cloning-a-repo-from-someone-elses-github-and-pushing-it-to-a-repo-on-my-github

[stackoverflow 2]: https://stackoverflow.com/questions/6116548/how-to-tell-git-to-use-the-correct-identity-name-and-email-for-a-given-project

[github help]: https://help.github.com/articles/changing-a-remote-s-url/
