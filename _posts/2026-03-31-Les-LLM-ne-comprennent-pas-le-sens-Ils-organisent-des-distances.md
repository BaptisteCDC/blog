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

![][image1]

Cette notion est fondamentale, car elle explicite la transformation d’un problème linguistique en problème géométrique.

Parler ne consiste plus à manipuler des idées, mais à se déplacer dans un espace vectoriel.  
Raisonner ne consiste plus à enchaîner des concepts, mais à suivre une trajectoire probable.


## **Le cœur du système : mesurer la proximité**

Dans cet espace, la relation entre deux idées se résume à une question de proximité, souvent mesurée à l’aide de la similarité cosinus :

![][image2]

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

![][image3]

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

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYoAAABGCAYAAADSI9NrAAAPFUlEQVR4Xu2dh68URRzH/Qcs2LtiRewVUGwQgy2CvfcCYsNgQwWD2FssiCUKRmNijxpLxC5FY0VFBBtRwILSrCjqmM8kv3Nu3u7c3Xu39+49vp9kom93do/b253vzK/tMk4IIYRIsEy8QQghhAiRUAghhEgioRBCCJFEQiGEECKJhEIIIUQSCYUQQogkEgohhBBJJBRCCCGSSCiEEEIkkVAIIYRIIqEQQgiRREIhhBAiiYRCCCFEEgmFEEKIJBIKIYQQSSQUQgghkkgohBBCJJFQCCGESCKhEKJJuOqqq9yyyy4bbxY1cM8997h1113X7b777u6NN97w23755Rd36aWX+m0bbbSRGzhwoBs/fnx0pEghoRCiSWBgQygQjM7AuHHj3NVXX+2uuOIKd/nll/s2cuTIUuPvUaNGuSuvvNJdc8017oYbbnA333yzu/32290DDzzgPvzwQ/fvv//Gp83lvvvuc/vvv7/74osv3KqrrurbSy+95HbaaSd3/vnnu6+++sp98MEHrlu3bm655ZZzr776anwKkYOEQogmYt999/ViYbPhjsqff/7pB+0tt9zSdenSxX+nDTbYwO2www5uxx139K179+5+O41VwFprrVX62xrHnHrqqe69996LP6IFPXv29EIAm222mT9+hRVWcK+88kpZv7PPPtvvu+iii8q2i3wkFEIUgJmR2tI6C/PmzXNrr722N/+EXHbZZW7NNdd0b7/9dmnbr7/+6h5++GE/62dFcNttt7nevXv7FcApp5zi5s6dG5zhfzgHogQLFizw/bmGHB9zxhln+H3nnntuvEvkIKEQNTFp0iTXq1evqmZ4SzMIRa3NVhM0/r8z0b9/fz/Qhxx66KHuuOOOK9tmfPPNN26NNdZwY8eO9X8///zzbuONN/arhkWLFkW9nfvkk09KpqRnn33WX8OuXbtmmq5Y1bDfzi0qI6EQNXHXXXf5h+y1116Ld4k2YP4JWmfxUYQgFMcee2zZtoMOOsidcMIJZdtChg0b5rbbbrvS34jH5ptv7o9LgUmJ63j00UfHu9ycOXNK1xmfhagOCYWoCbPvSijqi5mqOqNIwIABA9wxxxxTtu3AAw90J510Utm2kJdfftlfkz/++KO07amnnvLbcFjnscsuu/g+d9xxR7zLO8rZ16NHj3iXSCChEDXRp08fCUUBIBCNcGD/+OOP7tFHH3WDBw922267rdtkk03chhtu6J3GccMZ/c8//8SnaBWsAmKhQDxic1TI119/nSkKOL2vu+66sm1G6J/4+OOP491uzz339PtuvPFG/zemKfwiIo2EQlTNZ599Vopg6ahCcdZZZ/nQy6WN999/3w+SNohi0tl7773dIYcc4k00mIBOPvlkd9ppp7lBgwZ5h+9NN90Un6bV8DmxUGCOIqIpD5zgWffarrvu6s1SWTzzzDP+mPXWW6+FfwLTlZmdECHATHXeeeeV9RMtkVCIqmEGaA9a/PB2FBgcSbxaWvj777/dtdde6wWelcOIESO84Deaww47LFMoSH7LY/bs2f5ee+utt8q2b7PNNt6ElAUCwjFZ/on777/f72MlBQsXLvSrk3jFIloioWgA2Fjnz58fb/aw7I1nPlkQl54V7VErU6ZMcU8//bT76KOP3F9//RXvzgV7r4lERxaKe++918+qGYQaAdeYwboS3Af8xvXkhx9+cH379vW/FyuFn3/+Oe7SMA4//PCahYLIunD2D2RZI3r4L7JgEsAxZGjHcN+zz/4dQ4YM8ddFVEZCUWemTp3qbbs41Ej6WW211fzN2a9fv1Kfhx56yJ1++uk+TI9BizC+448/3j344IPBmZz77bff/AyQcFQz+RCPzuzMEouq4fPPP/eZqZaEZG2llVby5og4IclYsmSJf+AOPvjgsuNoe+21lzviiCPK2hNPPBGfounAnEESVp7pol5g6uE357NWXHFFf098+umncTcP9nLyCUg6y+vTGjD3LL/88j4vob058sgjWwjFAQcckBQKHNc8H4sXLy5tI8ub54XVQBbrr7++23TTTX10Uwz3M78Dv8f222/vRYJtojISijrz4osvthhUTSiYWWIjZ7l7zjnn+FDTM88809/41o8yBDBx4kS3xRZb+GXy8OHD/YyeWRmDO/0YAKqZ1T/33HN+EOIYwhMfeeQRb3p4/fXX/UNHUhMP49ChQ93vv/9ediyzt/h7pBomjo7AUUcd5WP081Z5bYXVGuffaqutvLkDfwDXhySyeFb/5ZdflvwGNEpb1AMzs2QlnLUHrREKHOBMioxbbrnF3/epCQmTokrOaVYoXHdRPRKKOoP5ALMGAz0heDYA7Lzzzn6Gt8cee3in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>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYoAAABSCAYAAABKZJPmAAAThUlEQVR4Xu2dhZMcxfuHv/8A7hLcAiRosASCBIciOBSFa4AQJLi7uwYIFiy4u1twCwmuwUKQ4ASbXz1N9VZvX3fvzNzu3v1uPk9VVy7TPXJ7O+/b/Vr/LxNCCCES/M8/IIQQQrhIUQghhEgiRSGEECKJFIUQQogkUhRCCCGSSFEIIYRIIkUhhBAiiRSFEEKIJFIUQgghkkhRCCGESCJFIYQQIokUhRDdgJNOOil76qmn/MOdplXXFdVCikKIbgDCfL311vMPd5pWXVdUCykKIVoMgjpPm2qqqfxTk/jnxxrX5V8hyiJFIUSLYVbfqJUR5v41Qs1el5+FKIsUhRBdDH6EokoiD626rqgeUhRdwJ9//ukfajpTpkzJ/v77b/+w6Ia0arbfquuK6iFF0WaefvrprFevXtlFF13kdzWVrbbaKuvXr1/22Wef+V1CCFEIKYo2Mnbs2GyWWWbJ1llnndKzfVYjKBuuleKrr77K5ptvvqxv377Zt99+63eLNvD7779nhx56aDb//PNnG220Ufbggw/6Q7J///03O//887PzzjvP70ry119/ZaeccoqZDHDthx56qK7/mWeeyZZccsns6KOPrjsuRBmkKNrEd999ly2++OLZvPPOm3355Zd+d0MmTZpkhA7n46CkLbbYYtljjz3mD63x6KOPZlNPPXU2aNAgI7REeznuuOPMym78+PG1v/0ff/xRN+aRRx4xf8tlllmm7ngj9thjj2zjjTfO3nvvvWyuueYykwL32ptttpm57nTTTZf9+uuvzplCFEeKog0w+8OpiNB++OGH/e6GvPPOO0bQ8OLvueee2bPPPpuNGjUqm3766bMZZpghaYs+/vjjzXnbbbedmb2K9oDJr3///kZBs3qcffbZzd/hjTfeqBs3fPhwc3zvvfeuO56CyUGfPn3MdWmzzTabucZrr71WG3PrrbfWJhRffPGFc7YQxZGiaAMHHnigeWH3228/v6shzz33XDbnnHOa888444y6PntdTFkx/vnnn2yVVVYx484880y/W7SInXbaKRsxYoT5+YknnjCf/xxzzNHB5LjccsuZvuuvv77uODD2jjvuMKsGl8033zw799xzzc8oDc6fddZZs99++61u3NZbb53NPPPMHe4pRFGkKFqM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>

[image3]: <data:image/png;base64,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>
