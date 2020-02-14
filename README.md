# gitea-docker

Installation Gitea with Docker

## Copy your `.env`

copy your .env file

```sh
cp -r .env.example .env
```

How to find your UID and GID:

```sh
# get UID
id -u
# get GID
id -g
```

## Start the Gitea

```yaml
version: "2"

networks:
  gitea:
    external: false

services:
  server:
    image: gitea/gitea:1.11.0
    environment:
      - USER_UID=${USER_UID}
      - USER_GID=${USER_GID}
    restart: always
    networks:
      - gitea
    volumes:
      - ./gitea:/data
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - "3000:3000"
      - "2221:22"
```
