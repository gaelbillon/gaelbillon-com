---
title: "CMS headless: avantages, inconvénients & comparatif des 5 leaders"
date: "2018-11-16T16:54:01.000Z"
template: "post"
draft: false
slug: "cms-headless-avantages-inconvenients-comparatif-des-5-leaders"
category: "Sites statiques"
tags: 
  - "CMS headless"
  - "Français"
  - "Sites statiques"
description: "Les CMS headless reposent sur un découplage fort ente le contenu et sa présentation. A l'heure de la multiplication des interfaces. Le contenu n'est plus toujours solidaire du front end."
socialImage: "/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/Headed-and-Headless-CMS-comparison-Drupal-Wordpress-Prestashop-Cockpit-Prismic-Contentful-Directus-Dato.png"
---

![Headless CMS comparison](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/Headed-and-Headless-CMS-comparison-Drupal-Wordpress-Prestashop-Cockpit-Prismic-Contentful-Directus-Dato-featurred.png)

A l'heure de la multiplication des supports et des interfaces. Le contenu n'est plus toujours solidaire du front end. Les CMS headless (littéralement, système de gestion de contenu sans tête) reposent sur un découplage fort ente le contenu et sa présentation. Avec ce que ça apporte comme avantages et inconvénients. Un CMS sans tête ne s'occupe que de la gestion du contenu en backend mais aucunement de l'affichage de ce contenu. Ca, c'est à votre charge, ou a celle des développeurs. Wordpress par exemple, est un CMS qui s'occupe à la fois de la gestion du contenu et de son affichage en frontend. Un CMS headless n'a pas de thèmes ou de templates, il n'affiche rien, pour l'utiliser il faut obligatoirement développer un site ou une application mobile ou pourquoi pas une application Google Glass ou un chatbot qui va se nourrir des données fournies par le CMS headless via son API.



## Avantages :

- L'éditeur n'est pas dévelopeur il se contente d'écrire du texte et pourquoi pas rajouter quelques images mais il n'a pas plus de pouvoir que ça. Il ne peut pas insérer de code ou provoquer de problème d'affichage du site puisqu'il ne contrôle pas l'affichage
- Toutes les données sont disponibles par le biais d'une API, généralement au format JSON, et parfois par GraphQL.
- L'interface de gestion du contenu est clair et intuitive est peut être agrémenter de prévisualisateurs personnalisés.
- Le contenu est disponibles pour différentes applications, différents appareils, on peut même envisager de l'envoyer à une machine qui n'a que faire de la façon dont le contenu est présenté.
- Ue interface plus conviviale pour les éditeurs, l'interface est épuré, elle ne présente que le strict nécessaire
- Possibilité d'ajouter du contenu par le biais d'une API et donc très facilement aussi par le biais d'une application ou pourquoi pas à l'aide d'un capteur.
- Plus de gestion de base de données qui s'engraisse et dont les performances de dégradent avec le temps (sauf si vous optez pour un CMS headless auto-hebergé).



## Inconvénients :

- L'éditeur du contenu n'a pas toutes les libertés de mise en page offertes par un CMS traditionnel.
- Le contenu est hébergé chez une tierce partie. (/!\\RGPD)
- Les fournisseurs de Content as a Service sont la plupart du temps payants. Les tranches gratuites peuvent toutefois convenir à des petits projets.
- Le prix n'est pas aussi clair qu'avec un CMS traditionnel, il faut bien regarder les limitations et anticiper les futurs besoin.
- Tout le monde n'est pas encore habitué à travailler avec ce genre de système et bien que leurs interfaces soient très intuitive, ça peut nécessiter un temps d'adaption ou de formation.
- C'est un nouveau composant du système à gérer et à payer en plus.



## CMS traditionnels en tant qu'headless

Certains CMS traditionnels peuvent eux aussi servir de CMS headless. C'est le cas de Drupal, Wordpress ou Prestashop, qui proposent depuis récemment des API. On peut alors utiliser Wordpress par exemple uniquement pour gérer du contenu sans utiliser la partie affichage de Wordpress.

Le CMS headless est seulement un outil supplémentaire, pas une nouvelle solution ultime. Chaque projet est différent et comme à l’accoutumée il convient de déterminer les besoins avant de faire le choix. Un des critères déterminant sera le nombre de supports/appareils/apps qui vont devoir afficher le contenu. Le choix fera également intervenir des question de propriété intellectuelle puisque les données sont hébergées ailleurs, à voir en fonction de la politique de confidentialité de chaque CMS qui n'ont pas tous la même approche. On pourra également se demander de quelles fonctionnalités on aura besoin : API, GraphQL, CDN, redimensionnement des images ?

Le CMS headless est un excellent compagnon aux [sites statiques](/posts/jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/) tels que ceux que l'on peut developper avec [Gatsby](https://gaelbillon.com/gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/) par exemple

## Comparatif des CMS headless

Avant toute chose il faut savoir qu'il existe plusieurs types de CMS headless : Git based ou API based.

- Un CMS Git based stock ses données sur un repo Git, les données vivent dans des fichiers, il ne propose pas d'API (sauf exceptions).
- API based, les données son stockés dans une base de données, une API est exposée permettant d'y accéder. Ci-dessous sont présentés uniquement des CMS API.


###Contentful

Avec l'offre gratuite :

- 5 utilisateurs
- 2 espaces,
- 10000 entrées
- 2 locales (i18n)
- 3 roles
- API (1 000 000 d'appels)
- Bande passante 1 TB
- CDN
- Webhooks (20)
- SDKs
- GraphQL à partir de la version à 776€ / mois

![Interface utilisateur du CMS headless Contentful](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/contentful-headless-CMS-interface-utilisateur.jpg)
<figcaption>Interface utilisateur du CMS headless Contentful</figcaption>


###DatoCMS

Offres plus diversifiées que chez Contentful qui monte très vite à 776€ / mois

Avec l'offre gratuite :

- 1 utilisateur
- 1000 entrées
- 15 models
- 1GB d'espace de stockage
- 1 locale (i18n)
- 1 utilisateur
- Bande passante 1 TB
- SDKs
- Webhooks & GraphQL ?

![Interface utilisateur du CMS headless DatoCMS](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/DatoCMS-headless-CMS-interface-utilisateur.jpg)
<figcaption>Interface utilisateur du CMS headless DatoCMS</figcaption>



###Prismic

Des plans bien répartis à 6€, 13€, 88€ et 441$ / mois

Avec l'offre gratuite :

- Toutes les fonctionnalités dispo en "fair use", Prismic se réserve le droit de mettre le hola si ça va plus loin que ce qu'ils estiment être "fair use"
- SDKs
- CDN
- GraphQL : presque, en beta public à ce jour (le 15 novembre 2018)

![Interface utilisateur du CMS headless Prismic](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/Interface-du-CMS-headless-Prismic.png)
<figcaption>Interface utilisateur du CMS headless Prismic</figcaption>



###Directus

Une version open source disponible sur [Github](https://github.com/directus) et une version CMSaaS (CMS as a Service)

Avec l'offre gratuite :

- 1 utilisateur
- 1000 Entrées
- 3 Collections
- GraphQL : non, même en version payante

![Interface utilisateur du CMS headless Directus](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/Interface-du-CMS-headless-Directus.png)
<figcaption>Interface utilisateur du CMS headless Directus</figcaption>



###Cockpit

Open source license MIT ([Github](https://github.com/agentejo/cockpit))

- Webhooks
- GraphQL sous forme d'addon ([Github](https://github.com/agentejo/CockpitQL))

![Interface utilisateur du CMS headless Cockpit](/media/2018-11-16---cms-headless-avantages-inconvenients-comparatif-des-5-leaders/Interface-du-CMS-headless-Cockpit.png)
<figcaption>Interface utilisateur du CMS headless Cockpit</figcaption>



### Et bien d'autres encore :

- [GraphCMS](https://graphcms.com)
- [Strapi](https://strapi.io)
- [Stroryblok](https://www.storyblok.com) The first headless CMS with an API-based visual editor
- [TakeShape](https://www.takeshape.io) with an integrated Static Content Generator
- [Netlify CMS](https://www.netlifycms.org) Git based, Open source, license MIT ([Github](https://github.com/netlify/netlify-cms))

### Sans oublier les CMS traditionnels utilisables en headless

- WordPress
- Drupal
- Prestashop

Et encore plus sur [https://headlesscms.org](https://headlesscms.org) qui répertorie de nombreux CMS headless.
