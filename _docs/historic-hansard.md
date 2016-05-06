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

[Historic Hansard](http://wragge.github.io/historic-hansard/) provides an easy-to-read version of the proceedings of the Commonwealth of Australia Parliament. It currently includes the House of Representatives Hansard from 1901 to 1965.

<http://wragge.github.io/historic-hansard/>

## Background

The Parliament of Australia provides access to Hansard through its [ParlInfo](http://parlinfo.aph.gov.au/parlInfo/search/search.w3p;orderBy=_fragment_number,doc_date-rev;query=Dataset%3Ahansardr,hansardr80;resCount=Default) database. ParlInfo lets you search Hansard (and other sources), but it's not easy to browse or read. Historic Hansard is the opposite -- there are currently no search facilities, but it's optimised for reading. You can explore what was happening in the House of Representatives day by day for 65 years.

## Usage

Hopefully it should be pretty obvious how to navigate through the site. Click on the big blue button to view a list of years. Click on the arrow next to a year to browse a list of sitting days. Click on a day or a debate and start reading. Just follow your nose!

From each day's proceedings there's a link to a PDF file from the Parliament website which provides scanned images of the original Hansard. So if the <a href="#" data-toggle="tooltip" title="{{ site.data.glossary.ocrd }}">OCRd</a> text seems a bit dodgy, you can check against the printed source.

There's also a link to the XML file for each day's proceedings. These files have been created by the Parliament from the OCRd text. They've been marked up to identify the structure of the day's events -- such as debates, speeches, and even interjections. I've used these files to create the web pages, so you might want to check them if you notice problems.

I've also incoporated [Hypothes.is](https://hypothes.is/) for all your web annotation needs. Hypothes.is enables you to add highlighting, annotations, and comments to any web page. Your annotations can be public or private. You can even create [groups](https://hypothes.is/blog/introducing-groups/) for collaboration or [instruction](https://hypothes.is/education/). It's easy to imagine a history unit where students work together to create an annotated version of Hansard.

To add annotations to Historic Hansard, just click on one of the Hypothes.is tabs which you'll find on the right-hand edge of your browser window. For more information see the [Hypothes.is help page](https://hypothes.is/docs/help).

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

I wrote a Python script to search ParlInfo by year and download all of these XML files. I've saved them all into [a GitHub repository](https://github.com/wragge/hansard-xml) where you can browse the files, or download the lot as a [big zip file](https://github.com/wragge/hansard-xml/archive/master.zip) (it's about 400mb). If you're interested in doing some large-scale text analysis or building your own Hansard viewer, grab these files and start playing!

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

I then used Jeckyll, a static site generator, to render all the Markdown files as HTML. Jekyll reads the front matter of each file and makes the values available as variables within the page template. So the nicely formatted date at the head of each page is created by Jekyll reading the date from the front matter and formatting it as directed by a template tag. Similarly, the index pages for each year are created by Jekyll pulling together the front matter details for a collection of pages.

XML afficianados will probably wonder why I didn't just create XSL templates to render the XML files directly. The truth is this was a quick hack and I used the tools I was most familiar with. Feel free to build your own version!

## Future plans

The first version of Historic Hansard was, quite literally, built in a weekend. I like to put some limits around these sorts of projects so I can deliver something quickly without obsessing too much about the bells and whistles! But there is, of course, much scope for further development.

Possible enhancements include:

* More content -- the Senate, and years beyond 1965.
* More indexes -- a consolidated list of bills, and a page for each member of parliament.
* A search facility -- as this is a static site (delivered directly as HTML files and not from a database) it's not easy to bake in search. But I might add a Google Custom Search to the mix.
* Visualisations? There all sorts of possibilities for representing the content, but I'm not sure what's permissable within the confines of the 'no derivatives' licence. Watch this space.

## Licensing

The contents of the Parliament of Australia website, including Hansard, are made available under a [CC-BY-NC-ND](http://www.aph.gov.au/Help/Disclaimer_Privacy_Copyright#c) licence. The 'ND' part of the licence specifies 'no derivatives'. As I understand it, simply reproducing a work in a different format, as I have done with Hansard, does not involve creating a derivative. It's not clear, however, what changes you can make under such a licence. I'll update this page with further information as it comes to hand.


