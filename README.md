Piet
======

Description
-----------

Piet is a gem that optimizes an image stored in a file, and it has
integration with CarrierWave uploaders.

This gem is named after the minimal Dutch painter [Piet Mondrian](http://en.wikipedia.org/wiki/Piet_Mondrian).

[![Build Status](https://secure.travis-ci.org/albertbellonch/piet.png)](http://travis-ci.org/albertbellonch/piet)

Installation
------------

This gem requires two image optimization utilities: **optipng** and
**jpegoptim**, available in various platforms such as Unix or Windows.
You can install them by following the instructions on each authors'
page:

* Installation for [optipng](http://optipng.sourceforge.net/)
* Installation for [jpegoptim](http://freecode.com/projects/jpegoptim)

After installing both utils, simply install the gem:

    gem install piet

Usage
-----

You simply require the gem

    require 'piet'

and then call the **optimize** method:

    Piet.optimize(path, opts)

The options are:

* **verbose**: Whether you want to get the output of the command or not. It is interpreted as a Boolean value. Default: false.


CarrierWave integration
-----------------------

As stated before, Piet can be integrated into CarrierWave uploaders.
This way, you can optimize the original image or a version

Examples
--------

* Simply Optimizing

    ```
    Piet.optimize('/my/wonderful/pics/piggy.png')

    Piet.optimize('/my/wonderful/pics/pony.jpg')
    ```

would optimize those PNG and JPEG files but ouput nothing.

* Optimizing PNG and getting feedback

    ```
    Piet.optimize('/my/wonderful/pics/piggy.png', :verbose => true)
    ```

would optimize that PNG file and ouput something similar to this one:

    ** Processing: piggy.png
    340x340 pixels, 4x8 bits/pixel, RGB+alpha
    Input IDAT size = 157369 bytes
    Input file size = 157426 bytes

    Trying:
      zc = 9  zm = 9  zs = 0  f = 1		IDAT size = 156966
      zc = 9  zm = 8  zs = 0  f = 1		IDAT size = 156932

    Selecting parameters:
      zc = 9  zm = 8  zs = 0  f = 1		IDAT size = 156932

    Output IDAT size = 156932 bytes (437 bytes decrease)
    Output file size = 156989 bytes (437 bytes = 0.28% decrease)

* Optimizing JPEG and getting feedback

    ```
    Piet.optimize('/my/wonderful/pics/pony.jpg', :verbose => true)
    ```

would optimize that JPEG file and ouput similar to this one:

    /my/wonderful/pics/pony.jpg 235x314 24bit JFIF  [OK] 15305 --> 13012 bytes (14.98%), optimized.

TODO
----

* Support for GIFs
* Binary tool for optimizing a file
* Add some testing!
