In the morning
==============

Getting up
----------

-   Turn off alarm
-   Get out of bed

Breakfast
---------

-   Eat eggs
-   Drink coffee

In the evening
==============

Dinner
------

-   Eat spaghetti
-   Drink wine

Going to sleep
--------------

-   Get in bed
-   Count sheep

Pretty code highlighting
========================

Some code from the revealjs presentation
----------------------------------------

``` {.javascript}
function linkify( selector ) {
  if( supports3DTransforms ) {

    var nodes = document.querySelectorAll( selector );

    for( var i = 0, len = nodes.length; i &lt; len; i++ ) {
      var node = nodes[i];

      if( !node.className ) {
        node.className += ' roll';
      }
    }
  }
}
```

Inclusion of R code
===================

R Markdown
----------

This is an R Markdown presentation. Markdown is a simple formatting
syntax for authoring HTML, PDF, and MS Word documents. For more details
on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document.

Slide with R Output
-------------------

``` {.r}
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

Slide with Plot
---------------

![](index_files/figure-markdown/pressure-1.png)
