---
layout: page
title: Image Gallery using Sigal 
permalink: /docs/image-gallery-sigal/
resource: true
categories:
- Web Publishing 
---

## How to Use 

Initialize
:   To get started, just run `sigal init` which will copy an example
    [configuration file](http://sigal.saimon.org/en/latest/configuration.html) in the current
    directory.

    All configuration values have a default; values that are commented
    out serve to show the default. Default values are specified when
    modified in this example config file.

Build
:   After adapting the configuration to your needs, put your images in a
    sub-directory and run `sigal build <your images directory>`.

    The next time you run `sigal build`, only the new images will be
    processed. You can use the `-f` flag to force the reprocessing of
    all the images. Images (resp. videos) that are smaller than the size
    specified by the `img_size` (resp. `video_size`) setting will not be
    resized.

    You may also want to know how to specify information about
	[albums](http://sigal.saimon.org/en/latest/album_information.html) and [images](http://sigal.saimon.org/en/latest/image_information.html).

## Example usage

If I wanted to generate a galery from a folder full of images and access them on my user directory I'd do the following:

    sigal build Pictures public_html

## Help on the `sigal build` command

    $ sigal build [-h] [-d] [-v] [-f] [-c CONFIG] [-t THEME] [-n NCPU]
            [source] [destination]

Required arguments:

`source`
:   Input directory

`destination`
:   Output directory (default: `_build/`)

Optional arguments:

`-h, --help`
:   Show this help message and exit

`-f, --force`
:   Force the reprocessing of existing images and thumbnails

`-v, --verbose`
:   Show all messages

`-d, --debug`
:   Show all message, including debug messages

`-c CONFIG, --config CONFIG`
:   Configuration file (default: `sigal.conf.py` in the current working
    directory)

`-t THEME, --theme THEME`
:   Specify a theme directory, or a theme name for the themes included
    with Sigal

`-n NCPU, --ncpu NCPU`
:   Number of cpu to use (default: all)

## More Information

This documentation was taken from <http://sigal.saimon.org/en/latest/>. Check them out.
