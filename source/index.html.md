---
title: Quero Pontos API Reference

language_tabs:

toc_footers:
  - Created with ❤ in Osasco - SP

includes:

search: true
---


# Authentication

Users levels: 

1 -> clients

2 -> cashiers

3 -> retailers

### HTTP Request

`POST https://www.queropontos.com.br/login`

### Query Parameters

Parameter |  Description
--------- |  -----------
email | Usado apenas no login do retailer, é utilizado para identificar o mesmo
cpf | Utilizado para autenticar cliente e caixa
password | -----------
level | Como passado na descrição da seção, identifica o nivel do usuário

```shell
curl "https://www.queropontos.com.br/login"
  -H "Content-Type: application/json" 
  -X POST
  -d '{"email":"xyz","password":"xyz", "level": "1"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
[
  {
    "user":  {
      ... user_object ...
    },
    "token": "auth_token"
  }
]
```


# Retailers

## GET retailer

```shell
curl "https://www.queropontos.com.br/retailer/:_id"
  -H "Content-Type: application/json" 
  -X GET
  -d '{"token": "auth_token"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": ":_id",  // ID DO USUÁRIO
  "name": "Loja do Arthur", // NOME DO RETAILER
  "email": "retailer@queropontos.com.br", // EMAIL DO RETAILER
  "razaoSocial": "Razao Social - LTDA", // RAZAO SOCIAL DO RETALER
  "uf": "SP", // ENDEREÇO DO RETAILER
  "city": "Osasco", // ENDEREÇO DO RETAILER
  "street": "Rua em Osasco",  // ENDEREÇO DO RETAILER
  "number":"00",  // ENDEREÇO DO RETAILER
  "neighborhood":"Bairro em Osasco",  // ENDEREÇO DO RETAILER
  "zipcode":"06060000", // ENDEREÇO DO RETAILER
  "actualPackage":"_id", // _ID DO PACOTE DE PONTOS ATUAL
  "manager":"_id", // _ID DO GERENTE DO RETAILER
  "status":true,  // STATUS DO RETAILER
  "totalScores":950,  // PONTUAÇÃO ATUAL DO RETAILER
  "totalUsedScores":50, // PONTUAÇÃO UTILIZADA
  "usedScores":[{
    "_id":"5a7c5b23e15bc837f47a3dc3", // DETALHE DO USO DA PONTUAÇÃO (_ID DA VENDA)
    "cashier":"5a7c55a9e15bc837f47a3dc2", // DETALHE DO USO DA PONTUAÇÃO (_ID DO CAIXA QUE DEU A PONTUAÇÃO)
    "client":"5a7c5b11b54e3a26f273abe2", // DETALHE DO USO DA PONTUAÇÃO (_ID DO CLIENTE QUE RECEBEU A PONTUAÇÃO)
    "scores":50, // DETALHE DO USO DA PONTUAÇÃO (VALOR DO PONTO)
    "date":"2018-02-08T14:13:55.272Z", // DETALHE DO USO DA PONTUAÇÃO (TIMESTAMP)
  }],
  "created_at":"2018-02-07T19:16:25.355Z",  // TIMESTAMP DE CRIAÇÃO USUÁRIO
  }
}
```

Esse endpoint retorna um retailer especifico

### HTTP Request

`GET https://www.queropontos.com.br/retailer/<:_id>`

### URL Parameters

Parameter | Description
--------- | -----------
:_id | O Id do retailer

## Editar um retailer especifico

```shell
curl "https://www.queropontos.com.br/retailer/:_id"
  -H "Content-Type: application/json" 
  -X PUT
  -d '{"token": "auth_token", }'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": ":_id",  // ID DO USUÁRIO
  "name": "Loja do Arthur", // NOME DO RETAILER
  "email": "retailer@queropontos.com.br", // EMAIL DO RETAILER
  "razaoSocial": "Razao Social - LTDA", // RAZAO SOCIAL DO RETALER
  "uf": "SP", // ENDEREÇO DO RETAILER
  "city": "Osasco", // ENDEREÇO DO RETAILER
  "street": "Rua em Osasco",  // ENDEREÇO DO RETAILER
  "number":"00",  // ENDEREÇO DO RETAILER
  "neighborhood":"Bairro em Osasco",  // ENDEREÇO DO RETAILER
  "zipcode":"06060000", // ENDEREÇO DO RETAILER
  "actualPackage":"_id", // _ID DO PACOTE DE PONTOS ATUAL
  "manager":"_id", // _ID DO GERENTE DO RETAILER
  "status":true,  // STATUS DO RETAILER
  "totalScores":950,  // PONTUAÇÃO ATUAL DO RETAILER
  "totalUsedScores":50, // PONTUAÇÃO UTILIZADA
  "usedScores":[{
    "_id":"5a7c5b23e15bc837f47a3dc3", // DETALHE DO USO DA PONTUAÇÃO (_ID DA VENDA)
    "cashier":"5a7c55a9e15bc837f47a3dc2", // DETALHE DO USO DA PONTUAÇÃO (_ID DO CAIXA QUE DEU A PONTUAÇÃO)
    "client":"5a7c5b11b54e3a26f273abe2", // DETALHE DO USO DA PONTUAÇÃO (_ID DO CLIENTE QUE RECEBEU A PONTUAÇÃO)
    "scores":50, // DETALHE DO USO DA PONTUAÇÃO (VALOR DO PONTO)
    "date":"2018-02-08T14:13:55.272Z", // DETALHE DO USO DA PONTUAÇÃO (TIMESTAMP)
  }],
  "created_at":"2018-02-07T19:16:25.355Z",  // TIMESTAMP DE CRIAÇÃO USUÁRIO
  }
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`GET https://www.queropontos.com.br/retailer/<:_id>`

### URL Parameters

Parameter | Description
--------- | -----------
:_id | O Id do retailer

