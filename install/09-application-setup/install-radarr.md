# Radarr

1. [URL](install-radarr.md#1-url)
2. [Settings](install-radarr.md#2-settings)
   1. [General](install-radarr.md#i-general)
   2. [Media Management](install-radarr.md#ii-media-management)
   3. [Download Client](install-radarr.md#iii-download-client)
      * [NZBGet](install-radarr.md#nzbget)
      * [ruTorrent](install-radarr.md#rutorrent)
   4. [Indexers](install-radarr.md#iv-indexers)
      * [NZBHydra2](install-radarr.md#nzbhydra2)
      * [Jackett](install-radarr.md#jackett)
   5. [Connect](install-radarr.md#v-connect)
      * [Torrent Cleanup](install-radarr.md#torrent-cleanup)
      * [Plex Autoscan](install-radarr.md#plex-autoscan)
3. [Movies Path](install-radarr.md#3-movies-path)
4. [API Key](install-radarr.md#4-api-key)

## 1. URL

* To access Radarr, visit [https://radarr.\_yourdomain.com\_](https://radarr._yourdomain.com_)

## 2. Settings

### i. General

1. Go to "Settings" -&gt; "General".
2. Set "Advanced Settings": `Shown`

#### Start-Up

* "Bind Address: `*`
* "Port Number": `7878`
* "URL Base": _blank_
* "Enable SSL": `No` \(_SSL is handled by Nginx-Proxy_\)
* "Open browser on start": `No`

#### Security

* "Authentication": `Forms (Login page)` \(_can also be set to `Basic (Browser popup)`_\)
* "Username": _your Radarr username_
* "Password": _your Radarr password_

#### Proxy Settings

* "Use Proxy": `No`

#### Logging

* "Log Level": `Debug`

#### Analytics

* "Enable": `No` \(_your preference_\)

#### Updates

* "Branch": `nightly` or `develop`
* "Automatic": `Off`

#### Save

* Click "Save".

### ii. Media Management

1. Go to "Settings" -&gt; "Media Management".
2. Set "Advanced Settings": `Shown`

#### Movie Naming

* "Rename Movies": `Yes`
* "Replace Illegal Characters": `Yes`
* Colon Replacement Format: `Delete`

  _Note: You could use `Replace with Space Dash` but only if your file naming format is not using spaces \(e.g. using dots\) to separate words._

* Set your preferred naming format \(you can use the ones mentioned below - CLICK to expand\).

   Plex's Naming Preference   


  Example:   


  ```text
    /Guardians of the Galaxy (2014)/Guardians of the Galaxy (2014).mkv
  ```

  Standard Movie Format:   


  ```text
    {Movie Title} ({Release Year})
  ```

  Movie Folder Format:   


  ```text
    {Movie Title} ({Release Year})
  ```

  Reference: [https://support.plex.tv/articles/200381023-naming-movie-files/](https://support.plex.tv/articles/200381023-naming-movie-files/)   
   &lt;/details&gt;  

Radarr's Wiki Example  
 Example:  
 \`\`\` The Movie Title \(2010\) - \[ULTIMATE EXTENDED EDITION\]\[BLURAY-1080P PROPER\]\[DTS 5.1\]\[X264\]-EVOLVE.mkv \`\`\` Standard Movie Format:  
 \`\`\` {Movie Title} \({Release Year}\) - {\[EDITION TAGS\]}{\[QUALITY FULL\]}{\[MEDIAINFO AUDIOCODEC}{ MEDIAINFO AUDIOCHANNELS\]}{\[MEDIAINFO VIDEOCODEC\]}{-RELEASE GROUP} \`\`\` Reference: https://github.com/Radarr/Radarr/wiki/Sorting-and-Renaming  
Desimaniac's Naming Guide  
 Example:  
 \`\`\` /Guardians of the Galaxy \(2014\)/Guardians.of.the.Galaxy.2014.1080p.BluRay.x264-SPARKS.mkv \`\`\` Reference: https://github.com/desimaniac/docs/blob/master/my\_sonarr\_and\_radarr\_naming\_guide.md

#### Folders

* "Create empty movie folders": `No`
* "Automatically Rename Folders": `No`
* "Movie Paths Default to Static": `No`

#### Importing

* "Skip Free Space Check": `No`
* "Use Hardlinks instead of Copy": `No`
* "Import Extra Files": `Yes` \(_can your preference_\)
* "Extra File Extensions": `srt, sub, idx`

#### File Management

* "Ignore Deleted Movies": `No` \(_can be your preference_\)
* "Download Propers": `No` \(_can be your preference_\)
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
   5. Username: \[\[Your NZBGet Username\|Install: NZBGet\#security\]\]
   6. Password: \[\[Your NZBGet Password\|Install: NZBGet\#security\]\]
   7. Category: `radarr`
   8. Use SSL: `No`
   9. Add Paused: `No`
3. Your settings will look like this:

   ![Radarr NZBGet Downloader](https://i.imgur.com/PxgKer9.png)

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
   7. Username: \[\[Your ruTorrent Username\|Install: ruTorrent\#login\]\]
   8. Password: \[\[Your ruTorrent Password\|Install: ruTorrent\#login\]\]
   9. Category: `radarr`
   10. Directory: _Leave Blank_
3. Your settings will now look like this:

   ![Radarr ruTorrent Downloader](http://i.imgur.com/XHB6NN2.png)

4. Click "Save" to add ruTorrent.

### iv. Indexers

1. Go to "Settings" -&gt; "Indexers".
2. Set "Advanced Settings": `Shown`
3. Add in your your favorite \[\[indexers\|Prerequisites: Usenet vs BitTorrent\]\].

#### NZBHydra2

1. Click "Settings" -&gt; "Indexers".
2. Click Add Indexer \(`+`\).
3. Select "Newznab".
4. Add the following:
   1. Name: NZBHydra2
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: `http://nzbhydra2:5076`
   5. API Key: \[\[Your NZBHydra2 API Key\|Install: NZBHydra2\#4-api-key\]\]
   6. Additional Parameters: _Leave Blank_
5. Your settings will look like this:

   ![Radarr NZBHydra2](https://i.imgur.com/LRANTOU.png)

6. Click "Save" to add NZBHydra2.

Note: The "Test" will keep failing until you add an indexer in \[\[NZBHydra2\|Install: NZBHydra2\]\].

#### Jackett

Note: Each Indexer will need to be added separately.

1. Click "Settings" -&gt; "Indexers".
2. Click Add Indexer \(`+`\)
3. Select "Torznab".
4. Add the following:
   1. Name: Indexer Name
   2. Enable RSS Sync: _Your Preference_
   3. Enable Search: _Your Preference_
   4. URL: \[\[Indexer's Torznab Feed\|Install: Jackett\#3-adding-indexers-to-sonarrradarr\]\]
   5. API Key: \[\[Your Jackett API Key\|Install: Jackett\#3-adding-indexers-to-sonarrradarr\]\]
   6. Additional Parameters: _Leave Blank_
5. Your settings will look like this:

   ![Radarr Jackett](https://i.imgur.com/T9vrrAW.png)

6. Click "Save" to add the indexer.

### v. Connect

#### Torrent Cleanup

Torrent Cleanup Script is a custom script that will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if the script detects that `.rar` files are in the folder that Radarr just imported from, it will delete the imported video file\(s\), leaving just the `.rar` files for seeding.

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

   ![Radarr Torrent Cleanup Script CloudBox](https://i.imgur.com/j4FV9ky.png)

5. Click "Save" to add the Torrent Cleanup script.

#### Plex Autoscan

1. Click "Settings" -&gt; "Connect".
2. Add a new "Webhook".
3. Add the following:
   1. Name: Plex Autoscan
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename: `Yes`
   6. Filter Movie Tags: _Leave Blank_
   7. URL: \[\[Your Plex Autoscan URL\|Install: Plex-Autoscan\#4-obtaining-the-plex-autoscan-url\]\]
   8. Method:`POST`
   9. Username: _Leave Blank_
   10. Password: _Leave Blank_
4. The settings will look like this:

   ![Radarr Plex Autoscan](https://i.imgur.com/jQJyvMA.png)

5. Click "Save" to add Plex Autoscan.

### 3. Movies Path

1. When you are ready to add your first movie to Radarr, click the "Path" drop-down and select "Add a different path".
2. Click the blue "Browse" button, select the `movies` folder, scroll to the bottom, and select "OK".
3. Click the green "check" button to add the path.
4. All movies added now will have that path set.

### 4. API Key

This is used during the setup of \[\[Ombi\|Install: Ombi\]\] and \[\[Organizr\|Install: Organizr\]\].

* Go to "Settings" -&gt; "General" -&gt; "Security" -&gt; "API Key".

