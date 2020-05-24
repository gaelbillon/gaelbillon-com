---
title: "Se connecter en SFTP à une instance EC2 avec Transmit"
date: "2013-05-11T17:18:46.000Z"
template: "post"
draft: false
slug: "se-connecter-en-sftp-a-une-instance-ec2-avec-transmit"
category: "Uncategorized FR"
tags: 
  - "Français"
  - "Uncategorized FR"
description: "Configurer Transmit pour se connecter en SFTP à une instance Amazon EC2"
socialImage: "/media/2013-05-11---se-connecter-en-sftp-a-une-instance-ec2-avec-transmit/Transmit-1.jpg"
---

On vu dans [cet article](/posts/configurer-un-serveur-ubuntu-en-10-min-avec-amazon-ec2-et-en-plus-cest-gratuit/ "Configurer gratuitement un serveur ubuntu en 10 min avec amazon EC2") comment se connecter en ssh à une instance EC2. Mais pour uploader/modifier des fichiers sur notre serveur, c'est quand même plus agréable en sftp (Secure FTP).

Si vous préferez uploader des fichier avec scp, c'est comme ça : 
```bash
scp -i  aws.pem .localized ubuntu@ec2-54-216-58-83.eu-west-1.compute.amazonaws.com:~/public_html
```

On va avoir besoin du certificat (fichier .pem) qui permet de se connecter en ssh à notre instance EC2. On va d’abord placer le certificat dans le dossier .ssh du repertoire utilisateur. `cp aws.pem ~/.ssh`

Si le dossier .ssh n'existe pas, il faut le créer `mkdir ~/.ssh`

On ouvre ensuite transmit, puis on crée un nouveau favori [![connect sftp ec2 transmit](/media/2013-05-11---se-connecter-en-sftp-a-une-instance-ec2-avec-transmit/Screen-shot-2013-05-10-at-3.20.11-PM.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-3.20.11-PM.png) Dans "serveur" on met l’adresse de notre instance ec2. Pour le nom d'utilisateur, ubuntu. Et rien pour le mot de passe, transmit va chercher tout seul les fichiers qui se trouvent dans .ssh, on aurait aussi pu cliquer sur la clé dans transmit et selectionner le certificat, on est donc pas obligé de deplacer le certificat dans .ssh mais c’est un bon endroit pour le ranger.

Ca y’est on peut se connecter et uploader ! [![connect sftp ec2 transmit](/media/2013-05-11---se-connecter-en-sftp-a-une-instance-ec2-avec-transmit/Screen-shot-2013-05-11-at-7.15.26-PM.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-11-at-7.15.26-PM.png)
