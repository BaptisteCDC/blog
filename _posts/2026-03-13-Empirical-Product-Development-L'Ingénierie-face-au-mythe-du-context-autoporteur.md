---
layout: post
title: "Empirical Product Development : L'Ingénierie face au mythe du context autoporteur"
date: 2026-03-13
author: Baptiste Macé
categories: [politique, société, histoire]
tags: [IA,Empirical,Product,Development,Architecture,logiciel]
---

On lit partout des récits sur l'automatisation totale : des multi-agents orchestrés, des MCP boostés au RAG, ou des IDE qui "comprennent" votre codebase comme par magie. C'est l'ère du **Spec-Driven Development (SDD)**. On sur-spécifie, on injecte des kilos de contexte, et on prie pour que le LLM converge vers une solution miracle.

Mais dans la réalité industrielle, cette approche est un cul-de-sac, car elle viole beaucoup de principes de l'ingénierie logicielle moderne. Le SDD repose sur une croyance : "Si je décris parfaitement l'état final, l'IA va le construire". C'est le retour déguisé du Cycle en V.

Le problème ? On ne connaît jamais parfaitement le système d'entrée. **Le mythe de "l'architecte omniscient", capable d'anticiper la totalité des invariants dès la conception initiale, est une illusion dangereuse.** Les invariants se découvrent en chemin. En cherchant à tout spécifier d'un coup, on masque l'erreur et on retarde la validation. On finit avec une démo "wow", mais un code qui échoue en production.

Un autre problème du SDD est qu’il encourage la dérive de générer sans maîtriser la conception de ce qui est généré ; cela peut devenir un obstacle à la reprise et l’évolution future du produit, et à la transmission aux remplaçants qui s’en occupent. 

Voici pourquoi j'ai choisi une approche différente : **Empirical Product Development (EPD)** assistée par IA. 

L'EPD ne traite pas le LLM comme un cerveau omniscient, mais comme un **accélérateur cognitif non fiable**. On ne lui donne pas les clés du camion ; on lui donne une tâche atomique et on dresse un mur de feedback autour de lui.

### Les 5 Piliers de l'EPD

1. **Tâches Atomiques** : Ne demandez pas "Construis-moi une API de paiement". Demandez "Crée le mapping de cette entité spécifique". Diviser pour mieux régner, mais surtout pour mieux valider.  
2. **Le Mur de Feedback** : C'est le cœur du système. Chaque proposition du LLM doit se fracasser contre la réalité technique :  
   * **Tests Automatisés** (Unitaires, Comportement,E2E) : Le code compile-t-il ? Les tests passent-ils ? les comportements sont ils les mêmes?  
   * **Performance et Robustesse:** Mons  
   * **Cohérence SI** : L'interaction avec la DB ou l'API tiers est-elle cohérente avec la réalité du terrain   
   * **Validation Métier (Le Dev devient PO)** : Une revue humaine critique pour s'assurer que l'intention initiale est respectée.  
   * Tout cela rejoint l’idée de [*Harness Engineering*](https://openai.com/index/harness-engineering/).  
3. **Recette Pas à Pas** : L'avancement se fait par itérations courtes et vérifiables. On privilégie le "Fail Fast" pour identifier les impasses immédiatement plutôt qu'en fin de cycle. Cette approche s'appuie sur des commits réguliers qui servent de points de retour sécurisés, validant chaque brique technique avant de passer à la suivante.  
4. **Vision Cible (Goal-Oriented)** : Avancer pas à pas ne signifie pas naviguer à vue. On garde toujours le résultat final en tête pour s'assurer que chaque micro-étape nous rapproche de l'objectif sans s'enliser dans la dette technique.  
5. **Éradication de l'Implicite** : Découper un objectif en étapes permet de lever les zones d'ombre. La réalisation concrète de la tâche *n* est le meilleur moyen de révéler les contraintes réelles de la tâche *n+1*, transformant l'incertitude théorique en feedback empirique.

### Le concept de "Bounded Cognition"

L'EPD s’inscrit dans le concept de **Rationalité Limitée** en psychologie qui remet en question l'hypothèse de la rationalité parfaite des individus dans la prise de décision.

Concrètement, cela signifie que, lorsqu'ils prennent des décisions, les êtres humains :

1. **Ne disposent pas d'une information complète et parfaite** : Ils doivent souvent décider avec des informations incomplètes, ambigües ou coûteuses à obtenir.  
2. **Ont des capacités cognitives limitées** : Notre cerveau ne peut pas traiter instantanément une quantité infinie d'informations ou calculer toutes les conséquences possibles d'une décision. Notre mémoire, notre attention et notre capacité de calcul sont limitées.  
3. **Utilisent des raccourcis mentaux (*heuristiques*)** : Pour simplifier le processus de décision face à la complexité, nous utilisons des règles empiriques, des habitudes ou des biais cognitifs, plutôt que d'effectuer une analyse rationnelle exhaustive.  
4. **Visent la *satisfaction* plutôt que l'optimisation maximale (*maximisation*)** : Au lieu de chercher la "meilleure" option possible (ce qui serait trop coûteux en temps et en énergie), nous cherchons une option "assez bonne" qui répond à un niveau d'aspiration minimal. C'est la notion de **satisficing** (portmanteau de *satisfy* et *suffice*).

La rationalité limitée décrit un **comportement réel** où les décisions sont prises de manière **suffisamment bonne** ou **satisfaisante** en tenant compte des **contraintes** d'information, de temps et de capacité cognitive. C'est une description plus réaliste du comportement humain que l'hypothèse classique de l'agent parfaitement rationnel. Cela rejoint aussi le domaine Complexe (et non pas Compliqué) dans le modèle [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework) de Dave Snowden. Dans cette perspective avant tout réaliste, l'IA n'est fiable que lorsqu'elle est contrainte par un environnement de feedback rigide. 

Cette approche rejoint aussi la limite des systèmes d'Intelligence Artificielle (IA) et des démarches de *Software Driven Development* (SDD) qui, en partant du principe qu'il est possible de tout spécifier parfaitement, courent le risque de tomber dans l'écueil de croire que l'IA sera intrinsèquement supérieure à l'humain. Cette confiance excessive peut mener à anticiper que l'IA sera capable de combler toute information manquante sans avoir recours à l'heuristique, et qu'elle ne cherchera pas juste à nous satisfaire sans remettre en question le bon sens.

En somme, le raisonnement n'est pas *dans* le LLM, il est dans l'**orchestration par un individu**.

1. **L'Intention** : Le développeur ou la développeuse identifie une problématique et définit sa stratégie de résolution.  
2. **La Délégation** : Le LLM prend en charge l'implémentation technique sur une base délimitée.  
3. **L'Intégration** : Vérification immédiate que l'élément fonctionne et s'insère sans friction dans l'application.  
4. **La Fortification** : Génération systématique des tests de non-régression et d'intégration par le LLM, et exécution des tests pour verrouiller l'étape.  
5. **La Validation**: L'élément développé est validé par le développeur ou la développeuse avant de passer à la brique suivante.

C'est une boucle de développement déterministe supervisée, qui a l’avantage d’intégrer l’information et l’apprentissage acquis à chaque pas.

**Conclusion** : si l'arrivée de l'IA change beaucoup de choses, elle ne change pas le fait que toute création de produit intègre une large part d'inconnu impossible à anticiper. L'IA ne fait qu'accélérer la vitesse à laquelle nous produisons. Ne nous laissons pas aller à céder à la tentation confortable de tout prétendre anticiper, et adoptons une démarche qui embrasse la découverte progressive comme moteur.

L'Empirical Product Development (EPD) est l'anti-dote à la pensée magique du "contexte autoporteur" : c'est un cadre pragmatique qui réaffirme le rôle central du jugement humain et du cycle de feedback rapide, garantissant que l'accélération fournie par l'IA se fasse au service de la maîtrise et de la robustesse, et non au détriment de l'ingénierie.

L'objectif de toute création de système est sa maîtrise : ce qui est produit doit être compris et respecter les piliers de l'architecture logicielle pour assurer sa capacité à évoluer. Sans cette rigueur, les coûts opérationnels deviennent imprévisibles. Maîtriser le cycle de vie du logiciel n'est plus une option : tests de performance, tests d'intégration, consommation CPU, gestion de la mémoire, réseaux et protocoles... Tout doit être sous contrôle.

L'IA est un formidable tuteur pour monter en compétence sur ces sujets complexes, mais elle ne "sait" pas mieux. Elle génère du plausible, pas du vrai. L'approche EPD exige donc de recouper ses sources et de vérifier systématiquement la cohérence du rendu.

Cela impose un nouveau paradigme : être moins spécialisé sur une stack unique, mais  
mieux appréhender l'ensemble de la chaîne (**Produit, Front, Back, DevOps, SRE**). L'IA permet d'adresser seul des projets complexes avec une vélocité inédite, à condition de conserver une compréhension fine de chaque artefact produit. Cela demande moins de "savoir-faire” purement syntaxique, et surtout davantage de connaissances transverses et de capacités de résolution de problèmes.
