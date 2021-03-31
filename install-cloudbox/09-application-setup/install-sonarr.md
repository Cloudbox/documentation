# Sonarr

1. [URL](install-sonarr.md#1-url)
2. [Settings](install-sonarr.md#2-settings)
   1. [General](install-sonarr.md#i-general)
   2. [Media Management](install-sonarr.md#ii-media-management)
   3. [Download Client](install-sonarr.md#iii-download-client)
      * [NZBGet](install-sonarr.md#nzbget)
      * [ruTorrent](install-sonarr.md#rutorrent)
   4. [Indexers](install-sonarr.md#iv-indexers)
      * [NZBHydra2](install-sonarr.md#nzbhydra2)
      * [Jackett](install-sonarr.md#jackett)
   5. [Connect](install-sonarr.md#v-connect)
      * [Torrent Cleanup](install-sonarr.md#torrent-cleanup)
      * [Plex Autoscan](install-sonarr.md#plex-autoscan)
3. [TV Path](install-sonarr.md#3-tv-path)
4. [API Key](install-sonarr.md#4-api-key)

## 1. URL

* To access Sonarr, visit [https://sonarr.\_yourdomain.com\_](https://sonarr._yourdomain.com_)

## 2. Settings

### i. General

1. Go to "Settings" -&gt; "General".
2. Set "Advanced Settings": `Shown`

#### Start-Up

* "Bind Address: `*`
* "Port Number": `8989`
* "URL Base": _blank_
* "Enable SSL": `No` \(_SSL is handled by Nginx-Proxy_\)
* "Open browser on start": `No` \[This setting does not appear in Sonarr v3\]

#### Security

* "Authentication": `Forms (Login page)` \(_can also be set to `Basic (Browser popup)`_\)
* "Username": _your Sonarr username_
* "Password": _your Sonarr password_

#### Proxy Settings

* "Use Proxy": `No`

#### Logging

* "Log Level": `Debug`

#### Analytics

* "Enable": `No` \(_your preference_\)

#### Updates

* "Branch": `phantom-develop`
* "Automatic": `Off`

#### Save

* Click "Save".

### ii. Media Management

1. Go to "Settings" -&gt; "Media Management".
2. Set "Advanced Settings": `Shown`

#### Episode Naming

* "Rename Episodes": `Yes`
* "Replace Illegal Characters": `Yes`
* Set your preferred naming format \(you can use the ones mentioned below - CLICK to expand\).

   Plex's Naming Preference   


  Example:   


  ```text
    /Gotham/Season 01/Gotham - s01e01 - Pilot.mkv
  ```

  Standard Episode Format:   


  ```text
    {Series Title} - s{season:00}e{episode:00} - {Episode Title}
  ```

  Anime Episode Format:   


  ```text
    {Series Title} - s{season:00}e{episode:00} - {Episode Title}
  ```

  Daily Episode Format:   


  ```text
    {Series Title} - {Air-Date} - {Episode Title}
  ```

  Season Folder Format:   


  ```text
    Season {season:00}
  ```

  Multi-Episode Style:   


  ```text
    Prefixed Range
  ```

  Reference: [https://support.plex.tv/articles/200220687-naming-series-season-based-tv-shows/](https://support.plex.tv/articles/200220687-naming-series-season-based-tv-shows/)   

Radarr's Wiki Example  
 Example:

`The Series Title 2010 - S01E01 - [HDTV-720P PROPER][DTS 5.1][X264]-RLSGRP.mkv`

Standard Episode Format:

`{Series Title} - S{season:00}E{episode:00} - {[QUALITY FULL]}{[MEDIAINFO AUDIOCODEC}{ MEDIAINFO AUDIOCHANNELS]}{[MEDIAINFO VIDEOCODEC]}{-RELEASE GROUP}`

Reference: https://github.com/Radarr/Radarr/wiki/Sorting-and-Renaming  


Desimaniac's Naming Guide  
 Example:  


`/Gotham/Season 01/Gotham.S01E01.1080p.BluRay.x264-DEMAND.mkv`

Reference: https://github.com/desimaniac/docs/blob/master/my\_sonarr\_and\_radarr\_naming\_guide.md

#### Folders

* "Create empty series folders": `No`
* "Delete empty folders": `No`

#### Importing

* "Skip Free Space Check": `No`
* "Use Hardlinks instead of Copy": `No`
* "Import Extra Files": `Yes` \(_can be your preference_\)
* "Extra File Extensions": `srt, sub, idx`

#### File Management

* "Ignore Deleted Episodes": `No` \(_can be your preference_\)
* "Download Propers": `Yes` \(_can be your preference_\)
* "Analyse video files": `No`
* "Change File Date": `None`
* "Recycle Bin": _blank_ \(Rclone deletes are sent to Gdrive trash folder, anyway\)

#### Permissions

* Set Permissions: `No`

#### Save

* Click "Save".

### iii. Download Client

1. Go to "Settings" -&gt; "Download Client".
2. Completed Download Handling
   * Enable: `Yes`
   * Remove: `Yes` \(_your preference_\)
3. Failed Download Handling
   * Redownload: `Yes`
   * Remove: `Yes`

#### NZBGet

1. Add a new "NZBGet" download client.
2. Add the following:
   1. Name: NZBGet
   2. Enable: `Yes`
   3. Host: `nzbget`
   4. Port: `6789`
   5. Username: [Your NZBGet Username](install-nzbget.md#security)
   6. Password: [Your NZBGet Password](install-nzbget.md#security)
   7. Category: `sonarr`
   8. Use SSL: `No`
   9. Add Paused: `No`
3. Your settings will now look like this:

   ![Sonarr NZBGet Downloader](https://i.imgur.com/2wUO8l2.png)

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
   9. Category: `sonarr`
   10. Directory: _Leave Blank_
3. Your settings will look like this:

   ![Sonarr ruTorrent Downloader](https://i.imgur.com/LPGPXHc.png)

4. Click "Save" to add ruTorrent.

### iv. Indexers

1. Go to "Settings" -&gt; "Indexers".
2. Set "Advanced Settings": `Shown`
3. Add in your your favorite [indexers](../../prerequisites/prerequisites-usenet-vs-bittorrent.md).

#### NZBHydra2

1. Click Add Indexer \(`+`\).
2. Select "Newznab".
3. Add the following:
   1. Name: NZBHydra2
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: `http://nzbhydra2:5076`
   5. API Path: `/api`
   6. API Key: [Your NZBHydra2 API Key](install-nzbhydra2.md#4-api-key)
   7. Additional Parameters: _Leave Blank_
4. Your settings will look like this:

   ![Sonarr NZBHydra2](https://i.imgur.com/gPJu1Ur.png)

5. Click "Save" to add NZBHydra2.

Note: The "Test" will keep failing until you add an indexer in [NZBHydra2](install-nzbhydra2.md).

#### Jackett

Note: Each Indexer will need to be added separately.

1. Click Add Indexer \(`+`\)
2. Select "Torznab".
3. Add the following:
   1. Name: Indexer's Name
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: [Indexer's Torznab Feed](install-jackett.md#3-adding-indexers-to-sonarr-radarr)
   5. API Path: `/api`
   6. API Key: [Your Jackett API Key](install-jackett.md#3-adding-indexers-to-sonarr-radarr)
   7. Additional Parameters: _Leave Blank_
4. Your settings will look like this:

   \(Note that the screenshot shows an `https` URL; this is incorrect. It should be `http` as described above\)

   ![Sonarr Jackett](https://i.imgur.com/cdFUhnd.png)

5. Click "Save" to add the indexer.

### v. Connect

1. Go to "Settings" -&gt; "Connect".
2. Set "Advanced Settings": `Shown`

#### Torrent Cleanup

Torrent Cleanup Script is a custom script that will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if the script detects that `.rar` files are in the folder that Sonarr just imported from, it will delete the imported video file\(s\), leaving just the `.rar` files for seeding.

1. Add a new "Custom Script".
2. Add the following:
   1. Name: Torrent Cleanup
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename:`No`
   6. Path: `/scripts/torrents/TorrentCleanup.py`
3. The settings will look like this:

   ![Sonarr Torrent Cleanup Script CloudBox](https://i.imgur.com/JHgExVI.png)

4. Click "Save" to add the Torrent Cleanup script.

#### Plex Autoscan

1. Add a new "Webhook".
2. Add the following:
   1. Name: Plex Autoscan
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename: `Yes`
   6. Filter Series Tags: _Leave Blank_
   7. URL: [Your Plex Autoscan URL](install-plex-autoscan.md#3-obtaining-the-plex-autoscan-url)
   8. Method:`POST`
   9. Username: _Leave Blank_
   10. Password: _Leave Blank_
3. The settings will look like this:

   ![Sonarr Plex Autoscan](https://i.imgur.com/NLtXVZJ.png)

4. Click "Save" to add Plex Autoscan.

### 3. TV Path

1. When you are ready to add your first show to Sonarr, click the "Path" drop-down and select "Add a different path".
2. Click the blue "Browse" button, select the `tv` folder, scroll to the bottom, and select "OK".
3. Click the green "check" button to add the path.
4. All TV shows added now will have that path set.

### 4. API Key

This is used during the setup of [Ombi](install-ombi.md) and [Organizr](install-organizr.md).

* Go to "Settings" -&gt; "General" -&gt; "Security" -&gt; "API Key".

