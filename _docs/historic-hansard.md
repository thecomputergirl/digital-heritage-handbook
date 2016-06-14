---
date: 2016-05-02
title: Historic Hansard
category: resources
type: Documentation
layout: default_module
status: draft
tags:
  - Jekyll
  - Python
  - XML
---

[Historic Hansard <i class="fa fa-external-link" aria-hidden="true"></i>](http://historichansard.net/) provides an easy-to-read version of the proceedings of the Commonwealth of Australia Parliament. It currently includes the House of Representatives Hansard from 1901 to 1965.

<http://historichansard.net>

[![Historic Hansard home]({{ site.baseurl }}/images/hansard-home.png){: .img-responsive .img-example}](http://historichansard.net)

## Background

The Parliament of Australia provides access to Hansard through its [ParlInfo <i class="fa fa-external-link" aria-hidden="true"></i>](http://parlinfo.aph.gov.au/parlInfo/search/search.w3p;orderBy=_fragment_number,doc_date-rev;query=Dataset%3Ahansardr,hansardr80;resCount=Default) database. ParlInfo lets you search Hansard (and other sources), but it's not easy to browse or read. Historic Hansard is the opposite -- there are currently no search facilities, but it's optimised for reading. You can explore what was happening in the House of Representatives day by day for 65 years.

## Usage

Hopefully it should be pretty obvious how to navigate through the site. Click on the big blue button, or the 'House of Reps' in the navigation bar, to view the available indexes. Currently you can browse by:

* [Year <i class="fa fa-external-link" aria-hidden="true"></i>](http://historichansard.net/hofreps/years/) 
* [Parliament <i class="fa fa-external-link" aria-hidden="true"></i>](http://historichansard.net/hofreps/parliaments/)
* [People <i class="fa fa-external-link" aria-hidden="true"></i>](http://historichansard.net/hofreps/people/) -- members of the House of Representatives
* [Bills <i class="fa fa-external-link" aria-hidden="true"></i>](http://historichansard.net/hofreps/bills/) -- legislation presented and debated in parliament

From each index you can navigate through to a list of sitting days. Click on a date or a debate and start reading. Just follow your nose!

From each day's proceedings there's a link to a PDF file from the Parliament website which provides scanned images of the original Hansard. So if the <a href="#" data-toggle="tooltip" title="{{ site.data.glossary.ocrd }}">OCRd</a> text seems a bit dodgy, you can check against the printed source.

There's also a link to the XML file for each day's proceedings. These files have been created by the Parliament from the OCRd text. They've been marked up to identify the structure of the day's events -- such as debates, speeches, and even interjections. I've used these files to create the web pages, so you might want to check them if you notice problems.

I've integrated links to [Voyant Tools <i class="fa fa-external-link" aria-hidden="true"></i>](http://voyant-tools.org/) that allow you to analyse the text of a particular day or year. On the pages for each year and sitting day you'll see a 'View in Voyant' button. Clicking on this sends the XML files for that particular day or year direct to Voyant for analysis. Once the corpus loads you'll see a variety of tools to help you explore trends and patterns within the text. See the [Voyant documentation <i class="fa fa-external-link" aria-hidden="true"></i>](http://voyant-tools.org/docs/#!/guide) for more information. Here's 30 August 1945 viewed using Voyant's Cirrus tool:

![Hansard viewed in Voyant]({{ site.baseurl }}/images/hansard-cirrus.png){: .img-responsive .img-example}

I've also incoporated [Hypothes.is <i class="fa fa-external-link" aria-hidden="true"></i>](https://hypothes.is/) for all your web annotation needs. Hypothes.is enables you to add highlighting, annotations, and comments to any web page. Your annotations can be public or private. You can even create [groups <i class="fa fa-external-link" aria-hidden="true"></i>](https://hypothes.is/blog/introducing-groups/) for collaboration or [instruction <i class="fa fa-external-link" aria-hidden="true"></i>](https://hypothes.is/education/). It's easy to imagine a history unit where students work together to create an annotated version of Hansard.

To add annotations to Historic Hansard, just click on one of the Hypothes.is tabs which you'll find on the right-hand edge of your browser window. For more information see the [Hypothes.is help page <i class="fa fa-external-link" aria-hidden="true"></i>](https://hypothes.is/docs/help).

## Errors and oddities

Throughout Historic Hansard you'll find things that don't look right such as strange formatting, inconsistent spelling, or even missing text. This is a combination of OCR errors, XML markup issues, and probably some things that I've stuffed up.

I've made no effort to clean up the XML and there's no easy solution to the markup problems. If you find a serious error in the XML you're welcome to [fork <i class="fa fa-external-link" aria-hidden="true"></i>](https://help.github.com/articles/fork-a-repo/) the [XML repository <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/hansard-xml), make your corrections, and send me [a pull request <i class="fa fa-external-link" aria-hidden="true"></i>](https://help.github.com/articles/using-pull-requests/).

Otherwise -- it is what it is.

## Technical stuff

Behind ParlInfo's version of Hansard are a series of XML files containing the marked-up version of each day's events.

For example, here's how the opening of a new day's business is recorded:

``` xml
<chamber.xscript>
    <para class="italic">
      <inline font-style="italic">HouseofRepresentatives.</inline>
    </para>
    <business.start>
      <day.start>1901-05-09</day.start>
    </business.start>
    <debate>
      <debateinfo>
        <title>PROCLAMATION</title>
        <page.no>16</page.no>
        <type>proclamations</type>
      </debateinfo>
      <para>Honorable members assembled at half-past eleven a.m., in a chamber in the western annexe of the Exhibition-building, Melbourne, pursuant to the proclamation of His Excellency the Governor-General convening Parliament. </para>
      <para>The  Clerk  read the proclamation. </para>
    </debate>
```

I wrote a Python script to search ParlInfo by year and download all of these XML files. I've saved them all into [a GitHub repository <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/hansard-xml) where you can browse the files, or download the lot as a [big zip file <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/hansard-xml/archive/master.zip) (it's about 400mb). If you're interested in doing some large-scale text analysis or building your own Hansard viewer, grab these files and start playing!

To generate the Historic Hansard site, I used a Python script to read each XML file and create a plain text version using Markdown. I also recorded some structured information about each file in a 'front matter' block using YAML. Something like this:

``` yaml
---
house: House of Representatives
date: 1901-05-09
year: 1901
session: 1
page_start: 16
parliament: 1
file_id: 19010509_reps_1_1
---
```

I then used Jekyll, a static site generator, to render all the Markdown files as HTML. Jekyll reads the front matter of each file and makes the values available as variables within the page template. So the nicely formatted date at the head of each page is created by Jekyll reading the date from the front matter and formatting it as directed by a template tag. Similarly, the index pages for each year are created by Jekyll pulling together the front matter details for a collection of pages.

XML afficianados will probably wonder why I didn't just create XSL templates to render the XML files directly. The truth is this was a quick hack and I used the tools I was most familiar with. Feel free to build your own version!

## Future plans

The first version of Historic Hansard was, quite literally, built in a weekend. I like to put some limits around these sorts of projects so I can deliver something quickly without obsessing too much about the bells and whistles! But there is, of course, much scope for further development.

Possible enhancements include:

* More content -- the Senate, and years beyond 1965.
* I've included a Google custom search, but it's not going to work until Google finishes indexing the site.
* Visualisations? There all sorts of possibilities for representing the content, but I'm not sure what's permissable within the confines of the 'no derivatives' licence. Watch this space.

## Licensing

The contents of the Parliament of Australia website, including Hansard, are made available under a [CC-BY-NC-ND <i class="fa fa-external-link" aria-hidden="true"></i>](http://www.aph.gov.au/Help/Disclaimer_Privacy_Copyright#c) licence. The 'ND' part of the licence specifies 'no derivatives'. As I understand it, simply reproducing a work in a different format, as I have done with Hansard, does not involve creating a derivative. It's not clear, however, what changes you can make under such a licence. I'll update this page with further information as it comes to hand.


