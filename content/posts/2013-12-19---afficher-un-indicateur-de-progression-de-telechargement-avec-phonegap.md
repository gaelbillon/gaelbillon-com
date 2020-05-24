---
title: "Afficher un indicateur de progression de téléchargement avec PhoneGap"
date: "2013-12-19T19:09:56.000Z"
template: "post"
draft: false
slug: "afficher-un-indicateur-de-progression-de-telechargement-avec-phonegap"
category: "Applications mobiles"
tags: 
  - "Applications mobiles"
  - "Français"
description: "Quelques lignes de javascript pour afficher une barre de progression lors d'un fileTransfer avec Phonegap/Cordova"
socialImage: "/media/2013-12-19---afficher-un-indicateur-de-progression-de-telechargement-avec-phonegap/phonegap-filetransfer-onpress-loading-indicator-302x150.jpg"
---

C'est pas très compliqué avec la propriété onprogress de l'objet fileTransfer de PhoneGap, il suffit de quelques lignes :

```javascript
var fileTransfer = new FileTransfer();

// Affichage du message "téléchargement... xx%"
fileTransfer.onprogress = function(progressEvent) {
    if (progressEvent.lengthComputable) {
        var pourcentage = Math.floor(progressEvent.loaded / progressEvent.total \* 100);
        console.log(pourcentage + "% téléchargés...";
    } else {
        console.log('.');
    }
};

// Téléchargement
fileTransfer.download(
    uri,
    filePath,
    function(entry) {
        console.log('le fichier à été téléchargé');
    },
    function(error) {
        console.log("problème avec le fichier source : " + error.source);
        console.log("problème avec le fichier cible : " + error.target);
        console.log("code d'erreur : " + error.code);
    },
    false
);
```

Et si vous avez besoin d'inspiration pour l'indicateur de progression, il y'a quelques beaux exemples [ici](http://designmodo.com/mobile-app-loading-progress-bars/ ).

