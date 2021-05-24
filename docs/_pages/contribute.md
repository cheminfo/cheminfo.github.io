---
layout: page
title: "Contribution guide"
description: "All contributions to cheminfo are more than welcome! For code contributions, we recommend to use our development setup"
---

## How can I contribute to the ELN?

All contributions are more than welcome! If you have a problem/found a bug you can [open an issue](https://docs.github.com/en/github/managing-your-work-on-github/creating-an-issue) on the [bug tracker](https://github.com/cheminfo/cheminfo.github.io/issues) or let us know in the [Slack workspace](cheminfo-eln.slack.com)).

### Where can I contribute to?

Cheminfo maintains project along different scopes and welcomes contributions to all of them:

#### Visualization/Front-End

##### React

We currently re-develop the ELN using the [React framework](https://reactjs.org/). The most mature project is [nmrium](https://github.com/cheminfo/nmrium) which is a fully-fledged tool for NMR data analysis and processing. Use our project generator with [`yo cheminfo:react-frontend`](https://github.com/cheminfo/generator-cheminfo) to start a new React project.

##### Legacy

The ELN that is currently in production uses the [visualizer](https://github.com/NPellet/visualizer) library, which cheminfo developers maintain. Some examples of how the visualizer library can be used can be found in the "Tutorial" section on [cheminfo.org](https://www.cheminfo.org/Tutorial/1._Introduction/1.1_Basic_example/index.html). Most graphical interfaces in the ELN are developed using this library. You can contribute new interfaces via [my.cheminfo.org](https://mydb.cheminfo.org/auth/login?continue=https%3A%2F%2Fmy.cheminfo.org%2F), where you can log in using a Google account. You will see that this system uses its own version control system.
Some background on how this library can be used without JavaScript is given in one of [our articles](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-019-0399-7) and the [accompanying code](https://github.com/jwist/hastaLaVista).

The visualizer can be used in a React component using the [react-visualizer library](https://github.com/cheminfo/react-visualizer).

Cheminfo also [hosts the development version of the JSME editor](https://github.com/cheminfo/jsme).

#### Parsers

A lot of effort in the cheminfo organization goes into the development of parsers for chemical data. Some examples are the [netcdfjs](https://github.com/cheminfo/netcdfjs) and [mrz](https://github.com/cheminfo/mrz) parsers. We maintain parsers for NMR spectroscopy ([Bruker](https://github.com/cheminfo/c6h6-documentation), [NMReData](https://github.com/cheminfo/nmredata), [JEOL](https://github.com/cheminfo/jeolconverter)), [chromatography](https://github.com/cheminfo/chromatography), [thermogravimetry](https://github.com/cheminfo/tga-spectrum), [gas adsorption isotherms](https://github.com/cheminfo/isotherm-analysis), [x-ray diffraction](https://github.com/cheminfo/xrd-analysis), [XPS](https://github.com/cheminfo/xps-analysis), and many more. Most of the data in the ELN is stored as [JCAMP](), a IUPAC recommended format, and we maintain the [jcampconverter library](https://github.com/cheminfo/jcampconverter) to deal with this filetype.

To contribute a new parser, use our project generator with [`yo cheminfo:module`](https://github.com/cheminfo/generator-cheminfo). We try to use [common-spectrum](https://github.com/cheminfo/common-spectrum) as the base for all new parsers. Common spectrum provides basic utilities that like `toJCAMP`, peak picking, or [baseline correction](https://github.com/cheminfo/baselines).

#### Mining chemical data

We maintain several projects that aim to "harvest" or to provide programmatic access to chemical data. A recent example is a wrapper around the [PubChem API](https://github.com/cheminfo/pubchem). We also [mine all the molecules on Wikipedia](https://github.com/cheminfo/wikipedia) and [PubChem](https://github.com/cheminfo/node-pubchem).

#### Data processing and machine learning

For chemical structure information we maintain [openchemlib-js](https://github.com/cheminfo/openchemlib-js). This is a library that also takes care of stereochemistry information.

The cheminfo lead developers also maintain the [ml.js GitHub organization](https://github.com/mljs), which provides [array methods and libraries with machine learning algorithms](https://github.com/mljs/ml). One library that is particular useful in the ELN is the [global spectral deconvolution](https://github.com/mljs/global-spectral-deconvolution) as well as the [peak shape generator](https://github.com/mljs/peak-shape-generator). But also the [PCA](https://github.com/mljs/pca) library can be used via the ELN.
An interesting side note is that [our neural network library is used in browser benchmarks](https://webkit.org/blog/7536/jsc-loves-es6/).


#### Core ELN

The ELN in production uses [CouchDB](https://couchdb.apache.org/) and cheminfo maintains the [rest-on-couch library](https://github.com/cheminfo/rest-on-couch) that provides an interface to CouchDB that allows the control of permissions on the documents and also allows setting up automatic importation of files into the folder. This library also powers the API of the ELN.

The ELN deployment is currently orchestrated via Docker compose, with the code being maintained in [its own repository](https://github.com/cheminfo/roc-eln-docker).

We are in the process of migrating to a new data schema, [which is based on TypesScript types](https://github.com/cheminfo/cheminfo-types).

#### Documentation

The ELN documentation is based on Markdown files. We are [in the process of migrating to a docusaurus-based system](https://github.com/cheminfo/eln-docs). The [legacy repository uses GitBooks](https://github.com/cheminfo/c6h6-documentation).

## How can I make contributions to code and documentation?

For contributions to code and documentation you will need a GitHub accounts, you will fork a repository, make a new branch, edit the code, and then make a pull request. In the following, we will go through all these steps.

1. If you do not already have one, create a GitHub account: To create a GitHub account, follow the instructions [on the GitHub page](https://github.com/join).
2. If you do not already have Git installed on your machine, you'll need to install it.

   - On Windows you can go to [GIT-SCM](https://git-scm.com/download/win) and download the executable.
   - On Mac, the most convenient way is to use [Homebrew](https://brew.sh/). For this you'll need to [install homebrew](https://brew.sh/) and then run `brew install git` from the terminal
   - On Ubuntu (i.e., also Windows subsystem for Linux) you can just run `apt-get install git` from the terminal

3. We recommend that you install [VSCode](https://code.visualstudio.com/) and some plugins. We wrote a [blog post](https://cheminfo.github.io/tutorial/cheminfo_dev_setup/) describing how to set up the development environment and the first section discusses the VSCode setup.
4. Once you have your GitHub account and your coding setup ready, you can [fork](https://docs.github.com/en/enterprise-server@2.20/github/getting-started-with-github/fork-a-repo) the repository you want to make a contribution to. "Forking" just means that you make a copy of the repository. To do so, you just need to click on the fork button in the top right corner. For contributions to the documentation, you'll need to fork the [c6h6-documentation](https://github.com/cheminfo/c6h6-documentation) repository.
5. Clone the fork to your local computer and make a new branch.
6. Make changes to the code or documentation. And commit them. We have a [blog post](https://cheminfo.github.io/tutorial/cheminfo_docs/) describing how the documentation works.
7. Push the changes to the remote and make a pull request.

We go through steps 4--7 in a video tutorial in the [blog post](https://cheminfo.github.io/tutorial/cheminfo_docs/).

We [maintain a list of tools we like to use](https://github.com/cheminfo/awesome).
