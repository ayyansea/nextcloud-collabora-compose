# nextcloud-collabora-compose

A Docker Compose project for Nextcloud + Collabora

**Important!** The compose file doesn't contain a reverse proxy mainly because I use an external nginx for this purpose.

## Usage

This is a very straightforward docker-compose project that will create the following resources:

* nextcloud container
* collabora container
* mysql container (for nextcloud)
* a network
* two volumes: for mysql's and nextcloud's data

To use it, clone this repo and move into its' directory:

```
git clone https://github.com/ayyansea/nextcloud-collabora-compose.git
cd nextcloud-collabora-compose
```

Using the provided example file, create your own .env file and configure the variables:

```
mv .env.example .env
vim .env # or nano .env, nvim .env, et cetera
```

After that, simply bring up the project:

```
docker compose up -d
```

By default, nextcloud is going to be accessible at http://127.0.0.1:9721 and collabora at http://127.0.0.1:9722.
Configure a reverse proxy to access them from outside with a public domain name. My nginx configuration and consists of two files since I use separate
domain names for my services. The configuration is very primitive, literally just a "location /" block that proxy_passes traffic to services on localhost.
