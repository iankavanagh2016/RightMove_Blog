---
layout: post
title:  "Deploying Jekyll"
date:   2016-05-25
tags:  [jekyll, deployment, github pages, git]
---
Once we finished building our Jekyll site we needed to decide where and how we wanted to deploy it.
 Because Jekyll is so tightly integrated with GitHub Pages, it was a natural starting point for deploying this blog.
We deployed our blog through GitHub Pages - The Jekyll documentation has a specific section on [deployment methods](http://jekyllrb.com/docs/deployment-methods/ "deployment methods")

Ensure you have git installed locally - choose one of the many [Git GUI Client's](https://git-scm.com/downloads/guis).
The first time, you will need to do the following at the command line prompt, using your github details.

{% highlight bash %}
C:\blog>git config –global user.name “Your Name
C:\blog>git config –global user.email “Your email address”
{% endhighlight %}

Sign into [github](https://github.com/) using your details and create a 'New repository'. Stick with the defaults as this blog will be built locally.
Once you've established a project repository for your Jekyll site, you'll need to connect your local development directory to it,
and once they are connected, we can deploy your site to GitHub and start blogging.
Back on the command prompt navigate to the directory that contains the blog. Type

{% highlight bash %}
C:\blog>git init
{% endhighlight %}

This will initialise the directory as a git repository.
github_pages will be our default the we are going to use, to refer to as the remote repository , the https is the address of the remote repository )

{% highlight bash %}
C:\blog>git remote add github_pages https://github.com//github.com/iankavanagh2016/right_move.git
{% endhighlight %}

Verify that the address is correct.

{% highlight bash %}
C:\blog>git remote -v
{% endhighlight %}

I created a project page subdirectory, rather than an organisation page,  so I had to update the baseurl in our `_config.yml` file to represent this.
This will also us to resolve the site url.


# Uploading the  blog

At this stage we have created a gh-pages branch, but have completed no stages or commits. Next we switch from the master branch to
whatever branch we want, `orphan` will ensure that it is separate to the master branch.
The website and the application don't need to be tracked together. We have switched to a new branch `'gh-pages'`

{% highlight bash %}
C:\blog>git checkout --orphan gh-pages
{% endhighlight %}

Now we add everything , stage everything to be committed and commit.

{% highlight bash %}
C:\blog>git add -A
C:\blog>git commit -a -m "Initial commit"
{% endhighlight %}

All that was left to do was push the blog up to the remote repository from the local repository and let github build the blog

{% highlight bash %}
C:\blog> git push github_pages gh-pages
{% endhighlight %}

It may ask you the first time for your github password and username, confirm and push all the files up.
Browse back to the repository and refresh the page and you will see the actual blog.
Click on Setting and it will give a check-mark if the site is published and an url to the live site.

# Updating a live githib site

Although our Jekyll site is currently live and online, you're still going to want to develop and test locally before you push your content up.
Since we've modified our base URL however, this can be a little bit of a problem.
If we want to continue developing locally, and make sure that we can preview the blog locally before we push the content online,
we need to start the local web-server as follows.

{% highlight bash %}
C:\jekyll serve --baseurl ''
{% endhighlight %}

This command only makes the change locally, it doesn't update any hosted content.

{% highlight bash %}
C:\git status
{% endhighlight %}

This will indicate any new files that have changed since the last commit.

{% highlight bash %}
C:\git add -A
{% endhighlight %}

Add all un-tracked files.

{% highlight bash %}
C:\git commit -a -m "add a comment indicating what files are to be changed"
{% endhighlight %}


{% highlight bash %}
C:\git push github_pages gh-pages
{% endhighlight %}