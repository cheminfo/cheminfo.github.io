---
layout: post
title: "The cheminfo development environment and workflow from a perspective of a new contributor"
date: 2021-02-04 14:11
categories: [tutorial]
---

This post outlines some tools and tricks that are used by cheminfo developers---summarized by someone who just recently started contributing (and was new to JavaScript). It is hopefully useful as a starting point for new contributors to the cheminfo ecosystem.

Most, if not all, contributors to the cheminfo ecoystem use the [VSCode editor](https://code.visualstudio.com/) with some plugins. We also follow a few conventions with respect to commit messages and directory structure. We also discuss some points in the [starting guide GitHub](https://github.com/cheminfo/generator-cheminfo/blob/master/START.md). This post is thought as a guide for new contributors to the cheminfo projects.

# VSCode setup

If you did not install [VSCode](https://code.visualstudio.com/) we recommend you install it. It is available on all major operating systems and comes with incredible support for Git, remote connections, and plugins for all kinds of languages.

## Plugins

We like to use the following plugins:

- [prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode): To automatically format your code nicely. It is useful to [configure to do this automatically upon saving](https://stackoverflow.com/questions/50606758/vscode-how-do-you-autoformat-on-save).

- [jest](https://marketplace.visualstudio.com/items?itemName=Orta.vscode-jest): To test your code using [Facebook's jest](https://jestjs.io/)

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint): This will underline lint errors in the code and suggest quick fixes. [This blog post by Digital Ocean gives some more information on how one can use ESlint with VSCode](https://www.digitalocean.com/community/tutorials/linting-and-formatting-with-eslint-in-vs-code)

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one): For powerful markdown preview and keyboard shortcuts.

- [Document this](https://marketplace.visualstudio.com/items?itemName=oouo-diogo-perdigao.docthis): To insert [JSDoc](https://jsdoc.app/) docstrings.

- [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github): To review pull requests from VS Code and show issues, you can directly "start working on an issue" and make a new branch.

It is also really useful to browse in the store as there are plugins for any possible application, i.e., to [color columns in csv files](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv), [highlight syntax in CIFs](https://marketplace.visualstudio.com/items?itemName=thisperiodictable.cif), [colorize matching brackets](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer), or to [launch a live development server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer). If you want to try incredible, deep learning powered, autocomplete you can give the [tabnine plugin](https://www.tabnine.com/) a shot. For editing key/value pairs of any kind the [Toggle Column Selection](https://marketplace.visualstudio.com/items?itemName=erikphansen.vscode-toggle-column-selection) can be useful.

To install a plugin you can just click on the extensions symbol (building blocks on the left menu bar) and then search for the extension you want and click on "install".

## Shortcuts and key bindings

There are a couple VSCode shortcuts that are handy to know. [In the VSCode documentation](https://code.visualstudio.com/docs/getstarted/tips-and-tricks) you can find an overview of key bindings.

- `CMD + P`: Is the main keybinding in VSCode. It will open menu which you can use to go to files. If you type `>` you can run command (like opening a new `ssh` connection)
- `CMD + Shift + F`: With this shortcut you can search through all files in a directory at once. The results will show up on the left, and you can use the arrow to open a search/replace box.
- `CMD+\`: If you highlight some code/text this will comment/uncomment it.
- `Option+UP/DOWN`: Moves the selected line up/down
- `CMD+K Z`: Toggles [Zen mode](https://code.visualstudio.com/docs/getstarted/userinterface)

## GitHub integration

Most of the things you might want to do on GitHub can be done from VSCode. If you are new to Git and GitHub there are a lot of excellent resources that explain the basics. A good introduction for scientist gives the [Turing way book](https://the-turing-way.netlify.app/reproducible-research/vcs/vcs-git.html).

### Branch, commit, pull requests

The Source Control icon in the Activity Bar (`CTRL+SHIFT+G`) the left will list the uncommitted changes in your workspace, you can enter a commit message and use the checkmark to commit the changes.

<img style="float:center; width: 16em" src="{{ site.url }}/assets/img/developer_tools/source_control.png">

In the footer you'll see an indication on which branch you are working on (and you can switch branches by clicking on it) and an icon that allows you to push the changes.

<img style="width: 20em float:center" src="{{ site.url }}/assets/img/developer_tools/activity_bar.png">

### Pull requests and issues

The [GitHub Pull Requests and Issues extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) allows browsing issues and pull requests. In the screenshot below we see that there are two pull requests in this particular repository one of which has been created by me and another one which has been created by [dependabot](https://dependabot.com/).
We can also see a list of all issues and directly create a new branch that is linked to a particular issue by clicking on the arrow that appears when we hover over the list.

<img style="width: 20em; float:center" src="{{ site.url }}/assets/img/developer_tools/pr.png">

# Other tools

- Node.js: You should install the [Node.js JavaScript runtime](https://nodejs.org/en/). One the website you will find downloads for all major operating systems
- [yeoman generator](https://yeoman.io/): `npm install -g yo` to bootstrap new projects
- [ncu](npm-check-updates): `npm install -g npm-check-updates` to update dependencies. It is useful to regularly run `ncu -u` to keep the dependencies updated
- [the cheminfo generator](https://github.com/cheminfo/generator-cheminfo) `npm i -g yo generator-cheminfo` as generator for the different cheminfo organizations

# Project structure

In general we like to organize or projects in a directory structure as `~/git/organization/project`. This is, we would work on the documentation repository in `~/git/cheminfo/c6h6-documentation`. We found that this makes it easier to collaborate.

## Creating a new project

To bootstrap new projects, we use a [yeoman generator](https://yeoman.io/). For using this, you will need to first install [the cheminfo generator](https://github.com/cheminfo/generator-cheminfo). Then you can `mkdir` your project directory, `cd` into it and run `yo cheminfo:module`. This will ask you some questions and create most of the boilerplate (like the `package.json`, some `README` template, [`eslint`](https://eslint.org/) rules, [`babel`](https://babeljs.io/) settings ...) for you.

## File organization

We typically like to have small files with [pure functions](https://www.freecodecamp.org/news/what-is-a-pure-function-in-javascript-acb887375dfe/) (where it makes sense).
In every subfolder we will make a `__test__ ` directory in which we will have a `module.test.js` file for every`module.js`. That is, a project might look like

```
├── package.json
├── src
│   ├── from
│   │   ├── __tests__
│   │   │   ├── fromJcamp.ntuples.test.js
│   │   │   ├── fromJcamp.test.js
│   │   │   ├── fromPerkinElmer.test.js
│   │   │   ├── fromPerkinElmerCSV.test.js
│   │   │   ├── fromTAInstrumentExcel.test.js
│   │   │   ├── fromTAInstruments.test.js
│   │   │   └── parseTAInstrumentExcel.test.js
│   │   ├── fromPerkinElmer.js
│   │   ├── fromPerkinElmerCSV.js
│   │   ├── fromTAInstruments.js
│   │   ├── fromTAInstrumentsExcel.js
│   │   ├── parsePerkinElmer.js
│   │   ├── parseTAInstruments.js
│   │   └── parseTAInstrumentsExcel.js
│   └── index.js
```

# Code style

We generally use the [ES6 specification](https://www.javatpoint.com/es6) and follow the typical coding conventions:

- variable names are `camelCase`
- global variables are `UPPERCASE`
- node packages use `-` in their name and not `_`

You should use `let` and `const` instead of `var`

Google wrote a [useful styleguide](https://google.github.io/styleguide/jsguide.html). Note that if you use prettier the formatting will be done automatically for you and ESlint (if you use the cheminfo generator) will let you know about variable naming and other issues that can be found via static code analysis.

Some other useful points are

- That typed arrays can be useful as they [can increase performance and reduce the likelihood of mistakes](<[typedarrays](https://stackoverflow.com/a/13334932)>)
- We try to use the same packages in different projects. We collect the most relevant ones in [the awesome cheminfo list](https://github.com/cheminfo/awesome)
- If you pass keyword arguments to a function, we usually use [destructuring](https://hacks.mozilla.org/2015/05/es6-in-depth-destructuring/) on a `options` object an example is

```
function xPadding(array, options = {}) {
  const { size = 0, value = 0, algorithm = '' } = options;
```

# Code documentation

We document the API using [jsdoc](https://jsdoc.app/). In addition to that we try to at least provide a meaningful snippet in the `README`.

# Test driven development

It can be practical to use the "watch mode" of jest. This will continuously run the test suite in the background `npx jest --watch`. If you just want to run the test suite once, you can use `npm run test`.
In practice, it can often be useful to write, in the spirit of [test driven development](https://en.wikipedia.org/wiki/Test-driven_development), tests before the actual implementation. This can also help to shape the API in an useable form.

# Commit messages

To automate the generation of the changelog and the releases, we use [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/). The basic structure is

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

where the most important types are

- `fix`: for patches, i.e., a `PATCH` bump in [semantic versioning](https://semver.org/)
- `feat`: for new features, i.e., a `MINOR` bump in semantic versioning
- `chore`: for changes that an external user would not notice (updating `.gitignore`, private methods, ...)

If there is a breaking change (`MAJOR` bump in semantic versioning) the commit message might look like

```
feat: add parseAbcXY

BREAKING CHANGE:

Renamed parseXY to parseAbcXY
```

# GitHub actions

In most of our projects we use several GitHub actions that build the documentation, make the release and run the tests.

- [Release Node.js package](https://github.com/cheminfo/.github/blob/master/workflow-templates/release.yml): Uses [release please](https://github.com/google-github-actions/release-please-action) to release the package on npm.
- [Node.js CI](https://github.com/cheminfo/.github/blob/master/workflow-templates/nodejs.yml)
- [Deploy on lactame.com](https://github.com/cheminfo/.github/blob/master/workflow-templates/lactame.yml)
- [Deploy documentation.js on GitHub pages](https://github.com/cheminfo/.github/blob/master/workflow-templates/documentationjs.yml)

If you create a new project in the cheminfo organization you can use the actions tab to add the actions to your repository. It can be useful to make a commit with `release-as: v0.1.0` as commit message to avoid that `release-please` starts with `v1` after an initial `feat` commit.

# Developing code for the visualizer

Many of the frontends (e.g, c6h6.org) are developed using the [visualizer library](https://github.com/NPellet/visualizer). There is unfortunately not a complete documentation for this project but a few useful resources:

- [The tutorial tab on cheminfo](http://www.cheminfo.org/#) has some basic tutorial on how the visualizer can be used
- You can use `CMD+M` to create new modules
- It is usually practical to use multiple layers to keep the code organized, e.g., one Admin layer for every major computational operation. You can edit the layers using a right click and the options under the `Switch layer` menu

<img style="float:center; width: 30em" src="{{ site.url }}/assets/img/developer_tools/switch_layer.png">

<hr>

<div class="post-categories">
  {% if post %}
    {% assign categories = post.categories %}
  {% else %}
    {% assign categories = page.categories %}
  {% endif %}
  {% for category in categories %}
  <a href="{{site.baseurl}}/categories/#{{category|slugize}}">{{category}}</a>
  {% unless forloop.last %}&nbsp;{% endunless %}
  {% endfor %}
</div>
