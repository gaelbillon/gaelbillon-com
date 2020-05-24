---
title: "Gatsby, le générateur de site statique basé sur React et GraphQL"
date: "2018-11-15T15:59:55.000Z"
template: "post"
draft: false
slug: "gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql"
category: "Sites statiques"
tags: 
  - "Français"
  - "gatsby"
  - "react"
  - "Sites statiques"
  - "static"
  - "statique"
  - "Web performance fr"
description: "Gatsby est un générateur de site statique basé sur React. Il est doté d'un riche écosystème de plugins et peut s'adapter à de nombreuses sources de données."
socialImage: "/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/logo-gatsby-0square-e1558085891772.png"
---

![logo gatsbyjs square](/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/logo-gatsby-0square-e1558085891772.png)

Gatsby est un [générateur de site statique](/posts/jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/) (SSG) basé sur React. Il s'agit d'un projet openSource ([GitHub](https://github.com/gatsbyjs/gatsby)) né en en mai 2015 auquel ont contribués plus de 1350 développeurs en 7000 commits à ce jour. Debut 2018 Kyle Mathews crée Gatbsy Inc pour soutenir le développement du projet. L'entreprise à levé 3,8 millions de dollars de seed money en mai 2018.

Les données peuvent provenir de nombreuse et diverses sources : fichiers Markdown, [CMS Headless](/posts/cms-headless-avantages-inconvenients-comparatif-des-5-leaders/), API Wordpress, fichiers Google docs, etc. grâce à de nombreux plugins.s

## Plugins

L'écosystème Gatsby est déjà riche de plus de 500 plugins. Il y'en pour tous les goûts, que ce soit pour afficher un feed Instagram, configurer Google Analytics ou se connecter sur un CMS headless.

- [gatsby-plugin-offline](https://www.gatsbyjs.org/packages/gatsby-plugin-offline/)
- [gatsby-plugin-google-analytics](https://www.gatsbyjs.org/packages/gatsby-plugin-google-analytics/?=)
- [gatsby-remark-prismjs](https://www.gatsbyjs.org/packages/gatsby-remark-prismjs/?=) pour le syntax highlighting
- [gatsby-source-twitter](https://www.gatsbyjs.org/packages/gatsby-source-twitter/?=) pour afficher des données à l'aide de l'API Twitter
- [gatsby-plugin-i18n](https://www.gatsbyjs.org/packages/gatsby-plugin-i18n/) pour l'internationalisation
- Et bien d'autres ici : [https://www.gatsbyjs.org/plugins/](https://www.gatsbyjs.org/plugins/)

Parmi eux certains sont quasiment indispensables et on les retrouvera dans la plupart des projets.

### Gatsby images

Le plugin gatsby-image est un composant clef de Gatsby qui simplifie l'experience dévelopeur pour servir des images optimisées.

- Utilisation d'images WebP pour les navigateurs le supportant
- Réservation l'emplacement des images pour éviter les saccades lorsque les images sont chargées
- Chargement de l'image optimale en fonction de la taille d'écran et de la résolution.

#### srcset

Génération de multiples version d'une image automatiquement grace à srcset. La taille adéquate est utilisée automatiquement par le navigateur en fonction de la taille de l'écran.

#### Lazy loading

Le lazy loading est intégré dans gatsby-image par défaut, il n'y a rien a configurer, ca fonctionne. Les images ne sont pas requêtées par le navigateur au chargement de la page mais uniquement lorsqu'on scroll vers le bas. Et ça améliore aussi grandement la performance d'un site.

#### Blur-up ou tracedSVG en un fragment.

Les fragments ce sont des briques de GraphQL qu'on peut créer et réutiliser par la suite, Blur up reprend une idée popularisée par la plateforme de blogging Medium et consiste à généré des versions floues et donc très légères des images affichées sur un site. Au chargement de la page c'est d'abord les images floutées qui seront afiichées enattendant que les images originales soient téléchargées. Le rendu est beaucoup plus agréable même si on ne distingue pas le contenu de l'image, on sait au moins qu'il y'a une image, le contenu ne sautera au moment du chargement puisque l'image est déjà en lace. Rien de révolutionnaire mais c'est tellement à mettre en place avec Gatsby qu'il serait dommage de s'en priver. TracedSVG fonctionne sur le même principe sauf qu'a la pace d'une version floutée de l'image on va cette fois la remplacer par une version vectorisée à l'aide du programme open source Potrace, automatiquement. Et le résultat est magnifique.

Un article très intéressant sur le préchargement et l'optimisation et des images : [How to use SVG as a Placeholder, and Other Image Loading Techniques](https://medium.freecodecamp.org/using-svg-as-placeholders-more-image-loading-techniques-bed1b810ab2c)

![TracedSVG placeholder Gatsby image optimisation](/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/TracedSVG-placeholder-Gatsby-image-optimisation.gif)

Vous pouvez également observer de véritables placeholder SVG dans leur habitat naturel sur ce site que j'ai réalisé pour découvrir Gatsby : [https://waterscap.es](https://waterscap.es). Très inspiré de [gatsby-starter-gcn](https://www.gatsbyjs.org/starters/gatsby-starter-gcn). Plus d'infos ici : [Waterscap.es un site statique réalisé avec Gatsby](/posts/portfolio-item/waterscap-es-un-site-statique-realise-avec-gatsby/).

## Themes

Il y'a bien évidement beaucoup moins de thèmes que pour les gros CMS et ils ont moins de fonctionnalités mais on commence cependant à en voir apparaitre quelques un intéressant.

- [https://shop.gatsbymanor.com](https://shop.gatsbymanor.com)
- [https://codebushi.com/gatsby-starters/](https://codebushi.com/gatsby-starters/)

![Gatsby JS themes](/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/Capture-d-ecran-2018-11-15-a-17.21.33.jpg)

## Showcase

Gatsby a beau être jeune, nombreux sont ceux qui l'utilisent déjà en production, parmi eux :

- [reactjs.org](https://reactjs.org/) (le site officiel de React)
- [Airbnb.io](https://airbnb.io)
- [Braun](https://ca.braun.com/en-ca)
- [Flamingo](https://www.shopflamingo.com) (E-commerce)
- Plus d'exemples ici : [https://www.gatsbyjs.org/showcase/](https://www.gatsbyjs.org/showcase/)

![Gatsby sites Showcase](/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/Capture-d-ecran-2018-11-15-a-17.24.27.jpg)

## Déploiement en un clic

Pour deployer son site, la commande `gatsby serve` s'en charge. Le site est envoyé directement chez l'hébergeur, Netlify ou Github pages par exemple et si le site est sur un repo Git il est aussi possible de configurer des webhooks qui déclencheront une compilation à chaque commit. Les webhooks peuvent aussi être configurés lors de la modification du contenu si celui ci est hébergé sur un CMS headless le supportant comme Contentful ou DatoCMS.

## Performance

Sans aucune optimisation, même pas la moindre directive cache-control, la plupart des sites développés avec Gatsby se chargeront incroyablement plus rapidement qu'un site équivalent (qui affiche la meme chose) développé avec Wordpress. D'autant plus que la plupart des hébergeurs de sites statiques fournissent le HTTPS, HTTP2 et le CDN par défaut. Et tout cela gratuitement. Etant statique, un site Gatsby n'aura aucun soucis à supporter une montée en charge due à un plus grand nombre de visiteurs.

## GraphQL

GraphQL et Gatsby fonctionnent quasiment main dans la main même si il reste possible d'utiliser ce que Gatsby appel des données déstructurées. L'utilisation de GraphQL est un vrai bonheur pour le développement, on demande l'information que l'on souhaite et le serveur nous la renvoi. Si vous utilisez Gatsby vous passerez surement pas mal de temps dans GraphiQL (prononcé Graphiqeule), la web app de GraphQL qui permet de tester une requête ou une mutation avec la possibilité d'utiliser des variables et même avec de l'autocomplétion sur les champs disponibles !

![gatsby et graphql](/media/2018-11-15---gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/graphiql-300x170.png)

## SEO

Gatsby est SEO friendly. Rien que le fait qu'un site static se charge rapidement boost sa position dans les SERP. Côté lecture par les robots, puisque les pages du site sont crées au build avant le déploiement du site, on ne retrouve pas les problèmes des SPA puisque tout est là, aisément lisible dans un seul fichiers par page. Et pour les metadata ? C'est l'indispensable plugin gatsby-plugin-react-helmet qui s'en charge.

## Multiplatformes ?

Un site Gatsby est avant tout un site React et ça peut être bien pratique dans le cas où l'on souhaite developper une application qui reprend certaines fonctionnalités du site (ou vice versa). Grâce au concepts de React où tout est "componentisé", il va être possible de récupérer ces composants pour les réutiliser dans une app ([Gatsby for Apps](https://www.gatsbyjs.org/blog/2018-11-07-gatsby-for-apps/)). Et c'est encore plus vrai et plus simple si on utilise GraphQL pour récupérer des données à partir d'une API. Ca commence à devenir vraiment très multi-platformes :)
