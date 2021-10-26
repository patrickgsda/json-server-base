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

POST /dependents

dependents é uma rota 640, significa o usuário tem que ser dono do item que ele irá gravar.
O atributo userId é obrigatório para vincular com o usuário
que está cadastrado na plataforma.

Exemplo de cadastro de dependentes:

{
"name": "Benjamin",
"type": "Pet",
"age": 5,
"userId": 2,
}

"userId" foi retirado do "id" do cadastro do Patrick:

{
"email": "patrickarruda30@gmail.com",
"password": "$2a$10$XB5poKRkpGQu4FFbjkLdV.wP0ZcBI2lYPsFOGs7QS7t8KCX59LxY.",
"name": "Patrick",
"age": 22,
"id": 2
}

A resposta da requisição após registrar será:

{
"name": "Benjamin",
"type": "Pet",
"age": 5,
"userId": 2,
"id": 1
}

Caso tente efetuar registro sem estar logado, o seguinte erro irá retornar:

401 Unauthorized "Missing token"

GET /dependents

Para efetuar o get da rota dependents, os usuários precisam estar logados.

O retorno da requisição será:

[
{
"name": "Benjamin",
"type": "Pet",
"age": 5,
"userId": 2,
"id": 1
},
{
"name": "Mari Santos",
"type": "wife",
"age": 31,
"userId": 2,
"id": 2
},
{
"name": "Nelma",
"type": "parents",
"age": 61,
"userId": 2,
"id": 3
},
{
"name": "Pamela",
"type": "brothers",
"age": 25,
"userId": 2,
"id": 4
}
]

Caso o usuário não esteja logado, o seguinte erro retornará:

401 Unauthorized "Missing token"

POST /contacts

contacts é uma rota 644, significa que o usuário tem que ser dono do item que ele irá gravar.
O atributo userId é obrigatório para vincular com o usuário
que está cadastrado na plataforma.

Exemplo de cadastro de contacts:

{
"phoneNumber": "51983238380",
"type": "Phone",
"country": "Brasil",
"state": "Rio Grande do Sul",
"city": "Canoas",
"address": "Rua Boqueirão",
"number": 3521,
"CEP": 92200170,
"userId": 2,
}

"userId" foi retirado do "id" do cadastro do Patrick:

{
"email": "patrickarruda30@gmail.com",
"password": "$2a$10$XB5poKRkpGQu4FFbjkLdV.wP0ZcBI2lYPsFOGs7QS7t8KCX59LxY.",
"name": "Patrick",
"age": 22,
"id": 2
}

GET /contacts

Para efetuar o get da rota dependents, os usuários não precisam estar logados.

O retorno da requisição será:

[
{
"phoneNumber": "51983238380",
"type": "Phone",
"country": "Brasil",
"state": "Rio Grande do Sul",
"city": "Canoas",
"address": "Rua Boqueirão",
"number": 3521,
"CEP": 92200170,
"userId": 2,
"id": 1
}
]

POST /groups

groups é uma rota 660, significa que o usuário precisa estar logado para gravar ou ler o item.

Exemplo de cadastro de groups:

{
"name": "We love React"
}

Caso tente efetuar registro sem estar logado, o seguinte erro irá retornar:

401 Unauthorized "Missing token"

GET /groups

O usuário precisa estar logado para conseguir ler o item.

O retorno da requisição será:

[
{
"name": "We love React",
"id": 1
}
]

Caso tente efetuar registro sem estar logado, o seguinte erro irá retornar:

401 Unauthorized "Missing token".
