# Instructions per Commit

## Docker-compose only (commit: `90946e5`)

Pure docker-compose to run locally, without any (Treafik) reverse-proxy. Run:
`docker-compose up -d`

## Docker-compose with Traefik (commit: `???????`)

Traefik added as separate docker-compose file. No added functionality yet (i.e., just HTTP/port 80, and no Traefik dashboard).
Docker-compose.overrride.yml is added to use during development.

- Run locally in development: `docker-compose up -d`
- Run on server:
  - Create external Docker network: `docker network create traefik-public`
  - Start Traefik reverse-proxy: `docker-compose -f docker-compose.traefik.yml up -d`
  - Start backend: `docker-compose -f docker-compose.yml up -d` (note: specifying yml file is needed, to avoid docker-compose.override.yml to kick in)
