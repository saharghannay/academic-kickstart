---
title: "Simulating ASR errors for training SLU systems"
date: 2018-05-07
authors: ["Edwin Simonnet","**Sahar Ghannay**","Nathalie Camelin","Yannick Estève"]
publication_types: ["1"]
abstract: "This paper presents an approach to simulate automatic speech recognition (ASR) errors from manual transcriptions and describes how it can be used to improve the performance of spoken language understanding (SLU) systems. In particular, we point out that this noising process is very usefull to obtain a more robust SLU system to ASR errors in case of insufficient training data or more if ASR transcriptions are not available during the training of the SLU model. The proposed method is based on the use of both acoustic and linguistic word embeddings in order to define a similarity measure between words dedicated to predict ASR confusions. Actually, we assume that words acoustically and linguistically close are the ones confused by an ASR system. By using this similarity measure in order to randomly substitute correct words by potentially confusing words in manual annotations used to train CRF- or neural based SLU systems, we augment the training corpus with these new noisy data. Experiments were carried on the French MEDIA corpus focusing on hotel reservation. They show that this approach significantly improves SLU system performance with a relative reduction of 21.2% of concept/value error rate (CVER), particularly when the SLU system is based on a neural approach (re- duction of 22.4% of CVER). A comparison to a naive noising approach shows that the proposed noising approach is particularly relevant."
featured: false
publication: "*11th edition of the Language Resources and Evaluation Conference (LREC 2018)*"
url_pdf: "https://www.aclweb.org/anthology/L18-1499.pdf"
url_poster: "poster.pdf"
---
