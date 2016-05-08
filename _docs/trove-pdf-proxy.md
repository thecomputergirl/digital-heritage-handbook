---
date: 2016-05-08
title: Trove PDF Proxy
type: Documentation
tags:
  - Trove
layout: default_module
status: under_construction
---

A simple proxy server that retrieves the url for a PDF generated from a newspaper article in Trove.

See: <http://trove-proxy.herokuapp.com/>

## Usage

`http://trove-proxy.herokuapp.com/pdf/[article_id]`

When the PDF has been generated and is ready for downloading, the server will reply with the url. Use the url to download the PDF!

Try: <http://trove-proxy.herokuapp.com/pdf/76672882>

## Code

* <https://github.com/wragge/trove-proxy>
