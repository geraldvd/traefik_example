# Instructions per Commit

## Docker-compose only (commit: `90946e5`)

Pure docker-compose to run locally, without any (Treafik) reverse-proxy. Run:
`docker-compose up -d`

## Docker-compose with Traefik (commit: `39e9bcf`)

Traefik added as separate docker-compose file. No added functionality yet (i.e., just HTTP/port 80, and no Traefik dashboard).
Docker-compose.overrride.yml is added to use during development.

- Run locally in development: `docker-compose up -d`
- Run on server:
  - Create external Docker network: `docker network create traefik-public`
  - Start Traefik reverse-proxy: `docker-compose -f docker-compose.traefik.yml up -d`
  - Start backend: `docker-compose -f docker-compose.yml up -d` (note: specifying yml file is needed, to avoid docker-compose.override.yml to kick in)

## Docker-compose with Traefik incl. HTTPS (commit: `5d078c9`)

Included HTTPS to docker-compose files. Usage the same as previous step, but with HTTPS.

- Run locally in development: `docker-compose up -d`
- Run on server:
  - (Create network if it doesn't yet exist: `docker network create traefik-public`)
  - Start Traefik reverse-proxy: `docker-compose -f docker-compose.traefik.yml up -d`
  - Start backend: `docker-compose -f docker-compose.yml up -d` (note: specifying yml file is needed, to avoid docker-compose.override.yml to kick in)

## Docker-compose with Traefik incl. HTTPS and Traefik Dashboard (commit: `???????`)

Added Traefik Dashboard, with authentication. Usage is the same as the previous step, but first environment variables with username and password need to be set (below we use both username and password to be `admin`)

- Run: `export TRAEFIK_USERNAME=admin`
- Run: `export TRAEFIK_PASSWORD=admin`
- Run: `export TRAEFIK_HASHED_PASSWORD=$(openssl passwd -apr1 $TRAEFIK_PASSWORD)`

Then, recreate the Traefik container:

- `docker-compose -f docker-compose.traefik.yml up -d`
