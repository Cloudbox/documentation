# Ansible Vault Primer

This page is a primer on Ansible Vault and, as an example, it will take you through encrypting your \[\[accounts.yml\|Install: accounts.yml\]\] file as well.

## Introduction

Ansible Vault is a feature of Ansible that allows users to encrypt data with AES 256 cipher. This allows us to secure sensitive data, such as passwords and keys, and have Ansible decrypt them automatically when they are needed.

When an Ansible Playbook is run the encrypted data is decrypted on the fly via a user-supplied password. This password is either provided via a password file or with a prompt.

## Ansible Vault Basics

### Encrypting a File

To encrypt `accounts.yml`, follow these steps.

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Run the following command:

   ```text
   ansible-vault encrypt accounts.yml
   ```

3. Set a new password at the prompt and confirm:

   ```text
   New Vault password:
   Confirm New Vault password:
   ```

4. When finished, you'll get this:

   ```text
   Encryption successful
   ```

5. The `accounts.yml` file will now look like this:

   ```text
   $ANSIBLE_VAULT;1.1;AES256
   38393264656134313831626566383335336438363265363163323736653834616537303030666537
   3561666539363138663162303633323264643665333938390a616638636531306439383034346166
   30656535656564366665333637633935656564393633636432613064373832373663313765653635
   3339666361393166340a316566386134376235366465626337313665353565323237376338633064
   32333838396136373038643963373932353632613033366665613836316336633538633737323466
   34653461323636626638613264643334613763623365626339616636646537343339383537323464
   64336331623665373362393435313730383831303163316161343664613731346139633737363264
   30396366636332663032633438376136613831663862313437633130656636353633323264643839
   36353665313231653564616636313931646538323965383539313931636164393861326635306235
   65623030393166343635346437633638393161363962363439336138613437336231353430323762
   38306435616535343737396438663930393933346434306139633538653861613633346536326663
   32373634383839653665
   ```

### Viewing an Encrypted File

To view the contents of `accounts.yml`, follow these steps.

_Note: The decryption only lasts while it is open on the screen, and until you hit the Q key._

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Run the following command:

   ```text
   ansible-vault view accounts.yml
   ```

3. Type in the password at the prompt:

   ```text
   Vault password:
   ```

4. The screen will now show you the contents:

   ```text
   ---
   user: seed
   passwd: password123
   domain: testcloudbox.ml
   email: your@email.com
   cloudflare_api_token:
   (END)
   ```

5. When finished viewing, hit Q.

### Editing an Encrypted File

To edit the contents of `accounts.yml`, follow these steps.

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Run the following command:

   ```text
   ansible-vault edit accounts.yml
   ```

3. Type in the password at the prompt:

   ```text
   Vault password:
   ```

4. This will open the decrypted file in nano.
5. When done editing, save the file: Ctrl + X Y Enter.

### Changing the Password of an Encrypted File

To change the password of `accounts.yml`, follow these steps.

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Run the following command:

   ```text
   ansible-vault rekey accounts.yml
   ```

3. Type in the current password at the prompt:

   ```text
   Vault password:
   ```

4. Type in and confirm a new vault password:

   ```text
   New Vault password:
   Confirm New Vault password:
   ```

5. After successful re-encryption, you'll see this:

   ```text
   Rekey successful
   ```

### Decrypting an Encrypted File

To decrypt `accounts.yml`, follow these steps.

_Note: The decryption here is permanent, until you re-encrypt the file again._

1. Go to the Cloudbox folder:

   ```bash
   cd ~/cloudbox/
   ```

2. Run the following command:

   ```text
   ansible-vault decrypt accounts.yml
   ```

3. Type in the password at the prompt:

   ```text
   Vault password:
   ```

4. When finished, you'll get this:

   ```text
   Decryption successful
   ```

5. `settings.yml` will now look like this:

   ```text
   ---
   user: seed
   passwd: password123
   domain: testcloudbox.ml
   email: your@email.com
   cloudflare_api_token:
   ```

## Password File Setup

Storing the password in a password file allows Ansible to run commands without a prompt.

The following commands can run without password prompts:

* `ansible-vault view`
* `ansible-vault edit`
* `ansible-vault encrypt`
* `ansible-vault decrypt`

Once a password file is created, it's location will need to be added to `ansible.cfg`.

_Note: Prompted vault passwords \(i.e. `--ask-vault-pass` or `--vault-id @prompt`\) will not work with Cloudbox's Ansible playbook, however, you can use some other scripted solution \(e.g. ssh based key script with ssh forwarding\) to generate a password file and pass the path location to the env variable `ANSIBLE_VAULT_PASSWORD_FILE`._

### Password File

1. First we need to create a password file. The location and name is up to you.

   ```text
   touch ~/.ansible_vault
   ```

2. Will use an example password of `password321`.

   ```text
   nano ~/.ansible_vault
   ```

3. Type in your password

   ```text
   password321
   ```

4. When done editing, save the file: Ctrl + X Y Enter.
5. The password file will look like this:

   Command:

   ```text
   cat ~/.ansible_vault
   ```

   Output:

   ```text
   password321
   ```

### Ansible Config

We will now need to add the location of the password file into `ansible.cfg`, in the format of:

```text
vault_password_file = /PATH/TO/PASSWORD/FILE
```

Example:

Command:

```text
cd ~/cloudbox
cat ansible.cfg
```

Output:

```text
[defaults]
inventory = inventories/local
callback_whitelist = profile_tasks
command_warnings = False
retry_files_enabled = False
hash_behaviour = merge
vault_password_file = ~/.ansible_vault
```

### Encrypt Settings

If you haven't already done so, encrypt the `accounts.yml` file. You will not be prompted for a password this time.

Command:

```text
ansible-vault encrypt accounts.yml
```

Output:

```text
Encryption successful
```

### Ansible Playbook

Running `ansible-playbook` tasks, will no longer prompt you for a vault password.

Each time a playbook is ran, the decryption will occur on-the-fly, but will remain encrypted after the playbook finishes.

Example:

```text
sudo ansible-playbook cloudbox.yml --tags cloudbox
```

