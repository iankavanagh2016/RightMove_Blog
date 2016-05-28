---
layout: post
title:  "Identifying Datasets and API's"
date:   2016-05-20
tags: [Dataset, web scraping, beautiful Soup, urllib, api]
---
One of the first tasks that needs to completed is the identification of potential dataset's and API's that will be required to produce a viable product.

Property prices can be obtained from either the [Residential Property Price Register](https://www.propertypriceregister.ie/website/npsra/pprweb.nsf/page/ppr-home-en)
or [Property Price Register Ireland](http://propertypriceregisterireland.com/). We initially looked at `Webscraping tools` such as `Beautiful Soup`, to scrape the information, but then identified that the
same information could be readily pulled using a simple urllib request. This .csv data could then be manipulated by Python package's such as `Pandas` - a powerful Python data analysis toolkit.

{% highlight python %}
import csv
import urllib.request
response = urllib.request.urlopen("https://www.propertypriceregister.ie/website/npsra/pprweb.nsf/PPRDownloads?OpenForm&Seq=1&File=PPR-2016.csv&County=ALL&Year=2016&Month=ALL").read()
print(response)
{% endhighlight %}

While we agreed that we would not pull specific property information from [daft](http://www.daft.ie/) or [myhome](http://www.myhome.ie/), daft does provide developers an [daft.api](http://api.daft.ie/gettingstarted/) to help them build tools and websites.
Statistics such as sales, rentals etc., number of houses available for sale in an area would be available.  A request has been made to see if they will supply us with an API, and their support staff are currently reviewing it.
.

... more to follow.



