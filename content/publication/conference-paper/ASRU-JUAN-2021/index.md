---
title: "OVERLAP-AWARE LOW-LATENCY ONLINE SPEAKER DIARIZATION BASED ON END-TO-END LOCAL SEGMENTATION"
date: 2021-12-17
authors: ["**Juan Manuel Coria**", "Hervé Bredin", "Sahar Ghannay","Sophie Rosset"]
publication_types: ["1"]
abstract: "We propose to address online speaker diarization as a combination of incremental clustering and local diarization applied to a rolling buffer updated every 500ms. Every single step of the proposed pipeline is designed to take full advantage of the strong ability of a recently proposed end-to-end overlap-aware segmentation to detect and separate overlapping speakers. In particular, we propose a modified version of the statistics pooling layer (initially introduced in the x-vector architecture) to give less weight to frames where the segmentation model predicts simultaneous speakers. Furthermore, we derive cannot-link constraints from the initial segmentation step to prevent two local speakers from being wrongfully merged during the incremental clustering step. Finally, we show how the latency of the proposed approach can be adjusted between 500ms and 5s to match the requirements of a particular use case, and we provide a systematic analysis of the influence of latency on the overall performance (on AMI, DIHARD and VoxConverse)."
featured: true
publication: "*IEEE Automatic Speech Recognition and Unserstanding Workshop (ASRU 2021)*"
url_pdf: "https://hal.archives-ouvertes.fr/hal-03375330/document"
---
