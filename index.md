  {#section .hideslideheader data-background="#333"}
-

::: {style="display:table;width:100%;table-layout: fixed;"}
::: {style="display:table-cell;width:20%;height:10%;padding-left:3%"}
![](images/somelogo.png)

 
:::

::: {.title-with-logo style="display:table-cell;width:65%;padding-right:3%;padding-left:3%;vertical-align:middle;"}
RMarkdown presentation template

This is a custom title slide in order to provide more presentation
information (plus a logo)

 
:::
:::

::: {style="display:table;width:100%;table-layout: fixed;"}
::: {.mytitlepage .linksection style="display:table-cell;width:50%;padding-left:3%;vertical-align:bottom;"}
<http://yourdomain.org>

<https://github.com/yoursource>

<https://yourdomain.org/thisprez>

<https://yourfunders.org/generous>
:::

::: {.mytitlepage .authorsection style="display:table-cell;width:50%;padding-right:3%;"}
  **The Speaker**

*Organisation*

 

*Occasion*

*Place*

 

*01. May 2018*

 

*<first.name@yourdomain.org>*
:::
:::

  {#section-1 .hideslideheader data-background="#333"}
-

::: {style="display:table;width:100%;table-layout: fixed;"}
::: {.title-without-logo style="display:table-cell;width:100%;padding-right:3%;padding-left:3%;vertical-align:middle;"}
RMarkdown presentation template

This is a custom title slide in order to provide more presentation
information (without a logo)

 

 

 
:::
:::

::: {style="display:table;width:100%;table-layout: fixed;"}
::: {.mytitlepage .linksection style="display:table-cell;width:50%;padding-left:3%;vertical-align:bottom;"}
<http://yourdomain.org>

<https://github.com/yoursource>

<https://yourdomain.org/thisprez>

<https://yourfunders.org/generous>
:::

::: {.mytitlepage .authorsection style="display:table-cell;width:50%;padding-right:3%;"}
  **The Speaker**

*Organisation*

 

*Occasion*

*Place*

 

*01. May 2018*

 

*<first.name@yourdomain.org>*
:::
:::

Presenter mode
--------------

Speaker notes can be added like this to any section:

``` {.markup}
<aside class="notes">
* These are some *presenter notes*.
* You can use `markdown` in those notes as well.
* Courtesy of the [reveal.js](https://revealjs.com/) framework.
</aside>
```

Press `S` to bring up a window in presenter mode.

<aside class="notes">
-   These are some *presenter notes*.
-   You can use `markdown` in those notes as well.
-   Courtesy of the [reveal.js](https://revealjs.com/) framework.

</aside>
Slide-specific customizations
=============================

Slides without headers
----------------------

You can create slides without headers by adding a horizontal line in the
markdown source:

``` {.markdown}
----

You can create slides without headers by adding a horizontal line in the markdown source:
```

Unfortunately, this prevents usage of additional styles specified with
headers, i.e. this will not work:

``` {.markdown}
---- {data-background="#1E8C45"}
```

A slide with a hidden header {#a-slide-with-a-hidden-header .hideslideheader}
----------------------------

Alternatively use the CSS class `.hideslideheader` to remove a slide
header.

``` {.markdown}
## A slide with a hidden header {.hideslideheader}

Alternatively use the CSS class `.hideslideheader` to remove a slide header.

As in this very slide.
```

As in this very slide.

Blockquotes {#blockquotes .quoteslide .hideslideheader data-background="#222"}
-----------

> "Reveal.js has support for nicely styled blockquotes. You just use the
> standard markdown syntax (i.e. lines preceded by '\> ') to add them.
> This slide uses a custom style (`.quoteslide`) to change the font and
> alignment for quotes as well as provide a different styling and
> alignment for the paragraph below the quote, which is assumed to
> contain a quote attribution.
>
> This has been combined with a hidden header and a different
> background!

Someone, 2018

In the morning
==============

Getting up {#getting-up .center .leftaligned}
----------

-   Turn **off** alarm
-   Get out of bed

Breakfast {#breakfast style="text-align: left;"}
---------

-   Eat eggs
-   Drink coffee

In the evening
==============

Dinner {#leftalignsection}
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

Some markdown
-------------

``` {.markdown}
# hello world

you can write text [with links](http://example.com) inline or [link references][1].

* one _thing_ has *em*phasis
* two __things__ are **bold**

[1]: http://example.com

---
```

Some R code
-----------

``` {.r}
library(rpackagetest)

hello_user <- function(name) {
  if (!is.null(name) && !is.na(name) && nchar(name) > 0) {
    print(paste("Hello, ", name, "!", sep = ""))
  } else {
    print("Hello, stranger!")
  }
}
```

Some YAML code
--------------

``` {.yaml}
---
title: "RMarkdown Presentation Template"
title: "Your Presentation Title"
author: "Your Name"
date: "10 March 2018"
theme: white
highlight: zenburn
transition: slide
---
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
