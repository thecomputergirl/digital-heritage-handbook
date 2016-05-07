---
date: 2016-05-07
title: Creating simple charts with Plot.ly
type: Activities
tags:
  - Plot.ly
layout: default_module
status: under_construction
---

Plotly is a web service that helps you make a variety of online charts.

In this activity we're going to create some simple bar charts using data from the South Australian census.

Before you get started, you should visit  [Plotly <i class="fa fa-external-link" aria-hidden="true"></i>](https://plot.ly/) and create a free account.

## Grabbing some data

We're going to use data from the [1901 South Australian Census <i class="fa fa-external-link" aria-hidden="true"></i>](http://hccda.ada.edu.au/documents/SA-1901-census), made available online by the [Australian Data Archive <i class="fa fa-external-link" aria-hidden="true"></i>](http://ada.edu.au/ada/home).

On [page eight of the census](http://hccda.ada.edu.au/pages/SA-1901-census-01_8) is a table showing South Australia's population in 1901 by division. The table also includes comparative figures for 1881 and 1891, and a breakdown by gender.

[![1901 SA Census, page 8]({{ site.baseurl }}/images/sa-census-1901.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/sa-census-1901.png)

Importantly, the table has been converted to HTML, so it is displayed on the website as text, rather than as an image. This means we can easily copy the data into Plotly.

Open up [the table](http://hccda.ada.edu.au/pages/SA-1901-census-01_8) in a new window and then click and drag from the left of 'Adelaide' to the bottom right hand corner of the table. You should have selected all of the data rows. Copy your selection using 'ctrl-c' or 'command-c' (depending on your operating system).

## Preparing the data in Plotly

Log in to your Plotly account and click on the 'New Project' button. Once your project opens click on the 'New Grid' tab to open up an empty table.

Change the chart type from 'Line plot' to 'Bar chart' using the dropdown selector to the left of the grid. You should have something that looks like this:

[![Plotly grid interface]({{ site.baseurl }}/images/plotly-grid.png){: .img-responsive .img-example }]({{ site.baseurl }}/images/plotly-grid.png)

Click in the first empty cell and paste in the census data using 'ctrl-v' or 'command-v' (depending on your operating system). The data from the census should magically fill the Plotly grid!

Click the down arrow next to the 'Col1' heading and choose 'Rename'. Type in 'Division' and hit enter. Column 1 in your grid should now be labelled 'Division'. Use the same method to change the name of column 2 to '1881', column 7 to '1891', and column 12 to '1901'. Your grid should now look like this:

[![Plotly grid interface with values]({{ site.baseurl }}/images/plotly-grid-2.png){: .img-responsive .img-example}]({{ site.baseurl }}/images/plotly-grid-2.png)

## Creating a bar chart

We need to tell Plotly which values to use for the X and Y axes of our chart. The 'Division' column might already have 'choose as x' highlighted. If not, click on 'choose as x'.

Now make sure 'choose as y' is highlighted for the '1881', '1891', and '1901' columns. By selecting multiple 'y' values we'll be able to see the values for each year grouped together by division.

We're ready to make a chart! Click on the blue 'Bar Chart' button. You'll be asked to give your grid a name -- enter something like 'SA Census 1901' and click 'Save'. Your bar chart should then appear. Hooray!

Click where it says 'Click to enter Plot title' and give your chart a name. In the same way you can label the Y axis 'Population' and the X axis 'Division.

Here's a live, embedded version of the completed chart:

<div>
    <a href="https://plot.ly/~wragge/412/" target="_blank" title="Population of South Australia, 1901 Census" style="display: block; text-align: center;"><img src="https://plot.ly/~wragge/412.png" alt="Population of South Australia, 1901 Census" style="max-width: 100%;width: 1983px;"  width="1983" onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="wragge:412"  src="https://plot.ly/embed.js" async></script>
</div>

One great thing about Plotly is that you can easily share your charts. Click on the 'Share' button on the left hand side of your chart. You might be asked to save your chart. Eventually the share dialogue will open. Click on 'Sharable link' and copy the url. You can now share this link with friends and colleagues. To embed the chart in your own website, click on 'Embed', copy the code, and paste it where you want it.

## Modifying your chart

One problem with our chart is that the population of Adelaide is so much greater than the other divisions that it's difficult to see what's going on elsewhere. Let's create a version that excludes Adelaide.

Go back to the original data grid and click on 'Copy'. A new grid will open with the census data. You'll need to reselect 'Bar chart' as the chart type, and make sure '1881', '1891', and '1901, are all selected as Y values as we did before.

Now highlight the first row by clicking on the '1' -- this selects all the Adelaide data. Right click on the row and select 'Remove selected rows'. Save your grid and generate a chart as you did before. Your new chart should look something like this:

<div>
    <a href="https://plot.ly/~wragge/414/" target="_blank" title="Population of South Australia (excluding Adelaide), 1901 Census" style="display: block; text-align: center;"><img src="https://plot.ly/~wragge/414.png" alt="Population of South Australia (excluding Adelaide), 1901 Census" style="max-width: 100%;width: 1983px;"  width="1983" onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="wragge:414"  src="https://plot.ly/embed.js" async></script>
</div>

## Things to try

* Can you make a chart that shows the male and female populations for each division in 1901?



