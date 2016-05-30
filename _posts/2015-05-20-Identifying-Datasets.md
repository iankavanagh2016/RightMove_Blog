---
layout: post
title:  "Identifying Datasets and API's"
date:   2016-05-20
tags: [Dataset, web scraping, beautiful Soup, urllib, api]
---
One of the first tasks that needs to completed is the identification of potential Dataset's and API's, that will be required to produce
 a viable product.

Property prices can be obtained from either the [Residential Property Price Register](https://www.propertypriceregister.ie/website/npsra/pprweb.nsf/page/ppr-home-en)
or [Property Price Register Ireland](http://propertypriceregisterireland.com/). We initially looked at  various `Web Scraping` tools, such as
`Beautiful Soup`, to obtain the information, but then identified that the same information could be readily pulled using a simple urllib request.
This .csv data can then be manipulated by Python package's such as `Pandas` - a powerful Python data analysis toolkit and
allow us to display the Average price paid for property in that area, the number of sales,
how the average price paid rates against the national average and possible value change ( Is the area on the up ? )

{% highlight python %}
import csv
import urllib.request
response = urllib.request.urlopen("https://www.propertypriceregister.ie/website/npsra/pprweb.nsf/PPRDownloads?OpenForm&Seq=1&File=PPR-2016.csv&County=ALL&Year=2016&Month=ALL").read()
print(response)
{% endhighlight %}

While we agreed that we would not pull specific property information from [daft](http://www.daft.ie/)
or [myhome](http://www.myhome.ie/), daft does provide
developers a [daft.api](http://api.daft.ie/gettingstarted/) to help them build tools and websites.
Statistics such as sales, rentals etc., number of houses available for sale in an area would be available.
A request has been made to see if they will supply us with an API key, and their support staff are currently reviewing it.
It is possible to scrape additional information from daft without the API key. For example every search on DAFT, always returns the
number of properties available for that specific area. This could be a possible option in the event that we don't receive the API key.

![Daft property details]({{site.baseurl}}/images/daft_details.jpg)

The following information - `Population breakdown` ( Social class and Socio-Economic Groups),`Crime Rates`, `Education`, `Transport` -
will also be beneficial in helping a potential buyer,in making up their minds, on whether a specific area is the one for them.

Many sites provide similar Dataset's that are mainly constructed from the 2011 census data.
The CSO provides numerous Dataset's, that would be valuable to us, such as ones on `'Families'`, `'Housing'`, `'Occupation'`.
All can be freely downloaded in TSV format from the [CSO Dataset site](http://data.cso.ie/datasets/index.html).
The CSO also provides another data source - the [Statbank API](http://www.cso.ie/webserviceclient/).

Another Census / CSO site provides rich [area profiles](http://census.cso.ie/areaprofiles/), though again based on the 2011 census data,
it allows us to view `'Age'`, `'Migration'`, `'Ethnicity and Religion'`, `'Families'`, `'Private Households'`, `'Housing` ( Social Class and Socio-Economic Groups -
professionals, manual skilled, unskilled etc )' information at a 1-Stop shop.

Next we looked at [AIRO](http://airo.maynoothuniversity.ie/) - a census mapping tool. AIRO also provides a Datastore's, making their working data more accessible to the public.
The have thankfully cleaned it up and added extra value to make it as useful as possible.
Data is available in .CSV and .SHP format, and the following Datastore's would be useful to our project.

1. [Social class All_Island Population](http://airo.maynoothuniversity.ie/files/dDATASTORE/all_island/csv/population.csv)
2. [Criminal Offenses at Station Level](http://airo.maynoothuniversity.ie/files/dDATASTORE/crime/garda%20stations/garda_stations.csv)
3. [All Persons - Live Register](http://airo.maynoothuniversity.ie/files/dDATASTORE/swo/csv/all_persons.csv)
4. [Primary Schools](http://airo.maynoothuniversity.ie/files/dDATASTORE/education/csv/primary_schools_2013_2014.csv)
5. [Migration, ethnicity and religion](http://airo.maynoothuniversity.ie/files/dDATASTORE/small_areas/theme_2_small_areas.csv)
6. [Social Class](http://airo.maynoothuniversity.ie/files/dDATASTORE/small_areas/theme_9_small_areas.csv)
7. [Education](http://airo.maynoothuniversity.ie/files/dDATASTORE/small_areas/theme_10_small_areas.csv)

I have noted via an [AIRO tutorial](https://www.youtube.com/watch?v=3sgJO6fmFhQ) ,that AIRO uses these CSV files with Open Street Map (OSM), to create their own interactive maps.

[Open Street Map](https://www.openstreetmap.org/#map=16/53.3851/-6.4251) contains huge amounts of data, which are relevant to people in a particular area, such as roads, railways, restaurants, shops, stations etc.
This would be an alternative to the usual Google API's ( GoogleMaps / Google Places API's )
It's also possible the this information could be extracted and saved in the backend by Python, and then made available to whatever framework ( GoogleMaps / Open Street Map) we decide on in the front end.
There is a detailed wiki page (http://wiki.openstreetmap.org/wiki/Map_Features) that references each of the tags that are freely available.
The following [Android CookBook example](https://androidcookbook.com/Recipe.seam?recipeId=2521) gives a tutorial on how to use OpenStreetMap in an Android Application.
[OSM data for Ireland and Northern Ireland](http://download.geofabrik.de/europe/ireland-and-northern-ireland.html) can be obtained in the event that we decide to use it in our project.

Other various sources reviewed were ...

[DubL:nked](http://dublinked.ie/) also has a large number of Dataset's, with an interesting [Dublin dashboard](http://dublindashboard.ie/pages/index ) but as it is Dublin centric we don't believe it's appropriate.

[Foursquare](https://developer.foursquare.com/overview/) and [TripAdvisor](https://developer-tripadvisor.com/content-api/) would allow us obtain details on local restaurant, attractions and accommodations.

The National Transport Authority have [real time information on various modes of transport](https://data.gov.ie/dataset/real-time-passenger-information-rtpi-for-dublin-bus-bus-eireann-luas-and-irish-rail)
