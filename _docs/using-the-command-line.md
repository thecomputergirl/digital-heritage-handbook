---
date: 2016-05-06
title: Using the command line
type: Documentation
tags:
  - Command line
layout: default_module
status: draft
---

## Opening a terminal

On MacOSX click on the magnifying glass at the top of the screen and search for 'Terminal'. Hit enter to open a terminal window.

On Windows, search for either 'Command prompt' or 'Powershell' and click on the top result.

## Learning to love the command line

There are some excellent tutorials around to ease you into the world of the command line. Start with these ones, especially designed for humanities types:

* [The Command Line <i class="fa fa-external-link" aria-hidden="true"></i>](http://praxis.scholarslab.org/scratchpad/bash/), from the Scholars' Lab
* [Introduction to the Bash Command Line <i class="fa fa-external-link" aria-hidden="true"></i>](http://programminghistorian.org/lessons/intro-to-bash), by Ian Milligan and James Baker, in *The Programming Historian*.

## Powershell permissions

If you're going to use Powershell to do useful things like running Python scripts you'll probably need to change the default permissions.

Search for 'Powershell' as you normally would, but this time right click on the top result. From the menu choose 'Run as administrator'. A new Powershell window will open.

At the Powershell prompt type:

``` shell
> Set-ExecutionPolicy RemoteSigned
```

It'll ask for confirmation. Just hit enter.

## Pasting into a Windows terminal

When you're learning (and when you're not!) you often want to paste commands into the terminal that you've copied from elsewhere. Unfortunately the usual 'Ctrl-v' key combination doesn't work inside Windows terminals.

To paste into the command prompt, click on the command prompt icon at the top left of the window, Choose 'Edit > Paste'.

To paste into Powershell, just right click somewhere inside the window.