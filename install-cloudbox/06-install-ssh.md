# SSH

The [preinstall]() created a user account for you based on what you had in [accounts.yml]().

If you are currently logged in as root, log out and log back in with the user account.

**From now on, you will always log into your server with this account \(i.e. not with root\).**

Example:

```bash
ssh yourusername@yourserveripaddress
```

Enter your password.

After Cloudbox setup, you may use a subdomain to ssh in if you choose:

```bash
ssh yourusername@<cloudbox/mediabox/feederbox>.yourdomain.ltd
```

You may want to set up [passwordless ssh logins](https://www.tecmint.com/ssh-passwordless-login-using-ssh-keygen-in-5-easy-steps/)