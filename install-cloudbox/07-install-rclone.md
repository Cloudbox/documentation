# Rclone

[Rclone](https://rclone.org) \(by Nick Craig-Wood\) is "rsync for the cloud". Basically, it is used to transfer data to or from a variety of supported cloud storage providers \(eg Google Drive\).

Rclone is used by \[Cloudplow\] and \[Cloudbox Backup and Restore\] to upload media and backup Cloudbox, respectively.

The guide below assumes you are using Google Drive.

If you would like to set this up with another cloud storage provider, but have not setup Rclone yet, then follow the guide [below](07-install-rclone.md) and replace all mentions of "Google Drive" with your preferred cloud storage provider's name.

If you already have Rclone configured, you can jump directly to the \[relevant section\].

## Google Drive setup

Create a \[\[Google Drive API Client ID and Client Secret\]\] for Rclone. Have the Application ID and Client Secret available, as you will need them for this proess.

## New Rclone Setup

This guide goes through setting rclone up to connect to a Google Drive "My Drive". You can substitute a Teamdrive if you are familiar with that process. Currently, that isn't documented here.

1. Run the following command:

   ```bash
   rclone config
   ```

2. Type `n` for "New remote" and press Enter.

   ```bash
   ~$ rclone config
   No remotes found - make a new one
   n) New remote
   s) Set configuration password
   q) Quit config
   n/s/q> n
   ```

3. For "name", type in `google` and press Enter.

   ```bash
   n/s/q> n
   name> google
   ```

4. For "Type of storage", type in `drive`, or the corresponding number, and press Enter. You will be presented with a long list of storage backends, which have been removed here for space.

   ```bash
   name> google
   Type of storage to configure.
   Enter a string value. Press Enter for the default ("").
   Choose a number from below, or type in your own value
   ...
   15 / Google Drive
   \ "drive"
   ...
   Storage> drive
   ```

5. For "Google Application Client ID", paste the Client ID you recorded earlier, and press Enter.

   ```bash
   Storage> drive
   ** See help for drive backend at: https://rclone.org/drive/ **

   Google Application Client Id
   Setting your own is recommended.
   See https://rclone.org/drive/#making-your-own-client-id for how to create your own.
   If you leave this blank, it will use an internal key which is low performance.
   Enter a string value. Press Enter for the default ("").
   client_id> 123456789012-REDACTED.apps.googleusercontent.com
   ```

6. For "Google Application Client Secret", paste the Client Secret from Step \#5, and press Enter.

   ```bash
   client_id> 123456789012-REDACTED.apps.googleusercontent.com
   OAuth Client Secret
   Leave blank normally.
   Enter a string value. Press Enter for the default ("").
   client_secret> ABC123def456GHI789jkl012
   ```

7. For the "Scope that rclone should use when requesting access from drive", type in `drive`, or the corresponding number \(i.e. `1`\), to select "Full access all files, excluding Application Data Folder", and press Enter.

   ```bash
   client_secret> ABC123def456GHI789jkl012
   Scope that rclone should use when requesting access from drive.
   Enter a string value. Press Enter for the default ("").
   Choose a number from below, or type in your own value
   1 / Full access all files, excluding Application Data Folder.
      \ "drive"
   2 / Read-only access to file metadata and file contents.
      \ "drive.readonly"
      / Access to files created by rclone only.
   3 | These are visible in the drive website.
      | File authorization is revoked when the user deauthorizes the app.
      \ "drive.file"
      / Allows read and write access to the Application Data folder.
   4 | This is not visible in the drive website.
      \ "drive.appfolder"
      / Allows read-only access to file metadata but
   5 | does not allow any access to read or download file content.
      \ "drive.metadata.readonly"
   scope> 1
   ```

8. For "ID of the root folder", leave blank and press Enter.

   ```bash
   scope> 1
   ID of the root folder
   Leave blank normally.

   Fill in to access "Computers" folders (see docs), or for rclone to use
   a non root folder as its starting point.

   Enter a string value. Press Enter for the default ("").
   root_folder_id>
   ```

9. For "Service Account Credentials JSON file path", leave blank and press Enter.

   ```bash
   root_folder_id>
   Service Account Credentials JSON file path
   Leave blank normally.
   Needed only if you want use SA instead of interactive login.

   Leading `~` will be expanded in the file name as will environment variables such as `${RCLONE_CONFIG_DIR}`.

   Enter a string value. Press Enter for the default ("").
   service_account_file>
   ```

10. For "Edit advanced config", type `n` and press Enter.

    ```bash
    service_account_file>
    Edit advanced config? (y/n)
    y) Yes
    n) No (default)
    y/n> n
    ```

11. For "Use auto config?", type `n` for "...remote or headless machine" and press Enter.

    ```bash
    y/n> n
    Remote config
    Use auto config?
    * Say Y if not sure
    * Say N if you are working on a remote or headless machine
    y) Yes (default)
    n) No
    y/n> n
    ```

12. In the next section, copy the link shown, and open it in your host PC's browser.

    ```bash
    y/n> n
    Please go to the following link: https://accounts.google.com/o/oauth2/auth?...
    Log in and authorize rclone for access
    Enter verification code>
    ```

13. If asked to login, use the Google Drive account you want to store your data in \(see \[\[Prerequisites\|Prerequisites: Cloud Storage\]\]\).

    ![](../.gitbook/assets/rclone-gdrive-choose-account.png)

14. Give access by clicking "Allow".

    ![](../.gitbook/assets/rclone-gdrive-permission.png)

15. You will now be given a "verification code". Copy it.

    ![](../.gitbook/assets/rclone-gdrive-auth-code.png)

16. Paste the "verification code" at the command prompt and press Enter.

    ```bash
    Please go to the following link: https://accounts.google.com/o/oauth2/auth?...
    Log in and authorize rclone for access
    Enter verification code> 4/1AY0e-REDACTED-REDACTED
    ```

17. For "Configure this as a team drive?", type `n` and press Enter.

    ```bash
    Enter verification code> 4/1AY0e-REDACTED-REDACTED
    Configure this as a Shared Drive (Team Drive)?
    y) Yes
    n) No (default)
    y/n> n
    ```

    NOTE: This guide is documenting the standard non-teamdrive case. If you are familiar with setting up teamdrives, you can do so here.  

18. After confirming that the remote details look OK, type `y` and press Enter.

    ```bash
    y/n> n
    --------------------
    [google]
    type = drive
    client_id = 695133368583-REDACTED.apps.googleusercontent.com
    client_secret = REDACTED
    scope = drive
    token = {"access_token":"REDACTED","token_type":"Bearer","refresh_token":"REDACTED","expiry":"2021-03-27T16:04:42.600702975Z"}
    --------------------
    y) Yes this is OK (default)
    e) Edit this remote
    d) Delete this remote
    y/e/d> y
    ```

19. To exit, type `q` and press Enter.

    ```bash
    Current remotes:

    Name                 Type
    ====                 ====
    google               drive

    e) Edit existing remote
    n) New remote
    d) Delete remote
    r) Rename remote
    c) Copy remote
    s) Set configuration password
    q) Quit config
    e/n/d/r/c/s/q> q
    ```

20. Confirm that the setup worked correctly by listing the drive contents:

    ```bash
    ~$ rclone lsd google:/
          -1 2018-10-22 04:17:52        -1 Media
    `
    ```

    That file listing should show the same directories as the Google Drive WebUI.

## Existing Rclone Setup

The default remote specified in [settings.yml](07-install-rclone.md) is `google` for Google Drive. If the Rclone remote in your config has the same name, then you are OK to skip this page and go on to the next.

If you are using Google Drive and the Rclone remote in your config has a different name, then you will need to either:

* Rename your current Rclone remote to the default one \(i.e. `google`\). Instructions for this are below.

  Or

* Edit the Rclone remote entry in [settings.yml](07-install-rclone.md) with yours.

If you prefer to use another cloud storage provider, you can add the name of the Rclone remote in to [settings.yml](07-install-rclone.md).

### Rename Existing Rclone Remote

To rename the Google Drive remote to `google`:

1. Find and edit your Rclone configuration file.

   ```bash
   nano $(rclone config file | tail -n 1)
   ```

2. Rename the Google Drive drive remote \(name between the brackets\) to `google`.
3. It will now look like this:

   ```text
   [google]
   type = drive
   client_id = 1234567890123-REDACTED.apps.googleusercontent.com
   client_secret = REDACTED
   token = {"access_token":"REDACTED...
   ```

4. Save the file and exit: Ctrl + X Y Enter.
5. Copy the config file to `~/.config/rclone/rclone.conf` \(if it isn't there already\):

   ```bash
   cp -n $(rclone config file | tail -n 1) ~/.config/rclone/rclone.conf
   ```

6. Give it the proper ownership and permissions. Replace `user` and `group` to match yours \(see [here](https://github.com/Cloudbox/gitbook/tree/52490170d387c232b354a47724ac278ab2998d5c/FAQ/README.md#find-your-user-id-uid-and-group-id-gid)\) \(if you have used the defaults during setup your user and group are both `seed`\):

   ```bash
   sudo chown seed:seed ~/.config/rclone/rclone.conf
   sudo chmod 755 ~/.config/rclone/rclone.conf
   ```

