---
layout: post
title:  "Installing Jekyll"
date:   2016-05-24
tags: [jekyll, Ruby, Ruby Gems, GitHub]
---
Installing Jekyll was a relatively simple process.
There are a number of dependencies and requirements that have to be satisfied first, before we can start installing and using Jekyll.

First, let’s cover what you’ll need to have installed before you can run Jekyll. The [Jekyll installation guide](https://jekyllrb.com/docs/installation/) lists
all of the requirements and has specific steps on how to get Jekyll up and running. It was geared more towards Linux, Unix and Mac OS X installs but
has a link, detailing how to run it on Windows - [you can read more about the process here](http://jekyll-windows.juthilo.com/ "jekyll for windows").

[Ruby](https://www.ruby-lang.org "ruby") and [Ruby Gems](https://rubygems.org/ "ruby gems") were the only requirements. To verify versions post installs, type the following at the command line prompt.

{% highlight bash %}
C:\ruby - v
ruby 2.3.0p0 (2015-12-25 revision 53290) [x64-mingw32]
C:\gem -v
2.5.1
{% endhighlight %}

Once all your dependencies are installed you’re ready to install Jekyll - it’s very straightforward, all you’ll need to do is type the following at the command line prompt. This can take a number of minutes to complete.

{% highlight bash %}
C:\gem install jekyll
{% endhighlight %}

Once you’ve got Jekyll installed you’re ready to start using it! The best way to get a feel on how Jekyll works is to generate a new site and then examine and explore its structure.
So before we even began to build out own blog, we created a new site based on Jekyll's default `bolierplate` site, which is nothing more than a default site.

{% highlight bash %}
C:\jekyll new blog
{% endhighlight %}

From C:\blog type the following into the command line prompt.

{% highlight bash %}
C:\jekyll serve
{% endhighlight %}

This will build the site and also launch a local webserver,so that we can preview it locally. Open up a browser and navigate to localhost:4000

![My First blog]({{site.baseurl}}/images/local_host.jpg)

We have our first generated Jekyll site. We wont go into the specifics on how this blog has been created - the templates used, are obtained from the default Jekyll site,
which was used in conjunction with the [lynda.com](http://www.lynda.com "lynda.com") course *Jekyll for Web Designers*.

Jekyll is a Ruby-based parsing engine that uses [YAML](http://yaml.org/ "YAML"), the [Liquid Templating language](http://liquidmarkup.org/ "liquid"), and [Markdown](http://daringfireball.net/projects/markdown/ "markdown") to assemble content into HTML.
All post in this blog will be written in Markdown.
