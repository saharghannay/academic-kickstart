---
title: "Enriching confusion networks for post-processing"
date: 2017-10-23
authors: ["**Sahar Ghannay**","Yannick Estève","Nathalie Camelin"]
publication_types: ["1"]
abstract: "The paper proposes a new approach for a posteriori enrichment of au- tomatic speech recognition (ASR) confusion networks (CNs). CNs are usually needed to decrease word error rate and to compute confidence measures, but they are also used in many ways in order to improve post-processing of ASR outputs. For instance, they can be helpfully used to propose alternative word hypotheses when ASR outputs are corrected by a human on post-edition. However, CNs bins do not have a fixed length, and sometimes contain only one or two word hypothe- ses: in this case the number of alternatives to correct a misrecognized word is very low, reducing the chance of helping the human annotator. Our approach for CN enrichment is based on a new similarity measure presented in this paper, computed from acoustic and linguistic word embeddings, that al- lows us to take into consideration both acoustic and linguistic similarities between two words. Experimental results show that our approach is relevant: enriched CNs (for a bin size equals to 6) increase the potential correction of erroneous words by 23% than initial CNs produced by an ASR system. In our experiments, a spoken language understanding task is also targeted."
featured: true
publication: "*Statistical Language and Speech Processing 2017*"
url_pdf: "https://hal.archives-ouvertes.fr/hal-01585768/document"
url_slides: "slides.pdf"
---
