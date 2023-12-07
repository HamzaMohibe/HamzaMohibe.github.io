+++
archetype = "chapter"
title = "Docker and Systemd"
weight = 3
+++
## Docker
More information on docker can be found [here](https://wiki.archlinux.org/title/docker).

## Systemd
To ensure that our Docker container runs when the machine starts and updates with the WAR file, we need to create a systemd service. Systemd is an "init system" that manages the daemons that initially start on our system (It also does other things but that's beyond scope). You can find more information on systemd [here](https://wiki.archlinux.org/title/systemd). The following is our service file, which starts the Docker container. I've configured systemd to run it every time the server starts.

![systemd](https://github.com/jrykns-org/not-a-virus-map/assets/55873910/0853e4d2-3ef4-4027-89cb-438d4f380204)
