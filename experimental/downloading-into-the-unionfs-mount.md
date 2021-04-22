# Downloading into the unionfs mount

## TODO: INCORPORATE THIS INTO APP SETUP PAGES

WARNINGS ONLY APPLY TO UNIONFS BINARY

This page will show you how setup Cloudbox so that it downloads into /mnt/unionfs/ and allows for instant moves from downloads to media folder.

**Details:**

When something downloads to a `/downloads` mount point, Docker sees this as a different file system from `/tv`, `/movies`, and `/mnt/unionfs` mounts, and as such, it does a “copy then delete” move between them. This is just a default behavior of Linux itself.

By downloading directly to a `/mnt/unionfs` path \(e.g. `/mnt/unionfs/downloads/nzbs/nzbget/...`\) and then having the destination as `/mnt/unionfs/` as well \(e.g. `/mnt/unionfs/Media/TV/...`\), Docker will do a direct/instant move between them.

The reason this is not setup by CB wiki by default is due to instability issues with using UnionFS with i/o intensive tasks \(see warnings on this page\).

**Warning:** Downloading within /mnt/unionfs/, and the subsequent high disk IO, may cause stability issues with UnionFS, and may lead to slow down of any program that accesses it \("gray dots" in Sonarr/Radarr, failed imports, etc\) or even a complete dismounting of the /mnt/unionfs path.

**Note:** MergerFS may handle this better than UnionFS \(the binary\).

Cloudbox has used `mergerfs` as the default for quite some time now.

## NZBGet

1. Go to "Settings" -&gt; "Paths".
2. Change paths to:

   | Setting | Path |
   | :--- | :--- |
   | Maindir | `/mnt/unionfs/downloads/nzbs/nzbget` |
   | Destdir | `${MainDir}/completed` |
   | Interdir | `${MainDir}/intermediate` |

_Note: This assumes your NZB downloads folder was set to `/mnt/local/downloads/nzbs` during the_ [_initial setup_](../install-cloudbox/04-install-settings.yml.md)_._

## ruTorrent

**Warning:** Even though this section covers ruTorrent, it is advised that you don't do this, as the heavy load of torrents reading/writing to UnionFS could crash the mount point and cause downloading/seeding failures.

1. Open `/opt/rutorrent/rtorrent/rtorrent.rc`.
2. Change `directory` to one of the following:

   if your ruTorrent is setup with the old download paths:

   ```text
   directory.default.set = /mnt/unionfs/downloads/rutorrent
   ```

   or, if your Torrent downloads folder was set to `/mnt/local/downloads/torrents` during the \[\[initial setup\|Install: Settings\]\]:

   ```text
   directory.default.set = /mnt/unionfs/downloads/torrents/rutorrent
   ```

   or, if your ruTorrent has subdirs setup AND your Torrent downloads folder was set to `/mnt/local/downloads/torrents` during the \[\[initial setup\|Install: Settings\]\]:

   ```text
   directory.default.set = /mnt/unionfs/downloads/torrents/rutorrent/incoming
   method.insert = d.get_finished_dir, simple, "cat=/mnt/unionfs/downloads/torrents/rutorrent/completed/,$d.custom1="
   ```

## Sonarr

### Settings

1. Go to "Settings" -&gt; "Media Management".
2. Set "Advanced Settings" to `Shown`.
3. Scroll down to "Importing".
4. Set "Use Hardlinks instead of Copy" to `No`.
   * **Note:** Having this option enabled will prevent actively seeded/open files from being uploaded during Cloudplow upload tasks.

### Root Paths

1. Go to "Series" -&gt; "Series Editor" -&gt; Select your TV Shows -&gt; "Root Folder" -&gt; "Add a different path".
2. On the popup window:
   1. Enter in:

      ```text
      /mnt/unionfs/Media/TV/
      ```

      _**Note:** If you are using \[\[customized paths\|Customizing Plex Libraries\]\], then select the proper TV shows path within `/mnt/unionfs/Media/`._

   2. Press the green check mark to close the window.
3. Click the blue "Save" button to change the root paths.

## Radarr

### Settings

1. Go to "Settings" -&gt; "Media Management".
2. Set "Advanced Settings" to `Shown`.
3. Scroll down to "Importing".
4. Set "Use Hardlinks instead of Copy" to `No`.
   * **Note:** Having this option enabled will prevent actively seeded/open files from being uploaded during Cloudplow upload tasks.

### Root Paths

1. Go to "Movies" -&gt; "Movies Editor" -&gt; Select your movies -&gt; "Root Folder" -&gt; "Add a different path".
2. On the popup window:
   1. Enter in:

      ```text
      /mnt/unionfs/Media/Movies/
      ```

      _**Note:** If you are using \[\[customized paths\|Customizing Plex Libraries\]\], then select the proper movies path within `/mnt/unionfs/Media/`._

   2. Press the green check mark to close the window.
3. Click the blue "Save" button to change the root paths.

## Plex Autoscan

No changes required.

## Plex

No changes required.

