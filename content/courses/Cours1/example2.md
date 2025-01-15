---
title: Named entity recognition
linktitle: TP 2
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  Cours1:
    parent: Semantic Representations
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---
[English version below]

# Objectif


L'objectif du TP est d'évaluer la performance des embeddings appris dans le TP1 ainsi qu'un modèle Transformer (BERT) sur la tâche d'entités nommées (NER) dans le domaine médicale. 
Un modèle NER par type d'embeddings sera appris et évalué.

  

# Ressources

- Les {{% staticref "files/scripts.zip" "newtab" %}} scripts {{% /staticref %}} à adapter pour la tâche de classification de séquence, un pour exécuter les modèles LSTM et CNN, un autre pour exécuter les modèles Transformer (BERT) 
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip

# Outils nécessaires

Veuillez installer les dépendances nécessaires pour executer les scripts



# Présentation rapide des corpus : 
Nous utiliserons un corpus annoté en entités issu du domaine médical (QUAERO_FrenchMed) de petit taille.

Ce corpus vous est fourni dans un format similaire au format conll : il contient cinq colonnes séparées par des espaces. 

Chaque mot correspond à une ligne et les phrases sont séparées par une ligne vide. 
Les colonnes correspondent dans l'ordre à l'index du mot dans la phrase, le mot, deux autres colonnes qui ne seront pas utilisées et la dernière colonne représente l'étiquette d'entité nommée.

Les étiquettes d’entité nommée sont au format I-TYPE qui indique que le mot fait partie d’une entité de type TYPE. 
Si deux entités de même type se suivent, le premier mot de la seconde aura pour étiquette B-TYPE pour indiquer qu’il s'agit d’une nouvelle entité. 
L’étiquette O indique que le mot ne fait pas partie d’une entité.

# Création de modèles
Afin de réaliser le travail il faut adapter les scripts pour la tâche de NER (étiquetage de séquence): principalement le chargement des données, la fonction objective (si besoin)
- En plus de cela, dans le script cnn_classification.py, les embeddings sont initialisés aléatoirement, il faut faire les modifications nécessaires pour les initialisés avec les embeddings appris dans le TP1.
- Dans le script transformer_classification il faut changer 'AutoModelForSequenceClassification'  par 'AutoModelForTokenClassification' 
- Les résultats seront évaluer en termes de rappel, précision et F1

# Questions
- Quel modèle obtient les meilleures performances ?  
- Voyez vous des différences entre les embeddings appris sur deux corpus différents de TP1 ? 
- Comparer ces résultats avec un modèle Transformer.


 
------------------

# Objective

The objective of the lab session is to evaluate the performance of the embeddings learned in TP1 as well as a Transformer model (BERT) on the named entity task (NER) in the medical domain.
A NER model for each embeddings type will be learned and evaluated.



# Ressources

- The scripts {{% staticref "files/scripts.zip" "newtab" %}} to be adapted for the sequence classification task, one to run the LSTM and CNN models, another to run the Transformer (BERT) models
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip

# Requirements 

Please install the dependencies to run the scripts



# Quick overview of the datasets : 
We will use a small medical corpus (QUAERO_FrenchMed) with named entity annotations. 

The dataset is provided in conll-like format and contain five columns separated by white spaces. Each word (or token) corresponds to a line and sentences are separated by an empty line. 

The columns correspond to: the token index within the sentence, the token, two columns that will not be used in this lab and finally, the last column contains the named entity tag.

Named entity tags are in the I-TYPE format, which indicates that the word is part of a TYPE entity. If two entities follow each other, the first word of the second entity will get a B-TYPE tag to indicate that it is a new entity. The O tag indicates that the word is not part of an entity.

# NER models training

In order to do the work, it is necessary to adapt the scripts for the NER task (token classification): mainly the data loading, the objective function (if needed)
- In addition to that, in the cnn_classification.py script, the embeddings are initialized randomly, it is necessary to make the modifications to initialize them with the embeddings learned in TP1.
- In the transformer_classification script, it is necessary to change 'AutoModelForSequenceClassification' to 'AutoModelForTokenClassification'
- The results will be evaluated in terms of recall, precision and F1

# Questions 
 
- Which model provides the best performance on each dataset?  
- Do you see any differences between the embeddings learned on two different corpora of TP1?
- Compare these results with a Transformer model.