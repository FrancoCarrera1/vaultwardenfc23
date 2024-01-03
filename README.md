# Vaultwarden for home use
Before we start all credit to the creation of this software goes [here](https://github.com/dani-garcia/vaultwarden), I did not create the software at all I simply want to provide a guide on how to install and configure the software for Home use, so others can use it, and so I can have documentation for myself. The link provides the official documentation, but I like creating my own.

# What is Vaultwarden?
Vaultwarden is Bitwarden written in Rust, it has all the paid features for FREE, and can be self-hosted or in the cloud, How I use it is as a password manager. I have it setup at home on an old PC running proxmox as the hypervisor. I then have an Ubuntu container thats spun up, and inside of that container is the Vaultwarden container. I am able to access from anywhere as long as there is internet, and can use the bitwarden Extension and App on my laptop and phone, to securely access my passwords from anywhere.

# Pre-requisites
<ol>
  <li>An old computer running your hypervisor or OS of choice, preferably Linux</li>
  <li>A domain which will cost money (if you dont care about the name it will be about $1/yr)</li>
  <li>I am deploying using Cloudflare tunnels so an account with them will be needed(you can also get the domain from them)</li>
  <li>And finally Patience, things will not work the first time.</li>

</ol>

