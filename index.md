  {#section .hideslideheader data-background="#333"}
-

::: {style="display:table;width:100%;table-layout: fixed;"}
::: {style="display:table-cell;width:20%;height:10%;padding-left:3%"}
![](images/somelogo.png)

 
:::

::: {.title-with-logo style="display:table-cell;width:65%;padding-right:3%;padding-left:3%;vertical-align:middle;"}
RMarkdown Presentation template

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

Heading levels: `#` vs `##`
===========================

Level 1 headings (i.e. `#`) do only allow header text!
======================================================

Additional slide text will only work with level 2 headings (i.e. `##`)
======================================================================

Like this one
-------------

-   which also opens up
-   another navigation level

Pressing the `Esc` key
----------------------

-   zooms out of the current presentation
-   and illustrates how level 1 and 2 headings structure a presentation

Presenter mode
==============

reveal.js supports speaker notes in presenter mode
--------------------------------------------------

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

Create your own custom CSS
--------------------------

The following slides show some of the styles included in the custom CSS
stylesheet for this template.

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

Smaller text
------------

<small>If you need text in certain paragraphs to be smaller you can wrap
it in `<small>` tags. This will apply to `<code>` sections that may be
enclosed between the small tags:

``` {.markdown}
<small>
If you need text in certain paragraphs to be smaller you can wrap it in `<small>` tags. 
</small>
```

And it will work across multiple paragraphs. </small>

More smaller text {#more-smaller-text .xs-small-pg-text}
-----------------

More control is possible with the use of CSS classes. Simply add one of
the classes that only apply only to paragraphs, for example:

``` {.markdown}
## More smaller text {.xs-small-pg-text}
```

  CSS class            Font size
  ------------------ -----------
  small-pg-text            0.9em
  x-small-pg-text          0.8em
  xs-small-pg-text         0.6em

... or you {#or-you style="font-size:0.6em;"}
----------

add a style to the header to resize everything on the slide.

**Code:**

``` {.markdown}
## ... or {style="font-size:0.6em;"}
```

**Tables:**

  CSS class            Font size
  ------------------ -----------
  small-pg-text            0.9em
  x-small-pg-text          0.8em
  xs-small-pg-text         0.6em

**Lists:**

-   Item 1
-   Item 2

Align slide left {#align-slide-left .center .left-aligned-slide}
----------------

This should:

-   align **all** elements
-   on a page left

Simply add:

``` {.markdown}
## Align slide left {.left-aligned-slide}
```

Align slide right {#align-slide-right .right-aligned-slide}
-----------------

Similarly, this will

-   align **all** elements
-   on a page right
-   by adding

``` {.markdown}
## Align slide right {.right-aligned-slide}
```

Vertical alignment {#vertical-alignment .top-aligned-slide .left-aligned-slide}
------------------

Generally, it will be visually more appealing to have slide content
vertically centered. This can be switched off by using the
`-V center=false` option with the `pandoc` command. Individual slides
could then be centered by adding `.center` to the slide header:

``` {.markdown}
## Vertically center this slide {.center}
```

If most slides are vertically centered and only a few slides need to be
aligned to the top the following class can be used.

``` {.markdown}
## Align slide to top {.top-aligned-slide}
```

But this is a bit of a hack because it has to use `!important` in the
CSS class definition.

Blockquotes {#blockquotes .quoteslide .hideslideheader data-background="#222"}
-----------

> \"Reveal.js has support for nicely styled blockquotes. You just use
> the standard markdown syntax (i.e. lines preceded by '\> ') to add
> them. This slide uses a custom style (`.quoteslide`) to change the
> font and alignment for quotes as well as provide a different styling
> and alignment for the paragraph below the quote, which is assumed to
> contain a quote attribution.
>
> This has been combined with a hidden header and a different
> background!

Someone, 2018

Pretty code highlighting
========================

Javascript
----------

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

Markdown
--------

``` {.markdown}
# hello world

you can write text [with links](http://example.com) inline or [link references][1].

* one _thing_ has *em*phasis
* two __things__ are **bold**

[1]: http://example.com

---
```

R
-

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

YAML
----

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

Mathematical formulas
=====================

Rendering mathematical notations
--------------------------------

By default a local copy of [MathJax](https://www.mathjax.org) is
included and utilised to support the correct rendering of mathematical
formulas. A notation included as

``` {.markdown}
$$\sum_{n=1}^{10} n^2$$
```

is rendered by MathJax as

`$$\sum_{n=1}^{10} n^2$$`

Thank You!
==========

Colophon {#colophon .colophon}
--------

**"RMarkdown presentation template"** by *The Speaker*

 

Presented at [occasion]() on \[this date\].

 

This presentation can be cited using: *doi:...*

 

**PRESENTATION DETAILS**

**Author/Affiliation:** The Speaker, Organisation

**Contributors:** Person 1, Person 2 and Person 3

**Presentation URL:**
<https://sdaume.github.io/rmarkdown-presentation-template>

**Presentation Handouts:**
[https://sdaume.github.io/rmarkdown-presentation-template\\handouts](https://sdaume.github.io/rmarkdown-presentation-template\handouts){.uri}

**Presentation Source:**
<https://github.com/sdaume/rmarkdown-presentation-template>

**Presentation PDF:** Speakerdeck

 

**CREDITS & LICENSES**

This presentation is delivered with the help of several free and open
source tools and libraries. It utilises the
[reveal.js](https://revealjs.com/) presentation framework and has been
created using [RMarkdown](https://rmarkdown.rstudio.com),
[knitr](https://yihui.name/knitr/), [RStudio](https://www.rstudio.com)
and [Pandoc](https://pandoc.org/).
[highlight.js](https://highlightjs.org) provides syntax highlighting for
code sections. [MathJax](https://www.mathjax.org) supports the rendering
of mathematical notations. PDF and JPG copies of this presentation were
generated with [DeckTape](https://github.com/astefanutti/decktape).
Please note the respective licenses of these tools and libraries.

 

If not noted and attributed otherwise, the contents (text, charts,
images) of this presentation are **Copyright © 2018 of the Author**.
