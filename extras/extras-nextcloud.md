# Nextcloud

1. [Introduction](extras-nextcloud.md#1-introduction)
2. [URL](extras-nextcloud.md#2-url)
3. [Initial Setup](extras-nextcloud.md#3-initial-setup)
   1. [Domain](extras-nextcloud.md#i-domain)
   2. [Install](extras-nextcloud.md#ii-install)
4. [Setup Wizard](extras-nextcloud.md#4-setup-wizard)
5. [Adding Folder\(s\)](extras-nextcloud.md#5-adding-folders)

## 1. Introduction

[Nextcloud](https://nextcloud.com) is a free, open-source, self-hosted file sharing solution, that functions similarly to Dropbox.

![](https://i.imgur.com/aIHp22i.png)

## 2. URL

* To access Nextcloud, visit [https://nextcloud.\_yourdomain.com\_](https://nextcloud._yourdomain.com_)

## 3. Initial Setup

### i. Domain

* See \[\[Adding a Subdomain\|Adding a Subdomain\]\] on how to add the subdomain `nextcloud` to your DNS provider.
* _Note: You can skip this step if you are using \[\[Cloudflare\|Prerequisites: Cloudflare\]\] with Cloudbox._

### ii. Install

* Run the following commands:

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags nextcloud
  ```

## 4. Setup Wizard

1. Visit [https://nextcloud.\_yourdomain.com\_](https://nextcloud._yourdomain.com_)

   ![](https://i.imgur.com/akcVDEl.png)

2. Under `Create an admin account`, set the following:
   * Username: fill in your preferred admin username.
   * Password: fill in your preferred admin password.
3. Click the `Storage & database` link.

   ![](https://i.imgur.com/BRpV7i6.png)

4. Under `data folder`, the path below should already be filled in.

   ```text
   /data
   ```

5. Select `MySQL/MariaDB` under `Configure the database`.

   ![](https://i.imgur.com/Ck012rr.png)

6. Fill in the following **exactly** as you see below:
   * Database user: `root`
   * Database password: `password321` \(The password is hard-coded in, so it cant be changed. But since the MariaDB container is closed to the outside, it's not an issue\).
   * Database name: `nextcloud`
   * Database host: `mariadb:3306`
7. Click `Finish setup`.

   ![](https://i.imgur.com/jU8wOUD.png)

8. You will now be logged into Nextcloud.

## 5. Adding Folder\(s\)

1. Click the icon at the top right and select "Apps".

   ![](https://i.imgur.com/cHQUv1Z.png)

2. Enable `External storage support`. Type in your admin password to confirm.

   ![](https://i.imgur.com/2nKCBVt.png)

3. Click the icon at the top right and select "Settings".

   ![](https://i.imgur.com/c3vDcR7.png)

4. Click "External storages" under "Administration".

   ![](https://i.imgur.com/Gi7Lhxe.png)

5. For each folder you want to add, set the following:

   1. Folder name: your preference.
   2. External storage: `local`.
   3. Authentication: your preference \(default is `None`\).
   4. Configuration: `/mnt/unionfs/Media/path/to/folder` \(make sure this path already exists; you could even share your entire `/mnt/unionfs/Media/` path\).
   5. Available for: your preference \(default is blank - for all users\).
   6. Press the checkmark to save.

   ![](https://i.imgur.com/YCLJm5w.png)

