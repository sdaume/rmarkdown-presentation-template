# Background
This repository provides a template for browser-based presentations that are built from [RMarkdown](https://rmarkdown.rstudio.com) documents and utilizes the [reveal.js](https://revealjs.com) presentation framework for the generated presentation. 

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

# Items to discuss
* Mention that presentations generated with the [revealjs_rpackage](https://github.com/rstudio/revealjs) are missing the presenter mode feature
* the latest controlsLayout feature is not working 
* the option `center` does only work when provided as a Pandoc variable
* there seems to be no way to get rid of the default title page



