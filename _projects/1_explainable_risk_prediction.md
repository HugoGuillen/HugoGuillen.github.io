---
layout: page
title: Explainable perioperative risk prediction
description: Machine-learning models that predict postoperative infection from routine hospital data, with risk attributions clinicians can read and act on.
importance: 1
github: https://github.com/HugoGuillen/postsurgicalinfections
---

Infections after surgery are a leading cause of morbidity, and they are often recognised late. Hospitals already record most of the signal needed to spot them earlier: diagnoses, procedures and repeated laboratory measurements. This line of work turns those routinely collected records into prediction models that work across procedures and explain each prediction.

In the CARESCORE pipeline, we analysed 91,794 surgical cases from the electronic health record of Inselspital, Bern. We modelled how laboratory values change after surgery, not only their levels, and imputed missing postoperative values in a clinically informed way. On postoperative day 2 the model reached a ROC AUC of 0.83. Its explanations pointed to combinations of hepatic, renal and bone-marrow markers that had not been linked to infection risk before.

Related work with clinical colleagues looks at what drives infection in the first place: the patient's own gut microbes before surgery, how patient characteristics shape the microbes found in surgical-site infections, and noise in the operating room as a marker of surgical difficulty.

**Publications and code**

- Guillen-Ramirez, H. *et al.* **Prediction of postoperative infections by strategic data imputation and explainable machine learning.** *Journal of the American Medical Informatics Association* 32(11), 1706–1717 (2025). [doi:10.1093/jamia/ocaf145](https://doi.org/10.1093/jamia/ocaf145). Code and pretrained model: [postsurgicalinfections](https://github.com/HugoGuillen/postsurgicalinfections).
- Zwicky, S. N. *et al.* **Preoperative enterosignatures predict surgical site infections after abdominal surgery.** *Open Forum Infectious Diseases* 12(9), ofaf549 (2025). [doi:10.1093/ofid/ofaf549](https://doi.org/10.1093/ofid/ofaf549)
- Peisl, S.\*, Guillen-Ramirez, H.\* *et al.* **Influence of patient characteristics on microbial composition in surgical-site infections: insights from national surveillance study.** *British Journal of Surgery* 111(6), znae138 (2024). \*Shared first authorship. [doi:10.1093/bjs/znae138](https://doi.org/10.1093/bjs/znae138)
- Peisl, S. *et al.* **Noise in the operating room coincides with surgical difficulty.** *BJS Open* 8(5), zrae098 (2024). [doi:10.1093/bjsopen/zrae098](https://doi.org/10.1093/bjsopen/zrae098)
