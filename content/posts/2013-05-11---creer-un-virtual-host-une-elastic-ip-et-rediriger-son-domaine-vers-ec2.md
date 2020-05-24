---
title: "Créer un virtual host, une elastic IP et rediriger son domaine vers EC2"
date: "2013-05-11T18:42:08.000Z"
template: "post"
draft: false
slug: "creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2"
category: "Uncategorized FR"
tags: 
  - "Français"
  - "Uncategorized FR"
description: "Voici la marche à suivre afin de créer un virtual host et une elastic IP sur serveur ubuntu sur Amazon EC2, On va ainsi pouvoir rediriger son ancien..."
socialImage: "/media/2013-05-11---creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/virtual-hosts-1.jpg"
---

## Configurer les virtual host

Après avoir [configuré un serveur ubuntu avec amazon EC2](/posts/configurer-un-serveur-ubuntu-en-10-min-avec-amazon-ec2-et-en-plus-cest-gratuit/ "Configurer gratuitement un serveur ubuntu en 10 min avec amazon EC2"), on va maintenant voir comment le configurer.

Il faut d’abord créer l’arboresscence nécessaire pour notre site

```bash
mkdir ~/ubuntu/public\_html
mkdir ~/ubuntu/public\_html/domain.com
mkdir ~/ubuntu/public\_html/domain.com/www
mkdir ~/ubuntu/public\_html/domain.com/log
chmod -R 755 ~/ubuntu/public\_html/domain.com
```

Il faut ensuite modifier la config d’apache pour qu’il sache ou se trouve notre dossier domain.com, par défaut les sites accesible par apache sont dans `/var/www` , ici on préfère mettre domain.com dans le repertoire utilisateur (`/home/users/ubuntu`) afin de pouvoir y accéder facilement avec un client ftp. Pour se connecter en SFTP tout est expliqué dans [cet article](/posts/se-connecter-en-sftp-a-une-instance-ec2-avec-transmit/ "Se connecter en SFTP à une instance EC2 avec Transmit").

On va créer un nouveau fichier dans sites-available nano /etc/apache2/sites-available/domain.com

Et y coller ceci, en remplacant bien sur domain.com par votre nom de domaine :

```apache
# Place any notes or comments you have here
# It will make any customisation easier to understand in the weeks to come
# domain: domain.com
# public: /home/ubuntu/public\_html/domain.com/www

<VirtualHost *:80>
# Admin email, Server Name (domain name) and any aliases
ServerAdmin webmaster@domain.com
ServerName domain.com
ServerAlias www.domain.com

# Index file and Document Root (where the public files are located)
DirectoryIndex index.html
DocumentRoot /home/ubuntu/public\_html/domain.com/www

# Custom log file locations
LogLevel warn
ErrorLog /home/ubuntu/public\_html/domain.com/log/error.log
CustomLog /home/ubuntu/public\_html/domain.com/log/access.log combined
</VirtualHost>
```

Il faut maintenant activer le site avec la commande suivante `sudo a2ensite domain.com`

Puis on rafraichit la configuration d’apache sudo service apache2 reload

## Créer une elastic IP

On se rend sur la console [AWS](https://console.aws.amazon.com/ec2). Si vous n'avez pas encore créé d'instance EC2, voir [cet article](/posts/configurer-un-serveur-ubuntu-en-10-min-avec-amazon-ec2-et-en-plus-cest-gratuit/ "Configurer gratuitement un serveur ubuntu en 10 min avec amazon EC2").

[![aws ec2 allocate new elastic IP](/media/2013-05-11---creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/Screen-shot-2013-05-10-at-4.42.48-PM-624x390.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-4.42.48-PM.png) et dans elastic ip, “allocate new adress”

[![allocate new elastic IP on amazon aws ec2](/media/2013-05-11---creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/Screen-shot-2013-05-10-at-4.42.55-PM-624x390.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-4.42.55-PM.png)

On choisi ec2 et on associe ensuite l’ip avec l’instance crée dans ce post

[![allocate new elastic IP on amazon aws ec2 associate with instance](/media/2013-05-11---creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/Screen-shot-2013-05-10-at-4.43.18-PM-624x390.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-4.43.18-PM.png)

 

[![aws ec2 new elastic ip created](/media/2013-05-11---creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/Screen-shot-2013-05-10-at-4.43.24-PM-624x390.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-4.43.24-PM.png)

## Editer la zone DNS

Il faut ensuite mofifier la zone DNS chez son registrar. Chez OVH c’est par [ici](https://www.ovh.com/managerv3/). Puis dans "Domaines & DNS" puis "Zone DNS". On va changer les champs de type A et remplacer leurs ip par l’elastic ip que l’on viens de créer chez amazon.

 

C'est fini ! domain.com devrait maintenant pointer vers notre nouveau serveur.
