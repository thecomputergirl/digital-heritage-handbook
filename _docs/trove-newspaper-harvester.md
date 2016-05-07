---
date: 2016-04-25
title: Trove Newspaper Harvester
layout: default_module
tags:
  - Trove
status: draft
type: Documentation
---

The Trove Newspaper Harvester is a command-line tool that helps you download large quantities of digitised newspaper articles from [Trove <i class="fa fa-external-link" aria-hidden="true"></i>](http://trove.nla.gov.au).

Instead of working your way through page after page of search results using Trove's web interface, the newspaper harvester will save the results of your search to a <a href="#" data-toggle="tooltip" title="{{ site.data.glossary.csv }}">CSV</a> (spreadsheet) file which you can then filter, sort, or analyse.

Even better, the harvester can save the full OCRd (and possibly corrected) text of each article to an individual file. You could, for example, collect the text of thousands of articles on a particular topic and then feed them to a text analysis engine like [Voyant <i class="fa fa-external-link" aria-hidden="true"></i>](http://voyant-tools.org/) to look for patterns in the language.

## Installation

The Newspaper Harvester is a command-line script written in the programming language Python. But that shouldn't scare you. If you're prepared to [open up a terminal]({{ site.baseurl }}/docs/using-the-command-line/), installation and use is pretty straightforward.

Before you get started you need to make sure you have [Python, Pip, and Virtualenv]({{ site.baseurl }}/docs/python-pip-virtualenv/) on your computer.

The next step is to use Virtualenv to [create a new working environment]({{ site.baseurl }}/docs/python-pip-virtualenv/#creating-and-activating-a-virtual-environment) where you can create and store all your Trove harvests.

Once you've activated your new environment, it's just a matter of typing:

``` shell
$ pip install troveharvester
```

To check that it's installed and ready, type:

``` shell
$ troveharvester -h
```

You should see a help message like this:

``` shell
usage: troveharvester [-h] {start,restart,report} ...

positional arguments:
  {start,restart,report}
    start               Start a new harvest
    restart             Restart an unfinished harvest
    report              Report on a harvest

optional arguments:
  -h, --help            show this help message and exit
```
Ok, we're ready to do some harvesting!

## Usage

As you can see from the default help message there are three basic commands that the harvester understands:

* `start` -- start a new harvest
* `restart` -- restart a stalled or interrupted harvest
* `report` -- retrieve the details of an existing harvest

### Starting a harvest

The start command has two required parameters and a number of options. The required parameters are:

* a Trove newspaper search url
* your Trove API key

If you don't have a Trove API key, now would be a good time to [go and get one <i class="fa fa-external-link" aria-hidden="true"></i>](http://help.nla.gov.au/trove/building-with-trove/api). It's a quick and painless process.

The Trove newspaper search url is just the url that Trove sends you to when you construct a search on the web site. So simply go to Trove's newspaper zone, build your search, then copy the url in your browser's location box. The newspaper harvester will translate your query into a form that the Trove API can understand.

Alternatively, you can use something like the [Trove API Console <i class="fa fa-external-link" aria-hidden="true"></i>](https://troveconsole.herokuapp.com/) to construct an API query yourself. The harvester will then just pass the url on without any translation.

There are three options you can add to the start command:

* `--pdf` -- save a PDF copy of every article
* `--text` -- save the text contents of every article to an individual file
* `--max [number]` -- harvest a maximum of [number] results

So if I wanted to harvest articles containing the word 'wragge' and my API key was 'thisismyapikey', I'd type:

``` shell
$ troveharvester start "http://trove.nla.gov.au/newspaper/result?q=wragge" thisismyapikey
```

Note that I've enclosed the query url in double quotes. If you don't do this you'll probably get odd errors about missing parameters.

If I wanted to harvest a maximum of 500 articles, I'd type:

``` shell
$ troveharvester start "http://trove.nla.gov.au/newspaper/result?q=wragge" thisismyapikey --max 500
```

And if I wanted to save pdfs and text files for every article:

``` shell
$ troveharvester start "http://trove.nla.gov.au/newspaper/result?q=wragge" thisismyapikey --pdf --text
```

{: .bg-danger .bg-context }
<i class="fa fa-exclamation-triangle" aria-hidden="true"></i> Note that in Windows you can't just paste your url and key into the command line using the normal 'ctrl-v' key combination. Here's [what you need to do]({{ site.baseurl }}/docs/using-the-command-line/#pasting-into-a-windows-terminal).

### Harvest results

When you start a new harvest, the harvester looks for a directory called `data`. If it doesn't exist it creates it. Within this directory it creates another directory for your harvest. The name of this directory will be in the form of a unix timestamp -- a very large number that represents the number of seconds since 1 January 1970. So this means the directory with the largest number will contain the most recent harvest.

The harvester saves your results inside this directory. There will be at least two files created for each harvest:

* `results.csv` -- a text file containing the details of all harvested articles
* `metadata.json` -- a configuration file which stores all the details of the harvest

If you've asked for PDFs or text files, there will be additional directories containing those files.

The `results.csv` file is a plain text CSV (Comma Separated Values) file. You can open it with any spreadsheet program. The details recorded for each article are:

* `article_id` -- a unique identifier for the article
* `title` -- the title of the article
* `newspaper_id` -- a unique identifier for the newspaper (this can be used to retrieve more information or build a link to the web interface)
* `newspaper_title` -- the name of the newspaper
* `page` -- page number (of course), but might also indicate the page is part of a supplement or special section
* `date` -- in ISO format, YYYY-MM-DD
* `category` -- one of 'Article', 'Advertising', 'Detailed lists, results, guides', 'Family Notices', or 'Literature'
* `words` -- number of words in the article
* `illustrated` -- is it illustrated (values are `y` or `n`)
* `corrections` -- number of text corrections
* `url` -- the persistent url for the article

### Restarting a harvest

Sometimes harvests get interrupted. While testing the harvester I noticed, for example, that Trove was sometimes returning 19 results instead of 20. This made the harvester think it was finished. If this happens, don't worry -- it's easy to restart things.

If you want to restart the current harvest, simply type:

``` shell
$ troveharvester restart
```

The harvester will look for the most recent results folder (they're named with timestamps remember?) and read the configuration details from the `metadata.json` file. It then inspects the `results.csv` file to see where the harvest got up to. Just to be on the safe side it removes the last row in the results file so that it can be reharvested. It then starts up again from where it was interrupted.

If you want to go back and restart an earlier harvest, you just need to supply the name of the folder containing the harvest:

``` shell
$ troveharvester restart --harvest [harvest directory name (timestamp)]
```

### Reporting on a harvest

The harvester includes a simple tool that reports on the configuration and status of a harvest. To see a report on your most recent harvest, type:

``` shell
$ troveharvester report
```

You'll see something like:

``` shell

HARVEST METADATA
================
Last harvest started: 2016-05-06T20:31:01.295082
Harvest id: 1462530661
API key: [your API key]
Query: http://trove.nla.gov.au/newspaper/result?q=wragge
Max results: 0
Include PDFs: False
Include text: False

HARVEST PROGRESS
================
Articles harvested: 180
Last article harvested:

[ u'112739205',
  u"Wragge's Forecast.",
  u'516',
  u'The Port Macquarie News and Hastings River Advocate (NSW : 1882 - 1950)',
  u'4',
  u'1922-11-11',
  u'Article',
  u'130',
  u'N',
  u'0',
  u'http://nla.gov.au/nla.news-article112739205']

```

Similar to the `restart` command, you can also specify the name of a harvest to report on.

``` shell
$ troveharvester report --harvest [harvest directory name (timestamp)]
```

## Notes

The Trove API regularly returns errors. The harvester just accepts this, waits a little while, then tries again. So sometimes you'll see a message like:

``` shell
$ The server didn't respond. Retrying in 1 seconds...
```

If there's still a problem after 10 retries the harvester will give up. That probably means that either Trove is down, the internet is down, or the world is coming to an end. In most cases just wait a while and try again, using the `restart` command.

As noted above, sometimes the API mysteriously returns 19 results instead of 20, tricking the harvester into thinking it's finished. If this happens, just use `restart` and the harvester will pick up where it finished.

The NSW Government Gazette is currently treated like a newspaper by the API, but not by the web interface. That means you can't just paste a search url from the gazette zone into the harvester. To harvest from the gazette zone, you need to change `gazette` in the url to `newspaper` and add `&l-title=525&l-title=526`. So if I was searching for `wragge` in the gazette zone, I'd change:

```
http://trove.nla.gov.au/gazette/result?q=wragge
```

to

```
http://trove.nla.gov.au/newspaper/result?q=wragge&l-title=525&l-title=526
```

Future versions of the harvester might do this automatically, depending on what happens with the API.

## Code

* [TroveHarvester on PyPi <i class="fa fa-external-link" aria-hidden="true"></i>](https://pypi.python.org/pypi/troveharvester)
* [TroveHarvester on GitHub <i class="fa fa-external-link" aria-hidden="true"></i>](https://github.com/wragge/troveharvester)

