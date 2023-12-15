+++
archetype = "chapter"
title = "Certbot and Nginx"
weight = 2
+++
## Nginx
 
Our front and backend use jetty to serve our web page and API, how ever it runs on port 8080, and because it's running in a docker container it's hard to change its configuration to use the default web port with SSL. That's where Nginx comes in, it's a "reverse proxy", which just means it can forward requests from a client to a server. In our case, it encrypts the traffic from the user, forwards it to port 8080 where Jetty is listening, and sends it back to the user with encryption. You can find more information on Nginx [here](https://wiki.archlinux.org/title/nginx).

## Certbot

For SSL to work we need trusted a certificate authority to give us a certificate file. Thankfully letsencrypt automatically gives out and installs certificates automatically through Certbot. The full configuration file at the end of the page shows how Certbot has installed a certificate and redirected all unencrypted traffic to the encrypted port. More information on Certbot can be found [here](https://wiki.archlinux.org/title/Certbot).

## Cron

![Crontab configuration](https://github.com/jrykns/not-a-virus-map/assets/55873910/40c0ed17-5041-4bfe-91c0-a357c0b43bf5)

To comply with best practices we need to generate new certificates regularly so if a certificate is stolen no attack can be used for long. Currently, the maximum time for a certificate to be in use is 2 years but to be proactive we're creating a new certificate each month. Cron is a daemon running on our server that will run a command at a specified interval, our configuration regenerates the certificate each month. More information on Cron can be found [here](https://wiki.archlinux.org/title/cron).

## Configuration file
![Nginx configuration](https://github.com/jrykns/not-a-virus-map/assets/55873910/15514973-d508-41b7-8dd7-2e0cc380371d)
