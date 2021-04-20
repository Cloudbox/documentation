# Sickbeard MP4 Automator

**MOVE TO ADVANCED?  NO MORE TAG**

1. [Introduction](extra-sickbeard-mp4-automator.md#1-introduction)
2. [Overview](extra-sickbeard-mp4-automator.md#2-overview)
3. [Initial Setup](extra-sickbeard-mp4-automator.md#3-initial-setup)
   1. [Settings](extra-sickbeard-mp4-automator.md#i-settings)
   2. [Install](extra-sickbeard-mp4-automator.md#ii-install)
4. [Setup](extra-sickbeard-mp4-automator.md#4-setup)
5. [Sonarr](extra-sickbeard-mp4-automator.md#5-sonarr)
6. [Radarr](extra-sickbeard-mp4-automator.md#6-radarr)
7. [Tips](extra-sickbeard-mp4-automator.md#7-tips)
8. [User Submitted Configs](extra-sickbeard-mp4-automator.md#8-user-submitted-configs)

## 1. Introduction

[Sickbeard MP4 Automator](https://github.com/mdhiggins/sickbeard_mp4_automator) Automatically converts video files to a standardized mp4 format.

## 2. Overview

1. Download is handed back to Sonarr/Radarr from NZBGet/ruTorrent.
2. Sonarr/Radarr renames the file and executes the Sickbeard MP4 Automator \(SMA\) script.
3. SMA runs, converts the renamed file to an mp4, following the config in `autoProcess.ini`, and deletes the original file \(can be changed in the settings\).
4. SMA executes the `plex_autoscan.py` post-processing script to notify Plex Autoscan to scan the new file's directory.
5. SMA notifies Sonarr/Radarr of the new filename and initiates a rescan of the file location to pick up the change.

## 3. Initial Setup

Sickbeard MP4 Automator is installed on 'Cloudbox' or 'Feederbox' setups.

### i. Settings

Set the following option in `adv_settings.yml`:

```yaml
sickbeard_mp4_automator: yes
```

### ii. Install

Run the following command:

```bash
sudo ansible-playbook cloudbox.yml --tags sickbeard_mp4_automator
```

or

```bash
sudo ansible-playbook cloudbox.yml --tags sma
```

## 4. Setup

### i. Add your Plex Autoscan URL into 'plex\_autoscan.py'

On a full 'Cloudbox' install, the `URL=` should be set to your \[\[Plex Autoscan URL\|Install: Plex-Autoscan\#3-obtaining-the-plex-autoscan-url\]\] on line 32 of `/opt/scripts/sickbeard_mp4_automator/post_process/plex_autoscan.py`.

If not, or if your are using a 'Feederbox' setup, replace `PLEX_AUTOSCAN_URL` with your \[\[Plex Autoscan URL\|Install: Plex-Autoscan\#3-obtaining-the-plex-autoscan-url\]\].

```python
url = "PLEX_AUTOSCAN_URL"
```

### ii. Fill in API Keys into 'autoProcess.ini'

Out of box, the install process would have put your Sonarr and Radarr API keys into `/opt/scripts/sickbeard_mp4_automator/autoProcess.ini`.

If they are missing, you will need to add them in yourself.

## 5. Sonarr

### i. Set 'Plex Autoscan' to rename only

_This is now handled by the 'plex\_autoscan.py' script._

1. Click "Settings" -&gt; "Connect".
2. Click 'Plex Autoscan'.
3. Set the following \(in order\):
   1. Name: Plex Autoscan
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `No`
   5. On Rename: `Yes`
   6. On Download: `No` \(this is not a typo\)
4. Click "Save"
5. The box will look like this:

   ![](https://i.imgur.com/aa1nt0Z.png)

### ii. Add 'Sickbeard MP4 Automator'

1. Click "Settings" -&gt; "Connect".
2. Add a new "Custom Script".
3. Add the following:
   1. Name: Sickbeard MP4 Automator
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename: `No`
   6. Path: `/scripts/sickbeard_mp4_automator/postSonarr.py`
   7. Arguments: \(blank\)
4. The settings will look like this:

   ![SMA for Sonarr](https://i.imgur.com/G5wVtC8.png)

5. Click "Save" to add the Sickbeard MP4 Automator script.

## 6. Radarr

### i. Set 'Plex Autoscan' to rename only

_This is now handled by the 'plex\_autoscan.py' script._

1. Click "Settings" -&gt; "Connect".
2. Click 'Plex Autoscan'.
3. Set the following \(in order\):
   1. Name: Plex Autoscan
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `No`
   5. On Rename: `Yes`
   6. On Download: `No` \(this is not a typo\)
4. Click "Save"
5. The box will look like this:

   ![](https://i.imgur.com/aa1nt0Z.png)

### ii. Add 'Sickbeard MP4 Automator'

1. Click "Settings" -&gt; "Connect".
2. Add a new "Custom Script".
3. Add the following:
   1. Name: Sickbeard MP4 Automator
   2. On Grab: `No`
   3. On Download: `Yes`
   4. On Upgrade: `Yes`
   5. On Rename: `No`
   6. Path: `/scripts/sickbeard_mp4_automator/postRadarr.py`
   7. Arguments: \(blank\)
4. The settings will look like this:

   ![SMA for Radarr](https://i.imgur.com/q6bjG3x.png)

5. Click "Save" to add the Sickbeard MP4 Automator script.

## 7. Tips

### Enable HW acceleration for supported Intel CPUs

Set the following in `/opt/scripts/sickbeard_mp4_automator/autoProcess.ini`:

```text
use-qsv-decoder-with-encoder = True
```

```text
video-codec = h264vaapi, h264, x264
```

Set the next one only if your server's CPU is capable of HW decoding HEVC. See [here](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding).

```text
use-hevc-qsv-decoder = True
```

## 8. User Submitted Configs

* \[\[Kinv\|SMA Config by kinv\]\]

