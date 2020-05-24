# [Configurer gratuitement un serveur ubuntu en 10 min avec amazon EC2](https://gaelbillon.com/configurer-gratuitement-un-serveur-ubuntu-en-10-min-avec-amazon-ec2/)

mai 10, 2013/par [Gaël Billon](https://gaelbillon.com/author/gael/)

Ca permet d’avoir le contrôle total sur son serveur, de pouvoir modifier la config d’apache, d’héberger beaucoup de sites et de bases de données installer GIT ou node.js, et pas mal d’autres choses impossibles avec un serveur mutualisé par exemple

On verra plus tard comment coupler son serveur EC2 avec deux autres services d’amazon, S3 et CloudFront pour améliorer la vitesse de chargement de son site

C’est gratuit pour une instance micro (613 MiB of memory, up to 2 ECUs (for short periodic bursts), EBS storage only, 32-bit or 64-bit).

Pour en profiter, c’est [par ici](https://aws.amazon.com/ec2) et cliquer sur “signup now”

On se rend ensuite sur l’[EC2 management console](https://console.aws.amazon.com/ec2/v2/home)

[![Aws ec2 console launch instance](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.35.20-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.35.20-AM.png)

Cliquer ensuite sur « launch instance »

[![Aws ec2 console choose ami](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.54.17-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.54.17-AM.png)

On choisi “classic wizard” puis “continue”

[![Aws ec2 console choose ami quick start](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.57.58-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.57.58-AM.png)

ici on sélectionne « Ubuntu Server 12.10 »

[![Aws ec2 console instance details](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.11-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.11-AM.png)

Laisser les paramètres par défaut.

[![Aws ec2 console advanced instance options](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.19-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.19-AM.png)

On laisse une nouvelle fois les paramètres par défaut

[![Aws ec2 console storage device configuration](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.36-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.58.36-AM.png)

Encore une fois on garde les paramètres par défaut pour “storage device configuration”

[![Aws ec2 console tags](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.59.50-AM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-11.59.50-AM.png)

Cliquer sur « continue »

[![Aws ec2 console create a new key pair](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.03.04-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.03.04-PM.png)

A l’étape “create a key pair” on va pouvoir télécharger un certificat qui nous permettra plus tard de se connecter au serveur en ssh ou sftp, choisissez ce que vous voulez pour le nom.

[![Aws ec2 console create a new security group](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.07.39-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.07.39-PM.png)

A l’écran « configure firewall” choisir http dans le menu déroulant “create a new rule” puis “add rule”, ça permettra de pouvoir accéder au serveur depuis un navigateur

[![aws ec2 console review](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.07.55-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.07.55-PM.png)

On arrive au récapitulatif de la config de notre instance, cliquer sur “Launch”

[![aws ec2 console your instances are now launching](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.08.01-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.08.01-PM.png)

Puis sur “close”

[![aws ec2 console running instances](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-6.08.40-PM1-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-6.08.40-PM1.png)

On attend que l’instance se lance, ca devrait prendre quelques secondes, puis on copie le « public DNS », ici : ec2-54-216-58-83.eu-west-1.compute.amazonaws.com.
On pourra aussi y accéder avec l’IP 54.216.58.83.

On va ensuite s’occuper du SSH, pour se connecter en sftp voir [ce post](https://gaelbillon.com/se-connecter-en-sftp-a-une-instance-ec2-avec-transmit/).
Pour se connecter en ssh , ouvrir un terminal, naviguer jusqu’au dossier contenant le fichier pem téléchargé.

Il faut d’abord changer les droit sur le fichier pem

```
chmod 400 aws.pem
```

On peut ensuite se connecter en ssh avec cette commande

```
ssh -i aws.pem ubuntu@ec2-54-216-58-83.eu-west-1.compute.amazonaws.com
```

Le message suivant devrait apparaître.

```
The authenticity of host 'ec2-54-216-58-83.eu-west-1.compute.amazonaws.com (54.216.58.83)' can't be established. RSA key fingerprint is d6:1c:ce:5a:3c:57:d6:1a:4f:55:2e:84:a2:12:55:c5. Are you sure you want to continue connecting (yes/no)?
```

 

Taper « yes »

[![ssh ubuntu aws ec2](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.16.05-PM.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.16.05-PM.png)

Ca y’est on est connecté sur notre serveur !

On va maintenant pouvoir configurer notre serveur.
D’abord, on mes à jour le cache des paquets avec

 

```
sudo apt-get update
```

 

On va ensuite installer apache mysql et php avec cette commande (avec le “^ » a la fin).

```
sudo apt-get install lamp-server^
```

[![ssh ubuntu ec2 install mysql](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-07-at-7.42.38-PM.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-07-at-7.42.38-PM.png)

A cette étape on choisi un mot de passe pour mysql.

A la fin de l’installation, le serveur est operationnel ! On peut verifier en se rendant à l ‘adresse du serveur depuis un naviguateur.

[![apache ec2 ubuntu it works](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.18.50-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.18.50-PM.png)

Il ne reste plus qu’a installer phpmyadmin

```
sudo apt-get install phpmyadmin
```

[![ssh ubuntu ec2 install phpmyadmin](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.19.21-PM.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.19.21-PM.png)
A cette étape on choise apache

[![ssh ubuntu ec2 install phpmyadmin choose server](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-07-at-7.56.11-PM.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-07-at-7.56.11-PM.png)

Puis no a la question “Configure database for phpmyadmin with dbconfig-common?”

On va ensuite ouvrir le fichier de configuration d’apache

```
sudo nano /etc/apache2/apache2.conf
```

et y inclure la configuration de phpmyadmin. Copier coller la ligne suivante :

```
Include /etc/phpmyadmin/apache.conf
```

[![configure apache phpmyadmin ubuntu ec2](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.22.32-PM.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.22.32-PM.png)

Il faut maintenant redemarrer apache pour que les changements de configuration soient pris en compte.

```
sudo service apache2 restart
```

on peut maintenant acceder a phpmyadmin à cette adresse

```
ec2-54-216-58-83.eu-west-1.compute.amazonaws.com/phpmyadmin
```

[![ubuntu ec2 login phpmyadmin](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.23.53-PM-1024x640.png)](https://gaelbillon.com/wp-content/uploads/2013/05/Screen-shot-2013-05-10-at-12.23.53-PM.png)

login : root
mot de passe : celui utilisé lors de l’installation de mysql
Dans le [prochain post](https://gaelbillon.com/creer-un-virtual-host-une-elastic-ip-et-rediriger-son-domaine-vers-ec2/) on vera comment configurer un virtualhost, créer une elasctic ip et rediriger un domaine existant vers ec2