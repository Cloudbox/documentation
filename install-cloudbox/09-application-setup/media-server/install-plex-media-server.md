# Plex Media Server

1. [URL](install-plex-media-server.md#1-url)
2. [Setup Wizard](install-plex-media-server.md#2-setup-wizard)
3. [Settings](install-plex-media-server.md#3-settings)
   * [Remote Access](install-plex-media-server.md#remote-access)
   * [Library](install-plex-media-server.md#library)
   * [Network](install-plex-media-server.md#network)
   * [Transcoder](install-plex-media-server.md#transcoder)
   * [DLNA](install-plex-media-server.md#dlna)
   * [Scheduled Tasks](install-plex-media-server.md#scheduled-tasks)
4. [Add Media Libraries](install-plex-media-server.md#4-add-media-libraries)
   * [Add the Movie Library](install-plex-media-server.md#add-the-movie-library)
   * [Add the TV Library](install-plex-media-server.md#add-the-tv-library)
5. [Scan Media Libraries](install-plex-media-server.md#5-scan-media-libraries)
6. [Webtools](install-plex-media-server.md#6-webtools)

## 1. URL

1. To access Plex, visit [https://plex.\_yourdomain.com\_](https://plex._yourdomain.com_)
2. Login with your Plex account

   ![](https://i.imgur.com/KMVu05O.png)

## 2. Setup Wizard

1. First time you log in, you will be presented with a welcome screen. Click "GOT IT!" to continue.

   ![](https://i.imgur.com/CTG955C.png)

2. Next screen will show you a list of servers, with a randomly generated name. Give it a friendly name and click "NEXT".

   ![](https://i.imgur.com/soGxdGm.png)

3. On the next screen, click "NEXT" \(we will add Libraries later\).

   ![](https://i.imgur.com/OQxsJd1.png)

4. Click "DONE".

   ![](https://i.imgur.com/uRr3o61.png)

## 3. Settings

### Remote Access

1. Click the Settings icon \(top right\) → "Server" \(top\) → "Remote Access" \(left\).
2. Enable "Manually specify public port", type in `443`, and click the "Retry" button.
3. You will get a "Not available outside your network" message. This is OK. Simply ignore it and click "ENABLE REMOTE ACCESS".
4. Click "SAVE CHANGES".

   ![](https://i.imgur.com/Ghjpoon.png)

### Library

1. Click the Settings icon \(top right\) → "Server" \(top\) → "Library" \(left\).
2. Set the following:
   * "Empty trash automatically after every scan": `disabled`
     * _Plex Autoscan will take care of this._
   * "Allow media deletion": `enabled`
   * "Generate video preview thumbnails": `never`
   * "Generate chapter thumbnails": `never`

> The reasoning behind disabling these thumbnails is related to Google Drive API usage, data transfer, and disk space. Accessing large portions of a given video file to generate thumbnails _may_ generate large numbers of Google Drive API calls, and large amounts of data transfer. Either of these things _may_ result in your account suffering one of the various types of 24-hour bans Google hands out, which _may_ prevent your server from playing media at all. Also, storing these images _will_ greatly inflate the size of `/opt/plex`, which can affect the speed of backups, your ability to download, and anything else related to disk space usage. These are generally considered Bad Things, so the recommendation is to avoid the possibility by turning these options off.

1. Click "SAVE CHANGES".

   ![](https://i.imgur.com/g6RxFdF.jpg)

### Network

1. Click the Settings icon \(top right\) → "Server" \(top\) → "Network" \(left\).
2. Set the following:
   * "Secure Connections": `Preferred`.
   * "Enable local network discovery \(GDM\)": `disabled`.
   * "Remote streams allowed per user": _your preference_.
   * "Custom server access URLs": `http://plex.yourdomain.com:80/,https://plex.yourdomain.com:443/` \(pre-filled\)
3. Click "SAVE CHANGES".

   ![](https://i.imgur.com/Qx9TcHX.jpg)

### Transcoder

1. Click the Settings icon \(top right\) → "Server" \(top\) → "Transcoder" \(left\).
2. Set the following:
   * "Transcoder temporary directory": `/transcode`
   * "Transcoder default throttle buffer": `150`
   * "Use hardware acceleration when available": `enabled`
   * "Maximum simultaneous video transcode": `unlimited`
3. Click "SAVE CHANGES".

   ![](https://i.imgur.com/QH3R8FF.png)

### DLNA

1. Click the Settings icon \(top right\) → "Server" \(top\) → "DLNA" \(left\).
2. Set the following:
   * "Enable the DLNA server": `disabled`
   * "DLNA server timeline reporting": `disabled`
3. Click "SAVE CHANGES".

   ![](https://i.imgur.com/8XiyMEk.png)

### Scheduled Tasks

1. Click the Settings icon \(top right\) → "Server" \(top\) → "Scheduled Tasks" \(left\).
2. Set the following:
   * "Update all libraries during maintenance": `disabled`
   * "Upgrade media analysis during maintenance": `disabled`
   * "Perform extensive media analysis during maintenance": `disabled`
3. Click "SAVE CHANGES".

   ![](https://i.imgur.com/0SHIJCM.jpg)

## 4. Add Media Libraries

In this section, we will add two libraries: one for Movies and one for TV.

_Note: If you would like to have custom Plex libraries \(more than just a Movies and TV one\), see_ [_Customizing Plex Libraries_](../../../advanced-configuration/customizing-plex-libraries-1.md)_._

### Add the Movie Library

1. In the main Plex screen \(Home icon on the top left\), click "+" next to "LIBRARIES".

   ![](https://i.imgur.com/zadq6ca.png)

2. In the "Add Library" window, select "Movies" and click "NEXT".

   ![](https://i.imgur.com/UcUFCix.png)

3. Click "BROWSE FOR MEDIA FOLDER".

   ![](https://i.imgur.com/5kywEro.png)

4. In second column of the "Add Folder" window, select `data`, then `Movies`, and then click the "ADD" button.

   ![ ](https://i.imgur.com/Embc9h9.png)

5. You will now see `/data/Movies` in the text box \(don't click "ADD LIBRARY" yet\).

   ![](https://i.imgur.com/qzlGMTN.png)

6. Click "Advanced" on the left.
7. Set the following:
   * "Enable Cinema Trailers": `disabled` \(optional\)
   * "Enable video preview thumbnails": `disabled`
   * "Find trailers and extras automatically \(Plex Pass required\)": `disabled` \(optional\)
8. Click "ADD LIBRARY".

   ![](https://i.imgur.com/4JV0orf.png)

### Add the TV Library

1. In the main Plex screen \(Home icon on the top left\), click "+" next to "LIBRARIES".

   ![](https://i.imgur.com/zadq6ca.png)

2. In the "Add Library" window, select "TV Shows" and click "NEXT".

   ![](https://i.imgur.com/gZtUgtQ.png)

3. Click "BROWSE FOR MEDIA FOLDER".

   ![](https://i.imgur.com/5kywEro.png)

4. In second column of the "Add Folder" window, select `data`, then `TV`, and then click the "ADD" button.

   ![ ](https://i.imgur.com/Embc9h9.png)

5. You will now see `/data/TV` in the text box \(don't click "ADD LIBRARY" yet\).

   ![](https://i.imgur.com/i03W0W0.png)

6. Click "Advanced" on the left.
7. Set the following:
   * "Enable video preview thumbnails": `disabled`
   * "Find trailers and extras automatically \(Plex Pass required\)": `disabled` \(optional\)
8. Click "ADD LIBRARY".

```text
![](https://i.imgur.com/JuZif0B.png)
```

## 5. Scan Media libraries

As mentioned in the [Introduction](../../../basics/basics-introduction.md#how-does-cloudbox-function) page, [Plex Autoscan](install-plex-autoscan.md) will automatically scan the media files into Plex as they are downloaded, but this will require the Plex database to not be completely empty. So for every new library that is added, a one-time, manual scan is required.

To do so:

1. Click the 3 dots next to a Plex library.
2. Select "Scan Library Files".

   ![](https://i.imgur.com/38OCwU5.png)

3. Repeat steps 1-2 for each library.

## 6. Webtools

Webtools for Plex comes preinstalled. If you wish to setup Webtools and install 3rd party add-ons, you can go to http://plex.\_yourdomain.com\_:33400 \(**http, not https**\) and login with your Plex account.

_Note: Use_ http://\_yourserveripaddress:33400 if the above URL doesnt work.\_

