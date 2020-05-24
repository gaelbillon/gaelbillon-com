---
title: "Photogrammétrie avec le Parrot Anafi et Pix4D Capture"
date: "2018-11-21T17:42:07.000Z"
template: "post"
draft: false
slug: "photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture"
category: "Drone"
tags: 
  - "Anafi"
  - "Drone"
  - "Français"
  - "Photogrammétrie"
  - "Pix4D"
  - "pll_5cdae292741fc"
description: "Une des solutions les plus simple, intuitive et portable actuellement pour faire de la photogrammétrie. Un très bon ratio volume/poids/prix/qualité d'image."
socialImage: "/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-flight-plan-on-iPhone-5S.jpg"
---

## Préparation du vol

La planification du vol est très simple grâce à l'interface intuitive dePix4D Capture. Le plan de vol est prêt en quelques minutes et tout les réglages indispensables sont présents.

![](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-flight-plan-on-iPhone-5S.jpg)

Il est possible de télécharger les maps (Mapbox ou Apple) pour une utilisation offline une fois sur site au cas où il n'y ait pas d'accès internet. Pour cela, il suffit d'ouvrir Pix4d et de se rendre sur la zone que l'on souhaite mettre en cache et d'attendre que la carte soit correctement chargée (que toutes les tuiles de la carte soient apparues dans leur meilleurs résolution possible)

## Pendant le vol

Le vol s'est très bien passé et même si le drone n'est pas allé très loin (pas plus de 300 mètres) le retour vidéo était assez stable malgré quelques freezes d'une seconde quand le drone passait derrière le bâtiment et un retour vidéo très basse définition de temps en temps (mieux que les freezes), globalement le vol s'est déroulé à merveille, il est facile de switcher entre la carte et le retour vidéo pour voir la progression du drone et les éventuels obstacles qui se présenteraient sur la route. D'autant plus que l'Anafi est programmé par Pix4D pour garder le "nez" vers l'avant.

> Il faudra tout de même faire attention en touchant l'écran du téléphone de ne pas toucher les sticks de la radio-commande ce qui aurait pour effet de repasser en mode pilotage manuel et de mettre la mission en pause. Pas très grave puisqu'il suffit d'appuyer sur "Resume" pour reprendre le vol automatique.

Le retour vidéo ne fait pas d'écran noir a chaque déclenchement mais Pix4D indique les photos prises sur la carte, enfin presque, Pix4D affiche la position à laquelle la commande de déclenchement à été envoyée mais l'app ne reçoit pas de feedback confirmant que la photo à bien été prise.

![Photogrammetry with Parrot Anafi and Pix4D Capture video feedback](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-video-feedback-1030x580.jpg)

> A l'atterrissage, il faut penser à orienter la caméra vers le ciel pour la protéger de tout ce qui va voler quand le drone se posera en particulier si c'est sur du sable ou des graviers. Pix4D n'ajoute pas de waypoint "Caméra à +90°" avant l'atterrissage. même si on touche la gâchette d'inclinaison de la nacelle l'atterrissage poursuivra sont cours et l'Anafi ne repassera pas en mode pilotage manuel.

Pendant le vol on peut suivre toutes les infos sur le statut de l'Anafi : Pourcentage de la batterie, vitesse, altitude, nombre de satellites, espace dispo sur la carte SD et distance au point home ou smartphone. Pour afficher toutes ces infos il est préférable d'avoir un écran de plus de 4", c'est un peu juste sur  un iPhone 5S et certaines infos sont cachées.

![Photogrammetry with Parrot Anafi and Pix4D Capture flight hidden informations on iPhone 5S](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-flight-hidden-informations-on-iPhone-5S-1030x580.jpg)

## Après le vol

L'Anafi s'est posé avec 23% de batterie après un vol de 19 minutes et 51 secondes à 3°c

Avec les réglages par défaut de Pix4D Capture le téléchargement des photos vers le téléphone est lancé automatiquement dès l'atterrissage. Il y'a eu un léger bug pendant le téléchargement des images mais qui a bien repris ensuite et toutes les images ont bien été copiées.

> Penser à garder de la batterie pour le transfert des photos. Pour 359 photos (1,96 Go, moyenne 5,46 Mo / photo) avec un iPhone 5S il faut compter une bonne vingtaine de minutes. Ca devrait passer large la plupart du temps mais si on pose à 2% pas sûr. Le transfer automatique des photos peut être désactivé dans les réglages de l'application.

 

![Photogrammetry with Parrot Anafi and Pix4D Capture downloading images after flight](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-downloading-images-after-flight-1030x580.jpg)

Les images téléchargées par Pix4D Capture et sauvegardées sur le téléphone sont correctement géotaggées. Sur la carte SD de l'Anafi on retrouve presque exactement la même chose, les photos JPG géotaggées. Une seule petite différence, sur la carte SD il y'a 3 photos de plus, dont 2 prises après le vol, pendant le transfert des photos et la troisième supplémentaire, eh bien je ne sais pas... Probablement pendant le vol, c'est peut être dû a la pause involontaire pendant le vol automatisé quand j'ai touché un stick de la radio-commande par inadvertance.

Il est ensuite possible d'uploader les photos sur Pix4D cloud afin d'effectuer les calculs et le rendu directement sur les ordinateurs de Pix4D. L'upload des photos sur le cloud Pix4D nécessite une licence valide. Il est possible d'obtenir une licence d'essai de 15 jours en créant un compte Pix4D ici : [https://account.pix4d.com/signup](https://account.pix4d.com/signup). Il faut ensuite télécharger le logiciel Pix4D et cliquer sur le bouton "Click for trial" en haut à droite de l'interface.

\[caption id="attachment\_730" align="aligncenter" width="750"\]![Photogrammetry with Parrot Anafi and Pix4D Capture upload images Pix4D cloud](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-upload-images-Pix4D-cloud-1030x580.jpg) Avec les paramètres par défaut, le téléchargement des photos depuis l'Anafi débute immédiatement après l'atterrissage\[/caption\]

### Pas de RAW

Pix4D ne sauvegarde que des JPG, le logiciel Pix4d Mapper ne sachant pas utiliser les RAW. C'est fort dommage on aurait aimé pouvoir récupérer les DNG de l'Anafi et les convertir en TIFF géotaggés que Pix4d Mapper sait lire. C'est paraît il la même chose avec les drones DJI. Mais même si c'était possible, il faudrait veiller à avoir une carte SD d'une bonne capacité puisque pour ce vol de 359 photos, si on considère que les DNG font en moyenne 48 Mo il faudrait 17,2Go pour stocker les photos et pourtant le vol aurait même pu faire quelques minutes de plus.

L'enregistrement des RAW est une fonctionnalité qui n'a pas encore été développée et qui ne serait d'ailleurs peut être pas si utilisée si on prend en compte qu'il faut entre 4 à 5 secondes pour que l'Anafi enregistre une photo DNG (~48 Mo), et qu'il faudrait donc diminuer la vitesse du vol, diminuer l'overlap ou augmenter l'altitude et donc diminuer la GSD. Sans compter qu'il faudrait énormément de temps supplémentaire pour le téléchargement des photos depuis le drone ainsi que pour l'upload des photos sur Pix4D cloud.

Mise à jour : il existe en fait un moyen (pas officiel) d'[enregistrer les DNG avec Pix4D Capture](/posts/prendre-des-photos-en-dng-raw-avec-le-parrot-anafi-et-pix4d-capture/)

## Qualité des photos

Il y'a un petit flou de mouvement sur une bonne partie des photos. Le vol s'est effectué à environ 2,7m/s mais la proximité du sol (30 mètres) et la faible luminosité ce jour là n'ont pas du aider.

D'après les Exif, on dirait que Pix4D laisse libre la vitesse d'obturation et les ISO, la focale étant fixe (f/2,4) sur l'Anafi. Ce qui est très bien puisque de toute façon on préfère bloquer l'ouverture pour la photogrammétrie afin de minimiser les variations de déformation d'objectif entre chaque photos.

- - Focale : f/2,4
    - Vitesse d'obturation : entre 1/25 et 1/100
    - ISO : entre 103 et 206

[![Photogrammetry with Parrot Anafi and Pix4D Capture photos EXIF geotagged](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-photos-EXIF-geotagged-1030x604.png)](/posts/wp-content/uploads/2018/11/Photogrammetry-with-Parrot-Anafi-and-Pix4D-Capture-photos-EXIF-geotagged.png)

\[caption id="attachment\_738" align="aligncenter" width="750"\]![Pix4D Parrot Anafi photogrammetry photo JPG](/media/2018-11-21---photogrammetrie-avec-le-parrot-anafi-et-pix4d-capture/P0770078-1030x774.jpg) Ouvrir l' [image pleine résolution](/media/2018-11-21---photogrammetry-with-parrot-anafi-and-pix4d-capture/P0770078.jpg) (5344 × 4016 | 5,6 Mo) dans un nouvel onglet\[/caption\]

## Conclusion

L'application est vraiment très bien conçue et agréable à utiliser, sans lire le mode d'emploi, sans créer de compte sans galérer a créer une mission sur un petit écran 4" on obtient très facilement un résultat correct. En fait je crois que je n'avais jamais programmé un vol aussi simplement. Le passage de l'écran de retour vidéo à l'affichage carte se fait sans problème et tant mieux parce que c'est quelque chose qu'on fait fréquemment pendant le vol, il faut juste faire attention à ne pas toucher aux sticks de la radiocommande. C'est donc vraiment dommage que l'application n'enregistre pas les raw, seul reprorche qu'on puisse faire à Pix4D Capture. L'Anafi est également très agréable à utiliser, il est très compact, léger, on a vraiment pas peur de l'emmener n'importe où et vu la place qu'il prend ca serait dommage de se priver. La possibilité de recharger la batterie sur un chargeur allume cigare USB ou une batterie externe est également un plus. Le drone se fait très discret à quelques dizaines de mètres du sol.

C'est à mon goût la solution la plus simple, intuitive et portable qui soit aujourd'hui disponible dans le commerce pour faire des photos et de la photogrammétrie. Le drone faisant moins de 800 grammes on évite aussi pas mal de tracasseries administratives et c'est aussi plus rassurant à faire voler, d'autant plus qu'il n'est pas excessivement cher. Ca reste un capteur 1/2,4" qui ne fera clairement pas le poids face au caméras embarquées sur des drones plus lourd mais disons qu'il s'agit d'une solution offrant un très bon ratio volume/poids/prix/qualité d'image.

 

## Add-on Flight Plan pour FreeFlight

Je comptais un peu sur cet "in-app purchase" pour faire des plans de vol mais même si cet add-on Flight Plan de l'application FreeFlight qui permet de programmer des vols à l'air plutôt bien conçu pour les vidéos automatisées, il sera inutile pour la photogrammétrie, il faut créer tous les waypoints manuellement, ce qui serait un peu fastidieux dans le cas d'une grid avec 200 waypoint ou même d'un plan de vol circulaire de 30 waypoints.

 

## Précautions

- Prévoir plusieurs ou une grosse carte SD si on souhaite effectuer plusieurs vol, ca se rempli très vite (~2Go / vol).
- Ne pas appuyer sur le bouton home du téléphone (en tout cas sur iOS). Même en relançant Pix4D rapidement, l'application aura perdue la connexion avec le drone et il faudra débrancher et rebrancher le câble USB qui relie le téléphone et la radio-commande pour la rétablir.

## Résultat

580 000 polys. Texture 8192x8192.

<iframe width="640" height="480" align="center" src="https://sketchfab.com/models/c34666babe56402495f023eb263cf583/embed" frameborder="0" allow="autoplay; fullscreen; vr" mozallowfullscreen="mozallowfullscreen" webkitallowfullscreen="webkitallowfullscreen"></iframe>
