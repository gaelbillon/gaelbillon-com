---
title: "Station de contrôle pour drone avec websockets et serialport"
date: "2013-05-29T10:27:46.000Z"
template: "portfolio"
draft: false
slug: "station-de-controle-pour-drone"
category: "Portfolio"
tags: 
  - "Applications mobiles"
  - "arducopter"
  - "drone"
  - "Français"
  - "mavlink"
  - "nodejs"
  - "uav"
description: "Une station de controle pour drones utilisants le protocol MAVLink. Réalisée avec HTML5, CSS3, Angular.js, Node.js & websockets et serialport"
socialImage: "/media/portfolio/2013-05-29---station-de-controle-pour-drone/Nodejs_websockets__angular_mavlink_ground-control-station_thumb.jpg"
---



![Nodejs websockets AngularJS Mavlink ground control station](/media/portfolio/2013-05-29---station-de-controle-pour-drone/Nodejs_websockets__angular_mavlink_ground-control-station.jpg)

Cette application est une "station de contrôle au sol" qui reçoit et affiche les informations (vitesse, altitude, inclinaison, etc) d'un véhicule aérien sans pilote.L'application ouvre une connection websocket entre le client (navigateur) et le serveur, la connection reste ensuite ouverte et permet au serveur de "pusher" des informations, le client n'a pas besoin de faire une requête toutes les X secondes pour avoir des informations à jours.

Les informations sont lues depuis le port série avec le module node.js : [serialport](https://npmjs.org/package/serialport) sur lequel est connecté un module de télémétrie comme celui ci-dessous.On traite ensuite les informations avec un autre module node : [mavlink](https://npmjs.org/package/mavlink) qui nous permet de decoder les messages du protocol [MAVLink](https://github.com/mavlink/qgroundcontrol) (protocol de communication pour drones)Les informations sont ensuite affichées en "Near real-time" sur l'interface par [Angular.js](/pages/outils-et-frameworks#angularjs) qui update automatiquement la "view" dès que de nouvelles données sont disponibles.Des transitions CSS3 permettent d'afficher une boussole sans avoir recours à de lourdes animations javascript.Cette application est utilisable mais à été développée avant tout dans un but ludique, et comme "proof of concept" afin de montrer ce qu'il était possible de faire avec les dernières technologies web. Il resterait pas mal de boulot pour en faire un "daily driver". Mais son utilisation est sans aucun risque pour le drone puisque l'application ne fait que récupérer les informations sans en envoyer. N'hésitez pas à forker ce projet sur [GitHub](https://github.com/gaelbillon/Nodejs-Websockets-GCS). A l'avenir, on pourrais imaginer par exemple pouvoir armer et désarmer les moteurs du drone, créer des missions ou utiliser les accéléromètres d'une tablette pour contrôler le drone en vol avec l'API "device orientation" du HTML5.

![radio-telemetry-kit-433mhz.jpg](/media/portfolio/2013-05-29---station-de-controle-pour-drone/radio-telemetry-kit-433mhz.jpg)

[https://ardupilot.org/copter/docs/common-sik-telemetry-radio.html](https://ardupilot.org/copter/docs/common-sik-telemetry-radio.html)

[Voir le projet sur GitHub](https://github.com/gaelbillon/Nodejs-Websockets-GCS) 