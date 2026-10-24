---
layout: page
title: Software
permalink: /software/
description: Open-source code behind my papers.
nav: true
nav_order: 3
---

<div class="software" markdown="1">

Everything below is public on [GitHub](https://github.com/HugoGuillen).


<h2>isitfair</h2>
<p class="software-meta">Python · MIT licence · <a href="https://github.com/HugoGuillen/isitfair">github.com/HugoGuillen/isitfair</a></p>

Fairness evaluation for clinical prediction models. You bring a trained model's predicted probabilities and the patient groups to compare. isitfair reports subgroup-stratified discrimination, calibration and decision-curve analysis, states which estimates the data can support, and writes a single HTML report aligned with TRIPOD+AI.

```bash
pip install git+https://github.com/HugoGuillen/isitfair.git
```

Companion paper: *Subgroup deployment-readiness audit of calibration and clinical utility in perioperative infection prediction.* JAMIA (2026), in press.

<h2>MAP-CARE</h2>
<p class="software-meta">Python · <a href="https://github.com/HugoGuillen/MAPCARE">github.com/HugoGuillen/MAPCARE</a> · <a href="https://doi.org/10.5281/zenodo.15453910">Zenodo archive</a></p>

A pipeline that translates Swiss procedure codes (CHOP) with a local large language model, embeds them, and maps them to other classifications such as the German OPS by semantic similarity. Companion paper: *LLM-augmented semantic embeddings enable cross-lingual mapping of medical procedure terms.* Scientific Reports (2026), [doi:10.1038/s41598-025-34778-7](https://doi.org/10.1038/s41598-025-34778-7).

<h2>Code and data for papers</h2>

- [postsurgicalinfections](https://github.com/HugoGuillen/postsurgicalinfections): pretrained model and notebook for *Prediction of postoperative infections by strategic data imputation and explainable machine learning*, JAMIA (2025).
- [microbialcomposition](https://github.com/HugoGuillen/microbialcomposition): the InSSIght dashboard notebook for exploring the microbiology of surgical-site infections.
- [riboswitch2018](https://github.com/HugoGuillen/riboswitch2018): datasets for *Classification of riboswitch sequences using k-mer frequencies*, Biosystems (2018).
- [imorns](https://github.com/HugoGuillen/imorns): supplementary material for *Accurate classification of immunomodulatory RNA sequences*, IJCNN (2017).

<h2>Earlier tools</h2>

- [genehtracker](https://github.com/HugoGuillen/genehtracker): traces the GENCODE annotation history of Ensembl gene IDs and symbols, and maps retired IDs. Presented at ECCB 2022.
- [refractiveindex.info-sqlite](https://github.com/HugoGuillen/refractiveindex.info-sqlite): an SQLite wrapper for the refractiveindex.info optical-constants database.
- [ezTracks](https://github.com/HugoGuillen/ezTracks): plots a GTF annotation with grouped BED tracks.
- [arff2pandas](https://github.com/HugoGuillen/arff2pandas): loads ARFF files as pandas DataFrames.

</div>
