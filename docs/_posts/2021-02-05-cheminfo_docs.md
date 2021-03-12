---
layout: post
title: "Where can I find help in the ELN and how can I improve it?"
date: 2021-02-04 14:11
categories: [tutorial]
---

In this blog post we will discuss where you can find help in the ELN and how you can help use improving the documentation.

# How does the documentation in the ELN work?

If you have been using the ELN you might have been noticing that there is a question mark icon in the top left corner of some pages in the ELN. If you click on it, it will open a popup with help relevant to the view you're currently looking at.

<img style="float:center; width: 40em" src="{{ site.url }}/assets/img/developer_tools/help_example.png">

All of this is built using [GitBook](https://github.com/GitbookIO/gitbook) which allows converting [markdown files](https://www.markdownguide.org/) into something that looks like an online book.
The core of the documentation is in the `src/book` folder of the [c6h6-documentation repository](https://github.com/cheminfo/c6h6-documentation/tree/master/src/book) where you can find subfolders for different categories.

## Mapping views to documentation pages

You might now ask yourself how the mapping between the view in the ELN and the page in the documentation works. This is set up in `index.yml` files like [this here for the PXRD documentation](https://github.com/cheminfo/c6h6-documentation/blob/master/src/book/spectra/pxrd/index.yml). The file contains one key called `uuid` which is the [uuid](https://en.wikipedia.org/wiki/Universally_unique_identifier) of the view. If we analyze the requests the ELN makes using the [network tab in the developer tools](https://developers.google.com/web/tools/chrome-devtools/network/) we find that this is indeed the UUID of the view.

<img style="float:center; width: 30em" src="{{ site.url }}/assets/img/developer_tools/uuid_developer_tools.png">

This is also what we find in the [visualizer helper library](https://github.com/cheminfo-js/visualizer-helper/blob/150b2bfea7a0d50778a85b53d2fad51939bde9d8/util/tips.js#L13-L26): for a given view we get the UUID `info._id` and then can use this to find the correct `yml` file that configures the sections of the documentation.

```javascript
async function showTips(info) {
  if (!info) info = await getViewInfo();
  if (!info._id) return;

  //  info._id='15c9a2dcd55c963fdedf2c18a1471b03';
  //  info.rev=90;
  // retrieve tips toc
  await fetch(`${tipsURL + info._id}/index.yml`)
    .then(async (response) => {
      let text = await response.text();
      processTipsToc(text, info);
    })
    .catch();
}
```

And the [`processTipsToc`](https://github.com/cheminfo-js/visualizer-helper/blob/150b2bfea7a0d50778a85b53d2fad51939bde9d8/util/tips.js#L49-L61) function is then the one that actually pops up the documentation.

# How can I help improve the documentation

Since the documentation lives in simple markdown files on GitHub you can contribute by simply editing the markdown files. The process is, as with all contributions to projects on GitHub, fork, edit, pull request.

## Getting started

To contribute to the documentation you need a [GitHub account](https://docs.github.com/en/github/getting-started-with-github/signing-up-for-a-new-github-account), you need to [install Git locally](https://git-scm.com/downloads/), and we recommend that you install [VSCode](https://code.visualstudio.com/) and a markdown plugin. The first points are explained in our contribution guidelines while latter is discussed in the first sections of our blog post about the development setup. Once you have all of this setup you can

1. Go to the [c6h6-documentation repository](https://github.com/cheminfo/c6h6-documentation/tree/master/src/book) and click on fork
   <img style="float:center; width: 30em" src="{{ site.url }}/assets/img/developer_tools/c6h6_repo.png">
2. In you fork (i.e., your personal copy) you can click on the ["clone"](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) button, copy the URL
   <img style="float:center; width: 30em" src="{{ site.url }}/assets/img/developer_tools/clone.png">

   In your terminal run `git clone <myurl>` (in my case `git clone git clone https://github.com/kjappelbaum/c6h6-documentation`). This will create a new folder in which you can go with `cd c6h6-documentation`. In this folder you can type `code .`, which will open VSCode (note that is easiest to start with the `HTTPS` URL, if you get used to working with GitHub it can be useful to [upload your SSH keys for authentication](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)). On Windows [you can perform these changes using command prompt](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/)

3. In VSCode, you can use the footer to make new branch. Likely, it will write "master".
   <img style="float:center; width: 25em" src="{{ site.url }}/assets/img/developer_tools/branch.png">

   If you click on this a small editor opens that allows you to make a new branch with a name of your choice.
   We recommend using a short name that describes the type of your change, e.g., `fix-isotherm-docs`

   <img style="float:center; width: 25em" src="{{ site.url }}/assets/img/developer_tools/branch_name.png">

4. Then you can start making the changes in the relevant files
5. Using the version control icon in the activity bar on the left you can ["stage" and then "commit"](https://githowto.com/staging_and_committing) the changes you made. For this you can just write a message like `doc: fixed typos in the isotherm documentation` and then click on the checkmark
   <img style="float:center; width: 20em" src="{{ site.url }}/assets/img/developer_tools/source_control.png">
6. Once you committed your changes, you can push them using the "synchronize changes" icon in the footer (status bar) of VSCode.
7. Once you have pushed the changes you'll see that there is a banner in your fork that gives you the option to make a [pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) by clicking on a green button.
   <img style="float:center; width: 25em" src="{{ site.url }}/assets/img/developer_tools/pr_button.png">
8. If you can click this button, you'll be directed to a from where you can describe your changes and make the pull request.
9. We will review the pull request and merge it to the main branch. As soon as the pull request is merged, GitHub will also show you as "Contributor".

## Where do I make the changes?

At first, it might be intimidating to find the relevant files in the `c6h6-documentation`, but in practice it is easy to find the file you need to edit

### I want to fix a typo or extend an existing page

If there is also an existing page, you can just search across all files for some text from this page and VSCode will find the relevant file, in the screenshot below we only search for "XRD" and directly find the relevant files

  <img style="float:center; width: 16em" src="{{ site.url }}/assets/img/developer_tools/xrd_search.png">

### I want to add a new page or new "tips" to an existing page

Adding a new page is slightly more difficult.

First, it is usually good to get inspired by existing pages. This is, if you want to add some documentation for IV curves you might find it practical to get started by copy/pasting the XRD documentation folder. If you want to add documentation for some spectra type, you'll do so in `src/book/spectra`. You will create a `README.md` file with the main documentation content and a `index.yml` with the metadata---that is, the `UUID` of the view. As shown above, you can get it from the Network tab in the developer tools (which you can open using right-click on the page, then inspect)

You may have noticed that for some techniques there is not only one `README.md` file but also some folders. Those are the other sections that will appear as "tips". For example, if you look at the PXRD documentation, you see that main `README.md` file will be shown as introduction (as on any other pages) but in the [`/src/book/spectra/pxrd/` directory](https://github.com/cheminfo/c6h6-documentation/blob/master/src/book/spectra/pxrd/index.yml) we also have a subfolder called `simulation` that contains a `index.md` file that will be shown as additional section in the documentation. You can add an unlimited number of such subfolders which will show up as separate "tips". Note that you have to add those tips to the `index.yml` file with a `title` and `name`. The `title` will be the title that shows up in the documentation in the ELN and the `name` is the name of the subfolder (please do not use spaces). An example of the complete `index.yml` file looks like

```yaml
description: View compare and simulate PXRD
uuid: c7bc5cf7caebbff02b1ae83e32bfd68f
tips:
  - minRev: 95
    title: Simulation from CIF file
    name: simulation
```

and the folder in the `/src/book/spectra/` directory looks like

```
pxrd
├── README.md
├── images
│   └── analysis.png
├── index.yml
└── simulation
    ├── index.md
    └── simulation.png
```

The `description` in the `yml` file is the title of the documentation section, the `uuid` is the UUID of the view that you can extract using the developer tools (as described above) and the `tips` lists contains all subfolders that you want to appear as separate tips (in this case, `simulation`). In the case of the PXRD documentation, the final product will look as follows

<img style="float:center; width: 40em" src="{{ site.url }}/assets/img/developer_tools/pxrd_docs.png">

### Basics of Markdown

Even if you now have the file you want to edit or create you still might wonder how you need to structure the file. All the files are written in Markdown, which in contrast to Microsoft Word or Google Docs follows the ["what you see is what you mean" principle](https://en.wikipedia.org/wiki/WYSIWYM). That is, there is usually some syntax you need to use to format your text, e.g., to make it bold or to make a header. To make it easier to see what is going on, you can open the ["Preview" in VSCode which will automatically update the document based on the markdown "code" you write](https://code.visualstudio.com/Docs/languages/markdown).

The Markdown syntax is pretty easy and there only a few things you need to know to make contributions to the documentation:

- To create headings, markdown uses hashtags (`#`). The number of hashtags indicates the heading level. That is, you might do something like

```markdown
# Section

## Subsection

### Subsubsection
```

And markdown will automatically adjust the font size for you and these headings can also be used for navigation or to create a table of contents.

- To add a hyperlink you will use `[linktext](link)`, if you want to link to google you might write something link `for more details you can just [google](www.google.com) it`.

- To make something **bold** you can use double underscores `__bold__`
- To _italicize_ something you can use stars `*in italics*`
- To add an image you use syntax that is quite similar to the hyperlink syntax `![alternative text](link to image)`
- If you need to add some formula you can use our [LaTeX generator tool](http://www.cheminfo.org/?viewURL=https%3A%2F%2Fcouch.cheminfo.org%2Fcheminfo-public%2F12c971bb3f9d5f93dfbf82f27e089d35%2Fview.json&loadversion=true&fillsearch=Convert+tex+latex+for+github) that will give you an "URL" that you can use with the image syntax, e.g, `![quadratic formula](https://tex.cheminfo.org/?tex=x%20%3D%20%7B-b%20%5Cpm%20%5Csqrt%7Bb%5E2-4ac%7D%20%5Cover%202a%7D)` will yield ![quadratic formula](https://tex.cheminfo.org/?tex=x%20%3D%20%7B-b%20%5Cpm%20%5Csqrt%7Bb%5E2-4ac%7D%20%5Cover%202a%7D)

It is often practical to include screenshots. macOS, Windows, and Linux all have useful tools and keybindings to create screenshots:

- On Mac you can simply use `CMD+SHIFT+4` and draw a rectangle around the area of interest. By default, screenshots are saved on the desktop, and you can use Preview to add highlights and annotations.
- On Windows you can use the [Snipping Tool](https://support.microsoft.com/en-us/windows/use-snipping-tool-to-capture-screenshots-00246869-1843-655f-f220-97299b865f6b) for this you only need to press the "Start" button and search for "snipping tool". Similar to the Mac tool you can select an area or capture the full screen. You can also directly annotate the screenshots.
- On Ubuntu you can just press the `Prt Scrn` button and will find a screenshot in your `home` directory. [But you can also search for screenshot](https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html) and use a utility that allows to select a region of interest.

Note that there are also some Chrome Plugins that allow you to take screenshots directly from the browser. [Some](https://www.awesomescreenshot.com/) even allow you to record short screencasts.

It is good practice to make a folder `images` for the images you add to the documentation.

## Hands on walkthrough

In the short video below we show you how you fork the [c6h6-documentation repository](https://github.com/cheminfo/c6h6-documentation/tree/master/src/book), make a new branch, make and commit changes to the documentation and then make a pull request.

{% include youtube.html id="SLvsZwa5KfY" %}

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
