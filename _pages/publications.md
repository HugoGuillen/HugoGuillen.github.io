---
layout: page
permalink: /publications/
title: Publications
description: Peer-reviewed articles and proceedings, newest first. My name is underlined.
years: [2026, 2025, 2024, 2023, 2022, 2021, 2020, 2019, 2018, 2017, 2013]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<p class="pub-profiles">Also on <a href="https://scholar.google.com/citations?user=uKT3kuEAAAAJ">Google Scholar</a>, <a href="https://orcid.org/0000-0003-0705-7432">ORCID</a> and <a href="https://www.scopus.com/authid/detail.uri?authorId=55822608900">Scopus</a>.</p>

<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
    {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

  <h2 class="year">preprints</h2>
  <p class="preprint-note">Not peer reviewed. Listed separately from the record above.</p>
    {% bibliography -f preprints.bib %}

</div>
