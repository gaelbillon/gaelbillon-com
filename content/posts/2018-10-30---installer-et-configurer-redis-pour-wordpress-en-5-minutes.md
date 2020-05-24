---
title: "Installer et configurer Redis pour Wordpress en 5 minutes"
date: "2018-10-30T19:44:40.000Z"
template: "post"
draft: false
slug: "installer-et-configurer-redis-pour-wordpress-en-5-minutes"
category: "Web performance fr"
tags: 
  - "Français"
  - "optimisation"
  - "performance"
  - "temps de chargement"
  - "vitesse"
  - "web performance"
  - "Web performance fr"
description: "Redis est une store clé-valeur qui permet de garder en mémoire les requêtes MySQL. C'est un système de mise en cache très simple à mettre en oeuvre."
socialImage: "/media/2018-10-30---installer-et-configurer-redis-pour-wordpress-en-5-minutes/wordpress-redis.png"
---



![Configuration Redis et Wordpress avec le plugin Redis Object Cache](/media/2018-10-30---installer-et-configurer-redis-pour-wordpress-en-5-minutes/wordpress-redis-medium.png)

## Introduction

[Redis](https://redis.io) est une base de données clé-valeur open-source développé par Salvatore Sanfilippo qui est sponsorisé par VMWare. Il est utilisé par des sites tels que Twitter, GitHub, Pinterest, Snapchat, Craigslist, Digg, StackOverflow et Flickr. Redis permet de garder en mémoire les requêtes mySQL. C'est un système de mise en cache extrêmement simple à mettre en oeuvre et qui peut apporter d'importants gains de performance. Bien que tous les sites soient différents et ne réagiront pas de la même façon, il n'est ainsi pas rare de voir le temps de chargement d'une page divisé par deux grâce à l'utilisation de Redis.

Memcached est un équivalent de Redis. Si vous vous demandez lequel utiliser, il vaut mieux opter pour Redis. Pour plus d'infos, voir cette [réponse extrêmement détaillée sur StackOverflow](https://stackoverflow.com/a/11257333).

## Comment ça marche ?

A chaque fois qu'une page est chargée sur votre site lors d'une visite, une requête vers la base de données MySQL est effectuée. Redis retient ces requêtes, on dit qu'il les met en cache. Par la suite, si un autre visiteur charge la même page, la requête vers la base de données étant la même, le résultat de la requête est donné par Redis directement depuis la mémoire sans interroger la base de données. Le temps de chargement s'en trouve considérablement réduit et les ressources du serveurs sont moins solicitées. Si une valeur est mise à jour dans la base de données (un nouvel article est crée par exemple), la valeur pour cette requête est invalidée puis mise à jour.



> Avant d'installer Redis, il est recommandé de backuper Wordrpess ou d'essayer d'abord sur un serveur de test. 



## Installer Redis

Rien de plus simple, sur Ubuntu :

`sudo apt-get install redis-server php5-redis`

Si le paquet et introuvable comme indiqué par ces lignes :

```
E: Unable to locate package redis-server
E: Unable to locate package php5-redis
```

Il faut updater comme suis : `apt-get update`

Si ça ne fonctionne toujours pas, il faut ajouter le repository universe :`sudo add-apt-repository univers`

## Configurer Redis

Redis peut être utilisé comme cache mais aussi en tant que base de données NoSQL. Ici nous souhaitons l'utiliser en tant que cache et allons donc procéder à une modification de sa configuration.

`sudo nano /etc/redis/redis.conf`

On ajoute ces deux lignes à la fin du fichier

```apache
maxmemory 256mb
maxmemory-policy allkeys-lru
```

On peut ensuite vérifier que Redis fonctione en tappan `redis-cli` puis `ping`  qui doit normalement répondre `pong`

```bash
user@vps123456:~$ redis-cli
127.0.0.1:6379> ping
PONG
127.0.0.1:6379>
```

Puis taper exit pour quitter redis-cli

## Editer wp-config.php

Il faut ensuite ajouter une ligne dans le fichier `wp-config.php` qui se trouve à la racine du site Wordpress. Dans `/var/www/monsite_ par exemple`.

`nano /var/www/monsite/wp-config.php`

Après `define('NONCE_SALT', 'xxxxxxxxxxxx')` on ajoute cette ligne `define('WP_CACHE_KEY_SALT', 'monsite.com')`

Il est possible de remplacer `monsite.com` par n'importe quel texte mais mettre l'URL du site est une pratique courante. L'important étant d'avoir une `CACHE_KEY` différente pour chaque site, au cas ou vous auriez plusieurs Wordpress sur le même serveur.

Il faut également ajouter cette ligne `define('WP_CACHE', true)` si elle n'est pas déjà présente dans `wp-config.php`, ce qui est fort probable si un plugin de cache est déjà installé. Il l'aura alors lui-même écrite dans `wp-config.php`.

On va ensuite relancer Redis et Apache :

```bash
sudo service redis-server restart
sudo service apache2 restart
```

## Installer le plugin Redis pour Wordpress

Il faut ensuite installer un plugin qui va permettre à Wordpress d'utiliser Redis. Pas la peine de passer trop de temps à chercher, le choix se porte sur le plus populaire, il y'en à d'autres mais celui fonctionne très bien -> [Redis Object Cache](https://wordpress.org/plugins/redis-cache/).

Après l'installation il n'y a plus qu'à activer le plugin puis se rendre dans ses réglages et cliquer sur "Enable Object Cache". Voici à quoi ressemble l'écran de configuration du plugin après l'activation du Object Cache :

![Configuration Redis et Wordpress avec le plugin Redis Object Cache](/media/2018-10-30---installer-et-configurer-redis-pour-wordpress-en-5-minutes/Configuration-Redis-et-WordPress-avec-le-plugin-Redis-Object-Cache.png)

## Vérifier que l'installation fonctionne

Pour être sur que les requêtes sont bien mises en cache, on va utiliser cette commande `redis-cli monitor` et charger une page du site ne la visitant depuis un navigateur. Redis-cli devrait afficher quelque chose comme ça :

```bash
user@vps123456:~$ redis-cli monitor
OK
1540926527.065181 \[0 127.0.0.1:33320\] "PING"
1540926527.068352 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:default:is\_blog\_installed"
1540926527.163400 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:options:notoptions"
1540926527.163749 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:options:alloptions"
1540926527.164753 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:site-options:1:notoptions"
1540926527.340377 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:userlogins:user"
1540926527.340603 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:users:20"
1540926527.340821 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:user\_meta:20"
1540926527.397905 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:default:yoast\_titles\_rich\_defaults\_wpseo\_titles"
1540926527.405984 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:site-options:1:notoptions"
1540926527.439025 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:posts:last\_changed"
1540926527.439300 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:posts:get\_pages:90fc8ab476d94daabffe7578772c763c:0.81130900 1540903129"
1540926527.441645 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:posts:get\_pages:77573666ef24e1ad91fd9fbfd44c872f:0.81130900 1540903129"
1540926527.446576 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:posts:get\_pages:f7220df17210d0587c39e777e2eba779:0.81130900 1540903129"
1540926527.447567 \[0 127.0.0.1:33320\] "GET" "monsite.com/fr/azbbo2r\_:posts:get\_pages:02b8038114158e6e8039262ece2f0908:0.81130900 1540903129"
1540926527.480608 \[0 127.0.0.1:33320\] "DEL" "monsite.com/fr/azbbo2r\_:default:yoast\_titles\_rich\_defaults\_wpseo\_titles"
1540926527.574190 \[0 127.0.0.1:33320\] "SET" "monsite.com/fr/azbbo2r\_:default:yoast\_titles\_rich\_defaults\_wpseo\_titles" "a:41:{s:10:\\"title-post\\";s:39:\\"%%title%% %%page%% %%sep%% %%sitename%%\\";s:13:\\"metadesc-post\\";s:0:\\"\\";s:12:\\"noindex-post\\";b:0;s:13:\\"showdate-post\\";b:0;s:23:\\"display-metabox-pt-post\\";b:1;s:23:\\"post\_types-post-maintax\\";i:0;s:10:\\"title-page\\";s:39:\\"%%title%% %%page%% %%sep%% %%sitename%%\\";s:13:\\"metadesc-page\\";s:0:\\"\\";s:12:\\"noindex-page\\";b:0;s:13:\\"showdate-page\\";b:0;s:23:\\"display-metabox-pt-page\\";b:1;s:23:\\"post\_types-page-maintax\\";i:0;s:16:\\"title-attachment\\";s:39:\\"%%title%% %%page%% %%sep%% %%sitename%%\\";s:19:\\"metadesc-attachment\\";s:0:\\"\\";s:18:\\"noindex-attachment\\";b:0;s:19:\\"showdate-attachment\\";b:0;s:29:\\"display-metabox-pt-attachment\\";b:1;s:29:\\"post\_types-attachment-maintax\\";i:0;s:13:\\"title-product\\";s:39:\\"%%title%% %%page%% %%sep%% %%sitename%%\\";s:16:\\"metadesc-product\\";s:0:\\"\\";s:15:\\"noindex-product\\";b:0;s:16:\\"showdate-product\\";b:0;s:26:\\"display-metabox-pt-product\\";b:1;s:26:\\"post\_types-product-maintax\\";i:0;s:18:\\"title-tax-category\\";s:53:\\"%%term\_title%% Archives %%page%% %%sep%% %%sitename%%\\";s:21:\\"metadesc-tax-category\\";s:0:\\"\\";s:28:\\"display-metabox-tax-category\\";b:1;s:20:\\"noindex-tax-category\\";b:0;s:18:\\"title-tax-post\_tag\\";s:53:\\"%%term\_title%% Archives %%page%% %%sep%% %%sitename%%\\";s:21:\\"metadesc-tax-post\_tag\\";s:0:\\"\\";s:28:\\"display-metabox-tax-post\_tag\\";b:1;s:20:\\"noindex-tax-post\_tag\\";b:0;s:21:\\"title-tax-post\_format\\";s:53:\\"%%term\_title%% Archives %%page%% %%sep%% %%sitename%%\\";s:24:\\"metadesc-tax-post\_format\\";s:0:\\"\\";s:31:\\"display-metabox-tax-post\_format\\";b:1;s:23:\\"noindex-tax-post\_format\\";b:1;s:22:\\"title-tax-product\_type\\";s:53:\\"%%term\_title%% Archives %%page%% %%sep%% %%sitename%%\\";s:25:\\"metadesc-tax-product\_type\\";s:0:\\"\\";s:32:\\"display-metabox-tax-product\_type\\";b:1;s:24:\\"noindex-tax-product\_type\\";b:0;s:30:\\"taxonomy-product\_type-ptparent\\";i:0;}"
```

## Conclusion

C'est tout ! Redis est installé et configuré. Il ne reste plus qu'à faire un test de temps de chargement à l'aide de Lighthouse, GTmetrix, Pingdom, webpagetest.org ou votre outil de mesure préféré pour observer le gain sur le temps de chargement du site.

Et si besoin de vider le cache de Redis, la commande est `redis-cli flushall`
