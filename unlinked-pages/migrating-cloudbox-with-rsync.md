# Migrating-Cloudbox-with-Rsync.md

\(work in progress\)

Useful for migrating server to server.

## Overview

1. Destination
   1. Dependencies
   2. Preinstall
   3. Login as user
   4. Setup and enable rsync server
   5. Create backup folder.
2. Source
   1. Create SSH key
   2. Send SSH key to Destination server.
   3. Test rsync URL.
   4. Setup backup config.
   5. Run backup.
3. Destination
   1. Verify local backup folder has backup tarballs.
   2. Run restore

## 1. Destination

### Setup and Enable Rsync Server

```text
sudo nano /etc/rsyncd.conf
```

Format:

```text
[rsync_name]
    path = /path/to/backups/as/specified/in/local/destination/in/backup_config.yml
    comment = Backup folder
    uid = seed
    gid = seed
    read only = no
    list = yes
```

Example:

```text
[backup]
    path = /home/seed/Backups/Cloudbox/Cloudbox
    comment = Backup folder
    uid = seed
    gid = seed
    read only = no
    list = yes
```

Start Rsync:

```text
sudo systemctl start rsync
```

## 2. Source

### 1. Create SSH Key

ssh-keygen

```text
➜ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/seed/.ssh/id_rsa):
Created directory '/home/seed/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/seed/.ssh/id_rsa.
Your public key has been saved in /home/seed/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:PLaFOPjdddFV2ePo6hRnctslaeWEq9wLnbD89/rkkVE seed@mediaserver
The key's randomart image is:
+---[RSA 2048]----+
|          .o   oo|
|         .. o .. |
|      . .  . . .E|
|     . * .  o .o.|
|    . = S +=+*+o.|
|     . = * *O++oo|
|      . o o..o.+.|
|         ..   ooo|
|         ..   .+=|
+----[SHA256]-----+
```

### Send SSH Key to destination

```text
ssh-copy-id -i ~/.ssh/id_rsa seed@ipaddress
```

Type in your password to confirm.

```text
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/user/seed/.ssh/id_rsa.pub"

Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'seed@newserveripaddress'"
and check to make sure that only the key(s) you wanted were added.
```

### Test Rsync

Format

```text
rsync -rdt rsync://user@newserveripaddress/rsync_name
```

Example:

```text
rsync -rdt rsync://seed@1.2.3.4/backup
```

### Backup Config

backup\_config.yml

Format:

```yaml
rsync:
  enable: true
  destination: rsync://user@newserveripaddress/rsync_name
```

Example:

```yaml
local:
  enable: false
  destination: /home/{{user}}/Backups/Cloudbox/Cloudbox
rclone:
  enable: false
  destination: whatever
rsync:
  enable: true
  destination: rsync://seed@1.2.3.4/backup
```

