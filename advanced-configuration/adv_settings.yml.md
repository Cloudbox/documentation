# adv\_settings.yml

- Work in Progress -

## Forward

Modifying adv\_settings.yml is only required if there is an option you need to change from the default setup \(e.g. custom subdomain for Ombi\) or an optional app requires some extra setup parameters \(e.g. Telly\).

As with the standard settings, changing values in this file requires that the relevant tag be re-run to apply the change.

## Overview of adv\_settings.yml \#\#

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

## Editing adv\_settings.yml \#\#

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

Choose one of the following:

* \[\[HTML Page\|[https://cloudbox.works/wiki/adv\_settings\_yml.html](https://cloudbox.works/wiki/adv_settings_yml.html)\]\] \(better format\) \(404 as of 20 May 2020\)
* \[\[Wiki Page\|Options in adv\_settings.yml\]\]

