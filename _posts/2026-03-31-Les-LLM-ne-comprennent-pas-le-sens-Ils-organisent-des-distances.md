---
layout: post
title: "Les LLM ne comprennent pas le sens. Ils organisent des distances."
date: 2026-03-31
author: Baptiste Macé
categories: [IA, technologie, science]
tags: [LLM, IA, NLP, embeddings, transformers, vecteurs]
---

# **Les LLM ne comprennent pas le sens. Ils organisent des distances.**

On parle beaucoup d’intelligence artificielle, comme des entités qui comprennent, qui raisonnent, qui seraient capables, d’une certaine manière, de saisir le monde comme nous le faisons.

Mais si l’on prend un peu de recul, et que l’on observe ces systèmes non pas à travers leur discours marketing, mais à travers leur mécanique mathématique, alors une réalité beaucoup plus simple apparaît.

Un LLM ne comprend pas le sens, Il organise des distances dans un espace vectoriel.

Et ce déplacement, du sens vers la distance, change profondément la nature de ce que ces systèmes produisent.


## **Le langage transformé en géométrie**

Dans un modèle de langage, les mots ne sont jamais manipulés comme des entités porteuses de signification intrinsèque. Ils sont transformés en vecteurs, c’est-à-dire en points dans un espace de grande dimension :

 ![espace de grande dimension](/assets/LLM/EspaceGrandeDimension.png "espace de grande dimension")

Cette notion est fondamentale, car elle explicite la transformation d’un problème linguistique en problème géométrique.

Parler ne consiste plus à manipuler des idées, mais à se déplacer dans un espace vectoriel.  
Raisonner ne consiste plus à enchaîner des concepts, mais à suivre une trajectoire probable.


## **Le cœur du système : mesurer la proximité**

Dans cet espace, la relation entre deux idées se résume à une question de proximité, souvent mesurée à l’aide de la similarité cosinus :

 ![similarité cosinus](/assets/LLM/similaritécosinus.png "similarité cosinus")

Ce calcul, répété des milliards de fois, permet au modèle de répondre à une seule question :

quelle est la suite la plus proche, dans cet espace, de ce qui vient d’être dit ?

Autrement dit, le modèle ne cherche ni le vrai, ni le juste, ni même le pertinent au sens humain. Il cherche juste ce qui est le plus probable, c’est-à-dire ce qui est le plus proche dans la géométrie qu’il a apprise.


## **Un espace latent de centaines de dimensions**

Les vecteurs manipulés vivent dans des espaces de très grande dimension et chacune de ces dimensions constitue un degré de liberté que le modèle ajuste pour minimiser son erreur.

Au départ, ces dimensions sont purement aléatoires.  
Puis, au fil de l’entraînement, elles se structurent progressivement sous l’effet de l’optimisation.

Aucune dimension n’est conçue pour représenter une idée précise.  
Elles deviennent utiles uniquement parce qu’elles permettent d’améliorer la prédiction.

Ce que l’on appelle “sens” n’est donc rien d’autre qu’une structure émergente dans cet espace.

Et la fonction de la transformation d’un token dans un espace dimensionnel s'appel embedding

### **Quelques modèles d’embeddings et leurs dimensions**

| Modèle | Dimensions | Usage | Cas d'usage recommandé |
| ----- | ----- | ----- | ----- |
| Word2Vec / GloVe | 300 | Mots | Analyse lexicale, NER |
| SBERT (Sentence-BERT) | 384, 768, 1024 | Phrases,pargraphes | FAQ, chatbots, support client |
| OpenAI text-embedding-3-small | 1 536 | Corpus interne | Documentation entreprise, KB métier |
| OpenAI text-embedding-3-large | 3 072 | Corpus volumineux | Recherche juridique, médicale, scientifique |


## 

## **Des axes invisibles, mais profondément structurants**

Il n’existe nulle part, dans le modèle, une dimension explicitement nommée :

* “bien / mal”  
* “légitime / illégitime”  
* “fréquentable / non fréquentable”

Et pourtant, ces oppositions finissent par apparaître.

Non pas comme des catégories déclarées, mais comme des directions implicites dans l’espace, issues des régularités du corpus d’entraînement.

Ces axes ne sont jamais écrits noir sur blanc, mais ils organisent la manière dont les idées se rapprochent, se repoussent, ou deviennent accessibles.

Autrement dit, ils structurent silencieusement le champ du pensable. 


## **Le sens devient une position**

Dans ce cadre, une idée n’est plus définie par une essence ou une vérité.  
Elle est définie par sa position relative :


![idée approvimative](/assets/LLM/ideaApproximative.png "idée approvimative") 

Comprendre une phrase revient alors à projeter un point dans cet espace, à mesurer ses distances aux autres points, puis  à sélectionner, à chaque étape, le token le plus probable compte tenu du contexte.

Il ne s’agit plus de compréhension, mais de navigation.


## **Influencer sans jamais écrire de règle**

Il est tentant d’imaginer qu’un système de ce type serait neutre, puisqu’il ne contient pas de règles explicites. En réalité, il n’en est rien.

Dans un espace vectoriel, il n’est pas nécessaire d’interdire une idée pour la faire disparaître. Il suffit de la rendre distante.

Si un concept est :

* fréquemment associé à certains contextes  
* rarement exposé dans d’autres  
* ou totalement absent

alors sa position dans l’espace sera affectée en conséquence.

Et cette position déterminera :

* sa probabilité d’apparition  
* sa manière d’être formulé  
* sa capacité à émerger dans une réponse


## **Invisibiliser par la structure**

Le mécanisme le plus puissant n’est donc pas la censure explicite. C’est l’organisation implicite.

Dans un LLM :

- ce qui est proche apparaît naturellement  
- ce qui est éloigné devient improbable  
- ce qui est absent devient difficilement pensable

L’optimisation mathématique se charge du reste.


## **Orwell revisité par la géométrie**

Dans *1984*, George Orwell décrivait la novlangue comme un outil de réduction du vocabulaire, destiné à rendre certaines pensées impossibles. Les modèles de langage introduisent une transformation plus subtile encore. On ne supprime pas nécessairement les mots. On modifie leur position. Ce n’est plus une réduction du langage, mais une reconfiguration de l’espace dans lequel il évolue.

Ce n’est plus : tu ne peux pas le dire

Mais : tu n’y accèdes pas, parce que les trajectoires qui y mènent sont devenues improbables

**Des modèles profondément occidentalisés**

Les modèles actuels sont entraînés majoritairement sur des données issues d’un espace culturel bien particulier : anglophone, occidental, filtré

Cela signifie que l’espace latent lui-même est structuré par ces références.

Certaines représentations du monde deviennent centrales, presque naturelles.  
D’autres sont marginalisées, déformées ou absentes (ex : les traditions orales).

Ce n’est pas un biais accidentel.  
C’est une conséquence directe du processus d’apprentissage.

Et cela pose une question fondamentale :

qui définit la géométrie du langage ?


## **Une question de souveraineté**

Si les LLM organisent le pensable à travers des distances, alors contrôler les données et les modèles revient à contrôler cette géométrie.

Autrement dit :

Contrôler les embeddings, c’est influencer les représentations du monde et donc c’est les décisions

La question n’est donc plus uniquement technique. Elle devient politique.

Dépendre de modèles entraînés ailleurs, avec d’autres référentiels culturels, d’autres priorités, d’autres filtres, c’est accepter que la structure même du discours soit externalisée.

La souveraineté ne concerne plus seulement les infrastructures ou les données. Elle concerne désormais la manière dont le sens lui-même est organisé.


## **Conclusion**

Les LLM ne manipulent pas le sens. Ils manipulent des positions, des distances et des probabilités Et à partir de cette géométrie, ils reconstruisent un monde plausible.

Un monde dans lequel certaines idées sont centrales, d’autres marginales, et certaines presque impossibles à atteindre.


