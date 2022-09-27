# Docker Home Server

Docker services running in a home server.

It's meant to work out of the box and without configuration, except for some
environment variables that will have to be filled after cloning.

## 1. Clone and set environment variables

In order to specify the settings fill the options in .env.dist
and then paste all the values to /etc/environment

Then make sure they are set with the command: ```printenv```

## 2. Create and launch containers

Containers definition are separated in different docker-compose files
to help launch desired services only. Once you launch them for
the first time they will keep alive with the system restarting
if necessary until you decide to stop them manually.

```bash
docker-compose \
    -f services/traefik/docker-compose.yml \
    -f services/ddclient/docker-compose.yml \
    -f services/plex/docker-compose.yml \
    -f services/transmission/docker-compose.yml \
    -f services/watchtower/docker-compose.yml \
    -f services/tautulli/docker-compose.yml \
    up -d
```

# 3. Check and manage

Check that all services are up:

```docker ps```

In case you need to stop or remove a container
use docker and the container name:

```docker stop minecraft && docker rm minecraft```

If you have doubts on the services please search google
for what they do. 

# 4. Open each service and configure it.

You should go over each service and check it's up and configure
it if necessary. All the configurations are going to be stored
inside the "volumes" folder. You can regularly back it up.

# 5. About SSL certificates

If you need ssl certificates and you have a domain, there is an option
to create it with Lets Encrypt. This repo is configured for using
OVH as a domain name provider. If you dont use OVH you can change the
configuration of ```traefik``` in order to use another one:

https://docs.traefik.io/configuration/acme/

Still this is a secondary step and will not stop your services from working.
