---
date: 2016-05-08
title: Harvest the front pages of The Gadfly
type: Activities
tags:
  - Python
  - Trove
layout: default_module
status: draft
---

Using tools like the [Trove Newspaper Harvester]({{ site.baseurl }}/docs/trove-newspaper-harvester) you can easily download large quantities of newspaper articles via the Trove API. But what if you want to go further?

In this tutorial we'll learn how to download images of all the front pages of the short-lived South Australian newspaper *The Gadfly*.

![Gadfly covers]({{ site.baseurl }}/images/gadfly-covers.png){: .img-responsive .img-example}

## Getting ready

You'll need a Trove API key, so [go and get one <i class="fa fa-external-link" aria-hidden="true"></i>](http://help.nla.gov.au/trove/building-with-trove/api) if you don't have one already.

This task involves some Python coding, so you'll need to know how to [fire up the command line](/docs/using-the-command-line/), and have [Python, Pip and Virtualenv](/docs/python-pip-virtualenv/) installed.

Once you're ready, use `virtualenv` to [create and activate](/docs/python-pip-virtualenv/#creating-and-activating-a-virtual-environment) a new working environment.

To make our lives easier later on, we're going to install a Python package called `python-dateutil`. It simplifies parsing and formatting of dates. Within your new working and activated environment, type:

``` shell
$ pip install python-dateutil
```

## Installing `trove_python`

We're going to make use of some [general Trove harvesting code <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/Trove-Toolshed/trove-python) that I've already created, but first we have to download and install it.

If you have [Git <i class="fa fa-external-link" aria-hidden="true"></i>](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git), it's just a matter of typing the following inside your working environment:

``` shell
$ git clone https://github.com/Trove-Toolshed/trove-python.git
```

If not, just download [this zip file <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/Trove-Toolshed/trove-python/archive/master.zip) and unzip it in your working environment.

Either way, you should have created a directory called `trove-python`.

To install the `trove_python` code, just type:

``` shell
$ cd trove-python
$ python setup.py install
```

This makes `trove_python` available to applications within your working environment. 

## Introducing `trove_harvest`

Within the `trove_python` package is a module called `trove_harvest`. This module includes most of what you need to construct your very own Trove harvester. 

In particular, it defines a class called `TroveHarvester`, which is like a little Trove data processing factory. Feed it an api query and it will loop through the search results until it gets to the end. However, the default harvester doesn't actually do anything with the results it finds. It's up to you to say how you want the factory to process all that data arriving from Trove. To do that we're going to create our own version of `TroveHarvester`.

## Your own TroveHarvester

If you'd like to follow along, the example code for this tutorial is [available on GitHub <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-demo). To copy it into your working environment either use:

``` shell
$ git clone https://github.com/wragge/gadfly-demo.git
```

Or download and unzip [this file <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-demo/archive/master.zip).

Either way you'll have created a `gadfly-demo` directory. Open up the `harvest_gadfly.py` file inside with the text editor of your choice (I like [Sublime Text <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.sublimetext.com/)). 

Alternatively, if you want to start from scratch, create a new file and follow the steps below!

First of all we're going to import the things we need from the `trove_python` package.

In your new file insert the following:

``` python
from trove_python.trove_core import trove
from trove_python.trove_harvest.harvest import TroveHarvester
```

We're going to use `trove` to store our API key, but the most important thing is the `TroveHarvester` class. Once it's imported we can subclass it to create our own version. Insert:

``` python
class GadflyHarvester(TroveHarvester):

def process_results(self, results):
        try:
            articles = results[0]['records']['article']
			# Do things with the articles!
        except KeyError:
            pass
```

In this bit of code we're creating a new class called `GadflyHarvester` based on the standard `TroveHarvester`. Then within this data factory we're defining a processing pipeline called `process_results()` to actually *do something* with the data. But what are we going to do?

## Finding front pages

To understand what we need to do, we first have to think about the way Trove presents its newspaper data. If you search for something in the Trove newspapers zone, you're searching for **articles**, not pages. However, once you've found an article you can navigate up to page level.

So to harvest front pages from *The Gadfly* we first have to search for articles that were published on the front page.

If we do that using the API, we get back records for each article that look something like this:

``` json
    {  
        "id": "197893514",
        "url": "/newspaper/197893514",
        "heading": "No Horseman.",
        "category": "Article",
        "title": {
            "id": "898",
            "value": "Gadfly (Adelaide, SA : 1906 - 1909)"
        },
        "date": "1906-09-12",
        "page": 1,
        "pageSequence": 1,
        "relevance": {
            "score": "3.9055936",
            "value": "very relevant"
        },
        "snippet": "... ...",
        "troveUrl": "http://trove.nla.gov.au/ndp/del/article/197893514?searchTerm=firstpageseq%3A1",
        "illustrated": "Y",
        "wordCount": 31,
        "correctionCount": 0,
        "listCount": 0,
        "tagCount": 0,
        "commentCount": 0,
        "identifier": "http://nla.gov.au/nla.news-article197893514",
        "trovePageUrl": "http://trove.nla.gov.au/ndp/del/page/21069750",
        "pdf": "http://trove.nla.gov.au/ndp/imageservice/nla.news-page21069750/print"
    }
```

Did you spot `trovePageUrl`? The number at the end of `trovePageUrl` is the identifier for the page on which the article is published -- in this case, the front page. So our processing pipeline needs to extract and save the page id from each article.

But wait a minute... there might be more than one article on the front page. So we'll have to do some sort of check for duplicate page ids.

Once we have our page ids we can download the images for each page. How? Page image urls are constructed like this:

```
http://trove.nla.gov.au/ndp/imageservice/nla.news-page[page id goes here]/level3'
```

We'll use each page id to construct an image url, and then download and save the image. While we're at it, it would probably be a good idea to capture the basic page metadata in a CSV -- just in case we want to do something with it later.

So `process_results()` needs to:

* get the page id for each article in the search results
* check to see if we have that page id
* if we don't then download the page image
* and save the details to a CSV file

## Processing records

Now we're ready to build our processing pipeline.

We're going to need a few extra modules, so let's import them now. At the top of the file include:

``` python
import re
import time
import csv
import os
from urllib import urlretrieve
from dateutil.parser import parse
```

Let's also add templates to make image urls and nice persistent links for the pages in the Trove web interface. We'll replace the `{}` with the page id later on:

``` python
IMAGE_URL = 'http://trove.nla.gov.au/ndp/imageservice/nla.news-page{}/level3'
PAGE_URL = 'http://nla.gov.au/nla.news-page{}'
```

Let's include a little utility function that will check to see if a directory called `images` exists in the current location and, if not, create it.

After `GadflyHarvester` add:

``` python
def make_images_dir(path='images'):
    images_dir = os.path.join(os.getcwd(), path)
    try:
        os.makedirs(images_dir)
    except OSError:
        if not os.path.isdir(images_dir):
            raise
    return images_dir

```

We need to keep a list of page ids so we can check for duplicates. But because `process_records.py` only processes one set of records at a time (20 by default), we need to save the list as part of our harvester class so it will available every time `process_records.py` runs. Inside `GadflyHarvester` before `process_records.py`, add:

``` python
page_ids = []
```

For each new article we can then do something like this to weed out the duplicates:

``` python
if page_id not in self.page_ids:
	self.page_ids.append(page_id)
	# save image using page_id
```

The `self` means that the `page_ids` variable is attached to the parent class.

Now we can start building up the rest of`process_records.py`. We'll start calling our new `make_images_dir()` function:

``` python
images_dir = self.make_images_dir()
```

To get the `page_id` in the first place we can use a regular expression to separate out the numeric bit at the end of `trovePageUrl`:

``` python
page_id = re.search(r'page\/(\d+)', article['trovePageUrl']).group(1)
```

We can then create the image url using the template we added earlier and download the image using `urlretrieve`:

``` python
url = PAGE_URL.format(page_id)
image_filename = '{}-{}.jpg'.format(article['date'], page_id)
urlretrieve(image_url, os.path.join(images_dir, image_filename))
```

We'll wrap all of this inside a CSV writer to save the page details to a file. So the completed `GadflyHarvester` looks something like:

``` python
class GadflyHarvester(TroveHarvester):
    page_ids = []
    
    def process_results(self, results):
        try:
            articles = results[0]['records']['article']
            images_dir = self.make_images_dir()
            # Open a CSV file to write the results
            with open('results.csv', 'ab') as results_file:
                writer = csv.writer(results_file)
                for article in articles:
                    # Get the page id
                    page_id = re.search(r'page\/(\d+)', article['trovePageUrl']).group(1)
                    # Check if the page_id is a duplicate
                    if page_id not in page_ids:
                        page_ids.append(page_id)
                        # Construct the image url 
                        image_url = IMAGE_URL.format(page_id)
                        date = parse(article['date'])
                        title = "The Gadfly, {:%e %B %Y}".format(date)
                        url = PAGE_URL.format(page_id)
                        image_filename = '{}-{}.jpg'.format(article['date'], page_id)
                        writer.writerow([article['date'], page_id, title, url, image_filename])
                        urlretrieve(image_url, os.path.join(images_dir, image_filename))
            time.sleep(0.5)
            self.harvested += self.get_highest_n(results)
            print('Harvested: {}'.format(self.harvested))
        except KeyError:
            pass
```

These couple of lines at the end are important:

``` python
time.sleep(0.5)
self.harvested += self.get_highest_n(results)
```

The first just inserts a brief pause so that the harvester isn't constantly hammering the Trove API. The second updates the base harvester class so that it can keep track of how many articles have been processed. If you don't include this, the harvester will stop after processing the first set of results.

## Constructing a query url

Our harvester is ready to go, but what are we actually harvesting? We need to construct a query url that will return the results we want from the Trove API.

In this case it's pretty simple. We want all articles on the front page of [*The Gadfly* <i class="fa fa-external-link" aria-hidden="true"></i>](http://trove.nla.gov.au/newspaper/title/898).

There's a sneaky little parameter that will limit our results to articles on page 1:

```
q=firstpageseq:1
```

You could change the '1' to anything else to retrieve articles from other pages.

To limit our query to *The Gadfly* we need to find its title id. The easiest way to do this is just click on the [Which newspapers have been digitised? <i class="fa fa-external-link" aria-hidden="true"></i>](http://trove.nla.gov.au/newspaper/about) link on the Trove newspapers home page. Search for 'Gadfly', and click on the link that appears. In your browser's location bar you'll see the url:

```
http://trove.nla.gov.au/newspaper/title/898
```

The '898' is the identifier for *The Gadfly*. We add this to the query url with `&l-title=898`. We also need to add `&reclevel=full` to make sure we get the complete record for each article -- otherwise the `trovePageUrl` will be missing. Let's also include `&sortby=dateAsc` so our results are in chronological order. The complete query url (without your API key) is:

```
http://api.trove.nla.gov.au/result?q=firstpageseq:1&zone=newspaper&encoding=json&l-title=898&reclevel=full&sortby=dateAsc
```

To make sure it works, [try it out <i class="fa fa-external-link" aria-hidden="true"></i>](https://troveconsole.herokuapp.com/?url=http%3A%2F%2Fapi.trove.nla.gov.au%2Fresult%3Fq%3Dfirstpageseq%3A1%26zone%3Dnewspaper%26encoding%3Djson%26l-title%3D898%26reclevel%3Dfull%26sortby%3DdateAsc) in the Trove API Console.

For convenience, let's add it to the top of our file:

``` python
QUERY = 'http://api.trove.nla.gov.au/result?q=firstpageseq:1&zone=newspaper&encoding=json&l-title=898&reclevel=full&sortby=dateAsc'
```

You might be wondering where your API key goes. Usually you just add it to your API query, but that would mean saving it in your code. Instead of doing that you can just supply your key to the harvester when you start it up and it will add it to the query automatically.

## Starting your harvest

Our harvester is ready to go, but we currently don't have anyway of starting it. The base `TroveHarvester` class includes a `harvest()` method that sets things in motion. All we need to do is initialise our harvester and run `harvest()`.

At the bottom of our file create a new function called `start_harvest`:

``` python
def start_harvest(key, query=QUERY):
    trove_api = trove.Trove(key)
    harvester = GadflyHarvester(trove_api, query=QUERY)
    harvester.harvest()
```

This function expects you to supply your API key. You could also supply a different API query, but it defaults to the one we defined earlier.

## Run it!

Nothing left now but to run the harvester. From the command line start up python and import the file containing our harvester code (`harvest_gadfly` in the example repository).

``` shell
$ python
>>> import harvest_gadfly
```

Then call `start_harvest()`, supplying your API key:

``` shell
>>> harvest_gadfly.start_harvest("[your API key]")
``` 

Here's what the [results <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-results/blob/master/results.csv) should look like, and here's the [page images <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-results/tree/master/images).

## What's next?

* Harvest the front pages of a different newspaper?
* Create an Omeka exhibition using the images and data? (coming soon)
* Extract faces from the covers? (coming soon)

## More info

* [Code on Github <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-demo)
* [Results on GitHub <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/gadfly-results)
* [Page gallery on DropBox <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.dropbox.com/sc/h6xbyjroji1fzsd/AABLbWu9wsblD1dEkf1E7mwga)
* [Trove-Python <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/Trove-Toolshed/trove-python) repository on GitHub




