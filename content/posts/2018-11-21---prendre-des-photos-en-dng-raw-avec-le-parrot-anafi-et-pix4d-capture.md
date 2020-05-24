---
title: "Prendre des photos en DNG (RAW) avec le Parrot Anafi et Pix4D Capture"
date: "2018-11-21T17:11:30.000Z"
template: "post"
draft: false
slug: "prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture"
category: "Drone"
tags: 
  - "Anafi"
  - "Drone"
  - "Français"
  - "Photogrammétrie"
  - "Pix4D"
  - "pll_5bf835d793813"
description: "L'application Pix4D Capture n'enregistre que des JPG. Heureusement il est possible de déjouer cette limitation et d''enregistrer les photos en DNG (RAW)"
socialImage: "/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-reconnected.jpg"
---

> Prudence ! 
> Il est possible que le changement d'application et la déconnexion du câble USB pendant le vol puissent perturber le bon fonctionnement du drone. Je n'ai pas eu de problème mais utilisez cette méthode à vos risques et périls. - Ces essais on été effectués avec un Parrot Anafi 1.2.4, SkyController 1.2.0, un iPhone 5S sur iOS 12, l'application FreeFlight 6.2.1. YMMV.

![Pix4D Parrot Anafi record RAW DNG FreeFlight reconnected](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-reconnected-300x169.jpg)L'application Pix4D Capture est très bien conçue pour préparer les plans de vols, que ce soit en grid, double grid, polygone ou circulaire. La préparation d'un plan de vol se fait très simplement, même sur un petit smartphone et tout les réglages importants comme le recouvrement ou l'inclinaison de la caméra sont présents. Seul petit bémol quand on fait de la [photogrammétrie avec le Parrot Anafi et Pix4D Capture](/posts/photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/), l'app n'enregistre que des JPG et c'est également le cas avec d'autres drones comme ceux de DJI.

Heureusement il est possible de déjouer cette limitation. Pour cela il faut :

1. Allumer l'Anafi et connecter le smartphone au SkyController3
2. Ouvrir Pix4D Capture et créer un plan de vol![Pix4D Parrot Anafi record RAW DNG photos with Pix4D Capture](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-with-Pix4D-Capture-1030x580.jpg)
3. Cliquer sur le bouton "Start" en bas à droite  dans Pix4D Capture. Passer l'écran qui demande de se connecter au drone. On arrive sur la checklist, c'est à ce moment là que l'app écrit le plan de vol sur l'Anafi. **Cliquer sur Cancel**.
  
![Pix4D Parrot Anafi record RAW DNG photos drone takeoff checklist](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-drone-takeoff-checklist-1030x580.png)
<figcaption>Une fois que "Mission uploaded to drone" est en vert, appuyer sur "Cancel"</figcaption>

4. Lancer l'application FreeFlight et accéder à l'écran de pilotage.![Pix4D Parrot Anafi record RAW DNG FreeFlight Pix4D switch](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-Pix4D-switch-e1542816095332-1030x580.jpg)
  
![Pix4D Parrot Anafi record RAW DNG FreeFlight not connected](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-FreeFlight-not-connected-1030x580.jpg)
<figcaption>FreeFlight affichera cet écran tant que le câble n'aura pas été reconnecté</figcaption>

5. Reconnecter le smartphone à la radio-commande avec le câble USB.
6. Modifier les paramètres photos : DNG/JPG, Style, iso, shutter speed. Vous pouvez choisir tous les paramètres qui vous conviennent, ils seront ensuite utilisés pedant le vol automatique.![Pix4D Parrot Anafi record RAW DNG choose photo settings](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-choose-photo-settings-1030x580.jpg)
7. Débrancher le câble USB qui relie le smartphone à la radio-commande.
8. Repasser sur l'application Pix4D Capture
9. Rebrancher le câble USB
10. Attendre que pix4D se re-connecte à l'Anafi puis ré-appuyer sur "Start" en bas à droite de l'écran. Et cette fois, sur l'écran "Drone take off checklist", on ne va pas cliquer sur Cancel mais sur Start. L'Anafi décolle immédiatement et commence son vol automatique.![Pix4D Parrot Anafi record RAW DNG photos drone takeoff checklist](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-drone-takeoff-checklist-1030x580.png)

Voila ! L'Anafi prendra toutes les photos suivantes en DNG+JPG avec les réglages que vous avez choisis dans FreeFlight.

![Pix4D Parrot Anafi record RAW DNG exif ISO 3200 shutter speed 1-4000](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-exif-ISO-3200-shutter-speed-1-4000.jpg)
<figcaption>On a bien un temps d'exposition à 1/400 et l'ISO à 3200 comme précédemment défini dans FreeFlight</figcaption>

![Pix4D Parrot Anafi record RAW DNG gallery](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-gallery-1030x580.jpg)
<figcaption>Les photos DNG dans l'explorateur de carte SD de FreeFlight</figcaption>

Après le vol, il ne sera pas possible de continuer avec le workflow Pix4D, l'application ne saura pas télécharger les photos depuis l'Anafi après la mission, ce qui est tout à fait normal puisqu'elle n'a pas été conçue pour le faire.

![Pix4D Parrot Anafi record RAW DNG photos arror when uploading images](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-photos-arror-when-uploading-images-1030x580.png)
<figcaption>Pix4D Capture ne pourra pas récupérer les photos si on force l'Anafi en DNG, l'application n'est pas prévue pour ça</figcaption>

Mais il restera bien sûr possible de récupérer les DNG géotaggés sur la carte SD de l'Anafi, de les convertir en TIFF puis de les utiliser dans Pix4D ou n'importe quel autre logiciel de photogrammétrie.

Malheureusement l'Anafi n'est pas capable d'enregistrer les DNG aussi vite que les JPG, il lui faudra entre 4 et 5 secondes entre chaque photo. Il faudra donc modifier certains réglages :

- Réduire la vitesse de vol (et donc augmenter le temps du vol et probablement diminuer la surface couverte)
- Diminuer l'overlap (ce qui n'est pas recommandé, les paramètres par défaut de Pix4D 80% ↕ et 70%↔  sont adaptés à la plupart des projets, les diminuer pourrait compliquer ou rendre impossible le travail de reconstruction du logiciel de photogrammétrie)
- Augmenter l'altitude (et donc diminuer la GSD et augmenter légèrement la durée du vol)

Ou un mélange des 3 qu'il est possible de définir selon un savant calcul. On perd donc certains avantages de l'application Pix4D qui en fonctionnement normal abstrait totalement ce genre de problèmes.

![Pix4D Parrot Anafi record RAW DNG HoudaGeo Pix4D Capture](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-HoudaGeo-Pix4D-Capture.jpg)
<figcaption>24 photos on été prises au lieu des 44 initialement prévues à cause du temps d'enregistrement des DNG (4 à 5 secondes)</figcaption>

![Pix4D Parrot Anafi record RAW DNG HoudaGeo Exif timestamp](/media/2018-11-21---prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/Pix4D-Parrot-Anafi-record-RAW-DNG-HoudaGeo-Exif-timestamp-1030x680.jpg)
<figcaption>En examinant les exif, on constate qu'il faut entre 4 et 5 secondes à l'Anafi pour enregistrer les photos en DNG</figcaption>
