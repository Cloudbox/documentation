# Logs

## Apps

### Backups

Logs are stored in `~/logs`.

#### Previous Backups:

```text
cat ~/logs/cloudbox_backup-<DATE>.log
```

#### Current Backup:

```text
tail -F ~/logs/cloudbox_backup-<DATE>.log
```

### Plex Autoscan

#### Check Status:

```text
sudo systemctl status plex_autoscan.service
```

#### Restart Service:

```text
sudo systemctl restart plex_autoscan.service
```

#### Previous Activity:

```text
cat /opt/plex_autoscan/plex_autoscan.log
```

Older logs are named as plex\_autoscan.log.1, plex\_autoscan.log.2, etc.

#### Live Log:

```text
tail -F /opt/plex_autoscan/plex_autoscan.log
```

or

```text
sudo journalctl -o cat -fu plex_autoscan.service
```

### Cloudplow

#### Check Status:

```text
sudo systemctl status cloudplow.service
```

#### Previous Activity:

```text
cat /opt/cloudplow/cloudplow.log
```

Older logs are named as cloudplow.log.1, cloudplow.log.2, etc.

#### Live Log:

```text
tail -F /opt/cloudplow/cloudplow.log
```

or

```text
sudo journalctl -o cat -fu cloudplow.service
```

## Remote Mount

Pick one of these.

### Rclone VFS

#### Check Status:

```text
sudo systemctl status rclone_vfs.service
```

#### See a live log:

```text
sudo journalctl -o cat -fu rclone_vfs.service
```

### Rclone Cache

#### Check Status:

```text
sudo systemctl status rclone_cache.service
```

#### See a live log:

```text
sudo journalctl -o cat -fu rclone_cache.service
```

### Plexdrive 4

#### Check Status:

```text
sudo systemctl status plexdrive4.service
```

#### See a live log:

```text
sudo journalctl -o cat -fu plexdrive4.service
```

### Plexdrive 5

#### Check Status:

```text
sudo systemctl status plexdrive5.service
```

#### See a live log:

```text
sudo journalctl -o cat -fu plexdrive5.service
```

## Union Mount

Pick one of these.

### MergerFS

#### Check Status:

```text
sudo systemctl status mergerfs.service
```

#### See a live log:

```text
sudo journalctl -o cat -fu mergerfs.service
```

### UnionFS

#### Check Status:

```text
sudo systemctl status unionfs.service
```

#### See a live log:

```text
sudo journalctl -fu unionfs.service
```

## Docker

Find the container name: `docker ps -a`

### Live logs

#### Live log \(from the beginning of the log\):

```text
docker logs --follow <container_name>
```

#### Live log \(from the last 10 lines of the log\):

```text
docker logs --follow --tail 10 <container_name>
```

#### Examples:

```text
docker logs -f plex
```

Note: `--follow` = `-f`

### Let's Encrypt

In addition to the above, you may use the following commands to display info about your existing certificates.

#### Cert Status

```text
docker exec letsencrypt /app/cert_status
```

#### Logs

```text
docker logs -f letsencrypt
```

