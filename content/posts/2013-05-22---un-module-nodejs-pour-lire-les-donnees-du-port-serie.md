---
title: "Un module node.js pour lire les données du port série"
date: "2013-05-22T12:10:15.000Z"
template: "post"
draft: false
slug: "un-module-nodejs-pour-lire-les-donnees-du-port-serie"
category: "Uncategorized FR"
tags: 
  - "Français"
  - "pll_5bf81c186da63"
  - "Uncategorized FR"
description: "Serialport est un module pour node.js qui permet de lire et écrire les données d'un port série, cet article explique l'utilisation basique de serialport."
socialImage: "/media/2013-05-22---un-module-nodejs-pour-lire-les-donnees-du-port-serie/node.js-serialport-sublime-text-screenshot-1.png"
---

![node.js-serialport-sublime-text-screenshot](/media/2013-05-22---un-module-nodejs-pour-lire-les-donnees-du-port-serie/node.js-serialport-sublime-text-screenshot-1.png)

[Serialport](https://npmjs.org/package/serialport) est un module node.js qui permet de lire les infos du port série, ce qui ouvre pas mal de possibilité au javascript comme...  allumer la lumière du salon ou [communiquer avec des drones](/posts/portfolio-item/station-de-controle-pour-drone/ "Station de controle pour drone").

Pour l'utiliser c'est assez simple

`npm install serialport`

> L'installation de serialport nécessite python 2.X et les "xcode command line tools" Pour les "command line tools" pas besoin de télécharger les quelques gigas de Xcode on peux les trouver [ici](https://github.com/kennethreitz/osx-gcc-installer#option-1-downloading-pre-built-binaries)

On va ensuite créer un serveur qu'on appelera server.js et y copier le code ci-dessous en précisant le bon "baudrate" et en remplaçant `tty.usbserial-A6023L0J` par l'adresse du port avec lequel on veux communiquer. `ls /dev/tty.*`  pour voir les port actifs

```javascript
var io = require('socket.io').listen(server); 
io.sockets.on('connection', socket);

var serialport = require("serialport");
var SerialPort = serialport.SerialPort;
var sp = new SerialPort("/dev/tty.usbserial-A6023L0J", {
parser: serialport.parsers.readline("n"),
baudrate: 57600
});

sp.on("open", function() {
console.log('open');
sp.on('data', function(data) {
console.log('data received: ' + data);
});
});
```
Puis on lance le serveur

node server.js

En admettant qu'un appareil soit branché sur un port série de votre ordinateur et qu'il envoi des données, le terminal devrait maintenant afficher le console.log qui ressemble à ça :

[![node.js serialport](/media/2013-05-22---un-module-nodejs-pour-lire-les-donnees-du-port-serie/Screen-shot-2013-05-30-at-11.32.53-AM.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-30-at-11.32.53-AM.png)

Serialport permet de lire mais aussi d'écrire sur le port série, ce qui laisse envisager de nombreuses d'utilisations, si ça vous intérresse voici deux articles intéressant, le premier sur le controle d'un arduino avec node.js et le deuxième sur le javascript et la robotique par l'auteur du module serialport.

[http://brandontilley.com/2012/03/02/controlling-an-arduino-from-nodejs.html](http://brandontilley.com/2012/03/02/controlling-an-arduino-from-nodejs.html)

[http://voodootikigod.com/nodebots-the-rise-of-js-robotics](http://voodootikigod.com/nodebots-the-rise-of-js-robotics)
