# Portainer

Portainer is a lightweight management UI which allows you to easily manage your different Docker environments (Docker hosts or Swarm clusters).

This repo includes my settings to use it on my server.

## Prerequisites

Make sure you have installed these:
- [Docker and Docker Compose](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04) - Will install all the required packages and software.
- (Optional) [Dockerized Nginx with SSL](https://github.com/madrigals1/nginx) - Will generate SSL certificates and make the app accessible through `SSL_DOMAIN`, that is set inside `.env`.

## Installation

Make a copy of `.env.example` file named `.env`

```shell script
cp .env.example .env
```

---

Environment variables:
- `SSH_PORT` - port, from which portainer will be available through SSH.
- `SSL_DOMAIN` - domain, on which portainer instance will be available through internet.
- `HTTPS_NETWORK` - network, in which our HTTPS server (Dockerized Nginx) should be running.
- `UI_PORT` - port, on which Web UI will be running.

```dotenv
# Docker settings
HTTPS_NETWORK=https_network
SSH_PORT=8000

# Let's encrypt settings
SSL_DOMAIN=portainer.example.com
UI_PORT=9000
```

---

Create network with the name, that we have in `HTTPS_NETWORK` environment variable.

> This step is not required, if you don't use this service over HTTPS

```shell script
docker network create https_network
```

---

Build the Docker image

```shell script
docker-compose build
```

## Running

Start
```
docker-compose up
```

Stop
```
docker-compose down
```

## Usage

- Access **Portainer** through `SSL_DOMAIN` or `localhost:UI_PORT` from browser.

## Authors
- Adi Sabyrbayev [Github](https://github.com/madrigals1), [LinkedIn](https://www.linkedin.com/in/madrigals1/)