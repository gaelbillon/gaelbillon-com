---
title: "Créer un utilisateur SFTP limité à un répertoire /var/www/ sur Ubuntu/Debian"
date: "2020-04-15T09:25:55.000Z"
template: "post"
draft: false
slug: "creer-un-utilisateur-sftp-limite-a-un-repertoire-var-www-sur-ubuntu-debian"
category: "Dev web"
tags: 
  - "acl"
  - "debian"
  - "Dev web"
  - "Français"
  - "pll_5e9702363d134"
  - "sftp"
  - "ubuntu"
description: ""
---

```
sudo nano /etc/ssh/sshd_config
```

La ligne `Subsystem sftp /usr/lib/openssh/sftp-server` doit être commentée et une nouvelle ligne doit être ajoutée juste en dessous `Subsystem sftp internal-sftp`

```
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
```

Ensuite, allez à la fin du fichier et ajoutez les lignes suivantes

```
Match Group sftpusers
    # Below, %u stands for user
    ChrootDirectory /home/%u
    X11Forwarding no
    AllowTcpForwarding no
    AllowAgentForwarding no
    PermitTunnel no

```

Les lignes sous `Match Group` s'appliqueront uniquement à ce groupe

`ChrootDirectory` est le répertoire où l'utilisateur ftp sera "chrooté" (restreint)

Autres variables

- %u (nom d'utilisateur)
- %U (ID de l'utilisateur)
- %h (répertoire de l'utilisateur)

Plus d'infos : [https://man.openbsd.org/sshd\_config#TOKENS](https://man.openbsd.org/sshd_config#TOKENS)

```
sudo service sshd restart
sudo mkdir user1/site1/
sudo addgroup sftpusers
sudo adduser user1
```

Ajouter un nouvel utilisateur au groupe sftpusers

```
sudo usermod -a -G sftpusers user1
```

Le répertoire doit appartenir à root

```
sudo chown -R root:root /home/user1
```

Créer un répertoire pour binder le répertoire `site1` à partir de `/var/www/site1/`

```
Sudo mkdir /home/user1/site1/
```

Editer fstab pour bind le répertoire (cela persistera même après reboot)

```
Sudo nano /etc/fstab
```

Ajouter cette ligne au fichier fstab

```
/var/www/site1/ /home/user1/site1/ none bind 0 0
```

Monter le nouveau bind

```
sudo mount -a
```

Si vous n'avez pas besoin que le bind persiste après un redémarrage, vous pouvez utiliser cette commande :

```
mount --bind /var/www/orpheogroup-ru-refonte/ /home/mikhail/orpheogroup-ru-refonte/
```

Vérifier le bind avec :

```
ls -la /home/user1/
```

Si vous voulez vérifier à quel utilisateur et à quel groupe appartient un répertoire, vous pouvez utiliser :

```
stat -c "%U %G" /var/www/site1/
```

Ou

```
 ls -la /var/www/
```

Ensuite, nous devons utiliser les listes de contrôle d'accès aux fichiers pour définir les autorisations des groupes

```
sudo setfacl -Rm d:g:sftpusers:rwx,g:sftpusers:rwx /var/www/site1/
sudo setfacl -Rm d:g:www-data:rwx,g:www-data:rwx /var/www/site1/
```

- R pour récursif
- m pour modifier les autorisations et les régimes de propriété existants
- d pour default
- g pour group

Ce qui précède devrait être suffisant, mais si vous avez besoin de définir des autorisations pour un utilisateur, vous pouvez utiliser `u:`

```
sudo setfacl -Rm d:u:user1:rwx,u:user1:rwx /home/user1/site1/
```

Vous pouvez supprimer l'ACL avec -x comme ci-dessous :

```
sudo setfacl -x g:sftpusers /var/www/site1/
```

Et getfacl pour lire l'ACL

```
sudo getfacl /var/www/site1/
```

Ca devrait ressembler à ça

```
# file: var/www/site1/
# owner: root
# group: www-data
# flags: -s-
user::rwx
group::rwx
group:www-data:rwx
group:sftpusers:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:sftpusers:rwx
default:mask::rwx
default:other::r-x
```

Et pour s'assurer que les fichiers nouvellement créés obtiennent les bonnes permissions pour www-data :

```
sudo setfacl -Rm d:g:www-data:rwx /var/www/ 
```

C'est tout, vous pouvez maintenant essayer de vous connecter avec un client FTP tel que CyberDuck ou ouvrir un terminal (sur mac)

```
sftp user1@xxx.xxx.xxx.xxx (<- IP address or name of the server)
```

## Cette partie est optionnelle, j'avais besoin d'un autre utilisateur sftp dans le même dossier mais sans droits d'écriture (lecture seule). Passer si vous n'en avez pas besoin

Insérez ces lignes à la fin de sshd\_config

```
sudo nano /etc/ssh/sshd_config
```

```
Match User user2
  ChrootDirectory /home/%u
  # Below, "-R" stands for "read only"
  ForceCommand internal-sftp -R
```

```
sudo service sshd restart
Sudo mkdir /home/user2/site1/
Sudo nano /etc/fstab
```

```
/var/www/site1/ /home/user2/site1/ none bind 0 0
```

```
sudo mount -a
sudo addgroup sftpusers
sudo adduser user1
sudo usermod -a -G sftpusers user2
sudo chown -R root:root /home/user2
Sudo mkdir /home/user1/site1/
```
