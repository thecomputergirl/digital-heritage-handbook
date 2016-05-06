---
date: 2016-04-25
title: Setting up Python, Pip, and Virtualenv
type: Documentation
tags:
  - Python
layout: default_module
status: draft
---

[Python <i class="fa fa-external-link" aria-hidden="true"></i>](https://www.python.org/) is a programming language that is relatively easy to learn and particularly popular with researchers. Lots of useful tools depend on it. This page should help you get Python up and running on your own computer.

Before we get started, make sure you know how to [open a terminal and are ready to start entering commands]({{ site.baseurl }}/docs/using-the-command-line/) using the command line.

## Installation

### MacOSX and Linux

Good news, you probably already have Python! Open up a terminal and type:

``` bash
$ python --version
```

If you have a recent version of MacOSX or Linux you should see something like:

``` bash
$ Python 2.7.10
```

If it says `2.7.[some number]` you should be right to go. Note, however, that the version of Python that comes with MacOSX is not recommended for development work. So if you want to go further than running something simple like my Trove Harvester you might want to [install a standard version of Python <i class="fa fa-external-link" aria-hidden="true"></i>](http://docs.python-guide.org/en/latest/starting/install/osx/#install-osx). 

### Windows

Go the the Python downloads page and download a Python installer. You'll have to choose between [Python 2 and Python 3 <i class="fa fa-external-link" aria-hidden="true"></i>](http://docs.python-guide.org/en/latest/starting/which-python/#the-state-of-python-2-vs-3). I'll assume you've gone with Python 2.

Once the file has dowloaded, just double click to install python.

{: .bg-danger .bg-context}
<i class="fa fa-exclamation-triangle" aria-hidden="true"></i> When the installer presents you with a list of components you can install, make sure you check the option to modify your system path. This will make it easier for you to run Python programs.

See [this guide <i class="fa fa-external-link" aria-hidden="true"></i>](http://docs.python-guide.org/en/latest/starting/install/win/) for more detailed information on the Windows installation process.

## Installing pip

Pip is the Python package installation tool. If you have a recent version of Python you should have pip already. Try:

``` shell
$ pip -h
```

You should see the pip help documentation.

If pip isn't installed you need to download the `get-pip.py` script and run it:

``` shell
$ python get-pip.py
```

See the [pip documentation <i class="fa fa-external-link" aria-hidden="true"></i>](https://pip.pypa.io/en/latest/installing/) for more details.

{: .bg-danger .bg-context}
<i class="fa fa-exclamation-triangle" aria-hidden="true"></i> If you get permission errors in Powershell when you try to run pip, you might need to [adjust your permission settings]({{ site.baseurl }}/docs/using-the-command-line/#powershell-permissions).

## Installing virtualenv

Virtualenv is another key Python tool. It enables you to create a series of controlled environments where you can install and experiment with Python modules without upsetting any previously installed software.

Installing it should simply be a matter of typing:

``` shell
$ pip install virtualenv
```

## Creating and activating a virtual environment

To create a new virtual environment, type:

``` shell
$ virtualenv [name of your new virtual environment]
```

Virtualenv will create a directory with the name you supplied and install all the bits and pieces you need inside it. 

Once it's finished, open the new directory by typing:

``` shell
$ cd [name of your new virtual environment]
```

Now you need to activate your environment. On MacOSX and Linux type:

``` shell
$ source bin/activate
```

On Windows using the command prompt, type:

``` shell
> Scripts\activate
```

On Windows using Powershell, type:

``` shell
> Scripts\activate.ps1
```

Your command prompt should now include the name of your environment in brackets. This is a reminder that your virtual environment is active.

Now if you use pip to install Python packages, they'll only be installed inside this environment. 

To deactivate, type:

``` shell
$ deactivate
```


