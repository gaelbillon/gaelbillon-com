---
title: "Create a SFTP user restricted to a /var/www/ directory on Ubuntu/Debian"
date: "2020-04-15T12:46:44.000Z"
template: "post"
draft: false
slug: "create-a-sftp-user-restricted-to-a-var-www-directory-on-ubuntu-debian"
category: "Webdev"
tags: 
  - "acl"
  - "debian"
  - "English"
  - "pll_5e9702363d134"
  - "sftp"
  - "ubuntu"
  - "Webdev"
description: ""
---

```
sudo nano /etc/ssh/sshd_config
```

The line `Subsystem sftp /usr/lib/openssh/sftp-server` needs to be commented and a new line must be added right below `Subsystem sftp internal-sftp right below`

```
#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp
```

Then go to the end of the file and add the following lines

```
Match Group sftpusers
    # Below, %u stands for user
    ChrootDirectory /home/%u
    X11Forwarding no
    AllowTcpForwarding no
    AllowAgentForwarding no
    PermitTunnel no

```

The lines below `Match Group` will apply only to this group

`ChrootDirectory` is the directory where the ftp user will be chrooted (restricted)

Other variables

- %u (username)
- %U (numeric user ID of the target user)
- %h (user home directory)

More info : [https://man.openbsd.org/sshd\_config#TOKENS](https://man.openbsd.org/sshd_config#TOKENS)

```
sudo service sshd restart
sudo mkdir user1/site1/
sudo addgroup sftpusers
sudo adduser user1
```

Add new user to sftpusers group

```
sudo usermod -a -G sftpusers user1
```

User directory must be owned by root

```
sudo chown -R root:root /home/user1
```

Create a directory to bind the site1 directory from `/var/www/site1/`

```
Sudo mkdir /home/user1/site1/
```

Edit fstab to bind the directory (this will persist across reboots)

```
Sudo nano /etc/fstab
```

Add this line to fstab file

```
/var/www/site1/ /home/user1/site1/ none bind 0 0
```

Then mount the new bind

```
sudo mount -a
```

Ifyou don't need the bind to persist across reboots you can use this command:

```
mount --bind /var/www/orpheogroup-ru-refonte/ /home/mikhail/orpheogroup-ru-refonte/
```

Check bind with:

```
ls -la /home/user1/
```

If you want to check to which user and group belong a directory you may use:

```
stat -c "%U %G" /var/www/site1/
```

Or

```
 ls -la /var/www/
```

Then we need to use File Access Control Lists to set permissions for groups

```
sudo setfacl -Rm d:g:sftpusers:rwx,g:sftpusers:rwx /var/www/site1/
sudo setfacl -Rm d:g:www-data:rwx,g:www-data:rwx /var/www/site1/
```

- \-R for recursive
- m for modify existing permissions and ownerships
- d is for default
- g is for group

The above should be sufficient but if you ever need to set permissions for a user you may use `u:`

```
sudo setfacl -Rm d:u:user1:rwx,u:user1:rwx /home/user1/site1/
```

You may remove ACL with -x as below:

```
sudo setfacl -x g:sftpusers /var/www/site1/
```

And getfacl to read the ACL

```
sudo getfacl /var/www/site1/
```

It should look like that

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

And to ensure that newly created files get the right permissions for www-data:

```
sudo setfacl -Rm d:g:www-data:rwx /var/www/ 
```

That's it, you may now try to connect with a FTP client such as CyberDuck or open a terminal (on mac)

```
sftp user1@xxx.xxx.xxx.xxx (<- IP address or name of the server)
```

## This part is optional, I needed another sftp user to the same folder but without write rights (read only). Skip if you don't need it

Insert these lines at the end of sshd\_config

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
