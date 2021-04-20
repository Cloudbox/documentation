# Cloudbox/Feederbox/Mediabox

This will install the rest of Cloudbox.

{% hint style="danger" %}
NOTE: You should NOT be logged into your server as `root` at this point. You should be logged in as the user you created/specified in the **[**preinstall**](05-preinstall.md)**.
{% endhint %}

{% tabs %}
{% tab title="Cloudbox" %}
Cloudbox is the standard all-in-one install.  All activities take place on this machine.  If you're not sure which install type you want to use, it is probably this one.

1. To start the install, run the following command:

   ```bash
   cb install cloudbox
   ```

   **NOTE**: _Pay attention to the output_, it may require you to run it more than once in some cases, for example if settings have changed.  
  
   If you did not enter your Plex credentials in [accounts.yml](03-install-accounts.yml.md), the install will stop and ask you for a [Plex Claim Token](../more-information/plex-access-token.md).  Paste it at the prompt.  
   _Note 1: You may not see the claim token after pasting it. If that occurs, assume it pasted OK and press enter to continue._  
   The next task on the screen will show you what claim token was submitted \(in lowercase\) and it will continue with the rest of the Cloudbox install.  
   _Note: After install, if you do not see your Plex server after logging in, then Plex claim token was likely entered-in incorrectly. To fix this, see_ [_here_](../troubleshooting/faq-from-cb.md#if-you-are-unable-to-find-your-plex-server)_._
{% endtab %}

{% tab title="Feederbox" %}
A Feederbox is a dedicated download box \[it doesn't have Plex or Emby installed, for example\]  It will typically be installed along with a Mediabox, and the two will typically be installed on different machines.  

If you are installing the Feederbox/Mediabox combination, install the Feederbox first, then the Mediabox.  Note that this means you will go through all the previous install steps on **both machines**.

1. To start the install, run the following command:

   ```bash
   cb install feederbox
   ```
{% endtab %}

{% tab title="Mediabox" %}
Mediabox is a dedicated media player box \[it doesn't have any download applications installed\]  It will typically be installed along with a Feederbox, and the two will typically be installed on different machines.  It doesn't have to be installed along with a Feederbox, though.  Perhaps you are accessing someone else's media store.

If you are installing the Feederbox/Mediabox combination, install the Feederbox first, then the Mediabox.  Note that this means you will go through all the previous install steps on **both machines**.

1. To start the install, run the following command:

   ```bash
   cb install cloudbox
   ```

   **NOTE**: _Pay attention to the output_, it may require you to run it more than once in some cases, for example if settings have changed.  
  
   If you did not enter your Plex credentials in [accounts.yml](03-install-accounts.yml.md), the install will stop and ask you for a [Plex Claim Token](../more-information/plex-access-token.md).  Paste it at the prompt.  
   _Note 1: You may not see the claim token after pasting it. If that occurs, assume it pasted OK and press enter to continue._  
   The next task on the screen will show you what claim token was submitted \(in lowercase\) and it will continue with the rest of the Cloudbox install.  
   _Note: After install, if you do not see your Plex server after logging_ 

   _in, then Plex claim token was likely entered-in incorrectly. To fix this, see_ [_here_](../troubleshooting/faq-from-cb.md#if-you-are-unable-to-find-your-plex-server)_._
{% endtab %}
{% endtabs %}

2. Reboot after Install completes. \(this is especially important for new installs\):

```text
sudo reboot 
```

3. After the reboot, the containers should start up and all apps should be available at their subdomains. THIS CAN TAKE SOME TIME, particularly on first install, since certificates need to be retrieved for all the subdomains. Give it a few minutes. If, after 10 minutes, you still can't connect to the applications, log in and verify that the containers are running: 

```text
docker ps
```

That should show you a list of all the containers with status. If the list is empty, run the install command above again. Chances are it terminated early with a message of some sort.

