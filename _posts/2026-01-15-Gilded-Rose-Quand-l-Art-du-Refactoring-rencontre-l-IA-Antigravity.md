---
layout: post
title: "Gilded Rose : Quand l'Art du Refactoring rencontre l'IA Antigravity"
date: 2026-01-15 06:00:00 +0100
categories: Software-Craftsmanship
author: Baptiste Macé
---

Le **Gilded Rose Kata** est une institution dans le monde du développement et pourtant je ne le conaissais pas. C'est le test de passage pour tout artisan logiciel qui souhaite prouver sa capacité à transformer un "legacy code" monstrueux en une architecture élégante. Aujourd'hui, je vous présente une résolution particulière de ce défi : une collaboration étroite entre l'œil aiguisé d'un expert et la puissance de l'IA **Antigravity**.

---

## 🏛️ Le Kata : Un Classique Immuable

Pour ceux qui ne le connaissent pas encore, le Kata Gilded Rose nous plonge dans une petite auberge gérée par Allison. Elle dispose d'un inventaire d'objets aux règles de péremption et de qualité bien précises (et souvent complexes) :
- **Aged Brie** : Sa qualité augmente avec le temps.
- **Sulfuras** : Objet légendaire, il ne perd jamais en qualité et ne se vend pas.
- **Backstage Passes** : Sa qualité explose à l'approche du concert, puis tombe à zéro après.
- **Conjured** : Une nouveauté qui se dégrade deux fois plus vite que les objets normaux.

Cet exercice m'a été inspiré par le travail de **Colin Damon**, dont l'approche pédagogique m'a donné envie de m'y replonger avec un angle neuf. Pour le point de départ, rien de mieux que le repository d'**Emily Bache**, qui propose un environnement C# extrêmement complet pour le kata.

Pourquoi le **C#** ? Parce que c'est mon langage de cœur. Désolé chers amis Javaistes, mais l'élégance de .NET 8 et la concision de C# sont imbattables pour ce type d'exercice ! 😉

---

## 🚀 The Journey : De la Confusion à la Clarté

La réussite de ce projet ne repose pas juste sur la génération de code, mais sur une **guidance "Tech Lead"** stricte appliquée à l'IA. Voici les étapes clés de notre voyage :

### 1. Le Pattern Strategy (IA + Expert)
Plutôt que d'empiler des `if-else` interminables dans une seule classe, nous avons extrait la logique de chaque item dans des stratégies dédiées.

```csharp
public interface IItemStrategy {
    Item Update(Item item);
}
```

### 2. Le Choc de l'Immuabilité (Guidance EXPERT)
L'une des contraintes majeures était de **ne pas modifier la classe `Item`**. Là où beaucoup se seraient contentés de muter les propriétés, J'ai imposé une approche fonctionnelle pure : les stratégies retournent un **nouvel objet** `Item`.
- **Résultat** : Un "Functional Core" sans effets de bord.

### 3. Découplage & Architecture Clean
J'ai pointé une erreur classique : le couplage du simulateur avec `Console.WriteLine`. Nous avons immédiatement refactoré pour injecter un `TextWriter`.
- **Bénéfice** : Notre simulateur peut maintenant écrire dans la console, un fichier, ou un `StringBuilder` pour les tests unitaires sans changer une ligne de code.

### 4. Multi-Interface & Web API
Le domaine est désormais 100% agnostique. Nous avons construit :
- Un projet **Console** classique.
- Une **Web API (Minimal API)** sous ASP.NET Core.
- Un **Dashboard Web** dynamique.

---

## 👁️ L'Expérience Antigravity

Faire ce kata avec **Antigravity**, c'est comme avoir un binôme extrêmement rapide, mais qui a besoin d'un capitaine pour garder le cap architectural. 

Le moment "WOW" ? Quand Antigravity a pris le contrôle d'un **vrai navigateur** via Playwright pour prouver que l'interface construite deux minutes plus tôt répondait parfaitement aux règles métier. Ce n'est plus seulement de l'écriture de code, c'est de l'ingénierie automatisée validée en temps réel.

![Simulation results](/assets/gilded-rose/results.png)


**Le moment du "slap" 👋** : Voici l'enregistrement de l'agent prenant le contrôle du navigateur pour valider la simulation de 5 jours.

![Browser Recording](/assets/gilded-rose/recording.webp)

---

## ✅ Le Bilan Technique

- **Couverture de tests : 100%** (26 tests unitaires et d'intégration).
- **Architecture : Decoupled & Functional**.
- **Stack : .NET 8, Playwright, XUnit**.

Le code est disponible sur mon nouveau repository : 
🔗 **[GildedRose-Refactored-Final](https://github.com/BaptisteCDC/GildedRose-Refactored-Final)**

C'était plus qu'un simple exercice de code, J'ai découvert ce qu'on peut accomplir quand on combine les principes du **Software Craftsmanship** avec une IA capable d'agir dans le monde réel.

---
*Ecrit avec passion, guidé par l'expertise, propulsé par Antigravity.*
