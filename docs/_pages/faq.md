---
layout: page
title: "FAQ"
description: "Frequently asked questions"
---

# What makes the cheminfo ELN different from other ELNs?

_With the cheminfo ELN [FAIR data](https://www.go-fair.org/fair-principles/) is not an afterthought of a data management plan (DMP)._

Upon importation to the ELN all data are converted into standard, open formats like [JCAMP-DX](http://jcamp-dx.org/). 
All synthesis, analysis, and notes are can be exported with metadata to the [Zenodo](http://zenodo.org/) repository in a form that is amenable to data mining.

_Data is "alive" all the time_

You can interact with the data *inside* the ELN. 
You can pick peaks, analyze them, superimpose them, zoom into them. 
But you ---or the readers of your paper--- can also use the same functionalities *after* the deposition on [Zenodo](http://zenodo.org/).

_Free and open-source_

All software developed for this ELN is free and open-source. 
This means that you can inspect in detail what is happening when converting file formats or analyzing your data ---something that is often not possible with proprietary software.

## Is this production-ready?

Many research groups, both at EPFL and around the world, use the cheminfo ELN as part of their daily work.
At EPFL, analytical services, such as the elemental analysis and mass spectra services, are tightly integrated with the ELN.

For the ELN, we have developed about 180 software packages which receive about 250'000 downloads per week, and have proven to be useful not just in the chemistry field.
[Browsers use one of our packages to perform speedtests](https://webkit.org/blog/7536/jsc-loves-es6/), and our most popular package [ml](https://github.com/mljs/ml) for machine-learning in the browser received [more than two thousand stars on GitHub](https://github.com/mljs/ml/stargazers).

## How can I get started?

We maintain an open instance of the cheminfo ELN at [c6h6.org](c6h6.org), where you can log in using your GitHub account and start playing around.
EPFL users visit [eln.epfl.ch](eln.epfl.ch) and log in with their GASPAR account.

If you like what you see, you are welcome to [deploy your own ELN](https://github.com/cheminfo/roc-eln-docker).
Feel free to [reach out](contact) if you have any questions about deploying the ELN yourself.

## Where is my data stored?

The manager of the ELN instance decides where to store live data.

The EPFL system is configured as [double master](https://en.wikipedia.org/wiki/Multi-master_replication), with two master databases hosted in different buildings that are synchronized continuously.
Data can be exported nightly to the file system for backup purposes (e.g., `sb1files.epfl.ch`) so that you can leave anytime with all your data. 

Users can download their data as a zip archive or publish it to the [Zenodo](http://zenodo.org/) repository in a couple of clicks (see [example](https://zenodo.org/record/4044212)).
