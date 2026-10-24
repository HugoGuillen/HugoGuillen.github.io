---
layout: page
title: Equity and deployment-readiness audits
description: Checking whether a clinical model is calibrated and useful for every patient subgroup, and how much the data can actually tell us, before it reaches the ward.
importance: 5
github: https://github.com/HugoGuillen/isitfair
---

A model with a good overall AUROC can still be miscalibrated for older patients, or offer no net benefit for a small subgroup. Small subgroups also make every estimate uncertain, so an audit has to say which comparisons the data can support at all.

This work audits perioperative infection models subgroup by subgroup: discrimination, calibration, decision curves and net benefit, with a separate check of what can be estimated. The audit is packaged as **isitfair**, an open-source Python library that works from any model's predicted probabilities and writes a single HTML report aligned with TRIPOD+AI reporting.

**Publications and code**

- Guillen-Ramirez, H., Lucas, K. L., Wintsch, Y. M., Blatter, T. U., Triep, K., Endrich, O., & Beldi, G. **Subgroup deployment-readiness audit of calibration and clinical utility in perioperative infection prediction.** *Journal of the American Medical Informatics Association* (2026), in press. doi:10.1093/jamia/ocag184
- Software: [isitfair](https://github.com/HugoGuillen/isitfair) (MIT licence). Install with `pip install git+https://github.com/HugoGuillen/isitfair.git`.
