# Advanced Settings

- Work in Progress -

## Forward

Modifying adv\_settings.yml is only required if there is an option you need to change from the default setup \(e.g. custom subdomain for Ombi\) or an optional app requires some extra setup parameters \(e.g. Telly\).

As with the standard settings, changing values in this file requires that the relevant tag be re-run to apply the change.

## Overview of adv\_settings.yml

```yaml
---
system:
  timezone: auto
docker:
  repo: edge
  version: latest
mounts:
  unionfs: mergerfs
  remote: rclone_vfs
plex:
  open_main_ports: no
  open_extra_ports: no
  force_auto_adjust_quality: no
  force_high_output_bitrates: no
  db_cache_size: default
suitarr:
  version: default
sonarr:
  version: v3
darkerr:
  enable: no
emby:
  version: latest
organizr:
  direct_domain: no
nginx:
  direct_domain: no
  subdomain: web
ombi:
  subdomain: ombi
sickbeard_mp4_automator: no
gpu:
  intel: yes
  nvidia:
    enabled: no
    driver: 418.30
hetzner_nfs:
  vlan_id: 4000
  mount_client: 3
```

## Editing adv\_settings.yml

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Open the file in nano:

   ```bash
   nano adv_settings.yml
   ```

3. When done editing, save the file: Ctrl + X Y Enter.

## Options in adv\_settings.yml



```yaml
---
system:
  timezone: auto
```

Set a timezone, or let cloudbox set it for you.

```yaml
docker:
  repo: edge
  version: latest
```

```yaml
mounts:
  unionfs: mergerfs
  remote: rclone_vfs
```

Choose mergerfs or unionfs, rclone\_vfs or rclone\_cache

```yaml
plex:
  open_main_ports: no
  open_extra_ports: no
  force_auto_adjust_quality: no
  force_high_output_bitrates: no
  db_cache_size: default
```

Adjust various Plex settings.

```yaml
suitarr:
  version: default
```

No longer used.

```yaml
sonarr:
  version: v3
```

No longer used.

```yaml
darkerr:
  enable: no
```

Install Darkerr theme for Radarr, Sonarr, and nzbget

```yaml
emby:
  version: latest
```

Choose version of emby; this must be a tag from [embyserver on dockerhub](https://hub.docker.com/r/emby/embyserver/tags)

```yaml
organizr:
  direct_domain: no
```

If `direct_domain: yes` organizr will be available at your base domain: DOMAIN.TLD rather than organizr.DOMAIN.TLD

```yaml
nginx:
  direct_domain: no
  subdomain: web
```

If `direct_domain: yes` a website will be available at your base domain: DOMAIN.TLD If `direct_domain: no` a website will be available at the specified subdomain: web.DOMAIN.TLD

After making changes here run the `nginx` tag to make them take effect.

```yaml
ombi:
  subdomain: ombi
```

Subdomain you want to use for ombi.

```yaml
sickbeard_mp4_automator: no
```

Set up the Sickbeard MP4 automator in the relevant apps.

NOTE: Due to image changes this currently has problems.

```yaml
gpu:
  intel: yes
  nvidia:
    enabled: no
    driver: 418.30
```

Settings for hardware transcoding in Plex.

After making changes here run the `plex` tag to make them take effect.

```yaml
hetzner_nfs:
  vlan_id: 4000
  mount_client: 3
```

Settings for the `hetzner_nfs` role.

NOTE: generally speaking, all of these settings will require some tags to be rerun to take effect. For example, if you turn Darkerr on, nothing's going to change until you rerun the Radarr, Sonarr, or nzbget tags.

