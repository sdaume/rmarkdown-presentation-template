  - [Quick setup of your own
    presentation](#quick-setup-of-your-own-presentation)
  - [Background and motivation](#background-and-motivation)
  - [Basic usage](#basic-usage)
      - [Artifacts and workflow](#artifacts-and-workflow)
  - [Advanced options](#advanced-options)
      - [Customized Pandoc template](#customized-pandoc-template)
      - [Syntax highlighting in code
        blocks](#syntax-highlighting-in-code-blocks)
      - [Custom CSS stylesheet](#custom-css-stylesheet)
      - [Use `controlsLayout` option](#use-controlslayout-option)
      - [Mathematical formulas with
        `MathJax`](#mathematical-formulas-with-mathjax)
  - [Custom slide styles - special
    cases](#custom-slide-styles---special-cases)
      - [Hiding slide titles](#hiding-slide-titles)
  - [Publishing and sharing](#publishing-and-sharing)
      - [Publishing via GitHub pages](#publishing-via-github-pages)
      - [Self-contained presentations](#self-contained-presentations)
      - [Export to PDF](#export-to-pdf)
  - [Presentation handouts](#presentation-handouts)
  - [Known issues](#known-issues)
  - [Miscellaneous resources](#miscellaneous-resources)
  - [Licenses](#licenses)

This repository provides a template for browser-based presentations that
are built from [RMarkdown](https://rmarkdown.rstudio.com) documents and
utilizes the [reveal.js](https://revealjs.com) presentation framework
for the generated presentation. [Pandoc](http://pandoc.org) is used to
built the final presentation. The
[highlight.js](https://highlightjs.org) framework is employed to provide
syntax highlighting.

Feel free to fork this repo and use it for your own presentations. Don’t
forget to **credit and observe the licenses of the used tools and
libraries** - ideally both in your [README](#licenses) and the
presentation itself.

Check the [live
version](https://sdaume.github.io/rmarkdown-presentation-template) of
this presentation template.

## Quick setup of your own presentation

Here is how you create a presentation from this repository.

1.  Fork this repository and (optionally) open the project in RStudio.

2.  Edit the `index_metadata.yaml` file with your presentation
    information (only the `title` is mandatory).

3.  Create your presentation by editing the `index.Rmd`. Consult the
    [RMarkdown](https://rmarkdown.rstudio.com) documentation if needed.

4.  [`knitr`](https://yihui.name/knitr/) your presentation (i.e. the
    `index.Rmd`) to create a standard `markdown` file - the default
    result will be `index.md`. (Just press the `knit` button when
    working in RStudio).

5.  Install `pandoc` and run command to produce the final presentation
    (`index.html`):
    
        pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 --mathjax --no-highlight -V highlighting-css=zenburn -V controlsLayout=edges

6.  Open the `index.html` in browser of your choice. Navigate with the
    arrow keys.

7.  Optionally, publish the presentation via GitHub pages (point to
    `master`).

## Background and motivation

The objectives for this template are to:

  - provide a reusable template to deliver high-quality presentations
  - enable data-driven presentations by integrating executable R code
  - create presentations that are easy to share
  - utilize a framework that allows presentations to be converted to PDF
  - create presentations that are permanently accessible and thus easily
    citable, which requires:
      - a permanent storage space for the source (i.e. GitHub repos)
      - a permanent delivery location (i.e. GitHub pages)
  - enable customizations both with regard to styling (CSS), custom
    HTML, Javascript integration (e.g. D3.js charts) and embedded social
    media content
  - create presentation handouts from RMarkdown source and host them
    together with the presentations

Presentations using the **reveal.js** framework and hosted on GitHub
pages meet all of these requirements. In order to utilise the latest
reveal.js features a workflow using [Pandoc](http://pandoc.org) directly
has been chosen over the
[revealjs\_rpackage](https://github.com/rstudio/revealjs).

## Basic usage

### Artifacts and workflow

  - **index.Rmd** is a [`RMarkdown`](https://rmarkdown.rstudio.com) file
    representing the presentation source. Consult the RMarkdown
    documentation for the available markdown syntax. This file could be
    named differently, but using `index` allows to share a shorter URL
    when publishing the presentation via GitHub pages. The file contains
    a minimal `YAML` header to drive the transformation to a `markdown`
    file. The specified target `markdown` format is [full Pandoc
    markdown](https://rmarkdown.rstudio.com/markdown_document_format.html).

  - **index\_metadata.yaml** is a [YAML](http://yaml.org) file
    containing metadata about the presentation itself (title, author,
    date) as well as metadata affecting the styling and rendering of the
    presentations (theme, code highlighting, etc). The minimum YAML
    would be this, because a `title` has to be provided to generate a
    reveal.js presentation:
    
        ---
        title: "Your Presentation Title"
        ---
    
    A YAML file with common variables that add more presentation
    information and picks a `theme` (default is *black*), a code
    highlight style (default is *zenburn*) and `transition` mode
    (default is *slide*) for the slides may look like this:
    
        ---
        title: "Your Presentation Title"
        author: "Your Name"
        date: "10 March 2018"
        theme: white
        highlight: zenburn
        transition: none
        ---

  - **index.md** is the result of *“knitting”* the `Rmd` presentation
    source to plain `markdown`. Either use the **Knit button** in
    RStudio or run `rmarkdown::render("input.Rmd")` from the console.
    The resulting markdown file can now be transformed into the final
    reveal.js presentation using Pandoc.

When the presentation source has been `knitr`ed to plain markdown,
Pandoc has to be run from the command line to generate the final
presentation. This command has been tested with Pandoc 2.1.2 and is run
relative to the directory where the presentation is located:

    pandoc -t revealjs -s -o index.html index.md index_metadata.yaml 
      -V revealjs-url=./reveal.js-3.6.0

The command specifies the target template (`-t revealjs`), the output
file (`-o index.html`), all input files (`index.md index_metadata.yaml`)
and a template variable for the location of the revealjs assets (`-V
revealjs-url=./reveal.js-3.6.0`). The setup in this repo opts for
keeping a local copy of the revealjs library. Alternatively, a remote
location could be specified: `-V
revealjs-url=http://lab.hakim.se/reveal-js` (see also
[here](https://github.com/jgm/pandoc/wiki/Using-pandoc-to-produce-reveal.js-slides)).
**However**, in that case the presentation will not be standalone and an
internet connection will be needed to show the slides. Furthermore,
revealjs’s presenter mode (triggered by pressing `s`) will not work.

## Advanced options

### Customized Pandoc template

This repo contains a custom Pandoc reveal.js template in order to enable
support for more recent features in the reveal.js framework. In order to
use this custom template run the following command relative to the
directory where the presentation is located:

    pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 

### Syntax highlighting in code blocks

Reveal.js comes packaged with a default code highlighting style
`zenburn`. In order for code highlighting with
[highlight.js](https://highlightjs.org/) to work, the custom Pandoc
template has to be used and Pandoc’s own highlighting has to be disabled
(`--no-highlight`). This can be accomplished with the following command:

    pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 --no-highlight -V highlighting-css=zenburn

This ensures that Pandoc does not parse and markup the code block. The
modifications in the custom Pandoc template trigger the highlight.js
library to be loaded and initialised. If the language for code block has
not been provided, highlight.js will try to determine it automatically.
See examples in the included slides.

Consult [highlight.js](https://highlightjs.org/) for the available
styles and supported languages. [highlight.js](https://highlightjs.org/)
offers downloads of customized packs. One of those has been included
here which provides support for “common” languages as well as `R`,
`YAML` and `Tex`.

### Custom CSS stylesheet

In order to include custom styles that can be referenced in individual
sections or to change presentation-wide styles a custom CSS stylesheet
can be specified. An example is included in the `css` folder of this
template.

Either specify the CSS in the YAML by adding a line containing `css:
./css/mycustom.css` or provide it as option to the `pandoc` command as
`-V css:=./css/mycustom.css`.

The example included here changes for example the base font size and
removes borders around images (presentation-wide). Furthermore, it adds
a custom style for slides with a `blockquote` and for slides which
should have hidden titles.

### Use `controlsLayout` option

The [reveal.js
v3.6.0](https://github.com/hakimel/reveal.js/releases/tag/3.6.0) added
support for the `controlsLayout` option, which allows to display
navigation arrows on the edges. This option seems to work only when
provided as an argument to the `pandoc` command. Use:

    pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 -V controlsLayout=edges

### Mathematical formulas with `MathJax`

Reveal.js provides [built-in
support](https://github.com/hakimel/reveal.js/#mathjax) for the
rendering of mathematical formulas using the [MathJax
library](https://www.mathjax.org). By default a remote repo of MathJax
is utilised for the rendering. In order to enable MathJax support the
Pandoc `mathjax` flag has to be included when processing the Markdown
source:

    pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 --mathjax

This repo includes a local (unmodified) copy of MathJax to enable
standalone offline presentations. The custom Pandoc template has been
modified accordingly in order point to the local copy of MathJax and
sets `TeX-MML-AM_SVG-full` as the default configuration file; the SVG
output processor (see MathJax documentation) has been chosen as it seems
to work best across different browsers.

**Note**, the full MathJax library is rather large. If a presentation
does not require support for mathematical formulas, it might be prudent
to remove it from the presentation repository.

## Custom slide styles - special cases

This section summarizes some styles that have been provided in the
custom CSS stylesheet for use in individual slides. This is not a
comprehensive list, but the template presentation contains examples for
all customization.

### Hiding slide titles

A slide without a title can be created by adding a horizontal line
`----` in the markdown document. The drawback of this approach is that
no styles can be used in this case, i.e. adding something like
`{data-background="#f2f2f2"}` after this line will not work anymore.

One workaround is to define a heading with an explicit whitespace as the
heading title: `## &nbsp; {data-background="#f2f2f2"}`. This can now be
treated as any other heading, that is styles can be added. The drawback
of this approach is that even an empty title will take up space on the
slide. The alternative is to add a custom style to the header that will
remove it:

    ## Some descriptive title {.hideslideheader data-background="#f2f2f2"}

This has the added advantage that you can still benefit from descriptive
titles, that might be useful even if not visible in the presentation
itself.

## Publishing and sharing

Publishing steps:

  - enable GitHub pages for the presentation
  - create a PDF and include a link in the presentation and README
  - consider publishing the PDF to Speakerdeck and include a link in
    your README
  - consider creating a DOI via Zenodo and create a nice badge to
    advertise that the presentation is citable
  - add some nice badges on top of your README to highlight the
    different formats to readers

### Publishing via GitHub pages

***TBD***

### Self-contained presentations

***TBD***

### Export to PDF

revealjs comes with a [default
option](https://github.com/hakimel/reveal.js#pdf-export) for creating
PDF copies of a presentation. However, this requires that you use Google
Chrome or Chromium and that the presentation is served from a webserver.
Consult the [revealjs
documentation](https://github.com/hakimel/reveal.js) for more
information.

A more versatile option is to use
[DeckTape](https://github.com/astefanutti/decktape). Install it via
`npm` and then run for example:

    decktape reveal <PRESENTATION_URL> <FILENAME>.pdf

This will result in a high-quality PDF copy of your presentation that
can be shared.

`decktape` offers a number of other options. A great feature is the
ability to export slides as invidual images (png, jpg). This is an added
benefit if you want to include some images of your slides in handouts.
The following command creates slide images of a presentation in addition
to the PDF:

    decktape reveal <PRESENTATION_URL> <FILENAME>.pdf --screenshots --screenshots-directory ./handouts/screenshots

Consult the [decktape
documentation](https://github.com/astefanutti/decktape) for more
configuration options.

## Presentation handouts

***TBD***

## Known issues

  - center option does not work from YAML; the option `center` does only
    work when provided as a Pandoc variable

## Miscellaneous resources

## Licenses

This repository utilises and/or includes components from the
[reveal.js](https://revealjs.com/), [Pandoc](https://pandoc.org/),
[highlight.js](https://highlightjs.org) and
[MathJax](https://www.mathjax.org) frameworks. The following licenses
apply:

  - **reveal.js** is [released](https://github.com/hakimel/reveal.js)
    under this [MIT
    license](https://github.com/hakimel/reveal.js/blob/master/LICENSE).
  - **Pandoc** is [released](https://github.com/jgm/pandoc) under this
    [GPLv2 license](https://github.com/jgm/pandoc/blob/master/COPYRIGHT)
  - **Pandoc templates** are
    [released](https://github.com/jgm/pandoc/tree/master/data/templates)
    under this dual [GPLv2 and BSD3
    license](https://github.com/jgm/pandoc/blob/master/data/templates/README.markdown).
  - **highlight.js** is
    [released](https://github.com/isagalaev/highlight.js) under this
    [BSD
    license](https://github.com/isagalaev/highlight.js/blob/master/LICENSE).
    **NOTE** that highlight.js [offers customized
    downloads](https://highlightjs.org/download/) with support for
    selected languages, the pack chosen for this presentation template
    includes support for “common” languages as well as `R`, `YAML` and
    `Tex`.
  - **MathJax** is [released](https://github.com/mathjax/MathJax) under
    this [Apache 2.0
    license](https://github.com/mathjax/MathJax/blob/master/LICENSE). An
    unmodified local copy of MathJax is utilised in this repository.
  - **[knitr](https://github.com/yihui/knitr)** and the
    **[tufte](https://github.com/rstudio/tufte)** packages have been
    used to generate presentation handouts. The former is released under
    a GPL2/GPL3 license and the latter under a GPL3 license.

Other credits:

  - **DeckTape** has been used to create a PDF copy of this presentation
    template as well as slide screenshots for the handouts. **DeckTape**
    is [released](https://github.com/astefanutti/decktape) is released
    under this [MIT
    license](https://github.com/astefanutti/decktape/blob/master/LICENSE).

**Make sure to credit these libraries and provide references to the
applicable licenses when forking this repository.**

All other contents in this repository that have been authored by me are
licensed under *[CC BY](https://creativecommons.org/licenses/by/4.0/)*.
