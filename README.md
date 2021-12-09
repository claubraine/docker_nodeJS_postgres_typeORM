
# Comandos Docker

**exibe todos os containers em execução no momento**
```bash
docker ps
```

**exibe todos os containers, independentemente de estarem em execução ou não**
```bash
docker ps -a
``` 

**conecta o terminal que estamos utilizando com o do container**
```bash
docker run -it NOME_DA_IMAGEM
```

**inicia o container com id em questão**
```bash
docker start ID_CONTAINER
```

**interrompe o container com id em questão**
```bash
docker stop ID_CONTAINER
```

**inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos**
```bash
docker start -a -i ID_CONTAINER
```

**remove o container com id em questão**
```bash
docker rm ID_CONTAINER
```

**remove todos os containers que estão parados**
```bash
docker container prune
```

**remove a imagem passada como parâmetro**
```bash
docker rmi NOME_DA_IMAGEM
```

**ao executar, dá um nome ao container**
```bash
docker run -d -P --name NOME dockersamples/static-site
```

**define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345**
```bash
docker run -d -p 12345:80 dockersamples/static-site
```

**define uma variável de ambiente AUTHOR com o valor Fulano no container criado**
```bash
docker run -d -P -e AUTHOR="Fulano" dockersamples/static-site
```






**hub docker**
```bash
https://hub.docker.com
```

**start a postgres instance**
```bash
https://hub.docker.com/_/postgres
```

```bash
docker run --name postgres -e POSTGRES_PASSWORD=docker -d postgres
```

**start a postgres instance setando a porta**
```bash
docker run --name postgres -e POSTGRES_PASSWORD=docker -p 5433:5432 -d postgres
```

**logs da imagem**
```bash
docker logs ID/IMAGE
```

**status da imagem**
```bash
docker stats ID/IMAGE
```

**arquivo docker-compose.yml**
```bash
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
```

**docker-compose.yml**
```bash
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
```


