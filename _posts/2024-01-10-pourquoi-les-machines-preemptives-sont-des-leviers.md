---
layout: post
title: "Pourquoi les machines préemptives sont un des leviers majeurs des futures stratégies Green IT de demain"
date: 2024-01-10 10:00:00 +0100
categories: GreenIT
author: Baptiste Macé
---

## Contexte

Dans un contexte de réchauffement climatique d’origine anthropique, les acteurs économiques revoient leurs pratiques.  
Le secteur informatique, qui représente **3 à 4 % des émissions mondiales de gaz à effet de serre**, n’échappe pas à cette remise en question.

Le **Green IT** vise à répondre aux enjeux environnementaux (réchauffement climatique, épuisement des ressources abiotiques, consommation d’eau, etc.) à travers plusieurs axes d’amélioration :  
- Sobriété numérique  
- Allongement de la durée de vie des équipements  
- Éco-conception logiciel  
- Optimisation de l’utilisation des infrastructures :contentReference[oaicite:2]{index=2}

Cet article **se concentre sur l’optimisation de l’utilisation des ressources serveur**, notamment via l’élasticité et l’usage de *machines préemptives*. :contentReference[oaicite:3]{index=3}

---

## Elasticité et charge maximale

Maximiser l’utilisation des processeurs d’un serveur physique est un objectif clé pour de nombreux ingénieurs SRE (Site Reliability Engineering) — que ce soit pour :

- Optimiser les coûts d’infrastructure,
- Réduire l’impact environnemental,
- Ajuster la capacité au plus juste selon la charge réelle.
L’enjeu est de **dimensionner dynamiquement l’infrastructure** pour répondre à des besoins de calcul non linéaires et imprévisibles.  
Pour cela, plusieurs technologies et pratiques sont combinées :

- Virtualisation  
- Infrastructure as Code (IaC)  
- Architectures *stateless*  
- Répartition de charge  
- Monitoring en temps réel  
- Scaling horizontal (*scaling out*)
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/65c42e83-9a20-4753-9939-5c8892359857" />


Une fois cette élasticité mise en place, on teste la configuration en conditions réelles pour déterminer la **charge maximale admissible**, qui sert ensuite à réserver la capacité nécessaire. 

---

## Optimisation des plages de calcul inutilisées

Même avec une infrastructure bien dimensionnée, une partie des ressources serveurs reste souvent **inutilisée** en dehors des pics de charge.

L’idée est de modéliser l’utilisation CPU sur plusieurs jours pour déterminer des **plages de capacité disponible**, qui peuvent ensuite être exploitées pour des traitements supplémentaires.  
Ce calcul permet de réduire la part de puissance non utilisée et d’améliorer l’efficacité globale de l’infrastructure.

---

## Les machines préemptives

Les **machines préemptives** (ou *spot instances* chez certains clouds) sont des instances de calcul proposées à prix réduit, mais **récupérables à tout moment par leur fournisseur avec un préavis court**.

### Avantages

- Moins coûteuses car partagées quand elles ne sont pas utilisées  
- Permettent d’exploiter des plages de calcul inutilisées sur un cluster

### Cas d’usage

Ces machines conviennent particulièrement à des traitements :

- Courts
- Non urgents
- Non bloquants  

Par exemple, dans une infrastructure e-commerce, on peut exécuter sur ces machines des tâches telles que :

- Insertion de données dans un CRM  
- Alimentation d’un data lake

Les grands fournisseurs Cloud proposent ce type d’instance nativement :

- **Preemptive VM** — Google Cloud  
- **Spot VM** — Azure  
- **Spot Instance** — AWS

---

## Compétences nécessaires

La mise en place de ce type d’architecture exige plusieurs compétences techniques :

- **Orchestration & Conteneurisation** (ex. Kubernetes, Docker)  
- **Développement logiciel** pour concevoir des applications adaptées  
- **Automatisation** (Terraform, Ansible, IaC)  
- **Gestion de charge** et répartition dynamique des ressources  
- **Monitoring en temps réel**  
- **Autoscaling**

---

## Limites des machines préemptives

Même si elles offrent des bénéfices importants, ces machines ont des contraintes :

- **Disponibilité limitée** principalement aux environnements Cloud  
- **Préavis court** pouvant interrompre les tâches en cours  
- Demande des **tâches courtes et non bloquantes**  
- Nécessite des **compétences techniques élevées** pour être exploitées efficacement

---

## Conclusion

L’élasticité des machines préemptives apparaît comme un **levier important pour les futures stratégies Green IT**, en permettant de maximiser l’utilisation des serveurs tout en minimisant les coûts et l’impact environnemental.

Cependant, pour que ces avantages se concrétisent, une mise en œuvre technique solide et une expertise pointue sont indispensables.  
Et surtout : **la sobriété reste un principe fondamental**, sans quoi tout gain d’efficacité peut être annulé par un effet rebond.

---
