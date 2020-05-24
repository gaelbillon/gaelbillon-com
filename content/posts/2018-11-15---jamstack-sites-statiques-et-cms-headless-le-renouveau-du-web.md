---
title: "JAMstack, statique, CMS Headless : Le renouveau du développement web"
date: "2018-11-15T13:43:21.000Z"
template: "post"
draft: false
slug: "jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web"
category: "Sites statiques"
tags: 
  - "Français"
  - "JAMstack"
  - "Sites statiques"
  - "statique"
description: "Générateur de sites statiques, APIs, Functions as a Service et CMS sans tête, voici les acteurs d'un mouvement qui révolutionne le développement web"
socialImage: "/media/2018-11-15---jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/gatsby-contentful-visual-studio-code.png"
---

![](/media/2018-11-15---jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/gatsby-contentful-visual-studio-code-791x321.png)

## Sites statiques

A l'origine du web tous les sites étaient statiques. C'est le web de Tim Berner Lee . [De simples fichiers html](http://info.cern.ch/hypertext/WWW/TheProject.html) demandés par un client et envoyés tels quels par le serveur. Et puis on a eu besoin de plus de fonctionnalités, besoin de donner la possibilité modifier le contenu d'un site sans être développeur web. Alors on ajouté des bases de données, on a compilé les pages dynamiquement à l'aide de languages comme PHP pour offrir un contenu sur mesure au visiteur d'un site. De fabuleux CMS tel que Wordpress on pu voir le jour. Aujourd'hui c'est plus de 30% des sites internets qui utilisent Wordpress.

Les éditeurs affectionnent les facilité d'édition d'articles et de pages grâce aux éditeurs WYSIWYG (bien que cela puisse être contesté étant donnée la multitude d'appareils et de tailles d'écrans [https://www.quaternum.net/2018/10/18/markdown-comme-condition-d-une-norme-de-l-ecriture-numerique/](https://www.quaternum.net/2018/10/18/markdown-comme-condition-d-une-norme-de-l-ecriture-numerique/)). Les développeurs l'apprécient pour sa facilité d'utilisation, l'installation se fait en quelques clics et en quelques de minute on a nouveau site prêt à être utilisé. On l'aime pour son vaste écosystème d'extensions qui permettent de parer à toute éventualité. Le client à besoin d'afficher sur le homepage un agenda qui se met à jour en même temps qu'un Google Calendar ? D'un système de réservation et de paiement en ligne ? D'ajouter une boutique en ligne ? D'afficher une carte des bureaux de l'entreprise à travers le monde ? Il y'a toujours un plugin à disposition et s'il n'yen a pas, il est relativement aisé d'en développer un.

Mais les sites dynamiques ont aussi apporté leurs lot de complications. La compilation des fichiers et le fonctionnement d'une base de donnée requiert plus de ressources que l'hébergement de simples fichiers HTML et qui dit plus de ressources dit plus gros serveurs avec plus de RAM, plus de CPU, plus d'espace disque et donc un coût d'hébergement plus élevé qu'il faudra l'ajuster en fonction de la fréquentation du site ou "loadbalancer" sur plusieurs serveurs. La sécurité est devenue plus délicate à gérer en raison de la nature dynamique de languages comme PHP et des bases de données, sensibles à de nombreuses attaques tel que les failles d'injection, XSS (cross-site scripting) ou CSRF (Cross-Site Request Forgery).

Et puis il y'a les problèmes de performance, le serveur doit executer du code pour générer les pages. Ce code, il doit être bien écrit, il doit être efficient, il ne doit pas provoquer de fuites de mémoire et même si tout fonctionne parfaitement, le code sollicitera toujours le processeur et la mémoire pour s'exécuter. C'est comme ça qu'on arrive à des usine à gaz, des sites Wordpress équipés de dizaines d'extensions, des pages qui prennent 10 secondes à charger, des sites hackés ou les articles du blog remplacés par des contenus pas très intéressants.

Wordpress et autres CMS comme Drupal ou Prestashop sont remarquables, ils font économiser un temps précieux et offres des milliers de possibilités, le ça gratuitement et c'est une vraie chance de pouvoir profiter de cet écosystème.

Mais depuis quelque temps une nouvelle mouvance apparaît. Le retour des sites statiques. Ils n'ont bien sur jamais disparus mais ont connu leur période de désuétude. Relancé notamment en 2008 par Jekyll, le générateur de site static développé par Tom Preston-Werner (fondateur de Github), le statique reprend depuis quelques années de l'ampleur et on voit fleurir un peu partout de nouveaux générateurs de site statiques :

- Jekyll
- Hugo (nodejs)
- Gatsby (react)
- Hexo (nodeks)
- Nuxt (vujs) Et bien d'autres...

Oui parce qu'un site static ça se génère. La génération c'est la compilation de plusieurs ressources en fichiers HTML à l'aide module bundlers comme Webpack. "Ah bon !? De la compilation, je croyais que c'était justement l'un des inconvénients des sites dynamiques ?" Oui, sauf que cette fois la compilation s'effectue uniquement lorsqu'une modification est effectuée sur le site, que ce soit son contenu ou son code. La compilation peut s'effectuer n'importe où (sur son ordi perso par exemple) puis les fichiers HTML sont envoyé sur le serveur.

## Headless CMS

L'une des beautés des sites statiques c'est le fort découplage entre contenu (le texte d'une page par exemple) et l'affichage de ce contenu (marge de 15 pixel à droite pour le texte du premier paragraphe par exemple). Dans un CMS, par le biais de son interface d'administration, l'éditeur qui n'est la plupart du temps pas un développer à le pouvoir de décider de l'affichage du contenu et peux insérer directement du code javascript dans la page et encore une fois c'est la l'une des grandes forces des CMS qui offre même à un débutant la possibilité de créer une page sans connaissance en développement à l'aide d'éditeurs WYSIWYG toujours plus avancés. Mais le découplement du contenu et de son affichage à ses avantages. Premièrement celui d'être "platform agnostic". Ca signifie que le contenu crée pour le site n'est pas forcément crée que pour ce dernier. Il pourra par exmeple être réutilisé dans une application mobile. Deuxièmement, l'éditeur d'une page ne peut plus faire n'importe quoi, comme par exemple insérer un code de suivi AdWords sur une page contact. Ce qui est censé être le travail du développeur. Les rôles sont ainsi mieux définis et l'éditeur ne peut plus provoquer de bugs sur le site, qu'il s'agisse de simple bugs d'affichage ou plus graves. Le contenu, c'est la partie Markup du JAMstack.

- [Prismic](https://prismic.io/)
- [DatoCMS](https://www.datocms.com)
- [Contentful](https://www.contentful.com)

Ces CMS offre des APIs qui permettent d'accéder à son contenu. Il est même possible d'effectuer les requêtes avec GraphQL !

Un article plus approfondi sur les CMS headless : [CMS headless: avantages, inconvénients & comparatif des 5 leaders](/posts/cms-headless-avantages-inconvenients-comparatif-des-5-leaders/)

## APIs et Functions as a Service

Mais les sites statiques ont aussi leurs inconvénients. Leur manque de dynamisme peut être problématique pour certains usages et il convient de bien étudier les besoins. Un système de commentaire par exemple, qui est fourni d'office avec Wordpress, n'est pas natif avec un site statique, il faut alors utiliser un système de commentaire externe comme Disqus ou Commento. Ces systèmes fonctionnent très bien mais il faut être prêt à héberger ses commentaires chez de tierces parties, à moins d'héberger soit même son système de commentaires sur un autre serveur (PHP + BDD nécessaires). Les formulaires de contact ne sont également pas aussi simples et nécessitent là aussi des services tiers (avec tout ce que ça implique en terme de GDPR) comme [Formspree](https://formspree.io) ou faire appel à une fonction hébergée ailleurs, chez AWS Lambda par exemple. On comprend alors un peu mieux l'émergence du mouvement Serverless et des Functions as a Service comme AWS Lambda. Ces services sont le A pour API de l'acronyme JAMstack.

### Javascript

Toutes les interactions dynamiques côté client se font à l'aide de Javascript (évidement puisqu'il n'y a pas de PHP). C'est le J de JAMstack, J pour Javascript.

## Avantages

- Le site peut être entièrement hébergé sur un CDN puisqu'il n'as pas besoin de code serveur.
- Le site est versionnable à l'aide des systèmes de gestion de versions comme Git ou SVN
- Ne générer qu'a la modification permet d'utiliser les outils du développement web moderne comme Webpack, Babel ou PostCSS.
- En configurant des Webhooks côté Headless CMS et côté repo Github, le site se met à jour automatiquement. Que ce soit lors d'une mise à jour du code ou une mise à jour du contenu.
- Un site statique n'a pas besoin d'être sécurisé, il l'est par défaut. Il n'a pas besoin d'être optimisé, le temps de chargement d'un site statique est largement moindre que celui d'un site dynamique (à site comparable).
- La base de donnée n'a pas besoin d'être finetuné, nettoyée ou optimisée.
- Il n'est pas nécessaire de passer des heures à configurer des plugins de cache qui poseront des problèmes d'invalidations du cache. Il n'est pas non plus nécessaire d'installer Redis ou Varnish pour accélérer le temps de chargement.
- Il faut toutefois continuer à optimiser les images mais les plugins de générateur comme [Gatsby](/posts/gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/) et les API des CMS headless comme [Contentful](https://www.contentful.com/developers/docs/references/images-api/) rendent la tâche tellement plus simple et plus élégante.
- Il n'y a pas se configuration de VHOST, d'ajout de directives, de configuration de SSL, si vous hébergez chez Netlify par exemple votre site est HTTPSisé HTTP2isé et CDNisé par défaut. Et l'hébergement est gratuit. Bien que j'héberge plusieurs sites chez Netlify, je ne saurais même pas vous dire si c'est Apache, NGINX ou nodejs qui sert les fichiers. On enlève la partie Devops du dévelopeur web Fullstack qui peut maintenant se reconcentrer sur la partie front. Il reste bien sûr possible de faire des redirections ou de l'authentification HTTP Basic à l'aide de fichiers de configuration toml par exemple.

![Exemple de workflow de l'agence web New Yorkaise Carrot Creative](/media/2018-11-15---jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/workflow-contentful-static.png) 
<figcaption>Exemple de workflow de l'agence web New Yorkaise Carrot Creative</figcaption>

## Conclusion

Voila pour un premier tour d'horizon de l'état de l'art du développement Web statique en 2018. Les sites statiques ont indéniablement le vent en poupe et de beaux jours devants eux et l'écosystème de thèmes et d'extensions s'accroit de jour en jour. Le web statique et le JAMstack ne sont évidement pas la solution à tous les problèmes et il convient de choisir judicieusement les outils en fonction du projet. Dans de nombreux cas un site dynamique est l'unique solution mais c'est indéniablement un vent de fraicheur qui souffle sur le développement web.

 

Quelques liens pour plus d'infos :

- [https://jamstack.org](https://jamstack.org)
- [https://jamstatic.fr](https://jamstatic.fr)
