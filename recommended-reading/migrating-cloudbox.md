# Migrating Cloudbox

This guide will outline some basic steps to copy/move your Cloudbox setup to another server and/or another domain name.

Listed below are some common scenarios and their migration instructions.

## Move Cloudbox to Another Server and Keep the Same Domain Name

### Previous Server

1. [Backup](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-backup) your current Cloudbox server.

### New Server

1. [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) Cloudbox to the new server \(skip steps \#7 and \#8 for now\).
2. If you are not using Cloudflare:
   * Point your domain's \[\[DNS\|Prerequisites: Domain Name\]\] to the new server.
3. Install the relevant Cloudbox type: \[\[Cloudbox\|Install: Cloudbox\]\], \[\[Mediabox\|Install: Mediabox\]\], or \[\[Feederbox\|Install: Feederbox\]\] \(step \#7 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
4. Install any extra, not-default containers you had installed previously \(step \#8 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
5. Check to see if your \[\[Plex Autoscan URL\|Install: Plex Autoscan\#3-obtaining-the-plex-autoscan-url\]\] has changed and update \[\[Sonarr\|Install: Sonarr\#plex-autoscan\]\], \[\[Radarr\|Install: Radarr\#plex-autoscan\]\], and \[\[Lidarr\|Install: Lidarr\#plex-autoscan\]\], accordingly.

## Move Cloudbox to Another Server and Change the Domain Name

### Previous Server

1. [Backup](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-backup) your current Cloudbox server.
2. \[\[Revoke\|Revoking SSL Certificates\]\] your domain's SSL certificates.[\[1\]](migrating-cloudbox.md#f1)

### New Server

1. [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) Cloudbox to the new server \(skip steps \#7 and \#8 for now\).
2. Add in your new domain name into \[\[settings\|Install: Settings\]\].
3. If you are using Cloudflare:
   1. Register your domain with \[\[Cloudflare\|Prerequisites: Cloudflare\]\].
   2. Add the Cloudflare API into \[\[settings\|Install: Settings\]\].
4. If you are not using Cloudflare:
   * Point your new domain's \[\[DNS\|Prerequisites: Domain Name\]\] to the new server.
5. Replace the domain name in app specific config files:
   * `/opt/cloudplow/config.json`
   * `/opt/emby/config/system.xml` \(only if installed\)
   * `/opt/motd/config.json`
   * `/opt/traktarr/config.json` \(only if installed\)
   * `/opt/plex_dupefinder/config.json` \(only if installed\)
   * `/opt/plex_patrol/settings.ini` \(only if installed\)
   * `/opt/sabnzbd/app/sabnzbd.ini` \(only if installed\)
6. Install the relevant Cloudbox type: \[\[Cloudbox\|Install: Cloudbox\]\], \[\[Mediabox\|Install: Mediabox\]\], or \[\[Feederbox\|Install: Feederbox\]\] \(step \#7 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
7. Install any extra, not-default containers you had installed previously \(step \#8 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
8. Check to see if your \[\[Plex Autoscan URL\|Install: Plex Autoscan\#3-obtaining-the-plex-autoscan-url\]\] has changed and update \[\[Sonarr\|Install: Sonarr\#plex-autoscan\]\], \[\[Radarr\|Install: Radarr\#plex-autoscan\]\], and \[\[Lidarr\|Install: Lidarr\#plex-autoscan\]\], accordingly.

## Keep Cloudbox on the Same Server but Change the Domain Name

1. [Backup](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-backup) your current Cloudbox server \(Optional, but recommended\).
2. \[\[Revoke\|Revoking SSL Certificates\]\] your domain's SSL certificates.[\[1\]](migrating-cloudbox.md#f1)
3. Add in your new domain name into \[\[settings\|Install: Settings\]\].
4. If you are using Cloudflare:
   1. Register your domain with \[\[Cloudflare\|Prerequisites: Cloudflare\]\].
   2. Add the Cloudflare API into \[\[settings\|Install: Settings\]\].
5. If you are not using Cloudflare:
   * Point your new domain's \[\[DNS\|Prerequisites: Domain Name\]\] to the server.
6. Replace the domain name in app specific config files:
   * `/opt/cloudplow/config.json`
   * `/opt/emby/config/system.xml` \(only if installed\)
   * `/opt/motd/config.json`
   * `/opt/traktarr/config.json` \(only if installed\)
   * `/opt/plex_dupefinder/config.json` \(only if installed\)
   * `/opt/plex_patrol/settings.ini` \(only if installed\)
   * `/opt/sabnzbd/app/sabnzbd.ini` \(only if installed\)
7. Install the relevant Cloudbox type: \[\[Cloudbox\|Install: Cloudbox\]\], \[\[Mediabox\|Install: Mediabox\]\], or \[\[Feederbox\|Install: Feederbox\]\] \(step \#7 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
8. Install any extra, not-default containers you had installed previously \(step \#8 of the [Restore](https://github.com/Cloudbox/gitbook/tree/4d7c0c5c8a2a3701c6b4104a930afe4866e08420/Cloudbox-Backup-and-Restore/README.md#cloudbox-restore) instructions\).
9. Check to see if your \[\[Plex Autoscan URL\|Install: Plex Autoscan\#3-obtaining-the-plex-autoscan-url\]\] has changed and update \[\[Sonarr\|Install: Sonarr\#plex-autoscan\]\], \[\[Radarr\|Install: Radarr\#plex-autoscan\]\], and \[\[Lidarr\|Install: Lidarr\#plex-autoscan\]\], accordingly.
10. Remove any files that contain your domain name in `/opt/nginx-proxy/vhost.d`. nginx will re-generate them automatically for your new domain. maually change the contents of any file in `/opt/nginx-proxy/conf.d` to point to your new domain. Not doing either of these steps will cause nginx to have issues restarting and will lead to "Page cannot be found" errors when attempting to browse to your services.

[**1**](migrating-cloudbox.md#a1) This will free up the domain name from Let’s Encrypt and you will be able to use it in the future without having to wait for the previous certificates to expire \(~90 days\).

