---
title: "Inicializando Aplicação back-end"
description: "Subindo o projeto social-sporte-api em ambiente local."
lead: "Subindo o projeto social-sporte-api em ambiente local."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "spring-boot"
weight: 60
toc: true
---

## Requisitos

Para rodar a aplicação na maquina local é preciso ter os seguintes recursos instalados:


* Java 11
* Maven
* Git
* Servidor [PostgreSql →]({{< relref "inicializando" >}}) 
* Inicializar base de dados [Social Sporte →]({{< relref "scripts" >}})


### Construir

{{< alert icon="👉" text="Utiliza-se o Maven para construir o arquivo .jar que será executado." />}}

1- Realizar o Clone do projeto no [git](https://github.com/social-sporte/social-sporte-api)

2- Executar o comando de construção do jar utilizando o maven

```bash
mvn clean package 
```
3- O Arquivo social-sporte-api-0.0.1-SNAPSHOT.jar será criado dentro da basta `target/` 

### Executar

Para executar o Social sport devemos escolher o profile de execução para definir o ambiente de acesso(local, dev) que esta configurado no arquivo `application.properties`  a configuração `spring.profiles.active=local`

```bash
cd target
java -jar social-sporte-api-0.0.1-SNAPSHOT.jar 
```

A aplicação executa na porta padrão 8080 e a uri do Swagger local é: `http://localhost:8080/swagger-ui.html`
