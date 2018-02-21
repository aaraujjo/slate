---
title: Quero Pontos API Reference

language_tabs:

toc_footers:
  - Created with ❤ in Osasco - SP

includes:

search: true
---


# Autenticação

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
    ... user_object ...,
    "token": "auth_token"
  }
]
```


# Retailers

## Get a retailer

```shell
curl "https://www.queropontos.com.br/retailer/:_id"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": ":_id",  // ID DO USUÁRIO
  "name": "Lojas do Osasco", // NOME DO RETAILER
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
```

Esse endpoint retorna um retailer especifico

### HTTP Request

`GET https://www.queropontos.com.br/retailer/<:_id>`

### URL Parameters

Parameter | Description
--------- | -----------
:_id | O Id do retailer

## Edit a specific retailer

```shell
curl "https://www.queropontos.com.br/retailer/:_id"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X PUT
  -d '{"name": "Novo nome da Loja", "email": "email@queropontos.com.br"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": ":_id",  // ID DO USUÁRIO
  "name": "Loja de Osasco", // NOME DO RETAILER
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
```

Esse endpoint edita um retailer especifico.

### HTTP Request

`GET https://www.queropontos.com.br/retailer/<:_id>`

### URL Parameters

Parameter | Description
--------- | -----------
:_id | O Id do retailer


# Stores

## Create a store

```shell
curl "https://www.queropontos.com.br/stores/"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X POST
  -d '{"name": "Salão de Barbearia Hipster", "description": "Barbearia e produtos para cuidados facial masculino. Aberto de terça a domingo à partir das 14h. Consulte agenda no site www.barbeariahipster.com.br", "cnpj": "25493685000186", "phone": "11999999999", "street": "St Quero Pontos", "number": "01", "city": "Osasco", "uf": "SP", "zipcode": "Zipcode", "retailerId": "59c99fac8cd9d76ecf7c61c3"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c99fac8cd9d76ecf7c61c5",
  "name": "Salão de Barbearia Hipster",
  "description": "Barbearia e produtos para cuidados facial masculino. Aberto de terça a domingo à partir das 14h. Consulte agenda no site www.barbeariahipster.com.br",
  "cnpj": "25493685000186",
  "phone": "11999999999",
  "retailerId": {
    ...retailer_object...
  },
  "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
  "street": "St Quero Pontos",
  "number": "01",
  "city": "Osasco",
  "uf": "SP",
  "zipcode": "ZIPCODE",
  "coordinates": [
    -23.5555939,
    -46.7874398
  ],
  "subscribed": "2017-09-26T00:30:36.668Z"
}
```

Esse endpoint registra uma nova loja

### HTTP Request

`GET https://www.queropontos.com.br/stores`

### URL Parameters

Parameter | Description
--------- | -----------
store_id | Id da loja

## Get all stores

```shell
curl "https://www.queropontos.com.br/stores"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
[
  {
    "_id": "59c99fac8cd9d76ecf7c61c5",
    "name": "Salão de Barbearia Hipster",
    "description": "Barbearia e produtos para cuidados facial masculino. Aberto de terça a domingo à partir das 14h. Consulte agenda no site www.barbeariahipster.com.br",
    "cnpj": "25493685000186",
    "phone": "11999999999",
    "retailerId": {
      ...retailer_object...
    },
    "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
    "street": "St Quero Pontos",
    "number": "01",
    "city": "Osasco",
    "uf": "SP",
    "zipcode": "ZIPCODE",
    "coordinates": [
      -23.5555939,
      -46.7874398
    ],
    "subscribed": "2017-09-26T00:30:36.668Z"
  },
  {
    "_id": "59c99fac8cd9d76ecf7c61c5",
    "name": "Sorveteria Gourmet",
    "description": "Melhores sorvetes da região",
    "cnpj": "25493685000186",
    "phone": "11999999999",
    "retailerId": {
      ...retailer_object...
    },
    "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
    "street": "St Quero Pontos",
    "number": "01",
    "city": "Osasco",
    "uf": "SP",
    "zipcode": "ZIPCODE",
    "coordinates": [
      -23.5555939,
      -46.7874398
    ],
    "subscribed": "2017-09-26T00:30:36.668Z"
  },
]
```

Esse endpoint retorna todas as lojas cadastradas no sistema

### HTTP Request

`GET https://www.queropontos.com.br/stores`

## Get a store

```shell
curl "https://www.queropontos.com.br/stores/<store_id>"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c99fac8cd9d76ecf7c61c5",
  "name": "Salão de Barbearia Hipster",
  "description": "Barbearia e produtos para cuidados facial masculino. Aberto de terça a domingo à partir das 14h. Consulte agenda no site www.barbeariahipster.com.br",
  "cnpj": "25493685000186",
  "phone": "11999999999",
  "retailerId": {
    ...retailer_object...
  },
  "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
  "street": "St Quero Pontos",
  "number": "01",
  "city": "Osasco",
  "uf": "SP",
  "zipcode": "ZIPCODE",
  "coordinates": [
    -23.5555939,
    -46.7874398
  ],
  "subscribed": "2017-09-26T00:30:36.668Z"
}
```

Esse endpoint retorna uma loja especifica

### HTTP Request

`GET https://www.queropontos.com.br/stores/<store_id>`

### URL Parameters

Parameter | Description
--------- | -----------
store_id | Id da loja

## Edit a store

```shell
curl "https://www.queropontos.com.br/stores/<store_id>"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X PUT
  -d "{'description': 'Barbearia e produtos para cuidados facial masculino.'}"
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c99fac8cd9d76ecf7c61c5",
  "name": "Salão de Barbearia Hipster",
  "description": "Barbearia e produtos para cuidados facial masculino.",
  "cnpj": "25493685000186",
  "phone": "11999999999",
  "retailerId": {
    ...retailer_object...
  },
  "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
  "street": "St Quero Pontos",
  "number": "01",
  "city": "Osasco",
  "uf": "SP",
  "zipcode": "ZIPCODE",
  "coordinates": [
    -23.5555939,
    -46.7874398
  ],
  "subscribed": "2017-09-26T00:30:36.668Z"
}
```

Esse endpoint edita uma loja especifica

### HTTP Request

`GET https://www.queropontos.com.br/stores/<store_id>`

### URL Parameters

Parameter | Description
--------- | -----------
store_id | Id da loja

## Delete a store

```shell
curl "https://www.queropontos.com.br/stores/<store_id>"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X DELETE
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c99fac8cd9d76ecf7c61c5",
  "name": "Salão de Barbearia Hipster",
  "description": "Barbearia e produtos para cuidados facial masculino.",
  "cnpj": "25493685000186",
  "phone": "11999999999",
  "retailerId": {
    ...retailer_object...
  },
  "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
  "street": "St Quero Pontos",
  "number": "01",
  "city": "Osasco",
  "uf": "SP",
  "zipcode": "ZIPCODE",
  "coordinates": [
    -23.5555939,
    -46.7874398
  ],
  "subscribed": "2017-09-26T00:30:36.668Z"
}
```

Esse endpoint apaga uma loja especifica

### HTTP Request

`GET https://www.queropontos.com.br/stores/<store_id>`

### URL Parameters

Parameter | Description
--------- | -----------
store_id | Id da loja

# Get a store by retailer id

```shell
curl "https://www.queropontos.com.br/stores/retailers/<retailer_id>"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
[{
  "_id": "59c99fac8cd9d76ecf7c61c5",
  "name": "Salão de Barbearia Hipster",
  "description": "Barbearia e produtos para cuidados facial masculino. Aberto de terça a domingo à partir das 14h. Consulte agenda no site www.barbeariahipster.com.br",
  "cnpj": "25493685000186",
  "phone": "11999999999",
  "retailerId": {
    ...retailer_object...
  },
  "formatted_address": "Endereço Formatado, 1154, Osasco, SP",
  "street": "St Quero Pontos",
  "number": "01",
  "city": "Osasco",
  "uf": "SP",
  "zipcode": "ZIPCODE",
  "coordinates": [
    -23.5555939,
    -46.7874398
  ],
  "subscribed": "2017-09-26T00:30:36.668Z"
}]
```

Esse endpoint retorna todas as lojas de um retailer especifico

### HTTP Request

`GET https://www.queropontos.com.br/stores/retailers/<retailer_id>`

### URL Parameters

Parameter | Description
--------- | -----------
retailer_id | Id do retailer

# Cashiers

## Get all cashiers

```shell
curl "https://www.queropontos.com.br/cashiers"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
[
  {
    "_id": "59c9a08a8cd9d76ecf7c61c6", // ID DO CAIXA
    "name": "Caixa 01", // NOME DO CAIXA
    "cpf": "99999999999", // CPF DO CAIXA
    "email": "caixa01@email.com", // EMAIL DO CAIXA
    "phone": "1199999999", // PHONE DO CAIXA
    "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
    "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
  },
  {
    "_id": "59db346f2c84ae4d2ebc4772", // ID DO CAIXA
    "name": "Caixa 02", // NOME DO CAIXA
    "cpf": "99999999999", // CPF DO CAIXA
    "email": "caixa02@email.com", // EMAIL DO CAIXA
    "phone": "1199999999", // PHONE DO CAIXA
    "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
    "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
  },
]
```

Esse endpoint retorna todos os caixas cadastrados no sistema

### HTTP Request

`GET https://www.queropontos.com.br/cashiers`

## Create a cashier

```shell
curl "https://www.queropontos.com.br/cashiers/"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X POST
  -d '{name: "Caixa 01", cpf: "99999999999", email: "caixa01@email.com", phone: "1199999999", password: "159753", storeId: "59c99fac8cd9d76ecf7c61c5", retailerId: "59c99fac8cd9d76ecf7c61c3"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c9a08a8cd9d76ecf7c61c6", // ID DO CAIXA
  "name": "Caixa 01", // NOME DO CAIXA
  "cpf": "99999999999", // CPF DO CAIXA
  "email": "caixa01@email.com", // EMAIL DO CAIXA
  "phone": "1199999999", // PHONE DO CAIXA
  "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
  "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
},
```

Esse endpoint cadastra um novo caixa

### HTTP Request

`GET https://www.queropontos.com.br/cashiers/`

## Edit a cashier

```shell
curl "https://www.queropontos.com.br/cashiers/"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X PUT
  -d '{"_id": "59c9a08a8cd9d76ecf7c61c6", "name": "John Doe"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c9a08a8cd9d76ecf7c61c6", // ID DO CAIXA
  "name": "John Doe", // NOME DO CAIXA
  "cpf": "99999999999", // CPF DO CAIXA
  "email": "caixa01@email.com", // EMAIL DO CAIXA
  "phone": "1199999999", // PHONE DO CAIXA
  "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
  "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
},
```

Esse endpoint edita um caixa especifico

### HTTP Request

`GET https://www.queropontos.com.br/cashiers/`

## Delete a cashier

```shell
curl "https://www.queropontos.com.br/cashiers/"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X PUT
  -d '{"_id": "59c9a08a8cd9d76ecf7c61c6", "storeId": "59c99fac8cd9d76ecf7c61c5", "retailerId": "59c99fac8cd9d76ecf7c61c3"}'
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
{
  "_id": "59c9a08a8cd9d76ecf7c61c6", // ID DO CAIXA
  "name": "John Doe", // NOME DO CAIXA
  "cpf": "99999999999", // CPF DO CAIXA
  "email": "caixa01@email.com", // EMAIL DO CAIXA
  "phone": "1199999999", // PHONE DO CAIXA
  "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
  "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
},
```

Esse endpoint deleta um caixa especifico

### HTTP Request

`GET https://www.queropontos.com.br/cashiers/`

## Get cashiers by store id

```shell
curl "https://www.queropontos.com.br/cashiers/<store_id>"
  -H "Content-Type: application/json" 
  -H "x-access-token: auth_token" 
  -X GET
```

> O comando acima retorna um JSON estruturado dessa forma:

```json
[
  {
    "_id": "59c9a08a8cd9d76ecf7c61c6", // ID DO CAIXA
    "name": "Caixa 01", // NOME DO CAIXA
    "cpf": "99999999999", // CPF DO CAIXA
    "email": "caixa01@email.com", // EMAIL DO CAIXA
    "phone": "1199999999", // PHONE DO CAIXA
    "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
    "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
  },
  {
    "_id": "59db346f2c84ae4d2ebc4772", // ID DO CAIXA
    "name": "Caixa 02", // NOME DO CAIXA
    "cpf": "99999999999", // CPF DO CAIXA
    "email": "caixa02@email.com", // EMAIL DO CAIXA
    "phone": "1199999999", // PHONE DO CAIXA
    "storeId": "59c99fac8cd9d76ecf7c61c5", // LOJA A QUAL O CAIXA PERTENCE
    "retailerId": "59c99fac8cd9d76ecf7c61c3", // RETAILER A QUAL O CAIXA E LOJA PERTECEM
  },
]
```

Esse endpoint retorna todos os caixas cadastrados em uma loja

### HTTP Request

`GET https://www.queropontos.com.br/cashiers/<store_id>`

### URL Parameters

Parameter | Description
--------- | -----------
store_id | Id da loja