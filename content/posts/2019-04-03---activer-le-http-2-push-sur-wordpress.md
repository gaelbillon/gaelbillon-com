---
title: "Activer le HTTP/2 push sur Wordpress"
date: "2019-04-03T10:03:03.000Z"
template: "post"
draft: false
slug: "activer-le-http-2-push-sur-wordpress"
category: "Web performance fr"
tags: 
  - "Français"
  - "Web performance fr"
description: "En plus du gain déjà apporté par le multiplexage avec http/2 on va pouvoir accélérer encore en envoyant des données au client avant même qu'il ne les ait demandé !"
socialImage: "/media/2019-04-03---activer-le-http-2-push-sur-wordpress/http2-push-verification-dans-chrome-outils-developeur-onglet-reseau-colonne-initiator.jpg"
---

Si votre serveur est déjà http2 que ce soit parce que vous avez upgradé Apache à une version >= à la 2.4.17 ou parce que vous passez par un service comme Cloudflare, alors il est possible d'accélérer encore un peu plus votre site en utilisant le push http/2.

Les gains en temps de chargement sont en général assez conséquent. En plus du gain déjà  apporté par le multiplexage des streams avec http/2 qui permet aussi d'éviter l'inlining, le domain sharing et la concaténation, on va pouvoir accélérer encore les choses en envoyant des données au client avant même qu'il ne les ait demandé !

Le gain de performance sera plus particulièrement perceptible sur les connections à faible bande passante ou haute latence.

Si on souhaitait le faire manuellement on ajouterait ces lignes dans le header.php du theme. C'est exactement comme pour le prefetch en HTTP1 les deux sont donc parfaitement compatibles. Si on ajoute le ```rel="preload"```, les données seront pushées si http/2 est actif et preloadées si on est en http/1.x

```php
<?php
  header("Link: </css/vendor.css>; rel=preload; as=style", false);
  header("Link: </css/styles.css>; rel=preload; as=style", false);
  header("Link: </images/site/logo--red.svg>; rel=preload; as=image", false);
?>
```

Il faudrait ensuite faire en sorte que les données déjà mises en cache par l'utilisateur ne soient pas inutilement repoussées à chaque fois.

Ces fonctionnalités ne sont pas encore supportées directement par Wordpress mais il existe bien sûr un plugin pour ça :

[![http2 server push plugin wordpress](/media/2019-04-03---activer-le-http-2-push-sur-wordpress/http2-server-push-plugin-wordpress.jpg)](https://fr.wordpress.org/plugins/http2-server-push/)

C'est extrêmement simple, il suffit de l'installer puis de l'activer, aucune configuration. Par contre il n'a pas l'air d'être compatible avec Wordpress 5 pour l'instant (2019\_04\_02). 4.9.10 max.

On peut ensuite vérifier que les données soient bien pushées à l'aide de ce site : [https://http2-push.io/](https://http2-push.io/)

Ou tout simplement dans l'inspecteur de Chrome, Firefox ou Safari dans l'onglet network puis dans la colonne Initiator :

![http2 push vérification dans chrome outils dévelopeur onglet réseau colonne initiator](/media/2019-04-03---activer-le-http-2-push-sur-wordpress/http2-push-vérification-dans-chrome-outils-dévelopeur-onglet-réseau-colonne-initiator.jpg)
