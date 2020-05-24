---
title: "Wordpress & JAMstack ! Gatsby en front, WP en CMS headless"
date: "2020-04-11T14:42:11.000Z"
template: "post"
draft: false
slug: "wordpress-jamstack-gatsby-en-front-wp-en-cms-headless"
category: "JAMstack"
tags: 
  - "CMS headless"
  - "Français"
  - "Headless CMS"
  - "JAMstack"
  - "JAMstack"
  - "Sites statiques"
  - "static"
  - "statique"
  - "Web performance fr"
  - "webdev"
  - "webperf"
  - "webperformance"
  - "worpdress"
description: "L’idée de combiner Gatsby (statique) et WP (dynamique) peut paraître saugrenue de prime abord. À moins qu'on tienne là un combo idéal du dev web moderne"
socialImage: "/media/2020-04-11---wordpress-jamstack-gatsby-en-front-wp-en-cms-headless/gatsby-wordpress-hero-845x321-1.jpg"
---

![Gatsby Wordpress hero image](/media/2020-04-11---wordpress-jamstack-gatsby-en-front-wp-en-cms-headless/gatsby-wordpress-hero-845x321-1.jpg)

L’idée de combiner Gatsby, spécialisé dans les sites statiques et Wordpress, le leader des sites dynamiques, peut paraitre saugrenue de prime abord… À moins qu'on tienne là un combo idéal du dev web moderne.  

Avec l’avènement du [JAMstack](/posts/jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/) la tentation est grande de franchir le pas et de profiter des avantages des sites statiques pour profiter des avantages en termes de rapidité, de sécurité et de simplicité. Mais Wordpress à tout de même de nombreux points forts : son interface intuitive, déjà utilisé par beaucoup de monde, son importante base de plugins et son importante communauté. Heureusement l'écosystème JAMstack évolue et s’adapte très vite.   

Les sites statiques font leur grand retour sur le devant de la scène, en partie à cause des sites Wordpress surchargés de plugins de de javascript et de CSS qui ralentissent le temps de chargement et font travailler le processeur. Les sites statiques évitent beaucoup de ces désagréments et offrent aussi une meilleur sécurité et scalabilité pour un coût d'hébergement bien moindre. Ce genre de site est aussi facilement versionable avec Git.  

Pour passer un site Wordpress en statique, la solution la plus simple et d’utiliser le plugin [WP2Static](https://wp2static.com/) qui exporte un site Wordpress en HTML et l'héberge dans un sous dossier, sur Netlify ou autre hébergement de votre choix.  

Mais nous allons ici nous intéresser à un usage différent qui consiste à n’utiliser Wordpress qu’en tant que [CMS headless](/posts/cms-headless-avantages-inconvenients-comparatif-des-5-leaders/). Wordpress est alors utilisé uniquement pour créer, éditer et stocker le contenu (pages, articles, images, etc). L’affichage du frontend est assuré par un site custom, à développer à l’aide d’un framework comme React à l’aide de [Gatsby](https://dev.gaelbillon.com/gatsby-le-generateur-de-site-statique-base-sur-react-et-graphql/) (React), ou Vue avec l’aide de [VuePress](https://vuepress.vuejs.org/) (Vue).

Ces deux générateurs sont les seuls qui, à ma connaissance, permettent une connexion simple à Wordpress mais il est toujours possible d’utiliser l’API Wordpress ou le plugin [WPGraphQL](https://www.wpgraphql.com/). On peut alors utiliser l’un des nombreux autres générateurs de sites statiques (SSG). Que vous pouvez les retrouver sur [StaticGen](https://www.staticgen.com/).  

En effet, VuePress et Gatsby offrent une solution toute prête pour utiliser la base de données de Wordpress. Via GraphQL, pour VuePress, à l’aide d’un serveur node qui se connecte à la base de données WP. Et chez Gatsby, avec un plugin ([gatsby-source-wordpress](https://www.gatsbyjs.org/packages/gatsby-source-wordpress/)) qui utilise l’API Wordpress.  

On peut ensuite récupérer le contenu des articles, des pages, des menus, et d'à peu près toutes les infos qui permettront de reconstruire le site. Avec le même contenu mais une interface différente.  

**Pourquoi choisir Wordpress + Gatsby**

- Pas besoin d’un base de données et de backends complexes
- Il n’y a aucun logiciel ou base de données à attaquer
- Découplement du contenu et du code
- Sites non surchargés par des tas de plugins 
- Meilleur performance / temp de chargement
- Et donc meilleur ranking dans le SERP
- Versionnage du code
- Permet une customisation beaucoup plus profonde du code
- Avoir un front séparé signifie que le développeur a le contrôle, le client devra payer pour des modifications qu’il aurait peut être pu faire lui même avec wordpress mais cela assure aussi que le site reste optimisé et qu’on ajoute pas une nouvelle couche de plugins et des sliders à chaque nouvelle page créée. Ca apporte en fait de la sécurité et de la stabilité au site.
- Wordpress est utilisé par quelque chose comme 30% des sites du monde, cela signifie que beaucoup de monde s’intéresse à hacker Wordpress. En servant uniquement un tas de fichiers html, il n’est pas impossible d’avoir un quelconque problème de sécurité mais les chances deviennent extrêmement faibles.

**Inconvénients**

- Moins de plugins disponibles
- Moins de thèmes
- Rebuilder le site à chaque modification peut être contraignant et prend plus de temps à chaque fois que du contenu est ajouté. Si un header ou une sidebar “Articles récents” présent sur toutes les pages du site est ajouté, il faudra alors rebuilder toutes les pages.
- Soit on build a chaque fois et c’est lourd, soit on build tous les X jours et le site n’est plus mis à jour aussi fréquemment qu’avant mais cela peut aussi être l’occasion d’adopter de bonnes pratiques, le site buildé uniquement avant de passer en prod permettant de détecter des problèmes avant de builder la version prod.
- Pour un site simple, le développement demandera un peu plus d’expertise que pour Wordpress, ou en tout cas une compétence un peu plus rare et peut donc coûter plus cher.
- Il faut trouver des solutions alternatives aux éléments dynamiques du site original, tel que les formulaires de contact, commentaires sur un article, champ de recherche.

La plupart des développeurs s’étant essayé au JAMstack aiment la philosophie et la simplicité, certains même disent avoir retrouvé la joie dans le développement web !   

Retrouver la joie dans le développement WordPress, avec React, Gatsby & GraphQL : 

> _Il va de soi que si vous travaillez avec un stack fun, vous apprécierez davantage votre travail. La combinaison de WordPress, React, Gatsby et GraphQL est exactement ça - fun. -_ [_Mark Bloomfield_](https://dev.to/markbloomfield/finding-joy-in-wordpress-again-with-react-gatsby-graphql-303j)  

Un site statique s'héberge très simplement. Sur Netlify par exemple qui est très agréable à utiliser, l’interface est bien conçue, il existe de nombreuses fonctionnalités accessibles depuis la web app : plus besoin de SSHer pour éditer des virtualhosts, générer des nouveaux certificats Let's Encrypt upgrader la version de PHP ou autres tâches qui pour un développeur front peuvent parfois paraître ennuyeuses et intéressantes.  

On commence à voir de nombreux tuto sur le sujet tel que ceux de Jason Lengstorf, précédemment responsable des relations développeurs chez Gatsby, aujourd’hui développeur principal expérience ingénieur chez Netlify et auteur des cours [Learn with Jason](https://www.learnwithjason.dev/). Ceux de [Tim Smith](https://www.iamtimsmith.com/blog/how-to-build-a-blog-with-wordpress-and-gatsby-part-1/) ou les tutos de [Netlify](https://www.netlify.com/blog/2020/03/23/migrate-your-wordpress-site-to-the-jamstack/).  

Si vous vous intéressez au SEO, vous n’êtes pas sans savoir que la performance, le temps de chargement est crucial pour bien ranker dans les moteurs de recherche. Passer en statique permet d’optimiser la webperf à moindre frais, sans se battre pendant des heures avec des plugins de caching, Cloudflare et autres optimisation Apache. En fait c’est tellement rapide, que même si il reste des choses à optimiser et que le score Pagespeed ou Yslow reste sous 90%, vous ne vous en soucierez même plus. Le temp de chargement perçu est sans comparaison avec un site Wordpress.

Voici grossièrement la procédure pour convertir son site Wordpress en site statique avec Gatsby :  

1. Installer les plugins Wordpress GraphQl et GraphiQl
2. Créer un repo Git
3. Créer une nouvelle app Gatsby (ex: gatsby new gatsby-wordpress)
4. Installer et configurer gatsby-source-graphql
5. Créer un template de page
6. Design, CSS
7. Ajouter le support des blocks Gutenber (npm install @wordpress/block-library)
8. Récupérer les menus et le recréer sur le site Gatsby
9. Builder et déployer
    1. Au build, Gatsby génère les pages en puisant dans la base de données Wordpress en passant par l’API Wordpress.
10. Configurer les webhooks
    1. Le site alors ensuite rebuildé automatiquement à chaque modification à l’aide de webhooks qui déclenchent un rebuild (sur Netlify par exemple). Grâce à un webhook Github quand le repo Git est mis à jour. Ou par un webhook Wordpress quand le contenu est actualisé (nécessite un plugin WP).

Il nous reste cependant à régler les problèmes sus-cités. Étant statique, le site manque évidemment toutes les fonctionnalités dynamiques telles que des formulaires de contact, des commentaires sur un article de blog ou un système de membre ou de compte utilisateur. Fort heureusement des solutions existent pour palier à ces limitations.

### Internationalisation

[WPGraphQL Polylang Extension](https://github.com/valu-digital/wp-graphql-polylang)

[wp-rest-polylang](https://github.com/maru3l/wp-rest-polylang)

### Advanced Custom fields 

Le plugin Advanced Custom Field (ACF) est très populaires chez les développeurs Wordpress. 

Il permet de créer des champs personnalisés pour tout type de message ou de page, remplacer les valeurs par défaut, créer un nombre illimité de champs pour l'utilisateur, allant des éditeurs WYSIWYG et des sélecteurs de date en passant par les galeries et les champs répétitifs. Grâce à cet outil, on peut vraiment personnaliser le site pour qu'il réponde exactement aux besoins du client.  

ACF ne représente pas vraiment un problème pour notre site statique puisqu’il existe un plugin ([ACF to REST API](https://fr.wordpress.org/plugins/acf-to-rest-api/)) qui, comme vous l’aurez sûrement déjà deviné, expose les données des champs personnalisés à l'api REST afin de pouvoir les utiliser dans un site Gatsby.  

La dernière version de WPGraphQL est désormais compatible avec ACF  

### Menus 

L'une des principales fonctionnalité de WordPress est la possibilité pour les utilisateurs de créer et de mettre à jour facilement les menus de leur site. Hardcoder les menus dans notre nouveau site Gatsby ne serait pas très élégant puisqu’on empêcherait alors les utilisateurs du backend de créer de créer et modifier des menus. Heureusement il existe encore une fois un plugin ([WP API Menus](https://wordpress.org/plugins/wp-api-menus/)) qui crée des routes REST pour les éléments du menu. Veuillez noter : selon la documentation de gatsby-source-wordpress, il doit s'agir de cette version du plugin et non de la plus récente. La version la plus récente ne fonctionnera pas.

### SEO   

**Plugin Gatsby**

[gatsby-plugin-react-helmet](https://www.gatsbyjs.org/packages/gatsby-plugin-react-helmet/)  

**Plugins Wordpress**

[Yoast to REST API - WordPress plugin](https://github.com/maru3l/wp-api-yoast-meta)

[WP REST Yoast Meta](https://wordpress.org/plugins/wp-rest-yoast-meta/)  

### Commentaires

[Disqus](https://disqus.com/) (10$/month)

[Commento](https://commento.io/) (open source)

Facebook Comments

[Staticman](https://staticman.net/). Gère le contenu généré par les utilisateurs et le transforme en fichiers de données qui se trouvent dans un dépôt GitHub avec le reste du contenu.

Netlify forms et Netlify Lambda functions. Tous les commentaires sont postés avec un formulaire et, une fois approuvés, affichés directement sur le site via un build. Aucun code JavaScript n'est nécessaire pour les afficher dans le navigateur. [Tuto sur CSS Tricks](https://css-tricks.com/jamstack-comments/)

Avec Reddit, en créant un subreddit pour le site et un nouveau post Reddit pour chaque article du site et en collant le lien en bas de la page de l’article. D’autres [idées ici](https://www.gatsbyjs.org/docs/adding-comments/).

### Sitemaps

[Gatsby-plugin-sitemap](https://www.gatsbyjs.org/packages/gatsby-plugin-sitemap/)

### Optimisation des images

Gatsby possède de nombreuses fonctionnalités d’optimisation des images qui permettent par exemple de lazy loader des placeholders moins lourd générées au build. Les placeholders générés peuvent être des versions floues des images ou des équivalent redessinées en SVG, magnifique à observer. Plus d'infos [par ici](https://www.freecodecamp.org/news/using-svg-as-placeholders-more-image-loading-techniques-bed1b810ab2c/).

![TracedSVG placeholder Gatsby image optimisation](/media/2020-04-11---wordpress-jamstack-gatsby-en-front-wp-en-cms-headless/TracedSVG-placeholder-Gatsby-image-optimisation.gif)

[gatsby-image](https://www.gatsbyjs.org/docs/using-gatsby-image/)

[gatsby-plugin-sharp](https://www.gatsbyjs.org/packages/gatsby-plugin-sharp/)  

### Search 

[gatsby-plugin-algolia](https://www.gatsbyjs.org/docs/adding-search-with-algolia/)   

### E-commerce

[Gatsby-plugin-snipcart](https://www.gatsbyjs.org/packages/gatsby-plugin-snipcart/)

[Gatsby-source-stripe  
](https://www.gatsbyjs.org/packages/gatsby-source-stripe/)

Le mouvement JAMstack reste pour l'instant limité à des développeurs intéressés par cette nouvelle technologie qui sont vites conquis par cette façon simple et rafraîchissante de faire du dev web mais les avancées sont rapides et prometteuses.

### Jobs

Il y’a même déjà de la demande pour ce genre de projet sur [codeur.com](https://www.codeur.com/projects/186454-gatsby-wordpress-vers-html)

![](/media/2020-04-11---wordpress-jamstack-gatsby-en-front-wp-en-cms-headless/codeur-freelance-job-gatsby-wordpress-300x180.png)

Ainsi que des [développeurs spécialisés Wordpress/Gatsby](https://www.malt.fr/s?q=gatsby+gatsbyjs+wordpress)

## Liste de ressources sur Gatsby et Wordpress

La plupart en anglais

### Tutos

- [Migrate Your WordPress Site to the Jamstack](https://www.netlify.com/blog/2020/03/23/migrate-your-wordpress-site-to-the-jamstack) - Netlify
- [Introduction à la Construction de Sites Web avec Gatsby et WordPress (Rapide et Statique)](https://kinsta.com/fr/blog/gatsby-wordpress/)
- [Créer un blog avec Gatsby et WordPress](https://abdessalam-benharira.me/creer-un-blog-avec-gatsby-et-wordpress/)
- [Use Gatsby & WordPress for Dynamic Sites](https://www.learnwithjason.dev/use-gatsby-wordpress-for-dynamic-sites) - Tuto de Jason Lengstorf et  Zac Gordon sur Youtube 
- [Dynamic Content with Gatsby and WordPress](https://www.youtube.com/watch?v=4vstfmB3wBE) - Scott Bolinger sur Youtube
- [How To Build A Blog with Wordpress and Gatsby.js - Part 1](https://dev.to/iam_timsmith/how-to-build-a-blog-with-wordpress-and-gatsby-js-part-1-4f9e) - Tim Smith
- [Migrate a WordPress Site to the JAMstack](https://www.youtube.com/watch?v=HkLF_vFk_Ek) - Netlify sur Youtube 
- [Porting the Twenty Nineteen WordPress Theme to Gatsby](https://javascriptforwp.com/porting-the-twenty-nineteen-wordpress-theme-to-gatsby/)
- [Headless WordPress + Gatsby + Netlify continuous deployment](https://justinwhall.com/headless-wordpress-gatsby-netlify-continous-deployment/) - Justin W Hall
- [How we’re using wordpress as a headless cms](https://indigotree.co.uk/how-use-wordpress-headless-cms/)

#### Tutos **e-commerce**

- [Gatsby E-commerce Tutorial sur gatsbyjs.org](https://www.gatsbyjs.org/tutorial/ecommerce-tutorial/)
- Antho Welc sur Youtube - [Un E-Commerce avec Gatsby et Snipcart](https://www.youtube.com/watch?v=uFN1cowLM3g)

### Thèmes

- Liste de [thèmes gatsby conçus pour fonctionner avec Wordpress](https://gatsbywpthemes.com/)
- [Gatsby WordPress Publisher Theme](https://github.com/staticfuse/staticfuse)
- [Twenty Nineteen Gatsby Theme](https://twentynineteen-gatsby-theme.netlify.com/)

### Articles intéressants

- [Gatsby and WordPress sur CSS Tricks](https://css-tricks.com/gatsby-and-wordpress/)
- [Voici un avant-goût de la nouvelle intégration de l'éditeur @WordPress #gutenberg avec @gatsbyjs, avec aperçus en direct pendant que vous écrivez. Le développement se fait sur https://github.com/pristas-peter/gatsby-wordpress-gutenberg](https://twitter.com/pristas_peter/status/1224674835453960195)
- [Javascript for Wordpress](https://javascriptforwp.com/) - Zac Gordon
- [Using WordPress as a static site generator](https://peterwm.com/using-wordpress-as-a-static-site-generator/) - Peter Warwick-Mahoney
- [Ockam.Io Is Open Source!](https://www.ockam.io/learn/blog/ockam_website_is_open_source)
- [La popularité croissante du JAMstack augmente le nombre de plugins WordPress pour déployer sur Netlify](https://wptavern.com/jamstacks-growing-popularity-brings-increase-in-wordpress-plugins-for-deploying-to-netlify)

### Tools

- [Gatsby-wordpress-gutenberg](https://github.com/GatsbyWPGutenberg/gatsby-wordpress-gutenberg) 
- [Gatsby + Headless WordPress + Netlify Starter](https://github.com/justinwhall/gatsby-wordpress-netlify-starter) - Justin W Hall

### Exemples 

- [Gatsby + Headless WordPress + Netlify Starter demo](https://gatsby-wordpress-netlify-production.netlify.com/) 
- [Demo du tuto de Jason Lengstorf et  Zac Gordon](https://jamstack-wordpress.netlify.com/)
- [Friesland school](https://twitter.com/carlbradburyjs/status/1246201815659696132) (le site n’est pas encore live, c’est une video de demo sur Twitter)
- [Tinder Swipe Life](https://swipelife.tinder.com/) 
- [Blog de Nate Finch](https://n8finch.com/) 
- [Helenzys Inc](https://helenzys.com/) 
- [Binaria](https://binaria.com/en/)
- [Field Office](https://field-office.ca/)
- [Demo très basique](https://using-wordpress.gatsbyjs.org/)

#### Ecommerce

- [Flamingo](https://www.shopflamingo.com/) 
- [Demo Gatsby e-commerce](https://gatsby-ecommerce-stripe.netlify.com/) 
- [gatsby-starter-ecommerce](https://parmsang.github.io/gatsby-starter-ecommerce/)

### Ressources diverses

- [Une liste régulièrement mise à jour de ressources sur WordPress en tant que CMS headless avec Gatsby comme générateur de site statique (SSG)](https://github.com/henrikwirth/awesome-wordpress-gatsby)
- [Using Gatsby with WordPress](https://www.gatsbyjs.com/guides/wordpress/) - Guide officiel sur Gatsbyjs.org
- [Documentation du plugin gatsby-source-wordpress](https://www.gatsbyjs.org/packages/gatsby-source-wordpress) pour extraire des données à partir de sites WordPress en utilisant l'API REST WP
