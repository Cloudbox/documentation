# Heimdall

1. [Intro](extras-heimdall.md#1-intro)
2. [URL](extras-heimdall.md#2-url)
3. [Initial Setup](extras-heimdall.md#3-initial-setup)
   1. [Domain](extras-heimdall.md#i-domain)
   2. [Install](extras-heimdall.md#ii-install)
   3. [Login](extras-heimdall.md#iii-login)
4. [Customizing](extras-heimdall.md#4-customizing)
   1. [Adding Items](extras-heimdall.md#i-adding-items)
   2. [Organizing](extras-heimdall.md#ii-organizing)
   3. [Tags](extras-heimdall.md#iii-tags)
   4. [Settings](extras-heimdall.md#iv-settings)
5. [Supported Applications](extras-heimdall.md#5-supported-applications)

## 1. Intro

[Heimdall](https://heimdall.site/) is a dashboard for all your web applications and any other links you like to add. It can be set as your browser's start page, with the ability to include a search bar using either Google, Bing, or DuckDuckGo.

![alt text](https://i.imgur.com/MrC4QpN.gif)

## 2. URL

To access Heimdall, visit [https://heimdall.\_yourdomain.com\_](https://heimdall._yourdomain.com_)

## 3. Initial Setup

### i. Domain

See \[\[Adding a Subdomain\|Adding a Subdomain\]\] on how to add the subdomain `heimdall` to your DNS provider.

_Note: You can skip this step if you are using \[\[Cloudflare\|Prerequisites: Cloudflare\]\] with Cloudbox._

### ii. Install

Run the following commands:

```bash
 cd ~/cloudbox/
 sudo ansible-playbook cloudbox.yml --tags heimdall
```

### iii. Login

Login settings are preset out of the box \(`user` / `passwd` as set in \[\[accounts.yml\|Install: Settings\]\]\).

## 4. Customizing

You are not limited to just the applications on your server with Heimdall. You can use it for anything, including all your bookmarks and your favorite search engine.

### i. Adding Items

1. You can add items to Heimdall by clicking the _items_ tab follow by the _add_ button.

   ![](https://i.imgur.com/0c5jFEx.png)

   ![](https://i.imgur.com/3OLPW88.png)

2. Many of the applications that you may use have logos and hex colors filled in. You are able to change these if needed, however, not all of your applications will have these and you will have to do it manually.

   ![](https://i.imgur.com/pydRkW7.png)

3. In the picture above, you will see a spot to login at the bottom. This is not used for every application as some will require just an API key. This allows you to have a quick glance at the service, pictured below.

   ![](https://i.imgur.com/1Mkwze1.png)

### ii. Organizing

1. Clicking this _switch_ allows you reorganize your tabs. This is very helpful after adding a whole bunch, in no certain order.

   ![](https://i.imgur.com/mxNEvpp.png)

2. You now be able to drag and drop. You will also see a _pin_ tab, which will disappear when you exit out.

   ![](https://i.imgur.com/o9dB7us.png)

3. This allows you to add and remove items very fast, while saving them for later.
4. If for any reason your tabs are not showing current information you can refresh with the _refresh_ button.

   ![](https://i.imgur.com/Ctm2nyq.png)

### iii. Tags

Have a lot of stuff? Want to organize each service? The _tags_ work much like a folder, where you can place items inside. You can even stack them on top of each other.

1. Just add a tag like you would a normal application. Then you can assign applications to the tag when setting up or editing them.

   ![](https://i.imgur.com/hsLOlXk.png)

2. The tag is seen with a tag symbol on the right.

   ![](https://i.imgur.com/gxtblyb.png)

### iv. Settings

In the _settings_ menu you can find the options to update, change the background, and even add a search engine to it.

![](https://i.imgur.com/tFyp4Br.png)

![](https://i.imgur.com/C7hLmrd.png)

## 5. Supported Applications

You can add your own applications to Heimdall, but below are the predefined ones. There are two different types. _Foundation_ apps are your basic applications without any api access. _Enhanced_ apps can have additional information to provide a quick glance at them.

**Enhanced**

* Couchpotato
* Tautulli
* Pihole
* Sabnzbd
* NZBGet
* RuneAudio

**Foundation**

* Watcher
* OpenMediaVault
* Krusader
* Airsonic
* Glances
* Dokuwiki
* SickRage
* Gitea
* Ombi
* TT-RSS
* Graylog
* NZBHydra
* NZBHydra2
* Medusa
* Deluge
* rTorrent/ruTorrent
* OPNSense
* Netdata
* Lidarr
* Sonarr
* Radarr
* pFsense
* UniFI
* Portainer
* Plex
* Emby
* Duplicati
* JDownloader
* openHAB
* McMyAdmin
* Plexrequests
* Traefik
* Nextcloud

_This guide and the Ansible role were initially submitted by Captain-NaCl._

