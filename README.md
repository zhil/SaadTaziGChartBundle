What is it?
===========
This is a super simple Bundle that facilitate the usage of [Google Chart Tool](http://code.google.com/apis/chart/interactive/docs/index.html), [Google Chart Image API](http://code.google.com/apis/chart/image/) and [Google Infographics](http://code.google.com/apis/chart/infographics/).

It allows to render:

  * QRCode 
  * Pie Chart (3 ways: canvas or svg, simple image from url, simple 3d image from url)
  * Column Chart
  * Bar Chart
  * Area Chart
  * scatter Chart
  * Combo Chart
  * Table
  * Gauge
  * Candlestick Chart
  * Map tree
  * Dynamic Icons

Make sure you read the [Chart Image terms](http://code.google.com/apis/chart/image/terms.html) and [Chart tool terms](http://code.google.com/apis/chart/interactive/terms.html) before using that bundle. 

It also contains some Twig extension that facilitates the integration.

Demo
----

http://blog.fruitsoftware.com/a-propos/demo-gchartbundle/

How to install it?
------------------

Thanks to [AaronDDM](http://example.com/ "AaronDDM"), you can use 
[composer](http://packagist.org/packages/saad-tazi/g-chart-bundle "composer") to instlall the bundle. 
```
composer require saad-tazi/g-chart-bundle
```

Or you can use the following method:

  1. Add this bundle to your ``vendor/`` dir:
      * Using the vendors script.

        Add the following lines in your ``deps`` file:

            [SaadTaziGChartBundle]
                git=git://github.com/saadtazi/SaadTaziGChartBundle.git
                target=/bundles/SaadTazi/GChartBundle

        Run the vendors script:

            ./bin/vendors install

      * Using git submodules.

            $ git submodule add git://github.com/saadtazi/SaadTaziGChartBundle.git vendor/bundles/SaadTazi/GChartBundle

  2. Add the SaadTazi namespace to your autoloader:

``` php

          // app/autoload.php
          $loader->registerNamespaces(array(
                'SaadTazi' => __DIR__.'/../vendor/bundles',
                // your other namespaces
          ));
```

  3. Add this bundle to your application's kernel:

``` php

          // app/ApplicationKernel.php
          public function registerBundles()
          {
              return array(
                  // ...
                  new SaadTazi\GChartBundle\SaadTaziGChartBundle(),
                  // ...
              );
          }
```

Optional: If you want to see the demo page, add the following to your routing.yml (requires Twig):

``` yaml
    _demo:
        resource: "@SaadTaziGChartBundle/Resources/config/routing.yml"
        type:     yaml
        prefix:   /gchart
```

Then you should be able to go to http://your.site.com/gchart/demo

Don't forget to include the required javascript in your layout, for example:

```
        <script type="text/javascript">
            // adds the package you need
            google.load("visualization", "1", {packages:["corechart", 'table', 'gauge']});
        </script> 
```

How to use it?
--------------

Mmm, please check the Controller\DemoController to see how to build DataTable,
and Resources\views\Demo\demo.html.twig

Notes
-----
I implemented almost all the corechart chart types from the Google Chart Tool.
But I only implemented 3 Google Chart Image types, because 
(<strike>they are ugly and</strike>) almost all of them can be built using 
the Google Chart Tool.
From the Visualization, I only implemented the marker. 

Ohh, please feel free to fork, add to it and send me pull requests!

Note: You don't have to use the Twig functions: you can use the php classes (in DataTable and or in Chart).
But you will probably find it a little bit "painful".

Mods
----

2012-03-20

* added composer support (thanks to AaronDDM)

2011-10-23 

* removed jQuery dependency (and div output - needs to be done "manually" now... Provides more control)

2011-09-22 

* zero value bug fix

2011-09-06

* Added DataTable::toStrictArray() that checks array keys (ticket #1)

2011-06-23

* Initial commit
