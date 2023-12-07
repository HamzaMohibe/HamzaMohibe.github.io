+++
archetype = "chapter"
title = "Azure"
weight = 1
+++
# Azure and our server technologies

## Azure groups

![Picture of Azure group](https://github.com/jrykns/not-a-virus-map/assets/55873910/be3f6a06-dda4-46bd-915c-dc58dc5d1b93)

When Azure creates a server, it also creates a "resource group" that contains everything else needed to make that machine connect to the internet, and in our case, it also contains an SQL server. This wiki page will document what the major components of our resource group are, and how they interact and will be updated as resources are added or changed.

## Virtual machine

![Picture of VM](https://github.com/jrykns/not-a-virus-map/assets/55873910/bb4bfb7b-8385-4b59-a551-e02f817b2851)

Our virtual machine is a standard Azure server with 1 vcpu and 1 GiB memory. This should be more than enough to handle the work load of our back end and front end the decision to go for this specific configuration was that java is memory hungry so the lower tiers with less memory might not give us enough to run the back end, front end and a data base in RAM (used in early development). 

The Linux distribution its running is Ubuntu server, this is corporate backed so there are lots of helpful guides and most common problems have well documented solutions. Its also a "stable release" distribution, this means the software is rigorously tested before we can use it, this ensures that our sever should have no unexpected downtime caused by software errors or bugs.

### RSA key authentication

To be as secure as possible our server uses RSA key authentication. This is a private/public key authentication method that is much harder to attack than a standard password, more information can be found [here](https://wiki.archlinux.org/title/SSH_keys).

### Static IP and domain name

![Picture IP](https://github.com/jrykns/not-a-virus-map/assets/55873910/d2d7477f-7a90-4028-8703-d16f6bdb04db)


To setup SSL we need a domain name, Azure can give us one for free. The picture below shows the Azure resource that contains our static IP and the domain we're using to host our application.

## Firewall configuration

![Picture of firewall](https://github.com/jrykns/not-a-virus-map/assets/55873910/a3151b7f-49d3-4d05-8029-0485de1a222d)

Our firewall blocks all ports except port 22, port 80, and port 443 (all other rules allow connections to other resources in the Azure resource group). Port 80 and 443 are used for our web front end (HTTP and HTTPS ports) and port 22 allows us to connect to our machine via ssh.

