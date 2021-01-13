---
title: Word embeddings training
linktitle: TP 1
toc: true
type: docs
date: "2018-05-05T00:00:00+01:00"
lastmod: "2020-09-09T00:00:00Z"
draft: false
menu:
  Cours1:
    parent: Semantic Representations
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---
[English version below]

# Objectif 


L'objectif du TP est de construire et de comparer différents type de plongements lexicaux (embeddings de mots) en utilisant les bibliothèques `gensim` et `fasttext`.  
Ces embeddings seront entrainés sur deux corpus différents : corpus en domaine médical (QUAERO_FrenchMed) de petite taille et un corpus non médical (QUAERO_FrenchPress) de grande taille. 
Ils seront évalués sur la tâche de détection d’entités nommées (NER : Named Entity recognition)  pendant le TP2 (l’après midi). 

Vous êtes invités à utiliser les approches **word2vec** (Cbow, skipgram) et **fasttext** (Cbow).

# Ressources

- Word2vec : [https://radimrehurek.com/gensim/models/word2vec.html#gensim.models.word2vec.Word2Vec](https://radimrehurek.com/gensim/models/word2vec.html#gensim.models.word2vec.Word2Vec)
- Fasttext : [https://fasttext.cc/docs/en/support.html](https://fasttext.cc/docs/en/support.html)
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip
  - Les fichiers `QUAERO_FrenchMed_traindev.ospl` et `QUAERO_FrenchPress_traindev.ospl` seront utilisés pour l'apprentissage des embeddings. Ils contiennent des corpus au format «une phrase par ligne», avec une segmentation des tokens qui sont séparés par des espaces. 

# Outils nécessaires 

Avant de commencer le TP, Je vous invite à suivre les étapes suivantes pour installer les outils :   

```
# Créer l'environnement de travail «miniconda»
# Télécharger le fichier et l'installer comme suit :
 wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
 chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
# Créer l'environnement et l'activer
  conda create -n myenv python=3.6
  Conda activate myenv
# Installer les outils nécessaires pour la création de plongements lexicaux
  pip install gensim==0.12.0
  pip install fasttext 
```

# Apprentissage des embeddings de mot

La première étape de votre travail va être de créer des scripts python et bash permettant d'apprendre les différentes approches d’embeddings **word2vec** (Cbow, skipgram) et **fasttext** (Cbow) sur les deux corpus médical et non médical **QUAERO_FrenchMed** et **QUAERO_FrenchPress** (au total 6 embeddings). 

Suivez les étapes nécessaires dans la documentation pour créer et sauvegarder les modèles et les embeddings de mots.

Vous pouvez utiliser ces hyper-paramètres pour l'apprentissage des embeddings : `dim=100`, `min_count=1`.


# Similarité sémantique

La deuxième étape consiste à trouver les mots les plus proches d'un mot donné en s'appuyant sur le calcul de similarité cosinus. 
Plusieurs évaluations à faire : 

- Comparer des  d'embeddings entrainés sur le même corpus :   
    - tester l'impact des approches (skipgram, cbow, fasttext) sur le résultats
- Comparer des embeddings (même approche) entrainés sur de corpus différents (médical et non médical) :
    - tester l'impact de données (type et quantité) sur les résultats 

Voici la liste de mots candidats :  `patient, traitement, maladie, solution, jaune`

Pour l'évaluation vous pouvez utiliser soit : 

- la méthode `spatial` de la bibliothèque python scipy, dans ce cas, vous devez charger les embeddings construits, et cherchez pour un mot donné la liste des 10 mots les plus proches
- la méthode `most_similar` du gensim, dans ce cas, vous devez charger les modèles sauvegardés
  - vous pouvez utiliser gensim pour charger les modèles word2vec et fasttext
------------------

# Objective

The objective of this lab session is to build and compare different word embeddings aproaches using the `gensim` and` fasttext` libraries.
These embeddings will be trained on two different corpora: a small medical corpus (QUAERO_FrenchMed) and a large non-medical corpus (QUAERO_FrenchPress).
They will be evaluated on the NER: Named Entity recognition task during the second pratical session TP2 (afternoon).

You are invited to use the **word2vec** (Cbow, skipgram) and **fasttext** (Cbow) approaches.

# Ressources

- Word2vec : [https://radimrehurek.com/gensim/models/word2vec.html#gensim.models.word2vec.Word2Vec](https://radimrehurek.com/gensim/models/word2vec.html#gensim.models.word2vec.Word2Vec)
- Fasttext : [https://fasttext.cc/docs/en/support.html](https://fasttext.cc/docs/en/support.html)
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip
  - The files `QUAERO_FrenchMed.ospl` and` QUAERO_FrenchPress_ID.ospl` will be used for learning embeddings. They contain corpora in “one sentence per line” format, with a segmentation of the tokens which are separated by spaces.

# Requirements 

Before starting, I invite you to follow the next steps to install the tools:

```
# Create the "miniconda" environment
# Download the file and install it as follows:
 wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
 chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
# Create the environment and activate it
  conda create -n myenv python=3.6
  Conda activate myenv
# Install the required tools to train word embeddings
  pip install gensim==0.12.0
  pip install fasttext 
```


# Word embeddings training

The first step of your work is to create python and bash scripts allowing you to train the different embeddings approaches: **word2vec** (Cbow, skipgram) and **fasttext** (Cbow), on the two medical and non-medical corpora, resulting to 6 embeddings models.

Follow the steps in the documentation to create and save the models and the word embeddings.

You can use these hyper-parameters to train the embeddings: `dim = 100`,` min_count = 1`.


# Semantic similarity

The second step is to find the closest words to a given word based on the cosine similarity calculation.
Several evaluations to do:

- Compare embeddings trained on the same corpus:
    - to test the impact of the embeddings approaches (skipgram, cbow, fasttext) on the results
- Compare embeddings (same approach) trained on different corpora (medical and non-medical):
    - to test the impact of data (type and quantity) on the results

Here is the candidate word list: `patient, treatment, disease, solution, yellow`

For the evaluation you can use either:

- `spatial` method of the python scipy library, in this case, you must load the embeddings vectors, and search for a given word for the list of the 10 closest words
- gensim's `most_similar` method, in this case you have to load the saved models
  - you can use gensim to load word2vec and fasttext models

