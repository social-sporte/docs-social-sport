---
title: "Centro Esportivo"
description: "Gerenciamento de quadras, horarios e funcionalidades para funcionario."
lead: "Funções que o centro esportivo possui."
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "regras"
weight: 630
toc: true
---

# Funcionalidades

- Centro esportivo
- Horario de funcionamento
- Quadras
- Horarios de cada quadra
- Horario Fixo
- Marcar Aula
- Notificacoes
- Funcionarios
- Configurações de Pagamento


## Centro esportivo

### Cadastro  

Fluxo:  
   
1. Valida o nome de usuário e verifica se todos os dados necessários estão disponíveis.
2. Gera uma nova senha composta por 6 dígitos numéricos aleatórios.
3. Registra o usuário.
4. Verifica a localização no Google e insere a geolocalização como parâmetro do sistema.
5. Registra o responsável, o centro esportivo e o endereço.
6. Tenta enviar a senha por e-mail. Em caso de falha, é feito um rollback das ações realizadas.
  

Request:  
<span style="font-size: smaller;">Request: POST   </span><br>
<span style="font-size: smaller;">PATH:/signup/sport-center  </span><br>
<span style="font-size: smaller;">JSON: </span><br>


```bash
{
    "address": {
        "logradouro": "Rua Sem saida",
        "number": "13",
        "complement": null,
        "district": "Miranda",
        "state": "MG",
        "cityId": 2282,
        "cep": "38444-230",
        "country": "Brasil",
        "latitude": "",
        "longitude": ""
    },
    "credential": {
        "username": "321323"
    },
    "lessor": {
        "name": "Nome da centro esportivo",
        "cnpj": ""
    },
    "owner": {
        "fullName": "Power Ranger Branco",
        "cpf": "870.989.970-72",
        "birthDate": "2023-05-23",
        "email": "biwef72549@peogi.com",
        "cellphone": "(38)98188-8238"
    }
}
```

Retornos:  
<span style="font-size: smaller;">200 OK  </span><br>
<span style="font-size: smaller;">400 Dados inválidos</span>
<span style="font-size: smaller;">422 Email não foi enviado</span>


### Consulta  

Fluxo:  
   
1. Consulta Usuario pelo token
2. Consulta Centro esportivo pelo usuario(regra para consultar para funcionario)
3. Retorna dados centro esportivo
  

Request:  
<span style="font-size: smaller;">Request: GET   </span><br>
<span style="font-size: smaller;">PATH:/api/sport-center  </span><br>


Retornos:  
<span style="font-size: smaller;">200 OK  </span><br>
<span style="font-size: smaller;">404 não encontrada</span>
<span style="font-size: smaller;">403 não permitido</span>
<span style="font-size: smaller;">401 não autorizado</span>

```bash
{
    "id": 1,
    "nomeCentroEsportivo": "arena ribeuri",
    "cnpj": "25.229.451/0001-26",
    "image": "https://social-sport-api.herokuapp.com/public/images/1687921067574-PhotoRoom_20230626_194901.jpeg?repository=profiles",
    "imageBanner": "https://social-sport-api.herokuapp.com/public/images/1687921060821-PhotoRoom_20230626_195147.jpeg?repository=profiles",
    "username": "quadradev",
    "responsavel": {
        "fullName": "pablo ribeiri",
        "cpf": "106.825.576-50",
        "birthDate": "1998-03-16",
        "cellphone": "(34)99284-3238",
        "email": "ribeiro.pablo@icloud.com",
        "foto": null
    },
    "endereco": {
        "cep": "38401-654",
        "country": null,
        "cityId": 3068,
        "nameCity": "Uberlândia",
        "district": "Jardim Brasília",
        "state": "MG",
        "logradouro": "Rua Realino Francisco da Costa",
        "number": "91",
        "complement": null,
        "longitude": null,
        "latitude": null
    },
    "employee": null
}
```


## Horario de funcionamento

Para constrolarmos o horarios de funcionamento temos um CRUD onde pode realizar o cadastro, a consulta e a deleção.

{{< alert icon="👉" text="Esta configuração é importante acontecer antes de qualquer outra configuração pois quando for registrar uma nova quadra, irá pegar os horarios de funcionamento para montar os horarios disponíveis de cada quadra." />}}

### Novo horario  
Request:  
<span style="font-size: smaller;">Request: POST   </span><br>
<span style="font-size: smaller;">PATH:/api/opening-hours  </span><br>
<span style="font-size: smaller;">JSON: </span><br>
```bash
{
    "startHour": "08:00",
    "endHour": "16:00",
    "dayOfTheWeek": "QUINTA"
}
```

Retornos:  
<span style="font-size: smaller;">200 OK  </span><br>
<span style="font-size: smaller;">404 não encontrada</span>
<span style="font-size: smaller;">403 não permitido</span>
<span style="font-size: smaller;">401 não autorizado</span>


### Consulta  
Request:  
<span style="font-size: smaller;">Request: GET   </span><br>
<span style="font-size: smaller;">PATH:/api/opening-hours  </span><br>

Retornos:  
<span style="font-size: smaller;">200 OK  </span><br>
<span style="font-size: smaller;">404 não encontrada</span>
<span style="font-size: smaller;">403 não permitido</span>
<span style="font-size: smaller;">401 não autorizado</span>

```bash
{
    "configDayOfTheWeek": [
        {
            "dayOfTheWeek": "DOMINGO",// SEGUNDA, TERCA, QUARTA, QUINTA ...
            "openingHours": [
                {
                    "id": 6,
                    "startHour": "08:00",
                    "endHour": "23:00"
                }
            ]
        }
    ]
}
```

### Delete  
Request:  
<span style="font-size: smaller;">Request: DELETE   </span><br>
<span style="font-size: smaller;">PATH:/api/opening-hours  </span><br>

Retornos:  
<span style="font-size: smaller;">204 OK  </span><br>
<span style="font-size: smaller;">403 não permitido</span>
<span style="font-size: smaller;">401 não autorizado</span>