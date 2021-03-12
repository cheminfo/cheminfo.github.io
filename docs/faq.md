---
layout: page
title: FAQ
permalink: /faq/
---

# What is eln.epfl.ch?

The eln.epfl.ch is a [fork](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/fork-a-repo#:~:text=A%20fork%20is%20a%20copy,without%20affecting%20the%20original%20project) of the ELN developed by the [cheminfo GitHub organization](github.com/cheminfo)

# What makes it different form other ELNs?

_With eln.epfl.ch [FAIR data](https://www.go-fair.org/fair-principles/) is not an afterthought of a data management plan (DMP)._

Upon importation to the ELN all data are converted into standardized, and open formats like [JCAMP-DX](http://jcamp-dx.org/). All synthesis, analysis, and notes can be exported with metadata to a Zenodo in a form that is amenable to datamining efforts

_Data is "alive all the time_

You can interact with the data in the ELN. You can peak picks, analyze it, superimpose it, zoom into it. But you---or the readers of your paper---can use the same functionalities after export to Zenodo.

_Free and open-source_

All software we develop(ed) for this ELN is free and open-source. This means that you can inspect in detail what is happening when we convert file formats or analyze your data---something that is typically not possible with proprietary software.

# Is this production-ready?

Many research groups around the world and at EPFL use it for production. In fact, many ISIC services, like the elemental analysis, are tightly integrated with the ELN.

For the ELN, we have developed about 180 packages which receive about 250'000 downloads per week---but not only for chemistry applications! [Browsers use one of our packages to perform speedtests](https://webkit.org/blog/7536/jsc-loves-es6/) and our most popular package, [ml](https://github.com/mljs/ml) has [more than two thousand stars on GitHub](https://github.com/mljs/ml/stargazers).

# How can I get started?

If you are based at EPFL, it is easy! You just have to visit eln.epfl.ch and log in with your GASPAR account.

If you are not based at EPFL, you can use many of the functionalities at c6h6.org or [deploy your own ELN](https://github.com/cheminfo/roc-eln-docker).

# Where is my data stored?

The system is configured as [double master](https://en.wikipedia.org/wiki/Multi-master_replication) meaning there are two master databases that are in different buildings at EPFL and are continuously synchronized.

Data can be nightly exported to the file system (e.g., `sb1files.epfl.ch`) so that you can anytime leave with all your data. Data can be published in a couple of clicks to Zenodo (for [here](https://zenodo.org/record/4044212) for an example) or downloaded as zip?
