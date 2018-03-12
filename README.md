# README
This repository provides a template for browser-based presentations that are built from [RMarkdown](https://rmarkdown.rstudio.com) documents and utilizes the [reveal.js](https://revealjs.com) presentation framework for the generated presentation. [Pandoc](http://pandoc.org) is used to built the final presentation. The [highlight.js](https://highlightjs.org) framework is employed to provide syntax highlighting.

Feel free to fork this repo and use it for your own presentations. Don't forget to **observe the licenses of the used tools and libraries** and **give credit** - ideally both in your [README](#credits---used-tools-and-licenses) and the presentation itself.


## Table of contents
***Coming SOON!***



## Background and motivation
The objectives for this template are to:

* provide a reusable template to deliver high-quality presentations
* enable data-driven presentations by integrating executable R code
* create presentations that are easy to share 
* utilize a framework that allows presentations to be converted to PDF
* create presentations that are permanently accessible and thus easily citable, which requires:
  * a permanent storage space for the source (i.e. GitHub repos) 
  * a permanent delivery location (i.e. GitHub pages)
* enable customizations both with regard to styling (CSS), custom HTML, Javascript integration (e.g. D3.js charts) and embedded social media content
* create presentation handouts from RMarkdown source and host them together with the presentations

Presentations using the **reveal.js** framework and hosted on GitHub pages meet all of these requirements. In order to utilise the latest reveal.js features a workflow using [Pandoc](http://pandoc.org) directly has been chosen over the [revealjs_rpackage](https://github.com/rstudio/revealjs). 


## Quick start
***Coming SOON!***


## Basic usage
### Artifacts and workflow

**index.Rmd** is a [`RMarkdown`](https://rmarkdown.rstudio.com) file representing the presentation source. Consult the RMarkdown documentation for the available markdown syntax.  This file could be named differently, but using `index` allows to share a shorter URL when publishing the presentation via GitHub pages.
The file contains a minimal `YAML` header to drive the transformation to a  `markdown` file. The specified target `markdown` format is  [full Pandoc markdown](https://rmarkdown.rstudio.com/markdown_document_format.html). 

**index.md** is the result of *"knitting"* the `Rmd` presentation source to plain `markdown`. Either use the **Knit button** in RStudio or run  `rmarkdown::render("input.Rmd")` from the console. The resulting markdown file can now be transformed into the final reveal.js presentation using Pandoc.

Two additional files are needed as input for Pandoc.

**index_metadata.yaml** is a [YAML](http://yaml.org) file containing metadata about the presentation itself (title, author, date) as well as metadata affecting the styling and rendering of the presentations (theme, code highlighting, etc). The minimum YAML would be this, because a `title` has to be provided to generate a reveal.js presentation:

```
---
title: "Your Presentation Title"
---
```

A YAML file with common variables that add more presentation information and picks a `theme` (default is *black*), a code highlight style (default is *zenburn*) and `transition` mode (default is *slide*) for the slides may look like this:

```
---
title: "Your Presentation Title"
author: "Your Name"
date: "10 March 2018"
theme: white
highlight: zenburn
transition: none
---
```

When the presentation source has been `knitr`ed to plain markdown, Pandoc has to be run from the command line to generate the final presentation. This command has been tested with Pandoc 2.1.2 and is run relative to the directory where the presentation is located:

```
pandoc -t revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0
```

The command specifies the target template (`-t revealjs`), the output file (`-o index.html`), all input files (`index.md index_metadata.yaml`) and a template variable for the location of the revealjs assets (`-V revealjs-url=./reveal.js-3.6.0`). The setup in this repo opts for keeping a local copy of the revealjs library. Alternatively, a remote location could be specified: `-V revealjs-url=http://lab.hakim.se/reveal-js` (see also [here](https://github.com/jgm/pandoc/wiki/Using-pandoc-to-produce-reveal.js-slides)). **However**, in that case the presentation will not be standalone and an internet connection will be needed to show the slides. Furthermore, revealjs's presenter mode (triggered by pressing `s`) will not work.



## Advanced usage
### Customized Pandoc template
This repo contains a custom Pandoc reveal.js template in order to enable support for more recent features in the reveal.js framework. In order to use this custom template run the following command relative to the directory where the presentation is located:

```
pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 
```

### Use `controlsLayout` option
The [reveal.js v3.6.0](https://github.com/hakimel/reveal.js/releases/tag/3.6.0) added support for the `controlsLayout` option, which allows to display navigation arrows on the edges. This option seems to work only when provided as an argument to `pandoc` command. Use:

```
pandoc -t revealjs --template=./custom_pandoc_template/default.revealjs -s -o index.html index.md index_metadata.yaml -V revealjs-url=./reveal.js-3.6.0 -V controlsLayout='edges'
```

## Known issues
* center option does not work from YAML; the option `center` does only work when provided as a Pandoc variable
* controlsLayout does not work at all


## Miscellaneous resources


## Credits - Used tools and licenses
***Coming SOON!***


