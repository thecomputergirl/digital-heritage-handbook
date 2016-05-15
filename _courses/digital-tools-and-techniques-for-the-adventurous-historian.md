---
date: 2016-05-08
title: Digital Tools and Techniques for the Adventurous Historian
type: Course
tags:
  - Linked Open Data
  - userscripts
  - data visualisation
  - mapping
  - Trove
  - RecordSearch
  - exhibitions
layout: default_module
status: under_construction
---

**A workshop organised by the History Council of South Australia for the SA History Festival 2016.**  
**Held at the State Library of South Australia, 10 May 2016.**

## Knowing what's possible

In three hours we're not going to give you all the knowledge and skills you need to make full use of digital tools and technologies in your historical work.

Sorry!

What we're aiming to do is to give you a sense of what's possible, so that when you have a particular task to do you'll know what tools are relevant, what sites to visit, what words to Google.

You can come back to this page at any time and explore in more depth. So don't worry about the technical details, think about the possibilities!

* [LODBook and layers](#lodbook-and-layers)
* [The web isn't a thing](#the-web-isnt-a-thing)
* [Hacking RecordSearch](#hacking-recordsearch)
* [Working with data](#working-with-data)
* [Harvesting Trove](#harvesting-trove)
* [Text as data](#text-as-data)
* [Finding faces](#finding-faces)
* [Telling stories with maps](#telling-stories-with-maps)
* [The read/write web](#the-readwrite-web)
* [Going further](#going-further)

----

## LODBook and layers

![LODBooks demo site](http://timsherratt.org/research-notebook/images/lodbook-demo.png){: .img-responsive .img-example}

LOD = Linked Open Data. It's a way of sharing structured data (like the stuff in databases) on the web so that it can be easily linked, collected, and used.

Historians create LOD all the time -- they define entities (people, places, events) and the relationships between them. But when we publish we tend to squeeze out the data, until all that it left is narrative text. I think we can have both -- narratives enriched with Linked Open Data.

Here you'll find a link to my LODBooks demo site, using a draft text created by [Kate Bagnall <i class="fa fa-external-link" aria-hidden="true"></i>](http://katebagnall.com/). Explore! Scroll! Click! I wanted to show it today because I believe we need to think more creatively about the ways we publish historical work online. Not just narratives, not just databases, but both -- together!

I also wanted to show it because it illustrates my general theme for today's workshop. There will be no talk of revolutions today, and hopefully I'll avoid using the word 'new' too much. Even as we explore this realm of digital possibilities, we are still historians. We must remain critical of our tools and sources. But what these tools and techniques offer are ways of working with the complex layers of history, of exposing structures in our sources, of creating complex narratives reveal their relationships with data.

### Sites to visit

* [James Minahan's Homecoming <i class="fa fa-external-link" aria-hidden="true"></i>](http://minahan.herokuapp.com/) -- the demo site, under construction.
* [LODBooks](http://timsherratt.org/research-notebook/projects/lodbooks/) -- more details in my open research notebook.

----

## The web isn't a thing

[![After]({{ site.baseurl }}/images/xray-goggles.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/xray-goggles.png)

But before we start peeling back the layers of digital history we first have to understand that this thing we call 'the web' isn't a thing at all. We talk about 'web publishing' and 'web pages' as if they're products of the print world. But if you look underneath what's presented in your browser you'll see each 'page' is an assemblage of files, standards, protocols, and technologies, all pulled together and rendered in a human-readable version by your browser.

This is important because we can play around with these layers. We don't have to take the web we're given. We can change it.

### Things to try

* [X Ray Goggles <i class="fa fa-external-link" aria-hidden="true"></i>](https://goggles.mozilla.org/) -- a great educational tool from The Mozilla Foundation. Deconstruct and remix websites. Share the results!
* [Stop Tony Meow <i class="fa fa-external-link" aria-hidden="true"></i>](http://stoptonymeow.com/) -- ok, it's a bit redundant now, but it's a great example of how web pages can be rewritten in our browser. MOAR KITTENS.


----

## Hacking RecordSearch

[![After]({{ site.baseurl }}/images/rs-after.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/rs-after.png)

I love the collections of the National Archives of Australia, but I am constantly frustrated by their online database RecordSearch. Here's a little hack which makes RecordSearch a bit more user friendly.

Remember, web pages aren't fixed. We have more control over them than we think. Our browsers can change the way they look, even the way they behave. Userscripts are little programs installed within browsers to customise specific websites. This userscript adds more detail to the display of search results in RecordSearch. Try it!

### Things to try

* [RecordSearch ShowPages Userscript]({{ site.baseurl }}/docs/recordsearch-showpages-userscript/)
* [Installing userscripts]({{ site.baseurl }}/docs/installing-userscripts/)

----

## Working with data 

[![Plotly chart of SA 1901 Census]({{ site.baseurl }}/images/sa-census2.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/sa-census2.png)

There is useful data everywhere on the web. Sometimes it's formatted in a convenient, structured way. Sometimes it isn't.

More and more institutions are sharing data through repositories such as data.gov.au. Often these are available in formats such as CSV (comma separated values) which can be opened and manipulated in any spreadsheet or database.

Organisations also share data through APIs (application programming interface). APIs deliver the data you want, when you want it, in a form that computers can understand. You can use APIs to harvest datasets, or build applications that retrieve and display data on the fly.

But sometimes the data you want is just presented as text on a website. No downloads, no structure -- just text. To get data like this into a useful form you often have to resort to things like 'screen scrapers' -- tools that use patterns and structures within the page to isolate the data you want. Zotero, for example, uses a whole series of little screen scrapers to extract stuctured data from websites.

Once you have your data you can start to explore, analyse and visualise it using a growing range of online tools.

### Things to try

* [Creating simple charts with Plotly]({{ site.baseurl }}/activities/creating-simple-charts-with-plotly/) -- copy population data from the 1901 South Australian Census and display it as a bar chart.
* [Zotero <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.zotero.org/) -- more than just a reference manager, Zotero is your personal research database. Extract metadata and images from sites like Trove and RecordSearch.
* [Trove API Console <i class="fa fa-external-link" aria-hidden="true"></i>](https://troveconsole.herokuapp.com/) -- try some of the potted examples to get an idea of how to get data out of Trove.
* DataBasic.io's [WTFcsv <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.databasic.io/en/wtfcsv/) -- learn how to find out what's hiding in CSV files, starting with The Titanic!

### Sites to visit

* [Pre-harvested data]({{ site.baseurl }}/docs/preharvested-data/) -- a small (and slightly weird) collection of data sources that I've packaged up for easy access. Hansard, ASIO files, faces & more!
* [Building with Trove <i class="fa fa-external-link" aria-hidden="true"></i>](http://help.nla.gov.au/trove/building-with-trove) -- Trove is not just a website, it's a platform! Grab collections data from the Trove API and build things.
* Government data -- try [data.gov.au <i class="fa fa-external-link" aria-hidden="true"></i>](http://data.gov.au/), and the various state repositories such as [data.sa.gov.au <i class="fa fa-external-link" aria-hidden="true"></i>](https://data.sa.gov.au/). What can you find?

----

## Harvesting Trove

[![Trove Harvester in action]({{ site.baseurl }}/images/trove-harvester.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/trove-harvester.png)

The Trove Newspaper Harvester lets you download lots and lots of digitised newspaper articles from Trove -- hundreds, or even thousands of articles. Why would you want this? Perhaps you're trying to trace trends over time. The harvester collects the publication details of all the articles into a single CSV file. You can harvest a particular search query and then open and explore the results in a spreadsheet or database. Or perhaps you want to look for patterns in the newspaper content itself -- the harvester can save all the OCRd text into separate files for analysis.

Digital tools enable us to harvest, process and visualise large quantities of data. Instead of looking for individual examples we can zoom out and trace patterns and trends across time. It doesn't have to be articles, it could be photographs, or sound files. Tools like the Trove Harvester, which retrieves data from the Trove API, enable us to assemble our own custom datasets for exploration or display. 

### Things to try

* [Trove newspaper harvester]({{ site.baseurl }}/docs/trove-newspaper-harvester/) -- command line tool to harvest articles in bulk.
* [Harvesting the front pages of *The Gadfly*]({{ site.baseurl }}/activities/harvest-the-front-pages-of-the-gadfly/) -- what else can you harvest? What about a collection of front pages?

-----

## Text as data

[![In a word]({{ site.baseurl }}/images/inaword.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/inaword.png)

Sometimes the text *is* the data. Using digital tools we can break texts down into their component parts -- words, phrases, and parts of speech -- and manipulate them. How are certain words used within collections of texts? We can analyse things like occurance, frequency, and context to better understand the layers of meaning within text. 

### Things to try

* DataBasic.io's [WordCounter <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.databasic.io/en/wordcounter/) and [SameDiff <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.databasic.io/en/samediff/) -- some simple and fun tools that introduce you to the possibilities of exploring text as data. Compare the lyrics of Beyonce and Aretha Franklin!
* [Voyant Tools <i class="fa fa-external-link" aria-hidden="true"></i>](http://voyant-tools.org/) -- upload and explore your texts! There are many tools and options, so you might want to look at the [Getting Started](http://voyant-tools.org/docs/#!/guide/start) guide. Try uploading [Hansard](https://github.com/wragge/hansard-xml)!
* [Getting started with Topic Modelling and MALLET <i class="fa fa-external-link" aria-hidden="true"></i>](http://programminghistorian.org/lessons/topic-modeling-and-mallet) by Shawn Graham, Scott Weingart and Ian Milligan, *Programming Historian* -- topic modelling is a way of finding 'themes' or 'topics' within a collection of texts.

### Sites to visit

* [In a word: currents in Australian affairs 2003-2013 <i class="fa fa-external-link" aria-hidden="true"></i>](http://inaword.dhistory.org/)
* [QueryPic <i class="fa fa-external-link" aria-hidden="true"></i>](http://dhistory.org/querypic/) -- visualise searches in Trove's digitised newspapers.
* [Bookworm <i class="fa fa-external-link" aria-hidden="true"></i>](http://bookworm.culturomics.org/) -- explore the occurrence of words and phrases across a range of texts.


## Finding faces

[![Real face of White Australia]({{ site.baseurl }}/images/faces.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/faces.png)

Computers are getting better at seeing. The things we take for granted, like the ability to recognise a face, are challenging tasks for computer vision. But recent years have brought great advances.

Computers can be taught to find shapes and patterns within images. Facial detection (finding a face in a photo) is pretty straightforward. This offers interesting possibilities for historians, but the use of such technologies for surveillance also presents political and social challenges.

### Things to try

* [The Vintage Face Depot <i class="fa fa-external-link" aria-hidden="true"></i>](https://wragge.github.io/face-depot/) -- for all your face replacement needs...
* [Face++ demo <i class="fa fa-external-link" aria-hidden="true"></i>](http://www.faceplusplus.com/demo-detect/) -- Hmmm, what do you think about this technology? You might want to read [The Perfect Face](http://discontents.com.au/the-perfect-face/)

### Sites to visit

* [The Real Face of White Australia <i class="fa fa-external-link" aria-hidden="true"></i>](http://invisibleaustralians.org/faces/) -- faces of people who lived under the White Australia Policy extracted from the National Archives of Australia.
* [Eyes on the Past <i class="fa fa-external-link" aria-hidden="true"></i>](http://eyespast.herokuapp.com/) -- is it art, or is it just creepy?
* [Faces from The Gadfly <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.dropbox.com/sc/qj0c1ghszkvqrvt/AACthT1HkTBM6pz1s030usoca) -- a quick example of facial detection using the fromt pages of *The Gadfly*.

----

## Telling stories with maps

[![Geolocated map of Adelaide]({{ site.baseurl }}/images/adelaide-overlay.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/adelaide-overlay.png)

Digital technologies have turned everyone into map makers. Whether you know it or not, it's likely that your electronic devices are currently plotting your movements through space. 

Online mapping tools make it easy to visualise geospatial data. But you can do more than just put markers on a map. What about layering historical maps over modern data? What about combining geospatial data with narrative to tell a story in time and space?

### Things to try

* [Making simple maps]({{ site.baseurl }}/lessons/making-simple-maps/) -- a quick introduction to MyMaps and CartoDB.
* [Geolocate historic maps with MapWarper]({{ site.baseurl }}/activities/geolocate-historic-maps-with-mapwarper/)
* [StoryMap <i class="fa fa-external-link" aria-hidden="true"></i>](https://storymap.knightlab.com/) -- create your own online!

### Sites to visit

* [My georectified maps of Adelaide <i class="fa fa-external-link" aria-hidden="true"></i>](http://104.236.162.148/#) -- here's something I prepared earlier...
* [American Panorama <i class="fa fa-external-link" aria-hidden="true"></i>](http://dsl.richmond.edu/panorama/) -- amazing new collection of data rich maps telling stories from American history
* [Odyssey.js <i class="fa fa-external-link" aria-hidden="true"></i>](https://cartodb.github.io/odyssey.js/) -- another tool that combines maps and stories.
* [Neatline <i class="fa fa-external-link" aria-hidden="true"></i>](http://neatline.org/) -- a plugin for Omeka that lets you create rich, multilayered maps with timelines, embedded documents, annotations and stories.

----

## The read/write web

[![Chinese in NSW]({{ site.baseurl }}/images/chinese-nsw.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/chinese-nsw.png)

We don't just consume the web, we make it. People generate vast quantities of online content through social media, and sharing sites. This is exciting raw material for historical analysis, but how can we make sure it's preserved and accessible?

The web also offers historians the opportunity to create, engage, and experiment. We can publish stories, start conversations, build exhibitions, and share our research.

### Things to try

* Preserve web pages and create persistent links with the [Wayback Machine <i class="fa fa-external-link" aria-hidden="true"></i>](http://archive.org/web/) and [Perma.cc <i class="fa fa-external-link" aria-hidden="true"></i>](https://perma.cc/).
* Use [Hypothes.is <i class="fa fa-external-link" aria-hidden="true"></i>](https://hypothes.is/) to annotate the web (and this workshop!).
* Create an [instant Trove exhibition <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/diy-trove-exhibition) -- all you need is a a few Trove lists and a GitHub account.

### Sites to visit

* [Omeka <i class="fa fa-external-link" aria-hidden="true"></i>](http://omeka.org/) -- create online exhibitions!
* [Documenting the now <i class="fa fa-external-link" aria-hidden="true"></i>](https://news.docnow.io/) -- important new project aimed at documenting communities and current events.

## Going further

* [DiRT <i class="fa fa-external-link" aria-hidden="true"></i>](http://dirtdirectory.org/) -- a directory of digital research tools.
* [The Programming Historian <i class="fa fa-external-link" aria-hidden="true"></i>](http://programminghistorian.org/) -- for historians who want to start exploring digital possibilities.