---
title: "Accéder à localhost avec l'émulateur Genymotion"
date: "2014-03-05T21:09:53.000Z"
template: "post"
draft: false
slug: "acceder-localhost-avec-lemulateur-genymotion"
category: "Applications mobiles"
tags: 
  - "Android"
  - "Applications mobiles"
  - "Français"
description: "Si vous ne connaissez pas [Genymotion](http://www.genymotion.com/) c'est à essayer d'urgence. Il s'agit d'un émulateur Android basé sur VirtualBox, qui fonctionne aussi bien que l'émulateur 'officiel'."
socialImage: "/media/2014-03-05---acceder-localhost-avec-lemulateur-genymotion/android-studio.jpg"
---

Si vous ne connaissez pas [Genymotion](http://www.genymotion.com/) c'est à essayer d'urgence. Il s'agit d'un émulateur Android basé sur VirtualBox, qui fonctionne aussi bien que l'émulateur "officiel".

En beaucoup plus rapide ! Plus besoin d'aller se faire un café à chaque fois qu'on lance une app ou d'acheter un pc surpuissant juste pour faire tourner l'émulateur.

Etant basé sur VirtualBox, il y'a quelques particularités notamment au niveau de la config réseau. Sur l'émulateur pour accéder à localhost il suffit de taper localhost, ça marche. Avec Genymotion, voici comment procéder :

Sur Mac OS, il faut ouvrir le Terminal et taper :

`ifconfig vboxnet0`

Ce qui devrait retourner quelque chose comme ça :


```bash
vboxnet0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 0a:00:27:00:00:00 
	inet 192.168.56.1 netmask 0xffffff00 broadcast 192.168.56.255
```
Il suffit d'utiliser cette IP sur l'émulateur pour accéder à localhost.

 

Par exemple si vous y accédez d'habitude avec localhost:8888  il faut utiliser 192.168.56.1:8888

Ca peut servir par exemple pour [débugger une web app avec Weinre](/posts/debugger-facilement-des-applications-sites-mobiles/ "Debugger facilement des applications & sites mobiles").
