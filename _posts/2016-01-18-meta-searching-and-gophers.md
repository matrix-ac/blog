---
layout: post
title:  "Meta Searching and Gophers"
date:   2016-01-18 09:28:01
categories: server
---
**TL;DR** Searx instance and gopher service. 

# Meta Searching
For the past few months we have been trialing a Searx instance. Searx is a meatasearch engine, which aggregates the results of other search engines without storing any private information,

You can access it: <https://matrix.ac/searx> checkout the [about page](/searx/about) which will answer some of your questions.

## Gopher

We've also been messing around with the [gopher protocol](https://en.wikipedia.org/wiki/Gopher_%28protocol%29). We now run a gopher service. If you wish to create a gopher page create a folder called "public_gopher" and that will be served up as <gopher://matrix.ac/~username>. 

For a good client we recommend [cgo](https://github.com/kieselsteini/cgo).
