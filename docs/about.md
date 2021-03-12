---
layout: page
title: About
permalink: /about/
---

## The cheminfo ecosystem

cheminfo stands for cheminformatics tools that run in your browser.
It includes more than 150 individual libraries and tools hosted in the following GitHub organizations:

- [cheminfo](https://github.com/cheminfo) and [cheminfo-js](https://github.com/cheminfo-js): parsers for various characterization techniques. Examples can be found in the [app registry](https://kjappelbaum.github.io/cheminfo-app-registry/).
- [cheminfo-py](https://github.com/cheminfo-py): webservices (server backends) written in Python, e.g., for predicting PXRD patterns or topology analysis
- [image-js](https://github.com/image-js): image analysis in the browser
- [mljs](https://github.com/mljs): linear algebra and optimization in the browser

{% include youtube.html id="SHN07asZaGc" %}

## The cheminfo electronic laboratory notebook (ELN)

The cheminfo ELN integrates tools from the cheminfo ecosystem into a fast and lightweight laboratory notebook that runs in your browser.

### Built by chemists for chemists

Data is entered into the ELN similar to how you would take notes in your paper-based lab notebook.
For example, you may want to have a reaction diagram, a reagent table, and a description of the synthesis.

<img style="width: 30em" src="../assets/img/pxrd_overview.png">

Different from a paper-based lab notebook, the reagent table automatically retrieves data from large chemical databases and computes the stochiometry for you.
For common characterization techniques in chemistry and materials science, dedicated tools are already available:

- predict and assign NMR spectra
- analyze mass spectra by matching fragment
- deconvolve your spectra (e.g., mass spectra, TGA)
- keep track for your chemicals with an inventory system
- or predict PXRD patterns for your crystal structures

All in the browser!

### FAIR data, straight from the instrument

> We aim to store any kind of information correctly, reliably and in a perennial and reusable way. [FAIR data](https://www.go-fair.org/fair-principles/) is not an afterthought.

<img style="width: 30em" src="../assets/img/importation.png">

In the ideal case shown above, data is captured automatically from the instrument, converted into an open format and ingested into the [CouchDB database](https://en.wikipedia.org/wiki/Apache_CouchDB) of the ELN.
Where this is not possible, data can be uploaded via drag-and-drop.

All synthesis or characterization data are stored with a rich set of metadata that make them easy to _find_ (for more details you can consult our [data schema](https://cheminfo.github.io/data_schema/)). For example, you can find samples based on peak position, molecular formula, the creator or the modification date.
A built-in barcode system helps with building your personal chemical library and ensures that nothing is lost.

Through a large library of parsers, the ELN takes care of converting all files into standardized, open formats.
This is essential in order to keep information _accessible_ tens of years from now -- independent of support from the instrument manufacturer.

When you are ready to publish, the ELN lets you create machine-readable archives (following guidelines of the [semantic web](https://en.wikipedia.org/wiki/Semantic_Web)).
Each archive is accompanied by a link that your readers can used to visualize the data directly in their browser. You can find an example of such an archive [here](https://zenodo.org/record/4044212).

### Agile development: easy to extend

The cheminfo ELN was designed as a highly modular collection of individual components.
This makes it possible to quickly adapt to new requirements, to implement new tools, support new data formats, or even to implement entirely new frontend (for example, the [chemotion ELN](https://chemotion.net/) reuses our [jcampconverter](https://github.com/cheminfo/jcampconverter#readme) and [spectra](https://github.com/cheminfo-js/spectra) libraries).

Supported formats are documented in the [database schema](https://cheminfo.github.io/data_schema/).
