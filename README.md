# https://hub.docker.com

start a postgres instance
https://hub.docker.com/_/postgres

# $ docker run --name postgres -e POSTGRES_PASSWORD=docker -d postgres

listar docker em execucao
# $ docker ps

listar docker que estão dormindo
# $ docker ps -a

parar docker
# $ docker stop ID

excluir docker
# $ docker rm ID

start a postgres instance setando a porta
# $ docker run --name postgres -e POSTGRES_PASSWORD=docker -p 5433:5432 -d postgres


# $ docker logs ID/IMAGE
# $ docker stats ID/IMAGE

startar docker
# $ docker start ID/IMAGE


# $ docker exec -it postgres bash


# Use postgres/example user/password credentials


# docker-compose.yml

version: '3.1'

services:

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_PASSWORD: example

  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080

# docker-compose.yml

version: '3.1'

services:

    postgres:
        image: postgres:12
        container_name: "postgres-v12"
        ports:
            - 5432:5432
        environment:
            POSTGRES_PASSWORD: admin
        volumes:
            - db_vol:/var/lib/postgresql/data

    pgadmin:
        image: dpage/pgadmin4
        container_name: pgadmin4
        ports:
            - 3333:80
        environment:
            PGADMIN_DEFAULT_EMAIL: admin
            PGADMIN_DEFAULT_PASSWORD: admin


volumes:
    db_vol:
        external:
            name: "postgres-v12"
