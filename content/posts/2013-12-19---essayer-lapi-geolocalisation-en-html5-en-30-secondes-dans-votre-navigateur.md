---
title: "Essayez l'API geolocalisation HTML5 en 30 secondes dans votre navigateur"
date: "2013-12-19T17:31:58.000Z"
template: "post"
draft: false
slug: "essayer-lapi-geolocalisation-en-html5-en-30-secondes-dans-votre-navigateur"
category: "Uncategorized FR"
tags: 
  - "Français"
  - "geolocation"
  - "html5"
  - "Uncategorized FR"
description: "Une quinzaine de lignes de JS à coller dans la console d'un navigateur qui affiche les coordonnées GPS de l'appareil"
socialImage: "/media/2013-12-19---essayer-lapi-geolocalisation-en-html5-en-30-secondes-dans-votre-navigateur/Geolocation.jpg"
---

C'est très simple,

## 1\. Ouvrir la console javascript

- ⌘ + ⌥ + J sur Chrome/Mac OS
- Ctrl + Shift + J sur Chrome/Windows
- ⌘ + ⌥ + K sur Firefox/Mac OS
- Ctrl + Shift + K sur Firefox/Windows
- Voir [ici](http://webmasters.stackexchange.com/questions/8525/how-to-open-the-javascript-console-in-different-browsers) pour les autres.

## 2\. Copier/coller ce code dans la console

```javascript
navigator.geolocation.getCurrentPosition(
  function (pos) {
    var crd = pos.coords;

    console.log('Votre position est :');
    console.log('Latitude : ' + crd.latitude);
    console.log('Longitude: ' + crd.longitude);
    console.log('A plus ou moins ' + crd.accuracy + ' mètres.');
  },
  function (err) {
    console.warn('ERROR(' + err.code + '): ' + err.message);
  },
  {
  enableHighAccuracy: true,
  timeout: 5000,
  maximumAge: 0
  }
);
```

## 3\. Autoriser le partage de la position

[![google.fr wants to use your computer location](/media/2013-12-19---essayer-lapi-geolocalisation-en-html5-en-30-secondes-dans-votre-navigateur/Screen-Shot-2013-12-19-at-18.05.42.png)](/posts/wp-content/uploads/2013/12/Screen-Shot-2013-12-19-at-18.05.42.png)

Votre position devrait maintenant s'afficher dans la console :

```javascript
Votre position est :
Latitude : 45.174001
Longitude: 5.802064
A plus ou moins 20 mètres.
```

L'API geolocation est disponible sur tout les principaux navigateurs, sauf Opera Mini. [caniuse.com/#feat=geolocation](http://caniuse.com/#feat=geolocation)
