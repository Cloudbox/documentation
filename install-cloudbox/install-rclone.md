# Rclone\|Install: Rclone

[Rclone](https://rclone.org) \(by Nick Craig-Wood\) is "rsync for the cloud". Basically, it is used to transfer data to or from a variety of supported cloud storage providers \(eg Google Drive\).

Rclone is used by \[\[Cloudplow\]\] and \[\[Backup\|Cloudbox Backup and Restore\]\] to upload media and backup Cloudbox, respectively.

The guide below assumes you are using Google Drive.

If you would like to set this up with another cloud storage provider, but have not setup Rclone yet, then follow the guide \[\[below\|Install: Rclone\#new-rclone-setup\]\] and replace all mentions of "Google Drive" with your preferred cloud storage provider's name.

If you already have Rclone configured, you can jump directly to the \[\[relevant section\|Install: Rclone\#existing-rclone-setup\]\].

## New Rclone Setup

This guide goes through setting rclone up to connect to a Google Drive "My Drive". You can substitute a Teamdrive if you are familiar with that process. Currently, that isn't documented here.

1. Run the following command:

   ```text
   rclone config
   ```

2. Type `n` for "New remote" and press Enter.

   ![](https://i.imgur.com/vYZn9Sb.png)

3. For "name", type in `google` and press Enter.

   ![](https://i.imgur.com/7N97EGa.png)

4. For "Type of storage", type in `drive`, or the corresponding number, and press Enter.

   ![](https://i.imgur.com/CPuWt5u.png)

5. Create a \[\[Google Drive API Client ID and Client Secret\]\] for Rclone.
6. For "Google Application Client ID", paste the Client ID from Step \#5, and press Enter.

   ![](https://i.imgur.com/59dHZqb.png)

7. For "Google Application Client Secret", paste the Client Secret from Step \#5, and press Enter.

   ![](https://i.imgur.com/SqSsa8z.png)

8. For the "Scope that rclone should use when requesting access from drive", type in `drive`, or the corresponding number \(i.e. `1`\), to select "Full access all files, excluding Application Data Folder", and press Enter.

   ![](https://i.imgur.com/P6o3cNz.png)

9. For "ID of the root folder", leave blank and press Enter.

   ![](https://i.imgur.com/Bdsb6BM.png)

10. For "Service Account Credentials JSON file path", leave blank and press Enter.

    ![](https://i.imgur.com/eaXumNJ.png)

11. For "Edit advanced config", type `n` and press Enter.

    ![](https://i.imgur.com/kxH6x1N.png)

12. For "Use auto config?", type `n` for "...remote or headless machine" and press Enter.

    ![](https://i.imgur.com/EbYDWTT.png)

13. In the next section, copy the link shown, and open it in your host PC's browser.

    ![](https://i.imgur.com/oL0DQPv.png)

14. If asked to login, use the Google Drive account you want to store your data in \(see \[\[Prerequisites\|Prerequisites: Cloud Storage\]\]\).

    ![](https://i.imgur.com/fTrfnTD.png)

15. Give access by clicking "Allow".

    ![](https://i.imgur.com/SCYqFgL.png)

16. You will now be given a "verification code". Copy it.

    ![](https://i.imgur.com/waUb6qz.png)

17. Paste the "verification code" at the command prompt and press Enter.

    ![](https://i.imgur.com/97cQOOv.png)

18. For "Configure this as a team drive?", type `n` and press Enter.

    ![](https://i.imgur.com/b7dfkIC.png)

    NOTE: This guide is documenting the standard non-teamdrive case. If you are familiar with setting up teamdrives, you can do so here.

19. To confirm that the remote details look OK, type `y` and press Enter.

    ![](https://i.imgur.com/igpNDKb.png)

20. To exit, type `q` and press Enter.

    ![](https://i.imgur.com/h9lbQDn.png)

## Existing Rclone Setup

The default remote specified in \[\[settings.yml\|Install: settings.yml\]\] is `google` for Google Drive. If the Rclone remote in your config has the same name, then you are OK to skip this page and go on to the next.

If you are using Google Drive and the Rclone remote in your config has a different name, then you will need to either:

* Rename your current Rclone remote to the default one \(i.e. `google`\). Instructions for this are below.

  Or

* Edit the Rclone remote entry in \[\[settings.yml\|Install: settings.yml\]\] with yours.

If you prefer to use another cloud storage provider, you can add the name of the Rclone remote in to \[\[settings.yml\|Install: settings.yml\]\].

### Rename Existing Rclone Remote

To rename the Google Drive remote to `google`:

1. Find and edit your Rclone configuration file.

   ```text
   nano $(rclone config file | tail -n 1)
   ```

2. Rename the Google Drive drive remote \(name between the brackets\) to `google`.
3. It will now look like this:

   ```text
   [google]
   type = drive
   client_id = 1234567890123-mjffsmxvendscftuvnyngkhegapovgnv.apps.googleusercontent.com
   client_secret = klflzftkrwuwuedesxzewsfz
   token = {"access_token":"ya30.gelftvrymioiilvdtfegfvhfgallrhocewjckdnnvmxdjpjzbdhkmgulvqhgbafkdtpottzthhnyzysxwlpf-38ikRIxZvimyoxyKdse$
   ```

4. Save the file and exit: Ctrl + X Y Enter.
5. Copy the config file to `~/.config/rclone/rclone.conf` \(if it isn't there already\):

   ```text
   cp -n $(rclone config file | tail -n 1) ~/.config/rclone/rclone.conf
   ```

6. Give it the proper ownership and permissions. Replace `user` and `group` to match yours' \(see [here](https://github.com/Cloudbox/gitbook/tree/52490170d387c232b354a47724ac278ab2998d5c/FAQ/README.md#find-your-user-id-uid-and-group-id-gid)\):

   ```text
   sudo chown user:group ~/.config/rclone/rclone.conf
   sudo chmod 755 ~/.config/rclone/rclone.conf
   ```

