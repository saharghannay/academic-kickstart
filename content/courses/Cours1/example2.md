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


L'objectif du TP est de construire et de comparer différents modèles de reconnaissance d'entités nommées à partir des plongements lexicaux (embeddings) construits lors du TP 1. Nous utiliserons un modèle neuronal LSTM implémenté par Ma et Hovy  

Vous êtes invités à construire plusieurs modèles pour chaque corpus de travail (voir ci-dessous) en faisant varier les paramètres suivants afin d’observer leur impact sur les performances de reconnaissance d’entités :
- taille du jeu d’entraînement ;  
- taille du corpus utilisé pour créer les plongements lexicaux
- modèle des plongements lexicaux
- adéquation entre le domaine du corpus utilisé pour la reconnaissance d’entités et les plongements. 
 
# Ressources

- L'outils `https://github.com/XuezheMax/NeuroNLP2`
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip

# Outils nécessaires

Veuillez installer cet outil dans votre environnement de travail.


```
# Installer l'outil nécessaire pour la reconnaissance d'entités nommées
  git clone https://github.com/XuezheMax/NeuroNLP2.git
  pip install torch==1.6.0+cpu torchvision==0.7.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
  pip install overrides
  pip uninstall scipy
  pip --no-cache-dir install scipy==1.1
  cd NeuroNLP2
  pip install .

```

# Présentation rapide des corpus : 
Nous utiliserons deux corpus annotés en entités, l’un issu du domaine médical (QUAERO_FrenchMed) de petit taille et l'autre issu de la presse (QUAERO_FrenchPress) de plus grande taille. 

Ces corpus vous sont fournis dans un format similaire au format conll : ils contiennent cinq colonnes séparées par des espaces. 

Chaque mot correspond à une ligne et les phrases sont séparées par une ligne vide. 
Les colonnes correspondent dans l'ordre à l'index du mot dans la phrase, le mot, deux autres colonnes qui ne seront pas utilisées et la dernière colonne représente l'étiquette d'entité nommée.

Les étiquettes d’entité nommée sont au format I-TYPE qui indique que le mot fait partie d’une entité de type TYPE. 
Si deux entités de même type se suivent, le premier mot de la seconde aura pour étiquette B-TYPE pour indiquer qu’il s'agit d’une nouvelle entité. 
L’étiquette O indique que le mot ne fait pas partie d’une entité.

# Création de modèles

La première étape de votre travail va être de créer des scripts shell permettant d’entraîner l'outil sous différentes configurations: 

- Utiliser comme base de travail le script `NeuroNLP2/experiments/scripts/run_ner_conll03.sh` 

Ajuster les paramètres concernant : le type de plongements, le fichier contenent votre vecteur de plongements,  --embedding_dict le répertoire de sortie désiré --model_path , le corpus --train  --dev --test

- Pour les besoins du TP (temps de calcul des modèles), vous pouvez ajuster certains paramètres dans la configuration du modèle : diminuer le nombre d’epoch --num_epochs 20, et de l’outil (script `NeuroNLP2/experiments/ configs/ner/conll03.json` ; par exemple, "crf": false,  "hidden_size": 128, "out_features": 64,). 
 
# Questions
- Quel modèle obtient les meilleures performances sur chacun des corpus ?  
- Voyez vous des différences entre les deux corpus ? 
- Comparer ces résultats avec une méthode « baseline » simple à base de règles
Pour cela, vous pourrez utiliser le script Perl `NeuroNLP2/experiments/eval/conll03eval.v2`

Pour aller plus loin : 
- Comparer le corpus QUAERO_FrenchMed utilisé en TP avec celui distribué lors de la campagne CLEF eHealth 2016 : `https://quaerofrenchmed.limsi.fr/` Constatez vous des différences ? Si oui, lesquelles ?
- Les résultats obtenus en TP peuvent-ils être comparés avec ceux obtenus lors de la campagne d’évaluation CLEF eHealth ? Pourquoi ? 

 
------------------

# Objective

The objective of this lab session is to build and compare different models of named entity recognition using the word embeddings created during lab session 1. We will use the biLSTM model implemented by Ma and Hovy

In this lab session, you should attempt to create several models for each dataset (see below). You may observe the impact of the following parameters on anmed entity recognition performance:
- size of the training set ;  
- size of the corpus used to create the word embeddings ;
- word embedding model ;
- consistency between the domain of the corpus used for entity recognition and the word embeddings. 


# Ressources

- NER tool `https://github.com/XuezheMax/NeuroNLP2`
- Corpus: https://perso.limsi.fr/neveol/TP_ISD2020.zip

# Requirements 

Please install this tool in your conda environement.

```
# Install the necessary tool for named entity recognition  git clone https://github.com/XuezheMax/NeuroNLP2.git
  pip install torch==1.6.0+cpu torchvision==0.7.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
  pip install overrides
  pip uninstall scipy
  pip --no-cache-dir install scipy==1.1
  cd NeuroNLP2
  pip install .
```

# Quick overview of the datasets : 
We will use two datasets with named entity annotations : a small medical corpus (QUAERO_FrenchMed) and a larger news corpus (QUAERO_FrenchPress). 

The datasets are provided in conll-like format and contain five columns separated by white spaces. Each word (or token) corresponds to a line and sentences are separated by an empty line. 

The columns correspond to: the token index within the sentence, the token, two columns that will not be used in this lab and finally, the last column contains the named entity tag.

Named entity tags are in the I-TYPE format, which indicates that the word is part of a TYPE entity. If two entities follow each other, the first word of the second entity will get a B-TYPE tag to indicate that it is a new entity. The O tag indicates that the word is not part of an entity.

# NER models training

The first step of your work will be to create shell scripts allowing you to train the tool in different configurations:
- Use the `NeuroNLP2/experiments/scripts/run_ner_conll03.sh` script as a working base

Adjust the parameters concerning: the type of embedding, the file contains your vector of embeddings, --embedding_dict the desired output directory --model_path, the corpus --train --dev --test
- Du to time constraint, you can adjust certain parameters in the model configuration: decrease the number of epoch --num_epochs 20, and of the tool (`NeuroNLP2 script/experiments/configs/ner/conll03.json`; for example, "crf": false, "hidden_size": 128, "out_features": 64,).
     
# Questions 
 
- Which model provides the best performance on each dataset?  
- Are there differences between the datasets ? 
- Compare the results of the models to a simple rule-based baseline method
You may use this Perl script : NeuroNLP2/experiments/eval/conll03eval.v2 

Going further : 
- Compare the QUAERO_FrenchMed dataset used in this lab session with the one distributed in the CLEF eHealth 2016 shared task : https://quaerofrenchmed.limsi.fr/ Do you see any différence ? Please, describe. 
- Can the results obtained in this lab session be directly compared to those of the CLEF eHealth shared task participants ? Please, explain.   

