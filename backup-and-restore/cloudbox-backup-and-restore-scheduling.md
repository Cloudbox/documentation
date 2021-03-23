# Scheduling

This page will assist you in scheduling Cloudbox backups to run periodically. This is set via Cron.

There are 2 ways to set this up:

1. [Have Cloudbox set it up for you](cloudbox-backup-and-restore-scheduling.md#scheduling-backup-via-cloudbox), or
2. [Create a Cron task, manually](cloudbox-backup-and-restore-scheduling.md#scheduling-backup-manually-via-cron).

## Scheduling Backup via Cloudbox

1. Make sure settings are filled out, see the \[\[here\|Cloudbox Backup and Restore Settings\]\].
2. Set the schedule:
   1. Go into your Cloudbox folder.

      ```text
      cd ~/cloudbox
      ```

   2. Run the backup command.

      ```text
      sudo ansible-playbook cloudbox.yml --tags set-backup
      ```

## Scheduling Backup Manually via Cron

1. Edit the crontab for the user.

   ```bash
   crontab -e
   ```

2. To add in your cron task, add the following after your desired cron schedule \(replace `seed` with your user name\):

   ```text
   sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/cloudbox.yml' --tags settings >> '/home/seed/logs/cloudbox_backup.log' 2>&1; sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/backup.yml' --tags backup >> '/home/seed/logs/cloudbox_backup.log' 2>&1
   ```

   **Note**: If you modify the one that Ansible creates [automatically](cloudbox-backup-and-restore-scheduling.md#scheduling-backup-via-cloudbox), you must remove/replace the comment header: \(`#Ansible: Cloudbox Backup`\), or else Ansible will keep resetting it.

3. Examples:
   * Weekly \(At Midnight Every Sunday\):

     ```text
     @weekly sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/cloudbox.yml' --tags settings >> '/home/seed/logs/cloudbox_backup.log' 2>&1; sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/backup.yml' --tags backup >> '/home/seed/logs/cloudbox_backup.log' 2>&1
     ```

   * At 6:00 AM Every Morning:

     ```text
     0 6 * * * sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/cloudbox.yml' --tags settings >> '/home/seed/logs/cloudbox_backup.log' 2>&1; sudo PATH='/usr/bin:/bin:/usr/local/bin' env ANSIBLE_CONFIG='/home/seed/cloudbox/ansible.cfg' '/usr/local/bin/ansible-playbook' '/home/seed/cloudbox/backup.yml' --tags backup >> '/home/seed/logs/cloudbox_backup.log' 2>&1
     ```

   * For more scheduling examples, visit [https://crontab.guru/](https://crontab.guru/).

