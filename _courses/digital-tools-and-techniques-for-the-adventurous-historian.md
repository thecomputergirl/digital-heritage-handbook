---
date: 2016-05-08
title: Digital Tools and Techniques for the Adventurous Historian
type: Course
tags:
  - Python
layout: default_module
status: under_construction
---

**A workshop organised by the History Council of South Australia for the SA History Festival 2016.**  
**Held at the State Library of South Australia, 10 May 2016.**

## Knowing what's possible

Introduction -- focus on knowing what's possible.

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

### Sites to visit

* [James Minahan's Homecoming](http://minahan.herokuapp.com/) -- demo site, under construction
* [LODBooks](http://timsherratt.org/research-notebook/projects/lodbooks/) -- research project

----

## The web isn't a thing

[![After]({{ site.baseurl }}/images/xray-goggles.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/xray-goggles.png)

### Things to try

* [X Ray Goggles](https://goggles.mozilla.org/) -- a great educational tool from The Mozilla Foundation. Deconstruct and remix websites. Share the results!
* [Stop Tony Meow](http://stoptonymeow.com/) -- ok, it's a bit redundant now, but it's a great example of how web pages can be rewritten in our browser. MOAR KITTENS.


----

## Hacking RecordSearch

Not fixed -- we can intervene.

[![After]({{ site.baseurl }}/images/rs-after.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/rs-after.png)

### Things to try

* [RecordSearch ShowPages Userscript]({{ site.baseurl }}/docs/recordsearch-showpages-userscript/)
* [Installing userscripts]({{ site.baseurl }}/docs/installing-userscripts/)

----

## Working with data 

Web as a source of data -- to be manipulated, analysed, visualised.

[![Plotly chart of SA 1901 Census]({{ site.baseurl }}/images/sa-census2.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/sa-census2.png)

### Things to try

* [Creating simple charts with Plotly]({{ site.baseurl }}/activities/creating-simple-charts-with-plotly/) -- copy population data from the 1901 South Australian Census and display it as a bar chart.
* [Zotero](https://www.zotero.org/) -- more than just a reference manager, Zotero is your personal research database. Extract metadata and images from sites like Trove and RecordSearch.

### Sites to visit

* [Pre-harvested data]({{ site.baseurl }}/docs/preharvested-data/) -- a small (and slightly weird) collection of data sources that I've packaged up for easy access. Hansard, ASIO files, faces & more!
* [Building with Trove](http://help.nla.gov.au/trove/building-with-trove) -- Trove is not just a website, it's a platform! Grab collections data from the Trove API and build things.
* Government data -- try [data.gov.au](http://data.gov.au/), and the various state repositories such as [data.sa.gov.au](https://data.sa.gov.au/). What can you find?

----

## Harvesting Trove

[![Trove Harvester in action]({{ site.baseurl }}/images/trove-harvester.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/trove-harvester.png)

### Things to try

* [Trove newspaper harvester]({{ site.baseurl }}/docs/trove-newspaper-harvester/) -- command line tool to harvest articles in bulk
* [Harvesting front pages of *The Gadfly*]()

-----

## Text as data

[![In a word]({{ site.baseurl }}/images/inaword.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/inaword.png)

### Things to try

* [DataBasic.io](https://www.databasic.io/en/) -- some simple and fun tools that introduce you to the possibilities of exploring text as data. Compare the lyrics of Beyonce and Aretha Franklin!
* [Voyant Tools](http://voyant-tools.org/) -- upload and explore your texts! There are many tools and options, so you might want to look at the [Getting Started](http://voyant-tools.org/docs/#!/guide/start) guide.
* [Getting started with Topic Modelling and MALLET](http://programminghistorian.org/lessons/topic-modeling-and-mallet) by Shawn Graham, Scott Weingart and Ian Milligan, *Programming Historian* -- topic modelling is a way of finding 'themes' or 'topics' within a collection of texts.

### Sites to visit

* [In a word: currents in Australian affairs 2003-2013](http://inaword.dhistory.org/)
* [QueryPic](http://dhistory.org/querypic/) -- visualise searches in Trove's digitised newspapers.
* [Bookworm](http://bookworm.culturomics.org/) -- explore the occurrence of words and phrases across a range of texts.


## Finding faces

[![Real face of White Australia]({{ site.baseurl }}/images/faces.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/faces.png)

### Things to try

* [The Vintage Face Depot](https://wragge.github.io/face-depot/) -- for all your face replacement needs...
* [Face++ demo](http://www.faceplusplus.com/demo-detect/) -- Hmmm, what do you think about this technology? You might want to read [The Perfect Face](http://discontents.com.au/the-perfect-face/)

### Sites to visit

* [The Real Face of White Australia](http://invisibleaustralians.org/faces/)
* [Eyes on the Past](http://eyespast.herokuapp.com/)
* [Faces from The Gadfly](https://www.dropbox.com/sc/qj0c1ghszkvqrvt/AACthT1HkTBM6pz1s030usoca)

----

## Telling stories with maps

[![Geolocated map of Adelaide]({{ site.baseurl }}/images/adelaide-overlay.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/adelaide-overlay.png)

### Things to try

* [Making simple maps]({{ site.baseurl }}/lessons/making-simple-maps/)
* [Georectify maps with MapWarper]()
* [StoryMap](https://storymap.knightlab.com/) -- create your own online!

### Sites to visit

* [My georectified maps of Adelaide](http://104.236.162.148/#)
* [American Panorama](http://dsl.richmond.edu/panorama/)
* [Odyssey.js](https://cartodb.github.io/odyssey.js/)
* [Neatline](http://neatline.org/)

----

## The read/write web

[![Chinese in NSW]({{ site.baseurl }}/images/chinese-nsw.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/chinese-nsw.png)

### Things to try

* Preserve web pages and create persistent links with the [Wayback Machine](http://archive.org/web/) and [Perma.cc](https://perma.cc/).
* Use [Hypothes.is](https://hypothes.is/) to annotate the web (and this workshop!).
* Create an [instant Trove exhibition](https://github.com/wragge/diy-trove-exhibition)

### Sites to visit

* [Omeka](http://omeka.org/)
* [Documenting the now](https://news.docnow.io/)

## Going further

* [DiRT](http://dirtdirectory.org/) -- a directory of digital research tools.
* [The Programming Historian](http://programminghistorian.org/) -- for historians who want to start exploring digital possibilities.