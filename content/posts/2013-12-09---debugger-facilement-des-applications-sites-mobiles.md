---
title: "Debugger facilement des applications & sites mobiles"
date: "2013-12-09T20:09:52.000Z"
template: "post"
draft: false
slug: "debugger-facilement-des-applications-sites-mobiles"
category: "Applications mobiles"
tags: 
  - "Applications mobiles"
  - "debug"
  - "Français"
  - "mobile"
  - "weinre"
description: "Pour débugger des applications PhoneGap ou des sites mobiles en temps réel  avec l'inspecteur Webkit, rien de plus simple."
socialImage: "/media/2013-12-09---debugger-facilement-des-applications-sites-mobiles/phonegap-and-mobile-site-debugging.jpg"
---

Pour débugger des applications PhoneGap ou des sites mobiles en temps réel  avec l'inspecteur Webkit, rien de plus simple.

## debug.phonegap.com

La première solution, très simple, c'est d'utiliser debug.phonegap.com, tout est expliqué sur la page.

[![debug-phonegap-com](/media/2013-12-09---debugger-facilement-des-applications-sites-mobiles/debug-phonegap-com.jpg)](/posts/wp-content/uploads/2013/12/debug-phonegap-com.jpg)

Mais debug.phonegap.com peut desfois s'avérer très lent.

## Weinre

On peut alors utiliser  la même chose que phonegap, ça s'appel Weinre (à prononcer comme le mot "winery" ou "weiner" en anglais, au choix).

[![weinre-screenshot](/media/2013-12-09---debugger-facilement-des-applications-sites-mobiles/weinre-screenshot.jpg)](/posts/wp-content/uploads/2013/12/weinre-screenshot.jpg)

C'est très simple à mêtre en place :

Si ce n'est pas déja fait, Il faut installer Node.js, par ici [http://nodejs.org/download](http://nodejs.org/download)

Une fois que Node.js est installé, sur mac ou linux, ouvrir le terminal et copier/coller ceci

`sudo npm install -g weinre`

`-g` signifie installation globale, c'est plus judicieux, vu qu'il s'agit d'un outil qui resservira très probablement pour d'autres projets

ça y'est weinre est installé on peut lancer le serveur en tapant

`weinre --boundHost -all`

`--boundHost -all` pour pouvoir accéder au serveur depuis un appareil qui n'aura pas la même IP. L'appareil doit se trouver sur le même réseau local.

Il ne reste plus qu'a insérer ceci dans la page qu'on veut débugger (index.html par exemple)

`<script src="http://localhost:8080/target/target-script-min.js#anonymous"></script>`

puis de se rendre à l'adresse

[http://localhost:8080/client/#anonymous](http://localhost:8080/client/#anonymous)

On peut remplacer `#anonymous` par n'importe quoi, du moment qu'on le change dans l'adresse du script et dans l'url.

Et voila on peut maintenant facilement débugger un site mobileou une application Phonegap ou Trigger.io

Tapez `alert('test')`  dans la console pour essayer.

Et si o nsouhaite pouvoir fermer le terminal sans arrêter le serveur Weinre, nohup est là pour ça.

`nohup weinre –boundHost -all`

## Adobe Edge Inspect

![adobe-edge-inspect-website-screenshot](/media/2013-12-09---debugger-facilement-des-applications-sites-mobiles/adobe-edge-inspect-website-screenshot.jpg)

La troisième solution, un tout petit peu plus simple mais aussi la plus chère, est d'utiliser [Adobe Edge Inspect](http://html.adobe.com/fr/edge/inspect/) qui consiste en une application windows, mac , accompagnée d'une application iOS, Android ou Kindle et d'une extension Chrome. (Nécessite de s'inscrire à Adobe Creative Cloud. 1mois gratuit puis 60€/par mois).
