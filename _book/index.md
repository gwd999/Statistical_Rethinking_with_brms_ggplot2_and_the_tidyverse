--- 
title: "*Statistical rethinking* with brms, ggplot2, and the tidyverse"
subtitle: "version 1.2.0"
author: ["A Solomon Kurz"]
date: "2020-10-11"
site: bookdown::bookdown_site
output: bookdown::gitbook
documentclass: book
bibliography: bib.bib
biblio-style: apalike
csl: apa.csl
link-citations: yes
geometry: margin = 0.5in
urlcolor: blue
highlight: tango
header-includes:
  \usepackage{underscore}
  \usepackage[T1]{fontenc}
github-repo: ASKURZ/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse
twitter-handle: SolomonKurz
description: "This project is an attempt to re-express the code in McElreath’s textbook. His models are re-fit in brms, plots are redone with ggplot2, and the general data wrangling code predominantly follows the tidyverse style."
---

# This is a love letter {-}

I love McElreath's [-@mcelreathStatisticalRethinkingBayesian2015] [*Statistical rethinking* text](https://xcelab.net/rm/statistical-rethinking/). It's the entry-level textbook for applied researchers I spent years looking for. McElreath's [freely-available lectures](https://www.youtube.com/channel/UCNJK6_DZvcMqNSzQdEkzvzA/playlists) on the book are really great, too.

However, I prefer using Bürkner's [brms package](https://github.com/paul-buerkner/brms) [@R-brms; @burknerBrmsPackageBayesian2017; @burknerAdvancedBayesianMultilevel2018] when doing Bayesian regression in R. [It's just spectacular](https://statmodeling.stat.columbia.edu/2017/01/10/r-packages-interfacing-stan-brms/). I also prefer plotting with [ggplot2](https://ggplot2.tidyverse.org/) [@wickhamGgplot2ElegantGraphics2016; @R-ggplot2], and coding with functions and principles from the [tidyverse](https://www.tidyverse.org/) [@R-tidyverse; @wickhamWelcomeTidyverse2019].

This project is an attempt to reexpress the code in McElreath's textbook. His models are re-fit with brms, the figures are reproduced or reimagined with ggplot2, and the general data wrangling code now predominantly follows the tidyverse style.

## Why this? {-}

I'm not a statistician and I have no formal background in computer science. Though I benefited from a suite of statistics courses in grad school, a large portion of my training has been outside of the classroom, working with messy real-world data, and searching online for help. One of the great resources I happened on was [idre, the UCLA Institute for Digital Education](https://stats.idre.ucla.edu), which offers an online portfolio of [richly annotated textbook examples](https://stats.idre.ucla.edu/other/examples/). Their online tutorials are among the earliest inspirations for this project. We need more resources like them.

With that in mind, one of the strengths of McElreath's text is its thorough integration with the [rethinking package](https://github.com/rmcelreath/rethinking) [@R-rethinking]. The rethinking package is a part of the R ecosystem, which is great because R is free and open source [@R-base]. McElreath has made the source code for rethinking [publicly available](https://github.com/rmcelreath/rethinking), too. Since he completed his text, [many other packages have been developed](https://www.youtube.com/watch?v=pKZLJPrZLhU&t=29073s&frags=pl%2Cwn) to help users of the R ecosystem interface with [Stan](https://mc-stan.org/) [@carpenterStanProbabilisticProgramming2017]. Of those alternative packages, I think Bürkner's [brms](https://github.com/paul-buerkner/brms) is the best for general-purpose Bayesian data analysis. Its flexible, uses reasonably-approachable syntax, has sensible defaults, and offers a vast array of post-processing convenience functions. And brms has only gotten [better over time](https://github.com/paul-buerkner/brms/blob/master/NEWS.md). Yet at the time I released the first version of this ebook, there were no textbooks on the market that highlight the brms package, which seemed like an evil worth correcting.

In addition, McElreath's data wrangling code is based in the base R style and he made most of his figures with base R plots. Though there are benefits to sticking close to base R functions (e.g., less dependencies leading to a lower likelihood that your code will break in the future), there are downsides. [For beginners, base R functions can be difficult both to learn and to read](http://varianceexplained.org/r/teach-tidyverse/). Happily, in recent years Hadley Wickham and others have been developing a group of packages collectively called the [tidyverse](https://www.tidyverse.org/). These tidyverse packages, such as [dplyr](https://dplyr.tidyverse.org) [@R-dplyr] and [purrr](https://purrr.tidyverse.org) [@R-purrr], were developed according to an [underlying philosophy](https://cran.r-project.org/web/packages/tidyverse/vignettes/manifesto.html) and they are designed to work together coherently and seamlessly. Though [not all](https://github.com/matloff/TidyverseSkeptic) within the R community share this opinion, I am among those who think the tidyverse style of coding is generally [easier to learn and sufficiently powerful](http://varianceexplained.org/r/teach-tidyverse/) that these packages can accommodate the bulk of your wrangling data needs. I also find tidyverse-style syntax easier to read. And of course, the widely-used [ggplot2 package](https://ggplot2.tidyverse.org) is part of the tidyverse, too.

To be clear, students can get a great education in both Bayesian statistics and programming in R with McElreath's text just the way it is. Just go slow, work through all the examples, and read the text closely. It's a pedagogical boon. I could not have done better or even closely so. But what I can offer is a parallel introduction on how to fit the statistical models with the ever-improving and already-quite-impressive brms package. I can throw in examples of how to perform other operations according to the ethic of the tidyverse. And I can also offer glimpses of some of the other great packages in the R + Stan ecosystem, such as [loo](https://github.com/stan-dev/loo) [@R-loo; @vehtariPracticalBayesianModel2017; @yaoUsingStackingAverage2018], [bayesplot](https://github.com/stan-dev/bayesplot) [@R-bayesplot; @gabry2019visualization], and [tidybayes](https://github.com/mjskay/tidybayes) [@R-tidybayes].

## My assumptions about you {-}

If you're looking at this project, I'm guessing you're either a graduate student, a post-graduate academic or a researcher of some sort, which suggests you have at least a 101-level foundation in statistics. If you're rusty, consider checking out the free text books by [Legler and Roback](https://bookdown.org/roback/bookdown-bysh/) [-@leglerBroadeningYourStatistical2019] or [Navarro](https://learningstatisticswithr.com/) [-@navarroLearningStatistics2019] before diving into *Statistical rethinking*. I'm also assuming you understand the rudiments of R and have at least a vague idea about what the tidyverse is. If you're totally new to R, consider starting with Peng's [-@pengProgrammingDataScience2019] [*R programming for data science*](https://bookdown.org/rdpeng/rprogdatascience/). For an introduction to the tidyvese-style of data analysis, the best source I've found is Grolemund and Wickham's [-@grolemundDataScience2017] [*R for data science*](http://r4ds.had.co.nz) (*R4DS*), which I extensively link to throughout this project.

That said, you do not need to be totally fluent in statistics or R. Otherwise why would you need this project, anyway? IMO, the most important things are curiosity, a willingness to try, and persistent tinkering. I love this stuff. Hopefully you will, too. 

## How to use and understand this project {-}

This project is not meant to stand alone. It's a supplement to the first edition of McElreath's text. I follow the structure of his text, chapter by chapter, translating his analyses into brms and tidyverse code. However, some of the sections in the text are composed entirely of equations and prose, leaving us nothing to translate. When we run into those sections, the corresponding sections in this project will sometimes be blank or omitted, though I do highlight some of the important points in quotes and prose of my own. So I imagine students might reference this project as they progress through McElreath's text. I also imagine working data analysts might use this project in conjunction with the text as they flip to the specific sections that seem relevant to solving their data challenges.

I reproduce the bulk of the figures in the text, too. The plots in the first few chapters are the closest to those in the text. However, I'm passionate about data visualization and like to play around with [color palettes](https://github.com/EmilHvitfeldt/r-color-palettes), formatting templates, and other conventions quite a bit. As a result, the plots in each chapter have their own look and feel. For more on some of these topics, check out chapters [3](https://r4ds.had.co.nz/data-visualisation.html), [7](https://r4ds.had.co.nz/exploratory-data-analysis.html), and [28](https://r4ds.had.co.nz/graphics-for-communication.html) in *R4DS*, Healy's [-@healyDataVisualization2018] [*Data visualization: A practical introduction*](https://socviz.co), Wilke's [-@wilkeFundamentalsDataVisualization2019] [*Fundamentals of data visualization*](https://serialmentor.com/dataviz/) or Wickham's [-@wickhamGgplot2ElegantGraphics2016] [*ggplot2: Elegant graphics for data analysis*](https://ggplot2-book.org/).

In this project, I use a handful of formatting conventions gleaned from [*R4DS*](https://r4ds.had.co.nz/introduction.html#running-r-code), [*The tidyverse style guide*](https://style.tidyverse.org/) [@wickhamTidyverseStyleGuide2020], and [*R markdown: The definitive guide*](https://bookdown.org/yihui/rmarkdown/software-info.html) [@xieMarkdownDefinitiveGuide2020].

* R code blocks and their output appear in a gray background. E.g., 


```r
2 + 2 == 5
```

```
## [1] FALSE
```

* Functions are in a typewriter font and followed by parentheses, all atop a gray background (e.g., `brm()`).
* When I want to make explicit the package a given function comes from, I insert the double-colon operator `::` between the package name and the function (e.g., `tidybayes::mode_hdi()`).
* R objects, such as data or function arguments, are in typewriter font atop gray backgrounds (e.g., `chimpanzees`, `.width = .5`).
* You can detect hyperlinks by their typical [blue-colored font](https://www.youtube.com/watch?v=40o0_0XTB6E&t=15s&frags=pl%2Cwn).
* In the text, McElreath indexed his models with names like `m4.1` (i.e., the first model of Chapter 4). I primarily followed that convention, but replaced the `m` with a `b` to stand for the brms package.

## You can do this, too {-}

This project is powered by Yihui Xie's [-@R-bookdown] [bookdown package](https://bookdown.org), which makes it easy to turn R markdown files into HTML, PDF, and EPUB. Go [here](https://bookdown.org/yihui/bookdown/) to learn more about bookdown. While you're at it, also check out Xie, Allaire, and Grolemund's [*R markdown: The definitive guide*](https://bookdown.org/yihui/rmarkdown/). And if you're unacquainted with GitHub, check out Jenny Bryan's [-@bryanHappyGitGitHub2020] [*Happy Git and GitHub for the useR*](https://happygitwithr.com/). I've even [blogged](https://solomonkurz.netlify.com/post/how-bookdown/) about what it was like putting together the first version of this project.

The source code of the project is available on GitHub at [https://github.com/ASKurz/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse](https://github.com/ASKurz/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse).

## We have updates {-}

For a brief rundown of the version history, we have:

### Version 0.9.0. {-}

I released the initial 0.9.0 version of this project in September 26, 2018. It was a full first draft and set the stage for all others.

### Version 1.0.0. {-}

In April 19, 2019 came the 1.0.0 version. Some of the major changes were:

* All models were refit with brms, 2.8.0.
* Adopting the `seed` argument within the `brm()` function made the model results more reproducible.
* The [loo package](https://github.com/stan-dev/loo) was updated. As a consequence, our workflow for the WAIC and LOO changed, too.
* I improved the brms alternative to McElreath's `coeftab()` function.
* I made better use of the tidyverse, especially some of the [purrr](https://purrr.tidyverse.org/) functions.
* Particularly in the later chapters, there's a 
greater emphasis on functions from the [tidybayes package](https://mjskay.github.io/tidybayes/).
* Chapter [11.3.1][Beta-binomial.] contains the updated brms 2.8.0 workflow for making custom distributions, using the beta-binomial model as the example.
* Chapter 12 received a new [bonus section][~~Summary~~ Bonus: Put your random effects to work] contrasting different methods for working with multilevel posteriors.
* Chapter 14 received a new [bonus section][~~Summary~~ Bonus: Meta-analysis] introducing Bayesian meta-analysis and linking it to multilevel and measurement-error models.
* With the help of others within the community, I corrected many typos and streamlined some of the code (e.g., [dropped an unnecessary use of the `mi()` function in Section 14.2.1](https://github.com/ASKurz/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse/issues/21))
* And in some cases, I corrected sections that were just plain wrong (e.g., some of my initial attempts in section 3.3 were incorrect).

### Version 1.0.1. {-}

In May 5, 2019 came the 1.0.1 version, which finally added a [PDF version](https://github.com/ASKurz/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse/blob/master/recoding_Statistical_Rethinking_1.0.1_PDF_version.pdf) of the book. Other noteworthy changes included:

* Major revisions to the LaTeX syntax underlying many of the in-text equations (e.g., dropping the "eqnarray" environment for "align*")
* Adjusting some of the image syntax
* Updating the reference for the Bayesian $R^2$ [@gelmanRsquaredBayesianRegression2019]

### Version 1.1.0. {-}

In March 1, 2020 came the 1.1.0 version. Noteworthy changes were:

* substantial expansions to Sections [10.3.1][Multinomial.] (multinomial regression) and [11.3.2][Negative-binomial or gamma-Poisson.] (negative binomial regression),
* the addition of a new section in Chapter 15 ([15.9][Code in public]) encouraging others to code in public,
* refitting all models with the current official version of brms, version 2.12.0,
* discussions ([Section 8.3.2][Estimation.]) on the new `Bulk_ESS` and `Tail_ESS` summaries of HMC effective sample size [@vehtariRanknormalizationFoldingLocalization2019],
* saving all fits as external files in the new [GitHub fits folder](https://github.com/ASKurz/Statistical_Rethinking_with_brms_ggplot2_and_the_tidyverse/tree/master/fits), primarily with the `file` argument,
* extensive use of the [patchwork package](https://patchwork.data-imaginist.com/) [@R-patchwork] for combining ggplots,
* improving/updating some of the tidyverse code (e.g., using `tidyr::crossing()`),
* updates to the `brms::custom_family()`-related code in [Section 11.3.1][Beta-binomial.] to match brms 2.11.0 updates,
* replacing the depreciated `brms::marginal_effects()` with `brms::conditional_effects()` (see [issue #735](https://github.com/paul-buerkner/brms/issues/735)), 
* replacing the depreciated `brms::stanplot()` with `brms::mcmc_plot()`,
* increased the plot resolution with `fig.retina = 2.5`,
* refreshed hyperlinks, and
* various typo corrections.

### Version 1.2.0. {-}

Welcome to version 1.2.0! Noteworthy changes include:

* the correct solution to the first multinomial model in [Section 10.16][Explicit multinomial models.];
* a coherent workflow for the Gaussian process model from [Section 13.4][Example: Spatial autocorrelation in Oceanic tools.];
* corrections to some of the post-processing workflows for the measurement-error models in [Section 14.1][Measurement error];
* refitting all models with the current official version of brms, version 2.13.5;
* improved in-text citations and reference sections using [BibTex](http://www.bibtex.org/) [@BibTeX2020], [Better BibTeX](https://github.com/retorquere/zotero-better-bibtex) [@BetterBibTeXZotero2020], and [zotero](https://www.zotero.org/) [@ZoteroYourPersonal2020]; and
* minor prose, hyperlink, and code edits throughout.

## Is this material obsolete? {-}

The first edition of McElreath's text now has a successor, *Statistical rethinking: A Bayesian course with examples in R and Stan: Second Edition* [@mcelreathStatisticalRethinkingBayesian2020]. Though the second edition kept a lot of the content from the first, it is a substantial revision and expansion. The book is longer and wildly ambitious in its scope. To be blunt, I believe McElreath moved to quickly in his revision and I suspect many applied readers might need to reference the first edition from time to time to time just to keep up with the content of the second. If McElreath ever releases a third edition, I hope he finds a happy compromise between the first two. So in the meantime, I believe there's a place for both first and second editions of his text. Accordingly, I believe this ebook should not be considered outdated relative to my [ebook](https://bookdown.org/content/4857/) translation of the second edition [@kurzStatisticalRethinkingSecondEd2020]. Use whatever you find helpful.

## Thank-you's are in order {-}

Before we move on, I'd like to thank the following for their helpful contributions:

* Shaan Amin ([\@Shaan-Amin](https://github.com/Shaan-Amin)),
* Louis Bliard ([\@lbiard](https://github.com/lbiard)),
* Paul-Christian Bürkner ([\@paul-buerkner](https://github.com/paul-buerkner)), 
* Joseph V. Casillas ([\@jvcasillas](https://github.com/jvcasillas)),
* Andrew Collier ([\@datawookie](https://github.com/datawookie)), 
* Marco Colombo ([\@mcol](https://github.com/mcol)),
* Jeff Hammerbacher ([\@hammer](https://github.com/hammer)), 
* Matthew Kay ([\@mjskay](https://github.com/mjskay)), 
* Katrin Leinweber ([\@katrinleinweber](https://github.com/katrinleinweber)),
* TJ Mahr ([\@tjmahr](https://github.com/tjmahr)), 
* Federico Marini ([\@federicomarini](https://github.com/federicomarini)),
* Stijn Masschelein ([\@stijnmasschelein](https://github.com/stijnmasschelein)), 
* JungSu Oh ([\@js-oh](https://github.com/js-oh)),
* Colin Quirk ([\@colinquirk](https://github.com/colinquirk)), 
* Rishi Sadhir ([\@RishiSadhir](https://github.com/RishiSadhir)),
* Jon Spring ([\@jonspring](https://github.com/jonspring)),
* Phil Straforelli ([\@pstraforelli](https://github.com/pstraforelli)),
* Richard Torkar ([\@torkar](https://github.com/torkar)),
* Aki Vehtari ([\@avehtari](https://github.com/avehtari)), and
* Matti Vuorre ([\@mvuorre](https://github.com/mvuorre)).



