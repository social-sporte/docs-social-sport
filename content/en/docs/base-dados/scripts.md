---
title: "Scripts"
description: "Scripts para criar a base, inserir dados e realizar rollback."
lead: "Scripts para criar a base, inserir dados e realizar rollback."
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "base-dados"
weight: 20
toc: true
---

{{< alert icon="👉" text="Os scripts ficam dentro do repositorio do projeto back-end na pasta `./src/main/resource/db.migration/`." />}}


### Criação do schema Social Sport

Executar os arquivos abaixo em sequencia:

* v1__init.sql => Criação das tabelas
* v2__Inserir_roles_users.sql => Roles de acesso
* v3__Inserir_dominios.sql => Esportes e configurações
* v4__Inserir_cidades.sql => Lista de cidades brasileiras


## Rollback

Para realizar o rollback do schema do social sport sem ter conflito de chaves, execute o script: 

*  rollback.sql => Deleta as tabelas e exclui o schema






