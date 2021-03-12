---
layout: post
title: "New seminar series / graduate course"
date: 2020-12-07 19:53:30 +0100
categories: [tutorial, news]
---

Over the last year we had the opportunity to participate in 4 doctoral school classes and it appears that some features of eln.epfl.ch that can be used to solve research projects are not well known.
For this reason we will organize some short (max 30 min) seminars by Zoom (https://epfl.zoom.us/j/81068501953) on regular base. They will take place Monday at 5PM (Swiss time) by Zoom.

## Schedule

### 18.1.2021: General introduction to eln.epfl.ch

The first seminar will focus on the "big picture"

- Philosophy
- Store / retrieve original data
- Extract knowledge
- Publish information to Zenodo

<a href="https://www.dropbox.com/s/u1fm0z0i3bggpac/topic%201.pdf?dl=1">Slides</a>

### 1.2.2021: Add a new sample

- Biological sample, material sample.
- Chemical structure, stereochemistry, mixture of isomers.
- Natural or modified peptidic and nucleic sequences.
- Keywords and meta information.

### 15.2.2021: Managing chemical libraries of synthesized products

- Find synthesized chemicals from former colleagues.
- How to create labels for new products (with chemical structure)?
- Define a location and status.
- Update the stock.

<a href="https://www.dropbox.com/s/f0rbmm5xiiu53i3/20200214_chemical_libraries.pdf?dl=1">Slides</a>


### 1.3.2021: Monoisotopic mass

- Determine possible molecular formula from monoisotopic mass
- Problem of ionization.
- Difference of mass and corresponding molecular formula.
- Pubchem lookup.

### 15.3.2021: Mass spectrometry of polymers

- Polymer, copolymer, ⍺ and ⍵ end groups.
- Kendrick chart.
- Advanced reporting.

### 29.3.2021: Electronic laboratory notebook

- Calculation of quantities.
- Definition of shortcuts.

### 12.4.2021: Mass spectrometry of natural or non-natural peptides

- How to enter a sequence?
- Fragmentation and internal fragmentation.
- Create a report for publication.

### 26.4.2021: Image analysis

- Bit depth, mask, ROI, resolution
- Hull, MBR, Ferret min, Ferret max, Compactness

### 10.5.2021: XRD and PXRD (Kevin Jablonka)

- Find topology of a periodic net
- Predict PXRD patterns / change cell parameters
- Match to pattern in database using Deep Learning
- Look up PXRD patterns form database

### 25.5.2021: Multiple spectra analysis

- Superimpose hundreds of spectra in one click
- Integration, relative spectra
- Export data for kinetic analysis

### 7.6.2021: Machine learning on spectra

- Preprocessing and normalization of spectra
- Principal component Analysis (PCA)
- Uniform Manifold Approximation and Projection (UMAP)

### 14.6.2021: Data exportation

- Create reports
- Export to Zenodo
- Download files as a ZIP

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
