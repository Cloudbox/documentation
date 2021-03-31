# Lidarr

1. [Intro](install-lidarr.md#1-intro)
2. [URL](install-lidarr.md#2-url)
3. [Settings](install-lidarr.md#4-settings)
   1. [General](install-lidarr.md#i-general)
   2. [Media Management](install-lidarr.md#ii-media-management)
   3. [Download Client](install-lidarr.md#iii-download-client)
      * [NZBGet](install-lidarr.md#nzbget)
      * [ruTorrent](install-lidarr.md#rutorrent)
   4. [Indexers](install-lidarr.md#iv-indexers)
      * [NZBHydra2](install-lidarr.md#nzbhydra2)
      * [Jackett](install-lidarr.md#jackett)
   5. [Connect](install-lidarr.md#v-connect)
      * [Torrent Cleanup](install-lidarr.md#torrent-cleanup)
      * [Plex Autoscan](install-lidarr.md#plex-autoscan)
4. [Music Path](install-lidarr.md#5-music-path)
5. [API Key](install-lidarr.md#6-api-key)

## 1. Intro

[Lidarr](https://lidarr.audio) is basically Sonarr for music. It functions as a music collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds from Bittorrent trackers and Usenet Indexers, looking for new tracks from your favorite artists and will grab, sort and rename them. It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available.

![](https://i.imgur.com/MZJEij2.png)

## 2. URL

* To access Lidarr, visit [https://lidarr.\_yourdomain.com\_](https://lidarr._yourdomain.com_)

## 3. Settings

### i. General

1. Go to "Settings" -&gt; "General".
2. Set "Advanced Settings": `Shown`

#### Host

* "Bind Address: `*`
* "Port Number": `8686`
* "URL Base": _blank_
* "Enable SSL": `No` \(_SSL is handled by Nginx-Proxy_\)
* "Open browser on start": `No`

#### Security

* "Authentication": `Forms (Login page)` \(_can also be set to `Basic (Browser popup)`_\)
* "Username": _your Lidarr username_
* "Password": _your Lidarr password_

#### Proxy Settings

* "Use Proxy": `No`

#### Logging

* "Log Level": `Debug`

#### Analytics

* "Send Anonymous Usage Data": `No` \(_your preference_\)

#### Updates

* "Branch": `develop`
* "Automatic": `Off`

#### Save

* Click "Save".

### ii. Media Management

1. Click "Settings" -&gt; "Media Management".
2. Enable "Rename Tracks".
3. Enable "Replace Illegal Characters".
4. Set your preferred naming format \(you can use the ones mentioned below\).

   Plex's Naming Preference  
    Example:  
    \`01 - Shine On You Crazy Diamond \(Parts I-V\).m4a\` Standard Track Format:  
    \`{track:00} - {Track Title}\` Artist Folder Format:  
    \`{Artist Name}\` Album Folder Format:  
    \`{Artist Name} - {Album Title}\` Ref: https://support.plex.tv/articles/categories/media-preparation/naming-and-organizing-music-media/  

5. Disable "Analyse audio files".
6. Click "Save".

### iii. Download Client

1. Click "Settings" -&gt; "Download Client".
2. "Completed Download Handling": `Enabled` Selected \(_your preference_\)
3. "Failed Download Handling": `Redownload` Selected.

#### NZBGet

1. Add a new "NZBGet" download client.
2. Add the following:
   1. Name: NZBGet
   2. Enable: `Yes`
   3. Host: `nzbget`
   4. Port: `6789`
   5. Username: [Your NZBGet Username](install-nzbget.md#security)
   6. Password: [Your NZBGet Password](install-nzbget.md#security)
   7. Category: `lidarr`
   8. Use SSL: `No`
   9. Add Paused: `No`
3. Your settings will now look like this:

   ![Lidarr NZBGet Downloader](https://i.imgur.com/dtwg0dY.png)

4. Click "Save" to add NZBGet.

#### ruTorrent

1. Add a new "rTorrent" download client.
2. Add the following:
   1. Name: ruTorrent
   2. Enable: `Yes`
   3. Host: `rutorrent`
   4. Port: `80`
   5. URL Path: `RPC2`
   6. Use SSL: `No`
   7. Username: [Your ruTorrent Username](install-rutorrent.md#login)
   8. Password: [Your ruTorrent Password](install-rutorrent.md#login)
   9. Category: `lidarr`
   10. Directory: _Leave Blank_
3. Your settings will look like this:

   ![Lidarr ruTorrent Downloader](https://i.imgur.com/NbWHz3c.png)

4. Click "Save" to add ruTorrent.

### iv. Indexers

1. Go to "Settings" -&gt; "Indexers".
2. Set "Advanced Settings": `Shown`
3. Add in your your favorite [indexers](../../prerequisites/prerequisites-usenet-vs-bittorrent.md).

#### NZBHydra2

1. Click "Settings" -&gt; "Indexers".
2. Click Add Indexer \(`+`\).
3. Select "Newznab".
4. Add the following:
   1. Name: NZBHydra2
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: `http://nzbhydra2:5076`
   5. API Path: `/api`
   6. API Key: [Your NZBHydra2 API Key](install-nzbhydra2.md#4-api-key)
   7. Additional Parameters: _Leave Blank_
5. Your settings will look like this:

   ![Lidarr NZBHydra2](https://i.imgur.com/isxTYGV.png)

6. Click "Save" to add NZBHydra2.

Note: The "Test" will keep failing until you add an indexer in [NZBHydra2](install-nzbhydra2.md).

#### Jackett

Note: Each Indexer will need to be added separately.

1. Click "Settings" -&gt; "Indexers".
2. Click Add Indexer \(`+`\)
3. Select "Torznab".
4. Add the following:
   1. Name: Indexer's Name
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: \[\[Indexer's Torznab Feed\|Install: Jackett\#3-adding-indexers-to-sonarrradarr\]\]
   5. API Path: `/api`
   6. API Key: \[\[Your Jackett API Key\|Install: Jackett\#3-adding-indexers-to-sonarrradarr\]\]
   7. Additional Parameters: _Leave Blank_
5. Your settings will look like this:

   ![Lidarr Jackett](https://i.imgur.com/bOhRdSL.png)

6. Click "Save" to add the indexer.

### v. Connect

#### Torrent Cleanup

Torrent Cleanup Script is a custom script that will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if the script detects that `.rar` files are in the folder that Lidarr just imported from, it will delete the imported video file\(s\), leaving just the `.rar` files for seeding.

1. Click "Settings" -&gt; "Connect".
2. Add a new "Custom Script".
3. Add the following:
   1. Name: Torrent Cleanup
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename:`No`
   6. Path: `/scripts/torrents/TorrentCleanup.py`
4. The settings will look like this:

   ![Lidarr Torrent Cleanup Script CloudBox](https://i.imgur.com/i5OsaWi.png)

5. Click "Save" to add the Torrent Cleanup script.

#### Plex Autoscan

**Plex Autoscan no longers work with music libraries as of version 1.18, so this feature will not work.** 

1. Click "Settings" -&gt; "Connect".
2. Add a new "Webhook".
3. Add the following:
   1. Name: Plex Autoscan
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename: `Yes`
   6. URL: [Your Plex Autoscan URL](install-plex-autoscan.md#3-obtaining-the-plex-autoscan-url)
   7. Method:`POST`
   8. Username: _Leave Blank_
   9. Password: _Leave Blank_
4. The settings will look like this:

   ![Lidarr Plex Autoscan](https://i.imgur.com/58MCXxM.png)

5. Click "Save" to add Plex Autoscan.

### 4. Music Path

1. When you are ready to add your first artist to Lidarr, click the "Path" drop-down and select "Add a different path".
2. Click the blue "Browse" button, select the `music` folder, scroll to the bottom, and select "OK".
3. Click the green "check" button to add the path.
4. All artist added now will have that path set.

### 5. API Key

This is used during the setup of [Organizr](install-organizr.md).

* Go to "Settings" -&gt; "General" -&gt; "Security" -&gt; "API Key".

