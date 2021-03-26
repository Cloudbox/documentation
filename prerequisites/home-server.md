# Home Server

## Required for home server installs: 

1. Make sure your ISP doesn't block ports 80 and 443.  All access to the apps is via a reverse proxy over ports 80 and 443, so if your ISP blocks these ports, it won't work. 
2. Make sure that your router supports hairpin NAT.  The apps are accessed by subdomain.yourdomain.tld, so if your router doesn't support hairpin NAT you won't be able to resolve the domain and won't be able to access your applications from inside your network. 
3. Open the relevant [ports](https://github.com/Cloudbox/Cloudbox/wiki/Reference%3A-Cloudbox-Ports) \(eg `80`, `443`, etc\) in your [router](https://portforward.com/router.htm)/firewall and forward them to the IP of the box on which you want to install Cloudbox, **before installing Cloudbox**. 
4. Point your domain at your home IP and configure some dynamic DNS software to keep it updated. Cloudbox has a dynamic dns client available \[it's not installed by default\], but there are many ways to set this up. Make sure that DNS has propagated and your domain returns your home IP via `ping` or something like it, **before installing Cloudbox**.

Those last two need to be done before installing Cloudbox to enable the certificate-generation system to work.

