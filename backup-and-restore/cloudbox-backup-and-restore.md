# Backup and Restore

* [Intro](cloudbox-backup-and-restore.md#intro)
* [Cloudbox Backup](cloudbox-backup-and-restore.md#cloudbox-backup)
* [Cloudbox Restore](cloudbox-backup-and-restore.md#cloudbox-restore)

## Intro

Backup and Restore is a built-in feature of Cloudbox that makes it easy to back-up your entire Cloudbox setup, with the ability to restore it anywhere.

{% hint style="info" %}
_Only app data located in '/opt' and relevant config files are backed up. For more details, see_ [_here_](../troubleshooting/faq-from-cb.md#what-is-backed-up)_._
{% endhint %}

{% hint style="info" %}
_If you wish to move your Cloudbox to another server via Backup / Restore, see_ [_Migrating Cloudbox_]()_._
{% endhint %}

## Cloudbox Backup

**Cloudbox Backup** backs up the Docker container app data \(i.e. `/opt`\), and all relevant config files, and uploads it to an Rclone or Rsync remote \(if they are enabled\).

[What is backed up?](../troubleshooting/faq-from-cb.md#what-is-backed-up)

Backup can be run manually \(steps below\), for an immediate, one-time backup, or [scheduled](cloudbox-backup-and-restore-scheduling.md) to run periodically.

{% hint style="info" %}
_During backup, all Cloudbox managed Docker containers will be shut down \(i.e. Plex will be unavailable\) while the tarball files are being made._
{% endhint %}

Steps to run a manual backup:

1. Make sure backup settings \(i.e. \`[~/cloudbox/backup\_config.yml](cloudbox-backup-and-restore-settings.md)\`\) are filled out.
2. Run the backup command

   ```text
   cb install backup
   ```

   via screen:

```text
screen -dmS cloudbox-backup cb install backup
screen -r
CTRL A + D
```

For scheduled backups, see [here](cloudbox-backup-and-restore-settings.md).

If for some reason your backup stops/ you accidentally reboot the server etc.: You'll need to remove the `backup.lock` file in your cloudbox directory, otherwise tags will not run.

## Cloudbox Restore

**Cloudbox Restore** downloads the backup from the cloud \(if Rclone or Rsync were enabled\) and restores it to the `/opt` folder \(this is done automatically and requires no manual intervention\).

If a local backup \(e.g. `/opt` tarball files\) already exists in the backup folder, those tarball files will be used instead.

Backup can be restored on the same server or brand new one, with everything exactly as you left it at the time of backup. See [Migrating Cloudbox](migrating-cloudbox.md) for more info.

Steps below assume you are restoring to a new / wiped server.

1. Install [dependencies](../install-cloudbox/02-install-dependencies.md) and download the Cloudbox project repository.
2. If the Restore Service was enabled in [settings](cloudbox-backup-and-restore-settings.md) \(i.e. `restore_service` credentials were supplied in [backup\_config.yml](cloudbox-backup-and-restore-settings.md)\), you will be able automatically restore the config files into the `~/cloudbox` folder.

   To do so run the following command \(replace `USERNAME` and `PASSWORD` with your `restore_service` credentials\).

   ```text
   curl -s https://cloudbox.works/scripts/restore.sh | bash -s 'USERNAME' 'PASSWORD'
   ```

   NOTE: Wrap your USERNAME and PASSWORD in quotes just as shown there.  
  
   NOTE: These are not \[necessarily\] your login credentials. This is a username/password that **you have to enter yourself** in the backup\_config.yml file. **The Cloudbox install does not automatically fill these in**.   
  
   **If you did not fill these in yourself**, then the Cloudbox Restore Service **is** _**NOT**_ **enabled**.

3. If the Cloudbox Restore Service was not enabled \(i.e. `restore_service` credentials were NOT supplied in [backup\_config.yml](cloudbox-backup-and-restore-settings.md)\) 
   * Find the following files in your backup and drop them into the `~/cloudbox` folder:
     * `ansible.cfg`
     * `accounts.yml`
     * `settings.yml`
     * `adv_settings.yml`
     * `backup_config.yml`
     * `rclone.conf` 
   * Note 1: These files were backed up separately from the backup tarball files so they can easily be copied here.
   * Note 2: During the restore process, the `rclone.conf` file will be moved to `~/.config/rclone/rclone.conf`.
   * Note 3: The `/opt` folder gets downloaded/restored automatically in the next step, and doesn’t require manual downloading or unpacking.
4. If you had Ansible Vault set up before, you'll need to create an Ansible Vault password file using the same vault password as last time.

   ```bash
   echo YOUR_VAULT_PASSWORD > /root/.ansible_vault
   ```

   of course, that should be your vault password, not literally YOUR\_VAULT\_PASSWORD.

5. Run [preinstall](../install-cloudbox/05-preinstall.md) command to create a user account:

   ```bash
   cb install preinstall
   ```

   _Note: It's ok to do this in root as it will create a new user account and move the cloudbox folder and config files to that new user's home folder._

   _**Now log out of your `root` session and log in as the user account from your `accounts.yml` file.**_

6. Run the restore command:

   _Note: Do not run this command while logged in as `root`. Log in as your user account; the account you specified in `accounts.yml`_

   ```bash
   cb install restore
   ```

   _Note: If you are getting an error, verify that you are not logged in as root. You should be logged in as the user account specified in `accounts.yml`.._

   _Note: If you are getting an error for rclone such as `permission denied` reboot the system then sign in as your user then run the restore tag again._

   That error will include: `... Failed to open log file: open /root/cloudbox/restore_rclone.log: permission denied", ...`

   _If you get an error related to a misconfigured rclone.conf file, check that file and make sure things look normal. Also run rclone config to check that a remote has actually been configured._

7. Install the relevant [Cloudbox type](../basics/basics-cloudbox-install-types.md). Example below.

   _Note: Do not run this command while logged in as `root`. Log in as your user account; the account you specified in `accounts.yml`_

   Example:

   ```bash
   cb install cloudbox
   ```

8. Reboot.
9. If you had any extra, or non-default, containers previously \(e.g Community Roles\), you can install those now.

All applications, and their data, will now be restored.

