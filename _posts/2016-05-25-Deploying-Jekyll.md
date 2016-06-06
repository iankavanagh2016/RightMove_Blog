---
layout: post
title:  "Deploying our blog"
date:   2016-05-25
tags:  [jekyll, deployment, GitHub pages, Git]
---
Once we finished building our Jekyll blog site, we needed to decide where and how we wanted to deploy it.
Because Jekyll is so tightly integrated with GitHub Pages, it was a natural starting point for deploying this blog.
The Jekyll documentation has a specific section specifically on [deployment methods](http://jekyllrb.com/docs/deployment-methods/ "deployment methods")

As a prerequisite , ensure you have Git installed locally - choose one of the many [Git gui client's](https://git-scm.com/downloads/guis).
The first time, you will need to do the following at the command line prompt, using your GitHub details.

{% highlight bash %}
C:\blog>git config –global user.name “Your Name
C:\blog>git config –global user.email “Your email address”
{% endhighlight %}

Sign into [GitHub](https://github.com/) using your details and create a `'New repository'`.
Stick with the defaults as this blog will be built locally.
Once we established a project repository for the blog, we needed to connect our local development directory to it,
and once these are connected, we could then deploy your site to GitHub and start blogging.
Back on the command prompt navigate to the directory that contains the blog. Type

{% highlight bash %}
C:\blog>git init
{% endhighlight %}

This will initialise the directory as a Git repository.
github_pages will be our default the we are going to use, to refer to as the remote repository , the https is the address of the remote repository )

{% highlight bash %}
C:\blog>git remote add github_pages https://github.com//github.com/iankavanagh2016/right_move.git
{% endhighlight %}

Verify that the address is correct.

{% highlight bash %}
C:\blog>git remote -v
{% endhighlight %}

We created a project page subdirectory, rather than an organisation page,  so we had to update the baseurl in our `_config.yml` file to represent this.
This will also us to resolve the site url.

As this blog uses pagination, you may get an error like
`you appear to have pagination turned on, but you haven't included the jekyll-paginate gem. Ensure you have gems: [jekyll-paginate] in your configuration file.`, when attempting to launch the website.
This can be resolved by running the following at the command prompt.

{% highlight bash %}
C:\blog>gem install jekyll-paginate
{% endhighlight %}


# Uploading the  blog

At this stage we have created a gh-pages branch, but have as yet, completed no stages or commits. Next we switch from the master branch to
whatever branch we want, `orphan` will ensure that it is separate to the master branch.
The website and the application don't need to be tracked together. We have switched to a new branch `'gh-pages'`

{% highlight bash %}
C:\blog>git checkout --orphan gh-pages
{% endhighlight %}

Now we add / stage all files to be committed and then commit.

{% highlight bash %}
C:\blog>git add -A
C:\blog>git commit -a -m "Initial commit"
{% endhighlight %}

All that was left to do was push the blog up to the remote repository from the local repository and let GitHub build the blog.

{% highlight bash %}
C:\blog> git push github_pages gh-pages
{% endhighlight %}

It may ask you the first time for your GitHub password and username, confirm and push all the files up.
Browse back to the repository and refresh the page and you will see the actual blog.
Click on Setting and it will give a check-mark if the site is published and an url to the live site.

# Updating a live GitHub site

Although our Jekyll site is currently live and online, you're still going to want to develop and test locally before you push your content up.
Since we've modified our base URL however, this can be a little bit of a problem.
If we want to continue developing locally, and make sure that we can preview the blog locally before we push the content online,
we need to start the local web-server as follows. This command only makes the change locally, it doesn't update any hosted content.

{% highlight bash %}
C:\jekyll serve --baseurl ''
{% endhighlight %}

This will indicate any new files that have changed since the last commit.

{% highlight bash %}
C:\blog>git status
{% endhighlight %}

Add all un-tracked files, commit and push to the remote repository.

{% highlight bash %}
C:\blog>git add -A
C:\blog>git commit -a -m "add a comment indicating what files are to be changed"
{% endhighlight %}


{% highlight bash %}
C:\blog>git push github_pages gh-pages
{% endhighlight %}