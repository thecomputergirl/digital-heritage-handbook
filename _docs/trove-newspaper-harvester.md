---
date: 2016-04-25
title: Trove Newspaper Harvester
layout: default_module
tags:
  - Trove
status: under_construction
type: Documentation
---

The Trove Newspaper Harvester is a command-line tool that helps you download large quantities of digitised newspaper articles from [Trove](http://trove.nla.gov.au).

Instead of working your way through page after page of search results using Trove's web interface, the newspaper harvester will save the results of your search to a <a href="#" data-toggle="tooltip" title="{{ site.data.glossary.csv }}">CSV</a> (spreadsheet) file which you can then filter, sort, or analyse.

Even better, the harvester can save the full OCRd (and possibly corrected) text of each article to an individual file. You could, for example, collect the text of thousands of articles on a particular topic and then feed them to a text analysis engine like Voyant to look for patterns in the language.

## Installation

The Newspaper Harvester is a command-line script written in the programming language Python. But that shouldn't scare you. If you're prepared to [open up a terminal](), installation and use is pretty straightforward.

Before you get started you need to make sure you have [Python, Pip, and Virtualenv]() on your computer.

The next step is to use Virtualenv to create a new working environment for your Trove harvests.





