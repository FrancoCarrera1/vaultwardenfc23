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

# Docker
Before we start on your container/VM/Server, we need to get docker installed. I am using an Ubuntu 23.04 image and will be using the commands for that OS, you can find the [Official Docs Here](https://docs.docker.com/engine/install/ubuntu/) for installing Docker.

# Installation
Once Docker is installed we will begin installing Vaultwarden, the following command will pull the image from Docker.
```bash
docker pull vaultwarden/server:latest
```
After we have pulled the image we now need to create a container using the image which is done with the following(after the --name argument you can put whatever container name you would like there) this command runs Docker as a daemon, and the container will come back up automtically in case of a restart:
```bash
docker run -d --name vaultwarden -v /vw-data/:/data/ --restart unless-stopped -p 80:80 vaultwarden/server:latest
```
We can then use the <b>docker ps</b> command to make sure our container is running, it should look like the following
<img src="https://github.com/FrancoCarrera1/vaultwardenfc23/blob/main/image/Screenshot%202024-01-02%20223700.png" height="80%" with="80%" alt="docker ps result"/>

Now after that is setup, you can use the <b>ip addr</b> command to see the containers IP Address, pasting it in your browser will take you to the Vaultwarden page, BUT you will not be able to create an account yet as you need to setup HTTPS, which we will be doing with CloudFlare


