---
layout: page
title: LLMs for multilingual clinical data
description: Large language models and semantic embeddings that align medical procedure terms across languages and national coding systems.
importance: 4
github: https://github.com/HugoGuillen/MAPCARE
---

Switzerland codes medical procedures in its own classification (CHOP) and documents them in German, French and Italian. That makes it hard to pool procedure data across hospitals and countries, or to compare it with English-language systems. Keyword search does not bridge the gap.

MAP-CARE uses large language models to translate and explain procedure codes, then places terms from different languages and classifications in one shared embedding space. Translation of procedure codes across English, German, French and Italian reached Acc@5 = 0.90. Mapping between two national procedure classifications gave exact or near matches for more than 53.8% of codes at the most detailed level. The framework can be extended to a new terminology from a single CSV file, and the code is public.

**Publications and code**

- Guillen-Ramirez, H., Triep, K., Gaudet-Blavignac, C., Phull, B., Beldi, G., & Endrich, O. **LLM-augmented semantic embeddings enable cross-lingual mapping of medical procedure terms.** *Scientific Reports* (2026). [doi:10.1038/s41598-025-34778-7](https://doi.org/10.1038/s41598-025-34778-7)
- Code: [MAPCARE](https://github.com/HugoGuillen/MAPCARE), archived on Zenodo: [doi:10.5281/zenodo.15453910](https://doi.org/10.5281/zenodo.15453910)
