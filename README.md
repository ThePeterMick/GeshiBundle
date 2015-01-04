About Geshi library
================================

GeSHi - Generic Syntax Highlighter
(C) 2004 - 2007 Nigel McNie, (C) 2007 - 2008 Benny Baumann

For changes, release notes, TODOs etc, see the relevant files in the docs/
directory.
    
    This file is part of GeSHi.
    
    GeSHi is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.
    
    GeSHi is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.
    
    You should have received a copy of the GNU General Public License
    along with GeSHi; if not, write to the Free Software
    Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

About GeshiBundle
================================

## Bundle Installation

This bundle is non-invasive to the original source code of Geshi.

It can be used within your symfony2 projects or any other that uses composer for package management.

## Bundle Installation with Composer (recommended)

If you are using a Symfony with composer, you need to update your composer.json file, add the entry in the require section and the repositories vcs entry set to our github repository

``` yml
    "require": {
        ...
        "geshi/geshi": "dev-master"
    }
    ...
    "repositories": [
        ...
        {
            "type": "vcs",
            "url": "https://github.com/ptrm04/GeshiBundle.git"
        }
    ]
```
Run composer update:

``` bash
$ php composer.phar update
```

That's it, you can now use the GeshiBundle. There is no need to update your autoload.php when using composer.

## Using the Bundle

Once installed, all you need to do is create new Geshi_Geshi instances, a wee sample:

``` php
// ...
$source = '$foo = 45;
for ( $i = 1; $i < $foo; $i++ ){
  echo "$foo\n";  --$foo;
}';
$language = 'php';
$geshi = new \Geshi_Geshi($source, $language);
return new Response($geshi->parse_code());
// ...
```

**Install using the vendors script**

Add the following lines in your `deps` file:

```
[geshi]
    git=git@github.com:ptrm04/GeshiBundle.git
    target=bundles/geshi
```

Download the bundle:

``` bash
$ php bin/vendors install
```

**Install using git submodules**

``` bash
$ git submodule add git=git@github.com:ptrm04/GeshiBundle.git vendor/geshi
$ git submodule update --init
```

**Install by manually downloading the library**

Download the files and put them under `vendor/geshi` directory.

## Configure the Autoloader

Add the `Geshi_` prefix to your autoloader (not required if you have used composer to install this bundle):

``` php
<?php
// app/autoload.php

$loader->registerPrefixes(array(
    // ...
    'Geshi_'       => __DIR__.'/../vendor/geshi/lib'
));
```
