---
title: "Un plugin PhoneGap / Cordova pour décompresser des zip"
date: "2014-02-02T10:51:12.000Z"
template: "post"
draft: false
slug: "un-plugin-phonegap-cordova-pour-decompresser-des-zip"
category: "Applications mobiles"
tags: 
  - "Applications mobiles"
  - "cordova"
  - "file api"
  - "Français"
  - "mobile"
  - "phonegap"
description: "Un plugin PhoneGap très simple et rapide à installer qui permet de dézipper les fichiers zip."
socialImage: "/media/2014-02-02---un-plugin-phonegap-cordova-pour-decompresser-des-zip/unzip-phongap-javascript-mobile.png"
---

Le Github/readme c'est par ici :

[https://github.com/MobileChromeApps/zip](https://github.com/MobileChromeApps/zip)

 

Et pour installer il suffit de faire ça

```
$ cordova plugin add https://github.com/MobileChromeApps/zip.git
```

 

Ca s'utilise comme ça :

```
zip.unzip('full file path', 'directory to extract into', function(){
        console.log('All done');
    });
```

 

Ca peut être utile pour télécharger plusieurs fichiers d'un coup sans avoir à lancer de multiples [FileTransfer](http://docs.phonegap.com/en/1.0.0/phonegap_file_file.md.html#FileTransfer) avec PhoneGap.
