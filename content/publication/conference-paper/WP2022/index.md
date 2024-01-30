---
title: "Analyzing BERT Cross-lingual Transfer Capabilities in Continual Sequence Labeling"
date: 2020-10-01
authors: ["**Coria Juan Manuel**","Veron Mathilde", "Ghannay Sahar","Bernard Guillaume","Bredin Hervé", "Galibert Olivier","Rosset Sophie"]
publication_types: ["1"]
abstract: "Knowledge transfer between neural language models is a widely used technique that has proven to improve performance in a multitude of natural language tasks, in particular with the recent rise of large pre-trained language models like BERT. Similarly, high crosslingual transfer has been shown to occur in multilingual language models. Hence, it is of great importance to better understand this phenomenon as well as its limits. While most studies about cross-lingual transfer focus on training on independent and identically distributed (i.e. i.i.d.) samples, in this paper we study cross-lingual transfer in a continual learning setting on two sequence labeling tasks: slotfilling and named entity recognition. We investigate this by training multilingual BERT on sequences of 9 languages, one language at a time, on the MultiATIS++ and MultiCoNER corpora. Our first findings are that forward transfer between languages is retained although forgetting is present. Additional experiments show that lost performance can be recovered with as little as a single training epoch even if forgetting was high, which can be explained by a progressive shift of model parameters towards a better multilingual initialization. We also find that commonly used metrics might be insufficient to assess continual learning performance."
featured: true
publication: "*First Workshop on Performance and Interpretability Evaluations of Multimodal, Multipurpose, Massive-Scale Models*"
---
