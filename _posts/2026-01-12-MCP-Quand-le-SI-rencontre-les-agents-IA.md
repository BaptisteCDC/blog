---
layout: post
title: "MCP - Quand le SI rencontre les agents IA"
date: 2026-01-12 10:00:00 +0100
categories: IA
author: Baptiste Macé
---

## **Du système d'information classique à l'architecture agentique gouvernée**

### **Introduction : Comprendre l'Agent et son Écosystème**

L'intégration de l'intelligence artificielle dans les systèmes d'information traditionnels représente un défi majeur, principalement en raison de la nature fondamentalement différente de ces deux mondes. Pour appréhender cette complexité, il est essentiel de commencer par définir les acteurs clés et les concepts qui les entourent.

Un **agent IA** est un programme logiciel conçu pour interagir avec son environnement. Sa capacité à "percevoir" signifie qu'il est configuré pour **recevoir des entrées de données structurées ou non structurées** (par exemple, du texte, des signaux numériques, des données de capteurs, des retours d'API) et à les traiter. Son fonctionnement repose sur des **algorithmes et des modèles computationnels** qui lui permettent de traiter ces entrées, de simuler des processus décisionnels et d'exécuter des actions. Il est programmé pour atteindre des objectifs spécifiques.

Contrairement aux applications logicielles purement déterministes qui suivent un ensemble fixe d'instructions, un agent IA peut présenter un comportement non-déterministe. Cela signifie que, face à des entrées ou des contextes similaires, il peut générer des réponses ou suivre des chemins d'exécution différents. Cette variabilité est inhérente à la complexité de ses modèles internes et de son environnement d'interaction, et n'implique pas une conscience ou une intention humaine.

Pour fonctionner, un agent IA dispose de plusieurs **outils** ou capacités :

*  **LLM (Large Language Model) embarqué** :  
Au cœur de nombreux agents IA modernes se trouve un modèle de langage étendu, entraîné sur de vastes ensembles de données textuelles pour prédire la suite la plus probable d’une séquence de mots. Le langage y est représenté sous forme de **vecteurs numériques (embeddings)** projetés dans un espace de grande dimension. La **distance entre ces vecteurs** permet de mesurer la proximité sémantique entre mots, phrases ou documents, même lorsqu’ils n’emploient pas les mêmes termes. Le LLM exploite ces relations de distance pour identifier des patterns, réaliser des inférences statistiques et générer des réponses cohérentes. Il ne comprend pas le sens au sens humain, mais manipule des similarités vectorielles apprises lors de l’entraînement. L’agent interagit avec ce LLM via des appels programmatiques afin d’interpréter les requêtes, détecter des intentions et formuler des réponses adaptées.

* **MCP (Model Context Protocol)** : Ce protocole est un mécanisme de communication essentiel pour qu'un agent puisse interagir de manière structurée et gouvernée avec un système d'information. Le MCP permet à l'agent d'exécuter des fonctions spécifiques (appelées "tools") ou de lire des ressources (données) du SI. Il agit comme une interface standardisée, traduisant les requêtes de l'agent en appels déterministes pour le système sous-jacent.  

* **A2A (Agent-to-Agent)** : Ce terme décrit la capacité d'un agent à communiquer et à échanger des informations ou des requêtes avec d'autres programmes agents IA. Il s'agit d'une interaction entre entités logicielles autonomes, souvent pour la délégation de tâches ou la combinaison d'expertises. Il est crucial de noter que les outils MCP sont conçus pour interagir avec des systèmes d'information déterministes et non pas pour orchestrer une cascade d'agents A2A, afin d'éviter une complexité et une imprévisibilité opérationnelles.

* **RAG (Retrieval-Augmented Generation)** :Ce terme décrit une architecture dans laquelle un agent IA **interagit avec une base de connaissances externe** afin d’enrichir son raisonnement avant génération. Il s’agit d’une **interaction contrôlée entre un agent génératif et un système de récupération d’information**, généralement basé sur des embeddings et une recherche vectorielle.

* **multi-turn (ou conversationnel à plusieurs tours)** : C’est un mode d’interaction où l’agent maintient un état conversationnel et une mémoire des échanges précédents. Cela lui permet d’intégrer le contexte historique dans ses décisions et ses réponses, de poser des questions de clarification et d’adapter son comportement au fil d’une séquence d’interactions prolongée. Cette capacité est toutefois **contrainte par la taille du contexte d’entrée (nombre de tokens)** : plus la fenêtre de contexte est large, plus l’agent peut conserver finement l’historique de la conversation. À l’inverse, lorsque cette limite est atteinte, l’agent doit **rationnaliser le contexte** (résumés, oubli de détails, sélection d’éléments jugés pertinents) pour poursuivre l’échange.


### **1\. Avant MCP : un SI prévisible et rigide**

Dans un système d'information (SI) classique, le fonctionnement est intrinsèquement déterministe. Chaque composant, de l'application à l'API et à la base de données, exécute des opérations et des flux de données prédéfinis et reproductibles. Les règles métier sont implémentées de manière statique dans le code, et les scénarios d'erreur sont généralement anticipés et gérés de manière explicite. Ce modèle déterministe est efficace et fiable jusqu'à l'intégration d'un agent IA.

### **2\. Le choc : connecter un agent à un SI**

La tentative initiale d'intégrer un agent IA dans un SI classique se heurte souvent à des difficultés inattendues. Un agent, par sa nature non-déterministe et son fonctionnement basé sur l'inférence plutôt que sur des instructions séquentielles strictes, introduit une variabilité que les systèmes traditionnels ne sont pas conçus pour gérer. L'agent peut initier des séquences d'appels imprévues, rendre la traçabilité des erreurs complexe (il est difficile de déterminer l'origine d'un dysfonctionnement entre le prompt, le modèle de l'agent et l'API du SI), et générer des coûts opérationnels non maîtrisés. Le problème fondamental réside dans l'absence d'un protocole standardisé pour établir un contrat d'interface clair entre le comportement exploratoire et probabiliste d'un LLM au sein d'un agent IA et la logique rigide et prévisible d'un SI. Les deux entités opèrent selon des paradigmes incompatibles sans un mécanisme d'intermédiation.

### **3\. MCP : une façade contractuelle entre l'IA et le SI**

C'est ici que le Model Context Protocol (MCP) intervient, en proposant une solution. Plutôt que de permettre aux agents IA d'interagir directement avec les composants d'un SI, le MCP instaure un serveur intermédiaire. Ce serveur expose un ensemble contrôlé et standardisé de capacités du SI sous forme de "tools" et de "ressources". Concrètement, l'interaction se structure ainsi : 

Agent IA → Serveur MCP → SI existant (ERP, CRM, bases de données, APIs) 

Le MCP remplit une triple fonction : il agit comme une façade technique, une couche de gouvernance pour contrôler l'accès et l'utilisation des fonctionnalités du SI, et un langage commun permettant aux modèles d'IA et aux systèmes existants de dialoguer de manière intelligible et contrôlée.

**Il est crucial de comprendre que MCP ne formalise pas un "contrat" directement avec le LLM de l'agent.** Le LLM, en tant qu'interprète statistique, n'est pas une entité contractante ; il agit selon les schémas appris lors de son entraînement. **Le contrat est établi entre le développeur qui configure l'agent (et donc son usage du MCP) et le SI.** MCP fournit une **couche de transport et de gouvernance standardisée** qui permet de canaliser les requêtes potentielles de l'agent vers des points d'accès définis et contrôlés du SI. La nature intrinsèquement "floue" ou imprévisible du LLM subsiste, mais MCP permet d'encadrer et de sécuriser la manière dont ses requêtes se traduisent en actions sur le SI. Même avec MCP, le LLM peut toujours générer des tentatives d'appels de tools avec des arguments non valides ou "halluciner" des ressources inexistantes ; c'est au MCP (et à la configuration des tools) de gérer ces scénarios de manière robuste.

### **4\. Ce que MCP expose réellement**

MCP structure les interactions autour de trois types d'éléments :

**Les ressources** (en lecture) : ce sont les données consultables comme des documents, des objets métier ou des états système.

**Les tools** (pour agir) : ce sont des fonctions exécutables. Par exemple, créer une facture, déclencher un workflow ou effectuer un calcul complexe.

**Le contexte** : ça inclut les règles métier, les prompts système et les contraintes d'usage.

  #### **4.1 Concrètement, comment ça marche ?**

MCP, c'est avant tout **un protocole de communication standardisé**. Il repose sur **JSON-RPC 2.0**, un format d'appel de procédure à distance simple et léger.

Contrairement à REST qui est orienté ressources (GET /users/123, POST /orders), JSON-RPC se concentre sur l'appel de méthodes : vous envoyez une requête JSON avec le nom de la méthode et ses paramètres, vous recevez une réponse JSON avec le résultat ou une erreur. C'est tout. Pas de verbes HTTP à gérer, pas de conventions d'URL — juste des appels de fonctions structurés.

Exemple d'appel JSON-RPC :

```json

{
  "jsonrpc": "2.0",
  "method": "tools/call",
  "params": {
    "name": "create_invoice",
    "arguments": {"client_id": "12345"}
  },
  "id": 1
}

```

Simple, direct, prévisible.

Le serveur MCP expose plusieurs **routes standardisées** :

* tools/list : pour découvrir les outils disponibles  
* tools/call : pour exécuter un outil spécifique  
* resources/list : pour lister les ressources accessibles  
* resources/read : pour lire le contenu d'une ressource  
* prompts/list et prompts/get : pour récupérer des contextes prédéfinis

  #### **4.2 Les modes de communication**

Les échanges peuvent se faire de deux manières principales :

**Via stdio** (entrée/sortie standard) : le serveur MCP tourne **en local, embarqué avec l'agent**. C'est comme un processus qui communique directement via son stdin/stdout. Pas de réseau, pas de latence réseau, tout se passe dans la même machine. C'est rapide, simple, mais ça limite à des scénarios locaux ou monolithiques.

**Via SSE** (Server-Sent Events) : là, le serveur MCP est **distant**. Il peut être hébergé ailleurs, mutualisé entre plusieurs agents, et il communique via HTTP avec du streaming unidirectionnel (le serveur peut envoyer des événements au client en continu). C'est plus flexible pour des architectures distribuées, mais ça introduit de la latence réseau et des questions de sécurité.

Le choix dépend de votre architecture :

* **stdio** pour un assistant local desktop  
* **SSE** pour un chatbot distribué en production

Ce qui est malin, c'est que MCP ne réinvente pas la roue. Il s'appuie sur des standards existants (JSON-RPC, HTTP, WebSocket) et définit juste une **convention** sur ce qu'on expose et comment on le structure.

Un point important à comprendre : **MCP ne fait rien d'intelligent en soi**. Il ne raisonne pas, il n'optimise rien. Il fournit juste un cadre standardisé qui rend l'intelligence du modèle possible et contrôlable. C'est une couche de contrat, pas une couche de magie.

### **5\. Mais pourquoi un agent "cherche" des tools ?**

C'est une question que beaucoup de gens se posent, et c'est normal.

  **Les agents ont simplement été entraînés à le faire**

Les grands modèles de langage modernes ne font pas que générer du texte. Ils ont aussi appris à agir. Pendant leur entraînement, ils ont vu des milliers d'exemples où il fallait réfléchir à un objectif, appeler une fonction, observer le résultat, puis décider de la suite.

Ils ont intégré le fait que certaines informations ne sont pas disponibles dans leur contexte immédiat, et que certaines actions nécessitent un appel externe. Du coup, MCP s'intègre naturellement dans leur façon de fonctionner.

### **6\. Fine-tuning, RLHF et usage des tools (en profondeur)**

  #### **6.1 Fine-tuning supervisé**

Pendant cette phase d'entraînement, le modèle est exposé à des exemples annotés montrant les bonnes et les mauvaises décisions, ainsi que des appels de fonctions bien formés. Il apprend progressivement quand appeler un tool, lequel choisir, et avec quels paramètres.

  #### **6.2 RLHF (Reinforcement Learning from Human Feedback)**

Ensuite vient le RLHF, où les comportements efficaces sont récompensés et les mauvais sont pénalisés. Par exemple, si l'agent appelle trois tools alors qu'un seul suffit, ou s'il ignore une capacité pourtant disponible, il est sanctionné.

Résultat : l'agent développe une sorte d'intuition sur le rapport coût/bénéfice de ses actions.

  #### **6.3 Pourquoi il explore quand même ?**

Parce que le contexte change constamment, les tools sont découverts de manière dynamique, et MCP ne garantit pas qu'il n'y ait qu'une seule façon sémantique de faire quelque chose.

Donc l'agent fait exactement ce qu'on lui a appris : il explore pour réduire l'incertitude.

### **7\. Le rôle fondamental des embeddings**

  #### **7.1 Ce que font les embeddings**

Les descriptions des tools, ressources et contextes sont transformées en vecteurs puis comparées à l'objectif actuel de l'agent. Il choisit le tool qui est sémantiquement le plus proche, pas forcément celui qui a le bon nom.

  #### **7.2 Exemple critique**

Imaginons deux tools : get\_client\_from\_crm et get\_client\_from\_erp.

**Description minimaliste (problématique) :**

```json

{
  "name": "get_client_from_crm",
  "description": "Récupère les informations d'un client"
}
{
  "name": "get_client_from_erp",
  "description": "Récupère les informations d'un client"
}

```

Si l'objectif de l'utilisateur est "créer une facture", les embeddings de ces deux descriptions sont quasi identiques. L'agent ne sait pas lequel choisir. Résultat : il appelle les deux pour être sûr, ou pire, il choisit au hasard.

**Description enrichie (bonne pratique) :**

```json
{
  "name": "get_client_from_crm",
  "description": "Récupère les données commerciales d'un client : historique des interactions, contacts, opportunités, cycle de vente. Utilisé pour les actions marketing et le suivi commercial."
}
{
  "name": "get_client_from_erp",
  "description": "Récupère les données financières et comptables d'un client : adresse de facturation, conditions de paiement, historique des factures, solde comptable. Utilisé pour la facturation et la gestion financière."
}
```

Maintenant, si l'objectif est "créer une facture", les embeddings vont naturellement rapprocher les concepts de "facture", "paiement", "comptable" et "ERP". L'agent choisira directement get\_client\_from\_erp, sans hésitation.

#### **Autre exemple : ambiguïté sur les produits**

**Descriptions floues :**

```json
{
  "name": "search_products",
  "description": "Cherche des produits"
}
{
  "name": "get_product_catalog",
  "description": "Récupère le catalogue produits"
}

```

Objectif utilisateur : "Montre-moi les nouveaux smartphones"

Que fait l'agent ? Il ne sait pas. Les deux semblent pertinents. Il va probablement appeler les deux.

**Descriptions enrichies :**

```json

{
  "name": "search_products",
  "description": "Recherche des produits disponibles en stock avec filtres (prix, catégorie, disponibilité). Retourne les produits vendables immédiatement avec leur prix actuel et stock temps réel."
}
{
  "name": "get_product_catalog",
  "description": "Récupère l'ensemble du catalogue produit avec descriptions détaillées, fiches techniques et spécifications. Utilisé pour consulter les caractéristiques complètes, pas pour vérifier la disponibilité."
}

```

Maintenant, pour "Montre-moi les nouveaux smartphones", l'agent comprend que search\_products est le bon choix car l'utilisateur veut probablement voir ce qui est disponible à la vente.

#### **Exemple supplémentaire : actions vs consultation**

**Sans contexte :**

```json

{
  "name": "update_order",
  "description": "Met à jour une commande"
}
{
  "name": "get_order",
  "description": "Récupère une commande"
}

```

Demande utilisateur : "Quelle est le statut de ma commande \#12345 ?"

Risque : l'agent pourrait confondre "statut" avec "mise à jour" si les embeddings sont mal alignés.

**Avec contexte :**

```json

{
  "name": "update_order",
  "description": "Modifie les informations d'une commande existante : adresse de livraison, articles, quantités. Action qui impacte les données. Nécessite une confirmation."
}
{
  "name": "get_order",
  "description": "Consulte les informations d'une commande : statut, articles commandés, adresse de livraison, date de livraison prévue. Lecture seule, aucune modification."
}

```

Ici, "statut" et "consulte" sont sémantiquement proches. L'agent choisit get\_order sans ambiguïté.

#### **La règle d'or**

**Plus vous donnez de contexte métier dans la description, plus vous guidez les embeddings vers le bon outil.**

Ne décrivez pas juste ce que fait le tool. Décrivez :

* **Quand** l'utiliser  
* **Quel type de données** il manipule  
* **Dans quel contexte métier** il s'inscrit  
* **Lecture ou écriture ?**  
* **Action réversible ou non ?**

Les embeddings ne lisent pas votre code. Ils lisent vos descriptions. Et c'est là que tout se joue.

  #### **7.3 Danger réel**

Si les descriptions des tools sont vagues ou se chevauchent, les embeddings vont se ressembler. L'agent va hésiter et finir par appeler plusieurs tools pour être sûr.

### **8\. MCP face à un SI classique**

**MCP ne remplace pas le SI. Il ajoute une couche d'abstraction par-dessus.**

Votre SI existe toujours avec ses APIs, ses bases de données, son ERP, son CRM. MCP vient se poser au-dessus pour exposer ces capacités d'une manière que l'agent peut comprendre et manipuler.

#### **Ce que ça change concrètement**

**Avant MCP :**

* L'agent appelle directement vos APIs REST/GraphQL  
* Il doit connaître la structure exacte de vos endpoints  
* Chaque modification d'API casse potentiellement l'agent  
* Pas de couche de contrôle entre l'agent et vos systèmes critiques

**Avec MCP :**

* L'agent appelle des tools standardisés (create\_invoice, get\_client)  
* Le serveur MCP traduit ces intentions en appels API concrets  
* Vous pouvez changer votre API interne sans toucher à l'agent  
* Vous contrôlez ce qui est exposé, comment et à qui

#### **Ce que MCP apporte vraiment**

**Abstraction** : l'agent ne sait pas (et n'a pas besoin de savoir) si get\_client interroge un CRM, un ERP ou une base PostgreSQL.

**Gouvernance** : vous décidez quels outils exposer, avec quelles limites (quotas, permissions, validation).

**Découvrabilité** : l'agent peut demander "qu'est-ce que je peux faire ?" via tools/list au lieu de parcourir une documentation OpenAPI.

**Intention métier vs API technique** : au lieu d'exposer POST /api/v2/invoices avec 15 champs obligatoires, vous exposez create\_invoice\_from\_quote qui encapsule la logique métier.

#### **Le coût de cette abstraction**

MCP ajoute :

* Une couche supplémentaire (latence)  
* De la sérialisation JSON-RPC  
* Du raisonnement LLM pour choisir le bon tool  
* De la complexité opérationnelle

**MCP n'optimise pas le SI en tant que tel.** Il l'ouvre à une nouvelle catégorie d'interactions, imprévisibles, exploratoires, conversationnelles, qui n'étaient tout simplement pas possibles avant.

C'est un peu comme ajouter une API GraphQL par-dessus votre REST : ça ne rend pas votre base de données plus rapide, mais ça change radicalement la façon dont on peut l'interroger.

### **9\. Limites de MCP – Performance et latence**

  #### **9.1 Chaque appel a un coût**

Il y a le raisonnement du modèle, la sérialisation des données, le réseau, l'orchestration... Un agent qui fait 10 appels MCP va mécaniquement avoir 10 fois plus de latence qu'un appel API direct.

  #### **9.2 MCP n'est pas temps réel**

Ce n'est clairement pas adapté aux chemins critiques ni aux systèmes qui nécessitent une très haute fréquence de traitement. MCP, c'est fait pour la décision, pas pour la micro-optimisation.

### **10\. Redondance : le piège architectural**

  #### **10.1 Redondance des tools**

Quand on a plusieurs tools qui font essentiellement la même chose avec des descriptions proches, on se retrouve avec des appels multiples, des coûts inutiles et des décisions parfois incohérentes.

**Mais il y a un piège encore plus grave :** MCP est conçu pour qu'un serveur MCP appelle **votre SI classique** — vos APIs, vos bases de données, votre ERP. Ce n'est **pas** fait pour qu'un serveur MCP appelle un autre agent IA ou déclenche une nouvelle boucle de raisonnement.

Si vous commencez à avoir des tools MCP qui eux-mêmes déclenchent des agents, vous créez une cascade de raisonnements non-déterministes, avec :

* Des coûts qui explosent exponentiellement  
* Une latence imprévisible (agent qui appelle un agent qui appelle un agent...)  
* Une impossibilité totale de tracer ce qui s'est réellement passé  
* Des boucles infinies potentielles

**MCP doit être la couche de terminaison** : l'agent appelle MCP, MCP appelle du déterministe (API, base de données, fonction), et retourne un résultat. C'est tout.

  #### **10.2 Règle d'or MCP**

**Un tool \= une intention métier claire.**

Et cette intention doit se traduire par un appel déterministe à votre SI. Pas par un autre agent. Pas par un autre LLM. Pas par une nouvelle phase de raisonnement.

MCP, c'est la frontière entre l'intelligence (l'agent) et l'exécution (le SI). Ne brouillez pas cette ligne.

### **11\. Coût environnemental 🌱**

Chaque boucle de raisonnement consomme des tokens, du calcul GPU et de l'énergie. Un agent qui explore beaucoup peut facilement consommer 10 à 100 fois plus qu'un flux API classique.

**MCP a un coût. Point.**

Et ce coût — qu'il soit financier, environnemental ou en latence — doit avoir un **ROI clair**. Si vous ne pouvez pas justifier en quoi l'usage de MCP apporte une valeur métier supérieure au coût engendré, alors la réponse est simple : **n'utilisez pas MCP**.

#### **Quand le coût est justifié**

* Vous orchestrez plusieurs systèmes complexes  
* La décision nécessite du contexte métier dynamique  
* L'interaction conversationnelle a une vraie valeur (support client, conseil)  
* Vous automatisez des tâches cognitives à forte valeur ajoutée

#### **Quand le coût n'est pas justifié**

* Vous faites du CRUD simple déguisé  
* Une requête SQL ou une API REST suffit  
* Le parcours utilisateur est déterministe  
* Vous ajoutez de l'IA "parce que c'est tendance"

**La question à se poser systématiquement :** est-ce que le bénéfice de cette interaction agentique vaut 10 à 100 fois le coût d'un appel API classique ?

Si la réponse n'est pas un "oui" franc, vous êtes probablement en train de sur-architecturer.

MCP peut amplifier considérablement l'impact environnemental et financier si l'architecture n'est pas bien pensée. Ne l'utilisez pas par défaut. Utilisez-le **quand ça a du sens**.

### **12\. Anti-patterns MCP**

#### **Quand MCP est une mauvaise réponse (ou une réponse surdimensionnée)**

MCP est puissant, mais ce n'est vraiment pas un outil universel. L'une des erreurs les plus fréquentes concerne les chatbots de recherche produit basés sur du RAG.

  #### **12.1 Anti-pattern n°1 : MCP pour une simple recherche produit**

Prenons un chatbot e-commerce qui doit chercher des produits, filtrer par prix, catégorie et stock, puis afficher les résultats.

L'architecture naïve consisterait à faire passer tout ça par MCP avec un tool `search_products` qui interroge la base produits.

Le problème ? La recherche produit est déterministe, très structurée, très fréquente et sensible à la latence. Or MCP introduit du raisonnement inutile, des appels répétés, une latence variable et un coût par requête.

On utilise un agent là où un simple moteur de recherche suffirait largement.

  #### **12.2 Anti-pattern n°2 : RAG \+ MCP en cascade**

C'est une architecture qu'on voit très souvent : l'utilisateur envoie une question, le modèle utilise le RAG pour comprendre, puis appelle MCP pour confirmer, compare les résultats et reformule.

Résultat : on récupère deux fois la même information, on a de la redondance sémantique, les coûts sont multipliés, et au final le bénéfice est quasi nul.

Symptôme typique qu'on entend : "Notre chatbot fonctionne bien, mais il coûte très cher."

  #### **12.3 Pourquoi le RAG suffit dans ce cas**

Le RAG est conçu exactement pour ça : recherche sémantique, filtrage rapide, haute fréquence et faible latence. Le moteur vectoriel est optimisé, déterministe, et ne raisonne pas inutilement.

MCP n'apporte strictement aucune valeur ajoutée dans ce contexte.

  #### **12.4 Anti-pattern n°3 : un tool MCP "search\_products" trop générique**

Si vous avez juste un tool avec une description floue comme "Recherche des produits", vous allez créer des embeddings flous, des appels multiples et de l'exploration inutile.

Mieux vaut découper par intention claire : `search_products_by_category`, `search_products_in_stock`, `get_product_details`, `create_quote`.

  #### **12.5 Règle de décision simple**

**Si la réponse peut être obtenue sans raisonnement, sans orchestration et sans décision, MCP est probablement un anti-pattern.**

  #### **12.6 Résumé des anti-patterns MCP courants**

* MCP pour du CRUD simple  
* MCP pour de la recherche full-text ou vectorielle  
* MCP pour des parcours ultra fréquents  
* MCP sans gouvernance des tools  
* MCP \+ RAG redondant

#### 

## **Conclusion – MCP n'est pas une baguette magique**

MCP ne rend pas l'IA :

* plus rapide  
* moins chère  
* plus intelligente par défaut

Il la rend :

* **intégrable** (via un protocole standardisé)  
* **gouvernable** (avec des tools maîtrisés)  
* **industrialisable** (dans un SI existant)

#### **MCP est une brique d'architecture**

Comme toute brique, mal posée, elle fragilise l'ensemble. Bien posée, elle ouvre des possibilités qui n'existaient pas.

#### **Les questions à se poser avant d'adopter MCP**

1. **Ai-je vraiment besoin d'un agent ?** Ou est-ce qu'une API classique suffit ?  
2. **Le coût est-il justifié ?** Le ROI est-il clair et mesurable ?  
3. **Mes tools sont-ils bien conçus ?** Descriptions précises, intentions claires, pas de redondance ?  
4. **Ai-je une gouvernance en place ?** Quotas, audit, sécurité ?  
5. **Mon architecture est-elle prête ?** MCP termine sur du déterministe, pas sur d'autres agents ?

#### **Quand MCP brille vraiment**

MCP devient pertinent quand vous devez :

* Orchestrer des décisions complexes entre plusieurs systèmes  
* Donner à un utilisateur une interface conversationnelle qui a du sens  
* Automatiser du raisonnement métier à forte valeur ajoutée  
* Permettre à l'IA d'explorer des possibilités que vous n'aviez pas anticipées

#### **L'avenir de MCP**

MCP est encore jeune. Les patterns émergent, les erreurs se répètent, les architectures se stabilisent. Ce qui est certain, c'est que **l'IA conversationnelle ne disparaîtra pas**, et qu'elle devra dialoguer avec nos SI existants.

MCP n'est probablement pas la solution finale, mais c'est **la première tentative sérieuse de standardisation** de cette interface entre l'intelligence artificielle et les systèmes d'information.

#### **Le mot de la fin**

MCP ne remplace ni un moteur de recherche, ni une base de données, ni un backend d'API.

Utilisez-le avec discernement. Gouvernez-le avec rigueur. Et surtout, ne l'utilisez que quand il apporte vraiment quelque chose que vous ne pourriez pas faire autrement.

Parce qu'au final, la vraie question n'est pas "Puis-je utiliser MCP ?" mais "Dois-je vraiment utiliser MCP ?"
