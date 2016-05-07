---
date: 2016-05-07
title: RecordSearch ShowPages Userscript
type: Documentation
tags:
  - RecordSearch
  - userscript
layout: default_module
status: draft
---

This is a [userscript]({{ site.baseurl }}/docs/installing-userscripts/) which improves the functionality of the National Archives of Australia's online database [RecordSearch <i class="fa fa-external-link" aria-hidden="true"></i>](http://recordsearch.naa.gov.au/scripts/Logon.asp?N=guest). 

Before you add this userscript to your browser, you need to have a [userscript manager installed]({{ site.baseurl }}/docs/installing-userscripts/#installation).

This userscript does two things:

* If a file is digitised, it retrieves the number of pages in the file and displays it as part of the link to the digitised file. This means you know without clicking through whether the file contains 1 or 300 pages.

* It also rewrites the link to the digitised file to STOP IT OPENING IN A TINY NEW WINDOW WITHOUT A TOOLBAR. The default behaviour is just **so annoying**.

Here's what RecordSearch results look like without this userscript:

[![Before]({{ site.baseurl }}/images/rs-before.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/rs-before.png)

And here's what it's like with the userscript running:

[![After]({{ site.baseurl }}/images/rs-after.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/rs-after.png)

You can tell at a glance how big a digitised file is. Simple, but useful!

The code for this userscript is displayed below. Once you have a [script manager installed]({{ site.baseurl }}/docs/installing-userscripts/#installation), just click on the 'view raw' button at the bottom to add it to your browser. The script manager will ask you to confirm that you really want to install this script. Say yes.

Then visit RecordSearch and be amazed at the difference!

{% gist wragge/b2af9dc56f7cb0a9476b %}