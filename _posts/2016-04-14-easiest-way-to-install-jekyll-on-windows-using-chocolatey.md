---
layout: post
title: Easiest Way to Install Jekyll on Windows using Chocolatey
description: Chocolatey is the BEST way to install and keep applications updated on Windows.
keywords: jekyll installation, windows os, chocolatey
---

Have you heard about Chocolatey? Chocolatey is the BEST way to install and keep applications updated on Windows. Let's not waste the time, here are the steps.

**STEP01.** Open a command prompt with Administrator access

**STEP02.** Paste this to install [Chocolatey](https://chocolatey.org/):

```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

**STEP03.** Close the command prompt as Chocolatey will not be available until we close and reopen.

**STEP04.** Open a command prompt again with Administrator access

**STEP05.** Paste this to install [Ruby](https://chocolatey.org/packages/ruby):

```
choco install ruby -y
```

**STEP06.** Close and reopen a new command prompt again with Administrator access

**STEP07.** Paste this to install [Jekyll](https://jekyllrb.com/):

```
gem install jekyll
```

**STEP08.** Done! Now we can use standard Jekyll commands to create a new site and serve it:

```
jekyll new myblog
cd myblog
jekyll serve
```

Credit: [David Burela](https://davidburela.wordpress.com/2015/11/28/easily-install-jekyll-on-windows-with-3-command-prompt-entries-and-chocolatey/)
