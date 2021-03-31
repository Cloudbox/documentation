# Updating Cloudbox Apps

The info below will show you how to update your Cloudbox apps, individually.

## Notes

* To update Cloudbox as a whole \(i.e. the core and all the default roles\), see [Updating Cloudbox](updating-cloudbox.md).
* Generally speaking, do not update the apps within the app itself.

## Update to a newer version

| Cloudbox Apps | How to update |
| :--- | :--- |
| Plex | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| PlexPy/Tautulli | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Plex AutoScan | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) or `git` |
| Sonarr | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Radarr | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| NZBGet | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| ruTorrent | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Jackett | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| NZBHydra2 | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Ombi | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Organizr | Update within the app |
| Portainer | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |
| Cloudplow | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) or `git` |
| Emby | [Ansible tag](updating-cloudbox-apps.md#ansible-tags-to-update-apps) |

**"How to update" options:**

* **"Ansible tag"**

  See the next section on how to update Cloudbox apps via their Ansible tag.

* **"Update within the app"**

  You can simply update within the app itself. Changes will persist after docker restarts.

* **"Container restart"**

  This means that the Docker container will auto-update the app on container restart. _Currently nothing by cloudbox is updated in this way._

  ```text
   docker stop <name> && docker start <name>
  ```

  or

  ```text
   docker restart <name>
  ```

  _Note: It's recommended to use `docker stop/start <container>` vs `docker restart <container>`, to prevent corrupting data, especially on apps like ruTorrent._

* **"git"**

  You can also go into the `/opt/appname` folder and `git pull` the latest updates. Be sure to install the `requirements.txt` modules and then restart the service afterwards.

## Ansible tags to update apps

When in doubt, you can always rerun the relevant Ansible tag to update the app.

| Apps | Ansible Tags |
| :--- | :--- |
| Plex | `plex` |
| PlexPy/Tautulli | `plexpy` |
| Sonarr | `sonarr` |
| Radarr | `radarr` |
| NZBGet | `nzbget` |
| ruTorrent | `rutorrent` |
| Jackett | `jackett` |
| NZBHydra2 | `nzbhydra2` |
| Ombi | `ombi` |
| Organizr | `organizr` |
| Portainer | `portainer` |
| Watchtower | `watchtower` |
| Nginx-Proxy and Letsencrypt | `nginx-proxy` |

**Instructions:**

1. Run the tag command:

   ```text
   cb install TAG
   ```

   Replace `TAG` with one of the above tags from the table.

   You can also run multiple tags, by placing them next to each other, separated by a comma, without spaces \(e.g. --tags TAG1,TAG2\).

   _Note: If the App is a docker container, running the update tag will rebuild and update the container._

   _Note: If you modified the container with flags like `plex_name`, you'll need to do the same thing here._

