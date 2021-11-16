# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

### Novas Rotas

GET /products

dependents é uma rota 444, significa que ninguém pode escrever o recurso e que qualquer usuário pode visualiza-lo.

A resposta da requisição após registrar será:

{
[
{
"image": "https://i.ibb.co/P1QVcr0/202109090436-skn5yx754p-1.png",
"name": "Hamburguer",
"category": "Sanduíches",
"price": 14,
"id": 1,
"quantity": 1
},
{
"image": "https://i.ibb.co/MVKPDNs/202109200440-8fcy91zr6le-1.png",
"name": "X-Burgue",
"category": "Sanduíches",
"price": 16,
"id": 2,
"quantity": 1
},
{
"image": "https://i.ibb.co/MfVR2kc/202109200440-749eet5vy86-1.png",
"name": "Big Kenzie",
"category": "Sanduíches",
"price": 18,
"id": 3,
"quantity": 1
},
{
"image": "https://i.ibb.co/WvntLND/202110050424-xijoowz172-1.png",
"name": "Combo Kenzie",
"category": "Sanduíches",
"price": 26,
"id": 4,
"quantity": 1
},
{
"image": "https://i.ibb.co/C7Sd4Z5/202108180426-tbwjnwcd1zq-1.png",
"name": "Fanta Guaraná",
"category": "Bebidas",
"price": 5,
"id": 5,
"quantity": 1
},
{
"image": "https://i.ibb.co/nPSXrKp/202108180426-861zezb4bh-1.png",
"name": "Coca Cola",
"category": "Bebidas",
"price": 7,
"id": 6,
"quantity": 1
},
{
"image": "https://i.ibb.co/CJH3RG7/202108250455-4498m9wq98e-1.png",
"name": "McShake Ovomaltine",
"category": "Sobremesas",
"price": 10,
"id": 7,
"quantity": 1
},
{
"image": "https://i.ibb.co/312j11Q/202110110503-g22mtz565td-1.png",
"name": "McSundae",
"category": "Sobremesas",
"price": 10,
"id": 8,
"quantity": 1
}
]
}

GET /cart

Para efetuar o get da rota cart, os usuários precisam possuir o recurso e estarem logados.

O retorno da requisição será:

[
{
"image": "https://lh5.googleusercontent.com/1S54mVj3Ilzub0YAraopjxsjIjuYBg_UoI0pIW-rZ5Gma2HekfMil5xQltXqY28oraXo04gouPkCuQ=w1920-h978",
"name": "Hamburguer",
"category": "Sanduíches",
"price": 14,
"id": 1,
"quantity": 1,
"userId": 1
},
{
"image": "https://lh5.googleusercontent.com/1S54mVj3Ilzub0YAraopjxsjIjuYBg_UoI0pIW-rZ5Gma2HekfMil5xQltXqY28oraXo04gouPkCuQ=w1920-h978",
"name": "Hamburguer",
"category": "Sanduíches",
"price": 14,
"id": 2,
"quantity": 1,
"userId": 2
}
]

Caso o usuário não esteja logado, o seguinte erro retornará:

401 Unauthorized "Missing token".

GET /users/id/cart
