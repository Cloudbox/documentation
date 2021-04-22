# Accounts

## Overview of accounts.yml

```yaml
---
user:
  name: seed
  pass: password123
  domain: testcloudbox.ml
  email: your@email.com
cloudflare:
  email: bing@bang.boing
  api: YOUR_CLOUDFLARE_API_KEY
plex:
  user: YOUR_PLEX_USER
  pass: YOUR_PLEX_PASSWORD
pushover:
  app_token: YOUR_PUSHOVER_APP_TOKEN
  user_key: YOUR_PUSHOVER_USER_KEY
  priority: YOUR_PUSHOVER_PRIORITY
apprise: YOUR_APPRISE_URL
```

{% hint style="danger" %}
The user in this file must not be **root**.
{% endhint %}

{% hint style="danger" %}
Enter a password for the user.  Don't leave it blank. Even if you are planning to use SSH keys to connect to your box.  This user and password are used to set up authentication for some applications in this repo and Community, and a blank password may cause trouble there.
{% endhint %}

{% hint style="info" %}
This is a YAML file, and is subject to standard YAML format rules.    
  
Generally, use only letters and numbers.  If you use something other than those, wrap the value in double-quotes \[and don't use a double-quote within it\].   More details [here](../placeholder-page.md).

Google can help if you are unfamiliar with this format.
{% endhint %}

## Editing accounts.yml

You will need to edit everything shown above to reflect your domain, email, user, and password.  Some of these values can remain blank.  Details below.

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Open the file for editing::

   ```bash
   nano accounts.yml
   ```

3. When done editing, save the file: Ctrl + X Y Enter.

## Options in accounts.yml

* `user`: User information.
  * `name`: User name for the server.
    * If user account with this name does not already exist, it will be created during install.
    * Also used to create first-time logins for NZBGet, ruTorrent, NZBHydra2, and potentially other apps.
    * Default is `seed`.
    * This parameter is **required**.
  * `pass`: Password for the user account and for misc apps.
    * Sets password for the server's user account when creating a new account. This will not change the password of an existing one.
      * Also used to create first-time logins for NZBGet, ruTorrent, NZBHydra2, and potentially other apps.
      * This parameter is **required**.
  * `domain`: Domain name for the Cloudbox server.
    * If you don't have one, see \[\[here\|Prerequisites: Domain Name\]\].
    * This should be the domain "below" the cloudbox subdomains. For example, if you want to access Sonarr at "sonarr.domain.tld", enter "domain.tld". If you want "sonarr.foo.domain.tld", enter "foo.domain.tld".
    * This parameter is **required**.
  * `email`: E-mail address.
    * This is used for the Let's Encrypt SSL certificates.
    * It does not have to be an email address at the domain above.
    * This parameter is **required**.
* `cloudflare`: Cloudflare Account
  * Fill this in to have Cloudbox add subdomains on Cloudflare, automatically; leave it blank, to have all Cloudflare related functions disabled.
  * Note: CDN \(i.e. proxy\) will not be turned on, by default, but you may turn them on later \(see \[\[here\|Prerequisites: Cloudflare\#post-setup\]\]\).
  * `email`: E-mail address used for the Cloudflare account.
  * `api`: \[\[API Token\|Prerequisites: Cloudflare\]\].
  * This parameter is optional.
  * Default is blank.
* `plex`: Plex.tv account credentials.
  * This will be used to 
    * claim the Plex server under your username
    * generate Plex Access Tokens for apps such as Plex Autoscan, etc. 
  * `user` - Plex username or email address on the profile.
  * `pass` - Plex password.
  * This parameter is optional.
  * **The new Two-Factor Authentication \[TFA\] system added by Plex will prevent these automated operations from succeeding.  The** [**Plex article introducing TFA**](https://support.plex.tv/articles/two-factor-authentication/) **has a possible workaround.  If successful, you will need to perform that workaround every time you run the `plex` tag.  You can also disable TFA while you run the cloudbox setup \[or the plex tag\] and then re-enable it when complete.**
* `pushover`: Pushover settings.
  * This will be used to send out messages during certain tasks \(e.g. backup\).
  * `app_token` - Pushover Application API Token \(create a new application for Cloudbox\).
  * `user_key` - Pushover User Key.
  * `priority` - Priority level for messages.
    * Choices are: `-2`, `-1`, `0`, `1`, and `2`.
    * Default is blank \(i.e. `0`\).
  * This parameter is optional.
* `apprise`: apprise url.
  * This will be used to send out messages during certain tasks \(e.g. backup\).
  * This parameter is not nested like the others in this file.
  * This parameter is optional.

