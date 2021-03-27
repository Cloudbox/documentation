# Cloudbox/Feederbox/Mediabox

This will install the rest of Cloudbox.

**NOTE: You should NOT be logged into your server as `root` at this point. You should be logged in as the user you created/specified in the** [**preinstall**](05-preinstall.md)**.**

{% tabs %}
{% tab title="Cloudbox" %}
1. To start the install, run the following command:

   ```bash
   cb install cloudbox
   ```

   **NOTE**: _Pay attention to the output_, it may require you to run it more than once in some cases, for example if settings have changed.

2. If you did not enter your Plex credentials in [accounts.yml](03-install-accounts.yml.md), the install will stop and ask you for a [Plex Claim Token](../more-information/plex-access-token.md).  Paste it at the prompt. _Note 1: You may not see the claim token after pasting it. If that occurs, assume it pasted OK and press enter to continue._ The next task on the screen will show you what claim token was submitted \(in lowercase\) and it will continue with the rest of the Cloudbox install. _Note: After install, if you do not see your Plex server after logging in, then Plex claim token was likely entered-in incorrectly. To fix this, see_ [_here_](../troubleshooting/faq-from-cb.md#if-you-are-unable-to-find-your-plex-server)_._
3. Reboot after install completes \(this is especially important for new installs\):

   ```bash
    sudo reboot
   ```

4. After the reboot, the containers should start up and all apps should be available at their subdomains. **THIS CAN TAKE SOME TIME**, particularly on first install, since certificates need to be retrieved for all the subdomains. Give it a few minutes. If, after 10 minutes, you still can't connect to the applications, log in and verify that the containers are running:

   ```bash
    docker ps
   ```

   That should show you a list of all the containers with status. If the list is empty, run the install command above again. Chances are it terminated early with a message of some sort.
{% endtab %}

{% tab title="Feederbox" %}
1. To start the install, run the following command:

   ```bash
   cb install feederbox
   ```

2. Reboot after install completes \(this is especially important the first time\):

   ```bash
   sudo reboot
   ```
{% endtab %}

{% tab title="Mediabox" %}
1. To start the install, run the following command:

   ```bash
   cb install mediabox
   ```

2. If you did not enter your Plex credentials in [accounts.yml](03-install-accounts.yml.md), the install will stop and ask you for a [Plex Claim Token](../more-information/plex-access-token.md).  Paste it at the prompt. _Note 1: You may not see the claim token after pasting it. If that occurs, assume it pasted OK and press enter to continue._ The next task on the screen will show you what claim token was submitted \(in lowercase\) and it will continue with the rest of the Cloudbox install. _Note: After install, if you do not see your Plex server after logging in, then Plex claim token was likely entered-in incorrectly. To fix this, see_ [_here_](../troubleshooting/faq-from-cb.md#if-you-are-unable-to-find-your-plex-server)_._
3. Reboot after install completes \(this is especially important the first time\):

   ```bash
   sudo reboot
   ```
{% endtab %}
{% endtabs %}

