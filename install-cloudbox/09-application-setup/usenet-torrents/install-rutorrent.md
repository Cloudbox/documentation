# ruTorrent

[ruTorrent](https://github.com/Novik/ruTorrent) \(by Novik\) is a front-end for the popular, lightweight, and extensible BitTorrent client [rtorrent](https://github.com/rakshasa/rtorrent) \(by Jari Sundell aka rakshasa\).

_Note: public trackers are disabled by default in the standard install. Refer to the FAQ for_ [_instructions on re-enabling them_](../../../troubleshooting/faq-from-cb.md#enable-access-to-public-torrent-trackers)_._

![](https://i.imgur.com/30dxlTc.png)

## 1. URL

* To access ruTorrent, visit [https://rutorrent.\_yourdomain.com\_](https://rutorrent._yourdomain.com_)

## 2. Basics

### Login

Login settings are preset out of the box \(`user` / `passwd` as set in [accounts.yml](../../03-install-accounts.yml.md).

_Note: If you need to change the password after installing Cloudbox, see the_ [_FAQ_](../../../troubleshooting/faq-from-cb.md#change-rutorrent-password-after-installation)_._

### Setup

The setup for [Sonarr](../media-pvrs/install-sonarr.md), [Radarr](../media-pvrs/install-radarr.md), and [Lidarr](../media-pvrs/install-lidarr.md) are done on their respective wiki pages.

## 3. Enable AutoUnpack

AutoUnpack is a plugin that will automatically unrar/unzip torrent data.

_This will allow Sonarr/Radarr/Lidarr to import the media files that would otherwise be ignored. After Sonarr and Radarr import the media files,_ [_Torrent Cleanup Script_](../../../reference/reference-cloudbox-tools.md#torrent-cleanup-script) _will then delete the extracted media files and ruTorrent will continue to seed the torrents \(until they are either removed manually or automatically via ruTorrent's Ratio Group rules\)._

To enable AutoUnpack:

1. Open "Settings" by clicking the gear icon ![](https://github.com/Novik/ruTorrent/wiki/images/icon06settings.png) at the top
2. Go to "Unpack" on the left.
3. Check "Enable autounpacking if torrents label matches filter" and add the following:

   ```text
   /.*(radarr|sonarr|lidarr).*/i
   ```

4. Leave the other fields blank.
5. Your settings will now look like this:

   ![](https://i.imgur.com/LqE16E1.png)

6. Click "OK".

## 3. Custom Plugins and Themes

You can have custom plugins and themes imported during Docker container rebuild. Just place them in the following paths:

```text
/opt/rutorrent/plugins/
```

```text
/opt/rutorrent/themes/
```

And then restart the Docker container:

```text
docker restart rutorrent
```

