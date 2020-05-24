---
title: "Comment optimiser le temps de chargement d'un site web"
date: "2018-09-14T16:33:26.000Z"
template: "post"
draft: false
slug: "comment-optimiser-le-temps-de-chargement-dun-site-web"
category: "Web performance fr"
tags: 
  - "Français"
  - "Web performance fr"
description: "Le temps de chargement est un facteur détérminant pour l'expérience utilisateur. Cet article détail pourquoi accélerer un site web et comment y parvenir."
socialImage: "/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/analyse-du-temps-de-chargement-dun-site-web-avec-outils-developpeurs-de-Chrome-2.png"
---

![Analyse du temps de chargement d’un site web avec outils developpeurs de Chrome](/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/analyse-du-temps-de-chargement-dun-site-web-avec-outils-developpeurs-de-Chrome-large.png)

La vitesse de chargement d'un site internet est devenu un élément clef du référencement depuis la mise à jour du moteur de recherche de Google de juillet 2018. Ca faisait un moment que Google insistait sur ce point et que les performance des sites étaient prises en compte mais cette mise à jour de juillet 2018, souvent appelée "The Speed Update" officialise encore un peu plus l'importance du temps de chargement pour le positionnement dans les résultat de recherche. Cette mise à jour se concentre principalement sur le temp de chargement sur mobile. Mais au delà du simple référencement, des études menées par des entreprises comme Walmart et Amazon montrent qu'un utilisateur abandonne très vite un site qui met trop de temps à se charger. Voici quelques exemples :

**Impact sur les recettes / ventes**

- 1 seconde de retard de chargement coûterait chaque année à Amazon 1,6 milliard.
- Si un site de commerce électronique génère 100 000 dollars par jour, un retard d'une page par seconde pourrait lui coûter 2,5 millions de dollars en pertes de ventes chaque année.

**Impact sur l'attitude et le comportement des utilisateurs**

- 47% s'attendent à ce qu'une page se charge en 2 secondes ou moins.
- 40% des utilisateurs abandonneront une page web si le chargement prend plus de 3 secondes.
- 79% des acheteurs insatisfaits des performances du site sont moins susceptibles d'acheter à nouveau sur le même site.
- 52% des acheteurs en ligne déclarent que le chargement rapide des pages est important pour la fidélité de leur site.

Plus de chiffres et de sources par ici : [https://medium.com/@vikigreen/impact-of-slow-page-load-time-on-website-performance-40d5c9ce568a](https://medium.com/@vikigreen/impact-of-slow-page-load-time-on-website-performance-40d5c9ce568a)

### Métrologie

Puisqu'on ne peut pas améliorer ce qu'on ne peut mesurer, nous allons avoir besoin d'outils. Fort heureusement il en existe plusieurs très bien fait qui indiquent en détail ce qui ralentit le temps de chargement mais aussi comment y remédier.

- [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) (par Google)
- [Yslow](http://yslow.org) (par Yahoo) une extension pour navigateurs
- [GTmetrix](https://gtmetrix.com), qui utilise à la fois PageSpeed Insights et Yslow en même temps
- [Pingdom](https://tools.pingdom.com)
- [WebPageTest](http://www.webpagetest.org)
- Les outils de développement de navigateurs Chrome, Firefox et Safari peuvent également apporter beaucoup d'information sur les performances d'un site.

Il en existe bien d'autres mais ceux sus-cités sont largement suffisants. Attention toutefois avec les outils de mesure, il est tout à fait possible d'obtenir un score  de 100% sur PageSpeed et Yslow pour une page qui met 15 secondes à charger.

![Exemple de rapport de performance GTmetrix](/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/Exemple-de-rapport-de-performance-GTmetrix-1.png)
<figcaption>Exemple de rapport de performance GTmetrix</figcaption>

#### Que mesure t on ?

**Le TTFB (Time To First Byte)** C'est le temps que met le serveur à envoyer la première réponse, le premier bit de données, on pourrait le comparer au ping pour les jeux vidéos. Il peut être amélioré de plusieurs façons :

- Changer d'hébergement pour un plus performant. C'est ce qui aura le plus gros impact sur l'amélioration du TTFB.
- Dans une moindre mesure, utiliser un CDN peut également réduire le TTFB parce qu'il route l'utilisateur vers le serveur le proche géographiquement de l'utilisateur.

**Le TTI (Time To Interactive)** C'est le moment à partir duquel la page devient utilisable par le visiteur. Quand une page à atteinte le TTI, cela signifie :

- Qu'elle affiche des informations utiles pour l'utilisateur,
- Que les "event handlers" sont actif pour la plupart des elements de la page.
- La page répond aux interactions de l'utilisateur en moins de 50 millisecondes.

#### Réduire le poids des images

Pour réduire le poids des images on peut modifier : leurs tailles, leurs résolutions et leurs compression. Il est bien sur possible de le faire manuellement avec photoshop, GIMP, paint ou n'importe quel autre logiciel de retouche d'image. Il faudra ensuite ré-uploader les images. Si votre site contient déjà des centaines ou des milliers d'images, ça risque d'être un peu fastidieux. Heureusement, il existe des outils pour automatiser cette tâche Sur macOS il existe une app gratuite, ImageOptim [https://imageoptim.com](https://imageoptim.com) qui est extrêmement simple d'utilisation, il suffit de glisser/déposer l'image à optimiser sur la fenêtre d'ImageOptim qui va automatiquement créer une nouvelle version mieux compressée. Mieux compressée signifiant : le meilleur ratio poids/qualité qui donnera une image pas trop lourde mais pas non plus trop dégradée par la compression.

Si votre site utilise Wordpress, alors c'est encore plus simple, il existe des plugins qui font tout le travail à notre place. Plus d'infos sur les plugins Wordpress de compression d'images dans la section : [Plugins Wordpress](#plugins-wordpress)

#### Diminuer le nombre de requêtes

**Pourquoi ?** Parce que le nombre de requêtes concurrentes (qui peuvent être effectuées en même temps par un naviguateur) est limité, voici les limites pour chaque navigateurs au 6 avril 2018

| Version                       | Maximum connections |
| ----------------------------- | ------------------- |
| Internet Explorer® 7.0        | 2                   |
| Internet Explorer 8.0 and 9.0 | 6                   |
| Internet Explorer 10.0        | 8                   |
| Internet Explorer 11.0        | 13                  |
| Firefox®                      | 6                   |
| Chrome™                       | 6                   |
| Safari®                       | 6                   |
| Opera®                        | 6                   |
| iOS®                          | 6                   |
| Android™                      | 6                   |

Cette limitation qui peut sembler étrange est en fait indispensable, elle permet de :

- Améliorer le temps de réponse et diminuer la congestion
- Ne pas dégrader les performances du naviguateur
- Eviter au client d'être considéré par le serveur come un attaquant DoS

La limite du nombre de requêtes concurrentes est défini dans les specifications HTTP RFC2616 : [https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)

Ce qui signifie que si un site charge plus de de fichiers que le nombre simultané autorisé par le navigateur, alors il faudra attendre que les premiers fichiers soient téléchargés avant de pouvoir commencer à charger les suivants.

Il existe plusieurs façon de diminuer le nombre de requêtes :

##### Combiner les fichiers

Les différents fichiers javascript et CSS par exemple peuvent être combinés ensemble afin de ne former plus qu'un seul gros fichier javascript et un autre gros fichier CSS plut que de faire appel à 10 fichiers javascript et 7 fichiers CSS

Sur Wordpress il est possible d'tiliser une extension pour combiner automatiquement les fichiers (voir section plugins Wordpress)

##### Utiliser des sprites CSS

De la meme façon qu'on peut combiner le javascript et le CSS, on peut combiner les images grâce au sprites CSS. La méthode est simple, on crée une grosse image contenant pleins de petites images qui sont placées cote a cote, puis grace au positionnement CSS on va choisir de n'afficher qu'une petite partie de la grosse image, cette partie correspondra exactement à une petite image.

##### Diminuer le nombre d'outils tierces (Facebook, Analytics, etc)

Tout les sites externes auquels un site fait appel vont également augmenter le nobre de requetes et de fichiers à chargé. Parmi les plus utilisés : Facebook qui est souvent utilisé pour gérer les commentaires et la publicité. Google Analytics pour les statistiques. Disqus pour la gestion des commentaires. Outils tierce affichant des popup d'inscription a des newsletter. Etc, il en existe des milliers.

#### Utiliser moins d'images

Ca paraît tout bête mais c'est un des meilleurs moyen de réduire le poids d'une page. Certaines images qui ont été utilisées pour illustrer une page par exemple ne sont peut etre pas tres utiles. Par exemple, une "stock photo" d'une banalité grotesque en header d'un article juste pour avoir une image ou des photos trop nombreuses et trop similaires qui n'apportent pas grand chose à la compréhension

#### Utiliser le bon format pour les images

Selon ce que représente une image, on utilisera différents formats pour l'enregistrer. Par exemple une photo comme celle ci-dessous sera mieux compressé en JPEG (compression lossy, avec perte de qualité)

![](/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/chien-jpg.jpg)

Alors qu'un dessin simple avec peu de couleurs comme celui ci

![](/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/chien-png.png)

pourra être enregistré en PNG (compression lossless, sans perte) tout étant plus petit que si on l'enregistrait en JPEG. A l'inverse, la photo, si on l'enregistrait en PNG serait enregistrée, sans perte, oui mais elle serait beaucoup plus lourde que son equivalent JPG sur lequel on ne remarquera même pas la compression.

#### Minifier

Les fichiers CSS et javascript peuvent être considérablement réduits (on appel ça "minifié") tout en procurant exactement les mêmes fonctionnalités que dans leurs version non minifiées. Pour cela, c'est très simple, un algorithme va supprimer les espaces, les commentaires (partie du code écrite par un développer pour indiquer comment fonctionne le code), réduire le nom des variables. Toutes ces modifications n'altèrent pas l'execution du code mais seulement sa compréhension par un humain, l'ordinateur le comprendra toujours de la même façon.

Ainsi, le code javascript suivant :
`function sum(num1, num2) { return num1 + num2; }`

Sera minifié comme suit :
`function sum(A,B){return A+B;}`

Et le code CSS suivant :
`span { color: DeepSkyBlue; }`

Comme ceci :
`span{color:#00BFFF;}`

Pour minifier le CSS et le Javascript, il existe plusieurs solutions :

- [YUI compressor](http://yui.github.io/yuicompressor/)  Un utilitaire Java qui permet de minifier le CSS et le Javascript
- [Google Closure Compiler](https://developers.google.com/closure/compiler/) Pour minifier le Javascript seulement, il existe sous la forme d'une application Java, d'une application web ou par une API
- Il existe aussi de nombreux plugins Wordpress qui peuvent se charger de la minification (plus d'infos dans la section Plugins Wordpress). Certains thèmes optimisées pour la performance proposent désormais de minifier les fichiers CSS et Javascript directement par les options de performance du thème.

#### La compression Gzip

La compression Gzip fonctionne de la même façon que pour les fichiers zip que nous utilisons sur nos ordinateurs. Un algorithme utilise plusieurs méthodes pour diminuer la taille d'un fichier sans en perdre les informations. Il n'est pas rare de voir la taille de certains fichiers diminuer de plus de 80% grâce à la compression gzip. La seule contrepartie étant le temps nécessaire côté client pour que le navigateur dézip le fichier mais pour les ordinateurs modernes c'est tellement rapide que c'est insignifiant. La compression Gzip est donc à utiliser sans modération. Le seul pré-requis étant que le client et le serveur acceptent la compression gzip, ce qui ne devrait poser aucun problème puisque la majorité des navigateurs et la majorité des serveurs HTTP (ex : Apache) savent très bien manipuler la compression gzip. Il est possible de Gzipper les fichiers : Javascript, CSS et HTML.

Pour activer la compression Gzip sur un serveur Apache, il faut ajouter ces lignes au fichier apache2.conf ou .htacces :

```apache
<IfModule mod\_deflate.c>
    # compress html, css, javascript, text, xml and fonts
    AddOutputFilterByType DEFLATE application/javascript
    AddOutputFilterByType DEFLATE application/rss+xml
    AddOutputFilterByType DEFLATE application/x-font
    AddOutputFilterByType DEFLATE application/x-font-opentype
    AddOutputFilterByType DEFLATE application/x-font-otf
    AddOutputFilterByType DEFLATE application/x-font-truetype
    AddOutputFilterByType DEFLATE application/x-font-ttf
    AddOutputFilterByType DEFLATE application/x-javascript
    AddOutputFilterByType DEFLATE application/xhtml+xml
    AddOutputFilterByType DEFLATE application/xml
    AddOutputFilterByType DEFLATE font/opentype
    AddOutputFilterByType DEFLATE font/otf
    AddOutputFilterByType DEFLATE font/ttf
    AddOutputFilterByType DEFLATE image/svg+xml
    AddOutputFilterByType DEFLATE image/x-icon
    AddOutputFilterByType DEFLATE text/css
    AddOutputFilterByType DEFLATE text/html
    AddOutputFilterByType DEFLATE text/javascript
    AddOutputFilterByType DEFLATE text/plain
    AddOutputFilterByType DEFLATE text/xml

    # you can also compress by file type/extension:
    <files *.html>
        SetOutputFilter DEFLATE
    </files>
</IfModule>
```

Pour Nginx, la compression Gzip devrait être activée par défaut, si ce n'est pas le cas, il faut editer le fichier nginx.conf et y ajouter les lignes suivantes :

```apache
##
# Gzip Settings
##

gzip on;
gzip_disable "msie6";

gzip_vary on;
gzip_proxied any;
gzip_comp_level 6;
gzip_buffers 16 8k;
gzip_http_version 1.1;
gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;
```

Et pour vérifier que la compression Gzip est bien active, il suffit de se rendre sur : [https://checkgzipcompression.com](https://checkgzipcompression.com) Il est aussi possible de le vérifier avec les outils de développement des navigateurs ou avec la commande curl.

#### La mise en cache

La meilleur façon de diminuer le temps de téléchargement d'une ressource c'est de ne pas la télécharger du tout. Bien sûr il faudra bien la télécharger au moins la première fois sinon il manquerait des éléments à la page chargée mais lors du re-chargement de la même page ou du chargement d'une autre page du même site, il est très souvent possible de réutiliser une ressource (une image par exemple) qui n'est pas modifiée fréquemment sur le serveur. C'est ce que l'on appel la mise en cache, le navigateur peut stocker localement certaines données afin de ne pas avoir à les re-télécharger par la suite. Pour ce faire, c'est très simple, lorsque le navigateur demande une ressource au serveur, le serveur lui renvoi la ressource à laquelle sont associés des header (Plus d'infos sur les headers par ici : [https://developer.mozilla.org/fr/docs/Web/HTTP/Headers](https://developer.mozilla.org/fr/docs/Web/HTTP/Headers) ). 
1. Un header `Cache-Control: max-age=360`, qui va indiquer au navigateur pendant combien de temps il peut réutiliser la ressource sans avoir besoin de la re-télécharger Tant que ce max-age (ici 360 secondes) n'est pas dépassé, le navigateur ne téléchargera plus la ressource depuis le serveur. 
2. Un header `ETag: "24rtu89/d556u4` qui ne veut pas dire grand chose mais il à la particularité d'être modifié dès que la ressource demandé à été modifié sur le serveur. Donc même si le max-age est dépassé, le navigateur va redemander la ressource au serveur mais en précisant qu'il a toujours en cache la ressource avec le header Etag `24rtu89/d556u4`. Si la ressource n'a pas changé, autrement dis, si le ETag est le même, le serveur répondra simplement avec un `304 Not Modified` qui indiquera au navigateur qu'il peut continuer à utiliser la même ressource. Il y'a toujours une requête mais on n'économise le temps du téléchargement

Plus d'infos sur la mise en cache HTTP par ici : [https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=fr](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=fr)

#### Plugins Wordpress

##### Plugins de cache

**W3 Total Cache (W3TC)** C'est le plus ancien et l'un des plus poussé. Très efficace mais il nécéssite d'avoir quelques connaissances afin de le configurer correctement, ça peut vite prendre pas mal de temps.

**Simple cache** Le plus simple à configurer, pas de réglages à part activé/désactivé.

**WP-Rocket** Très simple à configurer. C'est le seul de cette liste qui est payant mais il vaut vraiment le coup si vous souhaitez améliorer les performances de votre site rapidement sans passer des heures à le configurer. Excellent rapport qualité/facilité/prix.

D'autres plugins permettent de générer des fichiers html statiques à partir d'un site Wordpress dynamique

- **WP Fastest Cache**
- **WP Super Cache**
- **Cache Enabler**

Quelque soit le plugins que vous choisissiez, il vaut mieux vérifier la compatibilité avec les autres options et plugins de Wordpress (multisite, WPML, etc, ). Certains plugins nécessitent d'être désactivés pour effectuer les mises à jours de Wordpress.

##### Plugins de Lazy loading

Le lazy loading consiste à ne charger que le contenu visible d'une page dans un premier temps, puis de charger le reste quand l'utilisateur scroll vers le bas. Cette technique n'est généralement appliquée qu'aux images.

Il existe plusieurs façon pour ajouter du lazy loading :

- Il est peut être déjà inclus dans votre thème, il faut activer l'ption quelque part
- Le [module pagespeed](https://www.modpagespeed.com/doc/filter-lazyload-images) pour apache et Nginx peut s'en charger
- Ou par le biais de plugins Wordpress
    - [Rocket Lazy Load](https://fr.wordpress.org/plugins/rocket-lazy-load/)
    - [BJ Lazy Load](https://fr.wordpress.org/plugins/bj-lazy-load/)
    - WP Rocket

##### Plugins d'optimisation d'images

Deux plugins permettent de réduire très simplement le poids des images. Il peuvent optimiser les images déjà présentes dans les "Médias" de Wordpress mais peuvent aussi intervenir à chaque futur upload d'image.

- WP Smush
- EWWW Image Optimizer

Plus d'infos sur l'optimisation des images dans la section ["Réduire le poids des images"](#reduire-le-poids-des-images)

#### Sites web statiques

C'est un phénomène qui (re-)prend de l'ampleur depuis quelque temps. Il s'agit tout simplement d'un site composé de pages qui sont envoyées par le serveur telles qu'elles y sont stockés. En général il s'agit de fichiers HTML. Ces fichiers, contrairement à ceux générés par un site dynamique qui utiliserait PHP et une base de données, sont les mêmes pour tous les utilisateurs. Ils ne sont pas modifiés en fonction du temps, de la connexion de l'utilisateur à un compte sur le site, du navigateur, etc). C'est en quelque sorte un retour aux sources du web à l'époque où tout était "pur HTML"

Ce type de site offre plusieurs avantages :

- Securité accrue grâce à l'absence de base de données
- Excellentes performances, que ce soit au niveau du temps de chargement ou de la charge CPU et mémoire du serveur
- Plus fiable et plus simple à maintenir parce que moins de "pièces en mouvement", pas de PHP, pas de base de données.
- Hébèrgement très économique, voir gratuit sur Github ou Amazon S3

Mais il ont aussi des inconvenients :

- Impossibilité d'afficher du contenu dynamic évidemment
- Pas de formulaires de contact ou un systèmes de commentaires sur un article bien qu'il existe des "workarounds" comme l'utilisation de services externes tel que Disqus (link) pour les commentaires.

Les [sites statiques](/jamstack-sites-statiques-et-cms-headless-le-renouveau-du-web/) ne sont plus si statiques que ça puisqu'il existe maintenant des systèmes de gestion de contenu (CMS), à l'instar de Wordpress, qui permettent de modifier un site statique à l'aide d'une interface intuitive. Après une modification, les fichiers HTML sont re-générés, une seul fois et non à la volée, à chaque requête, comme dans le cas d'un site dynamique.

#### Le serveur : Apache / Nginx

Le choix du serveur HTTP peux aussi avoir un impact sur la performance d'un site internet. Apache est le numéro 1 des serveur HTTP, c'est le plus puissant et le plus répandu. Nginx (prononcer hainejaïllenex (fr) ou Engine X (us)) s'est hissé en quelques années à la place de numéro 2 et est réputé plus rapide. Mais tout dépend de l'utilisation qu'on en fait. Quelque soit le serveur HTTTP choisi, il faudra le configurer correctement. En effet on ne configurera pas de la même façon un serveur qui reçoit 100 requêtes par seconde qu'un autre qui reçoit 10 requêtes par jour. Il est aussi possible d'utiliser les deux en même temps avec Nginx en reverse proxy. Ce faisant, on profite de la puissance d'apache alliée à la rapidité d'Nginx

#### Cloudflare

Cloudflare est un service très simple à configurer et qui peut apporter de nombreuses améliorations de performance au niveau de la mise en cache et du CDN Ainsi que plusieurs outils maison comme :

- Chargement asynchrone de JavaScript avec Rocket Loader™
- Optimisation de réseau d’origine avec Railgun™
- Optimisations d’images avec Polish™
- Optimisations mobiles avec Mirage™

Pour l'utiliser, il suffit de modifier les nameservers de la zone DNS, une opération qui prend 2 minutes à réaliser. En plus de l'amélioration des performances, Cloudflare améliore la securité du site contre les attaques DDoS par exemple.

#### Diminuer la quantité de javascript

On a parfois tendance à charger plus de javascript que nécessaire, charger tout une bibliotheque pour n'en utiliser que queqlues fonctions. Il existe des moyens assez simple pour diminuer la quantité de javascript à charger. jQuery par exemple porpose un "Download builder" qui permet de choisir uniquement les fonctionnalités qui nous intéressent afin de réduire la taille du fichier jquery.js.

#### Différer le chargement du Javascript

Le javascript peut bloquer l'affichage d'une page. En effet, le code javascript ayant la capacité de modifier le contenu d'une page, par défaut, le navigateur attend donc que le javascript soit chargé afin de savoir si il doit modifier le rendu HTML. Il est cependant possible d'indiquer au navigateur qu'il n'a pas besoin d'attendre le chargement du Javascript avant de poursuivre l'analyse HTML et qu'il peut donc charger et executer le javascript à la fin, c'est à ça que sert l'attribut defer , il dit au navigateur : charge et affiche le HTML puis, quand tu auras fini, occupe to du javascript. La plupart du temps cela ne pose pas de problème excepté l'affichage de la page qui peut être légèrement modifié par le javascript après son chargement (insertion d'images, reflow du texte, etc). Mais si le code javascript à besoin d'interagir avec l'utilisateur avant de pouvoir afficher afficher la page, par le biais d'une alert box par exemple, les conséquences seraient plus ennuyeuses. Avec defer, l'exécution du javascript est simplement repoussée à la fin de l'analyse HTML, c'est l'équivalent de mettre le code javascript juste avant la fermeture du </body>

L'attribut async  permet lui de dire au navigateur : charge tous les fichiers javascript nécessaire quand ça t'arrange, peut importe l'ordre, premier téléchargé, premier exécuté. C'est la méthode qui permettra le chargement le plus rapide de la page, celui qui permettra d'arriver le plus rapidement possible à l'évènement DOMContentLoaded. Mais encore fois il faut être prudent parce que certains fichiers javascript peuvent avoir besoin que d'autres fichiers soient chargés (jQuery par exemple) avant de pouvoir être exécutés. Si les fichiers nécessaires n'ont pas encore été chargés, le javascript ne sera pas exécuté ou alors exécuté avec des erreurs.

C'est une méthode qui peut grandement diminuer le temps d'affichage d'une page mais il faut être prudent car si la page à absolument besoin du Javascript pour s'afficher correctement

#### Eliminer le CSS bloquant le rendu

Avant d'afficher une page, le navigateur va d'abord charger tous les fichiers CSS qu'on lui à demandé de charger. Voici quelques règles simples pour ne pas rallonger le temps de chargement des fichiers CSS

1. **Ne pas utiliser @import** La règle @import permet d'inclure dans un fichier CSS le code d'un autre fichier CSS. Mais cette @import augmente le temps de chargement du CSS. Que ce soit le @import utilisé dans le fichier CSS ou la @import utilisé dans le HTML comme ceci : `<style>@import url('a.css');</style>` En ce qui concerne les @import situé dans les fichiers CSS, il est préférable d'inclure directement le code importé, si ce n'est pas possible, il faut indiquer dans le HTML de charger plusieurs fichiers CSS. Plus d'informations et de tests de rapidité sur l'utilisation d'@import ici: [https://www.stevesouders.com/blog/2009/04/09/dont-use-import/](https://www.stevesouders.com/blog/2009/04/09/dont-use-import/)
2. **Indiquer correctement le CSS conditionnel** Le CSS conditionnel permet de charger différents fichiers CSS en fonction de l'usage ou de la taille de l'écran par exemple.

Fichier CSS chargé dans tous les cas

`<link href="style.css" rel="stylesheet"`

Chargement conditionnel, le fichier CSS n'est chargé que lorsque l'on souhaite imprimer la page, il n'est donc pas nécéssaire de charger à tous les coups

`<link href="print.css" rel="stylesheet" media="print"`

Chargement conditionnel, le fichier CSS n'est chargé que si l'écran fait plus de 40em de large

`<link href="autre.css" rel="stylesheet" media="(min-width: 40em)">`

Indiquer correctement au navigateur à quoi sert chaque fichier CSS va permettre de ne télécharger que le strict minimum et donc de diminuer le temps de chargement de la page.

3\. **Combiner les fichiers CSS** (voir la section "[Combiner les fichiers"](#combiner-les-fichiers))

4\. **Inliner le CSS**

Il s'agit simplement de placer le code CSS dans le code HTML à l'aide de la balise `<style` plutot que dans un fichier séparé. Cela permet d'économiser une requête et de télécharger d'autres ressources à la place.

#### Retirer le CSS inutile

Il s'agit de code CSS qui n'est utilisé par aucun element du site.

Par exemple le code suivant :

`optgroup:empty{display:none}`

N'a pas de raison d'être si il n'y aucun element HTML `<optgroup>`  utilisé sur le site.

Ce code prend de la place dans les fichiers CSS, 28 bytes pour le code ci-dessus, pas grand chose mais mis bout à bout ça peut représenter quelques kilobytes.

Ce code inutilisé provient la pupart du temps d'une bibliotheque CSS comme Bootstrap mais il peut très bien s'agir de code écrit spécifiquement il y'a longtemps et qui n'est aujourd'hui plus utilisé.

Pour trouver les sélecteurs CSS inutilisés il existe différents outils : des extension de navigateurs, des application en ligne ([https://uncss-online.com](https://uncss-online.com)), les outils de développeurs de Chrome ou bien des plugins pour les task runners/module bundlers tel que Webpack, Grunt ou Gulp ([https://github.com/FullHuman/purgecss](https://github.com/FullHuman/purgecss)).

Certaines bibliotheques CSS comme bootstrap proposent un download builder qui permet de ne sélectionner que les elements qui nous intéressent et d'ainsi réduire la taille d'un fichier css : [https://getbootstrap.com/docs/3.3/customize/](https://getbootstrap.com/docs/3.3/customize/)

#### Utiliser un theme plus léger

Certains themes pour les CMS (Wordpress, Prestashop, etc) sont optimisés par leurs développeurs pour accélérer le temps de chargement. Tant qu'à faire, au moment du choix du theme, autant opter pour ce genre de theme. Pour trouver un theme optimisé, il faut regarder la description sur les sites de themes comme ThemeForest. Certains en on même fait leur argument de vente :

![](/media/2018-09-14---comment-optimiser-le-temps-de-chargement-dun-site-web/Capture-d-ecran-2018-09-06-a-19.45.13-650px.png)

#### SSL

La mise en place d'un certificat SSL permettant de sécuriser un site augmente le temps de chargement, cela est du au "TLS handshake" initial qui permet au client et au serveur de s'identifier lors du premier contact.

Cependant étant donné les récentes evolutions, ce paramètre devient de plus en plus insignifiant. L'augmentation du temps de chargement en https sera de moins de 10ms voir même nulle et étant donnée l'amélioration considérable de la sécurité et le prix d'un certificat SSL aujourd'hui (gratuit), il serait absurde de s'en passer.

Plus d'informations à ce sujet et des tests avec/sans SSL : [https://www.keycdn.com/blog/https-performance-overhead/](https://www.keycdn.com/blog/https-performance-overhead/)

#### Mettre à jour PHP

PHP est un language en constante évolution et chaque nouvelle version apporte son lot d'améliorations qui peuvent parfois avoir un impact important sur le temps de génération d'une page. Cela est rendu possible grâce à différentes choses, voici par exemple les améliorations de la version de 7 de PHP :

- Amélioration du Zend Engine, l'interpréteur de PHP
- Réduction de l'utilisation de la mémoire
- Meilleur gestion du cache opcode

Tests comparatifs PHP 5.6 vs PHP 7 ici : [https://www.savvii.com/blog/wordpress-page-load-times-php7-vs-php-56/](https://www.savvii.com/blog/wordpress-page-load-times-php7-vs-php-56/)

#### HTTP/2 et SPDY

La spécification du protocol HTTP/2 a été publiée en mai 2015 et est supporté par la plupart des naviquateurs depuis fin 2015. C'est une mise à jour majeure du protocol HTTP/1.1 qui date de 1997.

Utiliser HTTP/2 peut améliorer de manière signiifcative la vitesse de chargement d'un site. Voici les 4 points clefs qui permettent au protocol HTTP/2 d'améliorer les performances :

- Multiplexing : permet d'atablir plusieurs flux sur une seule connexion TCP
- Priorisation : permet de en priorité certaines ressources
- Server push : le serveur peut désormais envoyer des ressources avant même qu'elles aient été demandées par le client
- Compression des En-têtes HTTP
