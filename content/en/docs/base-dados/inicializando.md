---
title: "Inicializando Servidor Postgres"
description: "Inicializando servidor de banco de dados local utilizando docker-compose."
lead: "Inicializando servidor de banco de dados local utilizando docker-compose."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "base-dados"
weight: 10
toc: true
---

## Requisitos

- [docker compose](https://docs.docker.com/compose/install/) — latest source release

{{< details "Por que docker-compose?" >}}
Para facilitar a instalação do servidor local
{{< /details >}}

#### Iniciar

{{< alert icon="👉" text="O script para subir a base via docker-compose fica dentro do repositorio do projeto back-end na pasta `./infra/docker-compose.yml`." />}}


```bash
sudo docker-compose up -d
```


#### Executar os scripts

[Scripts →]({{< relref "scripts" >}})
