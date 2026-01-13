
---
layout: post
title: "Trois amigos et un concombre : quand le BDD fait son théâtre 🎭💻🥒"
date: 2025-04-02 10:00:00 +0100
categories: BDD
author: Baptiste Macé
---
### **Introduction**

Dans la grande pièce qu'est le développement logiciel agile, la qualité du code n'est pas un simple décor de fond : elle est au cœur de la mise en scène. Mais attention, pas question d'en faire un acte isolé ou une répétition générale de dernière minute \! La qualité doit être intégrée dès les premières lignes du script, en collaboration avec toute la troupe.

C’est là qu’entrent en scène les Trois Amigos – Développeur, QA et Product Owner – accompagnés de deux dramaturges de renom : Cucumber, maître des dialogues en Gherkin, et Playwright, metteur en scène des interactions utilisateur. Ensemble, ils orchestrent des tests end-to-end et automatisent les validations avec GitHub Actions, assurant ainsi que chaque scène du développement se joue sans accroc.

Dans cet article, découvrez comment ces protagonistes collaborent pour écrire des scénarios clairs, fluidifier le jeu et garantir un spectacle (numérique) sans fausse note \! 🎬✨

---

### **Le BDD et les tests end-to-end**

Le Behavior-Driven Development (BDD) permet d’uniformiser la compréhension des besoins métiers et des comportements attendus du système. Il repose sur un langage commun, compréhensible par toutes les parties prenantes – développeurs, PO et testeurs – afin de garantir une vision alignée du produit. En favorisant une écriture claire des exigences sous forme de scénarios, le BDD améliore la communication et réduit les ambiguïtés fonctionnelles.

Les tests end-to-end (E2E) jouent un rôle clé dans la validation du bon fonctionnement d’une application dans son ensemble. Contrairement aux tests unitaires ou d’intégration, ils simulent des scénarios utilisateurs réels, garantissant que l’interaction entre les différents composants du système fonctionne comme prévu. Des outils comme Cucumber et Playwright permettent d’implémenter cette approche de manière efficace.

📌 Martin Fowler met en garde contre l’abus des tests E2E dans sa pyramide des tests, rappelant qu’ils ne doivent pas se substituer aux tests unitaires et d’intégration, mais venir en complément. Leur exécution est plus lente et sujette aux flakiness, d’où l’importance de les utiliser avec discernement pour valider les parcours critiques et assurer une transition sereine vers la production.

Avec Cucumber, il est possible de définir des tests sous forme de scénarios en Gherkin, un langage naturel accessible, tandis que Playwright se charge de leur exécution en simulant des interactions utilisateur précises sur le front-end. Cette combinaison permet d’automatiser les tests fonctionnels tout en maintenant une forte lisibilité et une collaboration efficace entre équipes.

```
Feature: Submit button functionality 
  Scenario: User clicks the submit button 
    Given I am on the homepage 
    When I click the submit button 
    Then I should see the success message
```

Cet exemple montre comment l'approche BDD rend les tests compréhensibles et partageables par l'ensemble des parties prenantes.

---

### **L'importance des IDs dans le front**

Dans le cadre des tests end-to-end, l’utilisation d'IDs uniques et bien définis dans le front-end joue un rôle stratégique. Non seulement ces IDs facilitent la sélection d’éléments pour les tests, mais ils contribuent également à rendre ces tests stables et fiables. Il est essentiel que les tests ne soient pas affectés par des modifications du design ou de la structure HTML.

Par exemple, un simple composant React utilisant un ID unique pour un bouton d'envoi pourrait ressembler à ceci :

```
function MyButton() 
  { 
    return ( <button id="submit-button">Submit</button> ); 
  }
```

Ensuite, vous pouvez utiliser Playwright pour automatiser un test end-to-end qui vérifie le bon fonctionnement du bouton d’envoi en utilisant cet ID :

```
const { test, expect } = require('@playwright/test'); 

test('should click the submit button', async ({ page }) => { 
  await page.goto('http://localhost:3000'); 
  const button = await page.locator('#submit-button'); 
  await button.click(); 
  const successMessage = await page.locator('#success-message'); 
  await expect(successMessage).toBeVisible(); 
});
```

### **Variante avec data-testid**

Une alternative souvent utilisée dans les projets front-end consiste à utiliser des attributs data-testid. Ces attributs sont dédiés aux tests et n’interfèrent pas avec le design ou d'autres fonctionnalités :

```
function MyButton() 
  { 
return ( <button data-testid="submit-button">Submit</button> ); 
  }
```

Voici le test correspondant en Playwright :

```
const { test, expect } = require('@playwright/test'); 

test('should click the submit button', async ({ page }) => { 
  await page.goto('http://localhost:3000'); 
  const button = await page.locator('[data-testid="submit-button"]');
  await button.click(); 
  const successMessage = await page.locator('[data-testid="success-message"]');
  await expect(successMessage).toBeVisible(); 
});
```

### **Pourquoi utiliser data-testid ?**

* Clarté et séparation des responsabilités : L’attribut data-testid est spécifiquement conçu pour les tests, ce qui permet de différencier les sélecteurs utilisés pour les tests des autres propriétés HTML.  
* Résilience aux changements : Contrairement aux IDs ou classes, qui peuvent être modifiés pour répondre aux besoins de design ou d'accessibilité, les data-testid sont moins susceptibles d’être affectés par ces évolutions.

En combinant des IDs ou des data-testid bien pensés avec des outils comme Playwright, vous améliorez la robustesse de vos tests end-to-end et leur résistance aux changements dans le code ou le design.

---

### **Les tres amigos : QA, PO, Dev**

La collaboration entre le PO, les QA et les Dev — aussi appelée l’approche des tres amigos — est essentielle pour garantir que les tests sont non seulement exhaustifs, mais qu'ils répondent aux besoins métier. Chaque acteur doit apporter sa perspective et son expertise pour assurer la couverture optimale des tests.

* Le PO : veille à ce que les tests soient alignés avec les besoins des utilisateurs finaux.  
* Le QA : assure la cohérence des tests et leur robustesse pour prévenir les bugs.  
* Le Dev : se charge de l'implémentation des fonctionnalités tout en veillant à la maintenabilité du code.

Cette collaboration ne se limite pas aux tests manuels, elle s'étend aussi à l'écriture des tests automatisés, où chacun contribue à la définition des critères de réussite et à l'écriture des tests dans un langage compréhensible par tous.

### **Intégration de Playwright avec Cucumber**

L'intégration de Playwright avec Cucumber combine la puissance des tests end-to-end (E2E) et la clarté des scénarios métier définis en langage Gherkin. Cucumber permet de décrire les tests sous forme de scénarios lisibles et compréhensibles par toutes les parties prenantes (PO, QA, développeurs), tandis que Playwright assure l'exécution rapide et fiable de ces scénarios en simulant les interactions utilisateur sur une application.

Dans cette intégration, chaque étape des scénarios Gherkin (définie avec Given, When, Then) est implémentée dans un fichier de définition en JavaScript ou TypeScript. Playwright est utilisé dans ces définitions pour interagir directement avec le DOM ou effectuer des actions comme des clics, des saisies, ou des vérifications d'état.

Un exemple de scénario Gherkin pourrait être :

```
@user_case
Scenario: Vérifier la connexion de l'utilisateur 
  Given l'utilisateur est sur la page de connexion 
  When il entre ses identifiants et clique sur "Se connecter" 
  Then il est redirigé vers la page d'accueil
```

Les définitions associées utiliseraient Playwright comme suit :

```
const { Given, When, Then } = require('@cucumber/cucumber'); 
const { expect } = require('@playwright/test'); 

Given('l\'utilisateur est sur la page de connexion', async function () { 
   this.page.goto('http://localhost:3000/login'); 
}); 

When('il entre ses identifiants et clique sur "Se connecter"', async function () { await this.page.fill('#username', 'testuser'); 
await this.page.fill('#password', 'password123'); 
await this.page.click('#login-button'); 
}); 

Then('il est redirigé vers la page d\'accueil', async function () { 
await expect(this.page).toHaveURL('http://localhost:3000/home'); 
});
```

Cette intégration facilite la collaboration interdisciplinaire tout en offrant une exécution rapide et fiable grâce à Playwright, garantissant que les comportements métiers sont correctement traduits et validés dans le système.

---

### **Automatisation des tests avec GitHub Actions et ciblage par tags**

L'automatisation des tests avec GitHub Actions permet d'améliorer la réactivité et la qualité des tests. Chaque modification du code déclenche automatiquement une série de tests, permettant de détecter rapidement d’éventuelles régressions. Par exemple, l'intégration de Playwright dans GitHub Actions peut être configurée de la manière suivante :

```
name: Playwright Tests 
on: 
  push: 
    branches: 
      - main paths: - '**/*.js' 
jobs: 
  test: 
    runs-on: ubuntu-latest 
    steps: 
      - name: Checkout code uses: actions/checkout@v2 
      - name: Install dependencies run: | npm ci npm install playwright 
      - name: Run Playwright tests run: | npx playwright install npx playwright test
```

L’ajout de tags dans les tests permet de les cibler spécifiquement selon les parties du code modifiées. Par exemple :

```
test('should click the submit button', async ({ page }) => { 
  test.setTimeout(5000); const button = await page.locator('#submit-button'); 
  await button.click(); 
  const successMessage = await page.locator('#success-message'); 
  await expect(successMessage).toBeVisible(); }).tag('submit');
```

Les tags permettent de sélectionner et d'exécuter uniquement les tests liés à une fonctionnalité spécifique, optimisant ainsi les temps d'exécution et l'efficacité du processus.

---

### **Conclusion**

Ainsi s’achève notre pièce, mais le spectacle du développement continue \! 🎭 L’intégration des tests automatisés, du BDD et des outils comme Playwright et GitHub Actions ne se résume pas à un simple gain en qualité : c’est une mise en scène où chaque acteur – Développeur, QA, PO – tient un rôle clé.

En répétant dès les premières scènes du développement et en automatisant les validations, la troupe assure une représentation fluide, sans fausses notes ni imprévus en coulisses. Résultat ? Un code bien rodé, une collaboration harmonieuse et un spectacle qui se joue sans accroc à chaque nouvelle itération. Rideau… jusqu’au prochain sprint \! 🎬✨

