A url base da API é https://samuel-sz-portela.onrender.com

Rotas que necessitam de autorização
Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:
Authorization: Bearer {token}

Endpoints

Login
POST /login - FORMATO DA REQUISIÇÃO
{
  "email": "joaopaulo@mail.com",
  "password": "123456"
}

Caso dê tudo certo, a resposta será assim:
POST /login - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvYW9wYXVsb0BtYWlsLmNvbSIsImlhdCI6MTY3Nzk1NDA4MiwiZXhwIjoxNjc3OTU3NjgyLCJzdWIiOiIyIn0.o8PpwjblbliYRXMImlggPNzA-mP_3w2blxO2KAf5wnw",
	"user": {
		"email": "joaopaulo@mail.com",
		"name": "João Paulo",
		"nickname": "JP",
		"img": "url",
		"background": "url",
		"id": 2
	}
}

CADASTRAR USUÁRIO
POST /users - FORMATO DA REQUISIÇÃO
{
  "name": "Alice Chagas",
  "nickname": "ali",
  "img": "url",
  "background": "url",
  "email": "ali@mail.com",
  "password": "123456"
}

Caso dê tudo certo, a resposta será assim:
POST /users - FORMATO DA REQUISIÇÃO – STATUS 201
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFsaUBtYWlsLmNvbSIsImlhdCI6MTY3Nzk3MTI0MiwiZXhwIjoxNjc3OTc0ODQyLCJzdWIiOiI3In0.oYmABStZCdWCmHiRQ8QIkixU4c3LqQfGEuSHPF_Fl3M",
	"user": {
		"email": "ali@mail.com",
		"name": "Alice Chagas",
		"nickname": "ali",
		"img": "url",
		"background": "url",
		"id": 7
	}
}

EDITAR USUÁRIO (TOKEN)
PUT /users/{userId} - FORMATO DA REQUISIÇÃO
{
  "age": 23,
  "name": "Letícia Silva",
  "email": "ali@mail.com",
  "password": "123456"
}

Caso dê tudo certo, a resposta será assim:
PUT /users/{userId} - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"age": 23,
	"name": "Letícia Silva",
	"email": "ali@mail.com",
	"password": "$2a$10$CO/RG8Mo1T9dBWbChUJuq.VT.5qFC51il3wNwKOt/sBmSdzGJWlT2",
	"id": 7
}

DELETAR USUÁRIO (TOKEN)
DELETE /users/{userId} - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
DELETE /users/{userId} - FORMATO DA REQUISIÇÃO – STATUS 200
{ }

PERFIL DO USUÁRIO (TOKEN)
GET /users/{userId} - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /users/{userId} - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"email": "joaopaulo@mail.com",
	"password": "$2a$10$NHeq447rCZOj1ZuBtpC0LuwWppYngCJ0PKxY5TZD1X3HKW2inguL.",
	"name": "João Paulo",
	"nickname": "JP",
	"img": "url",
	"background": "url",
	"id": 2
}

BUSCAR ANIMES DO USUÁRIO (TOKEN)
GET /users/{userId}?_embed=animes - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /users/{userId}?_embed=animes - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"email": "joaopaulo@mail.com",
	"password": "$2a$10$NHeq447rCZOj1ZuBtpC0LuwWppYngCJ0PKxY5TZD1X3HKW2inguL.",
	"name": "João Paulo",
	"nickname": "JP",
	"img": "url",
	"background": "url",
	"id": 2,
	"animes": [
		{
			"book": "Mundo de Sofia",
			"author": "Victoria Aveyard",
			"year": 2015,
			"userId": 2,
			"id": 3
		}
	]
}

BUSCAR ANIMES FAVORITOS DO USUÁRIO (TOKEN)
GET /users/{userId}?_embed=favorites - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /users/{userId}?_embed=favorites - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"email": "joaopaulo@mail.com",
	"password": "$2a$10$NHeq447rCZOj1ZuBtpC0LuwWppYngCJ0PKxY5TZD1X3HKW2inguL.",
	"name": "João Paulo",
	"nickname": "JP",
	"img": "url",
	"background": "url",
	"id": 2,
	"favorites": [
		{
			"id": 1,
			"animesIds": [
				1,
				2
			],
			"userId": 2
		}
	]
}

LISTA PERSONALIZADA DO USUÁRIO (TOKEN)
GET /users/{userId}?_embed=customlist - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /users/{userId}?_embed=customlist - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"email": "joaopaulo@mail.com",
	"password": "$2a$10$NHeq447rCZOj1ZuBtpC0LuwWppYngCJ0PKxY5TZD1X3HKW2inguL.",
	"name": "João Paulo",
	"nickname": "JP",
	"img": "url",
	"background": "url",
	"id": 2,
	"customlist": [
		{
			"id": 2,
			"userId": 2,
			"name": "exemplo1",
			"animesIds": [
				3,
				2
			],
			"quantidadeAnimes": 2
		}
	]
}

CADASTRAR ANIMES (TOKEN)
POST /animes - FORMATO DA REQUISIÇÃO
{
	"book": "O dia depois de amanhã",
	"author": "Victoria Aveyard",
	"year": 2015,
	"userId": 4
}

Caso dê tudo certo, a resposta será assim:
POST /animes - FORMATO DA REQUISIÇÃO – STATUS 201
{
	"book": "O dia depois de amanhã",
	"author": "Victoria Aveyard",
	"year": 2015,
	"userId": 4,
	"id": 6
}

BUSCAR ANIMES
GET /animes - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /animes - FORMATO DA REQUISIÇÃO – STATUS 200
[
	{
		"book": "A Rainha Verde",
		"author": "Victoria Aveyard",
		"year": 2015,
		"userId": 3,
		"id": 1
	},
	{
		"book": "Mundo de Sofia",
		"author": "Victoria Aveyard",
		"year": 2015,
		"userId": 2,
		"id": 3
	},
	{
		"book": "O dia do curinga",
		"author": "Victoria Aveyard",
		"year": 2015,
		"userId": 4,
		"id": 4
	},
	{
		"book": "O dia depois de amanhã",
		"author": "Victoria Aveyard",
		"year": 2015,
		"userId": 4,
		"id": 5
	},
	{
		"book": "O dia depois de amanhã",
		"author": "Victoria Aveyard",
		"year": 2015,
		"userId": 4,
		"id": 6
	}
]

BUSCAR ANIMES FAVORITOS (TOKEN)
GET /favorites - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /favorites - FORMATO DA REQUISIÇÃO – STATUS 200
[
	{
		"id": 1,
		"animesIds": [
			1,
			2
		],
		"userId": 2
	},
	{
		"id": 2,
		"animesIds": [
			1,
			2
		],
		"userId": 3
	}
]

BUSCAR USUÁRIO DE UM ANIME ESCOLHIDO COMO FAVORITO (TOKEN)
GET /favorites/{Id do anime favorito}?_expand=user - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /favorites/{Id do anime favorito}?_expand=user - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"id": 2,
	"animesIds": [
		1,
		2
	],
	"userId": 3,
	"user": {
		"email": "olivier@mail.com",
		"password": "$2a$10$ZH5m/60iBY7/82r9GvLPter89.u5O02SfAx8MRbQ3zkei5Km0zLKu",
		"name": "Carlos Olivier",
		"nickname": "Coli",
		"img": "url",
		"background": "url",
		"id": 3
	}
}

BUSCAR LISTA PERSONALIZADA (TOKEN)
GET /customlist - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
GET /customlist - FORMATO DA REQUISIÇÃO – STATUS 200
[
	{
		"id": 2,
		"userId": 2,
		"name": "exemplo1",
		"animesIds": [
			3,
			2
		],
		"quantidadeAnimes": 2
	},
	{
		"id": 3,
		"userId": 3,
		"name": "exemplo2",
		"animesIds": [
			3,
			2
		],
		"quantidadeAnimes": 2
	},
	{
		"userId": 3,
		"name": "exemplo77",
		"idsAnime": [
			2,
			3
		],
		"quantidadeAnimes": 2,
		"id": 4
	},
	{
		"userId": 4,
		"name": "exemplo22",
		"idsAnime": [
			2,
			3
		],
		"quantidadeAnimes": 2,
		"id": 5
	}
]

CADASTRAR LISTA PERSONALIZADA (TOKEN)
POST /customlist  - FORMATO DA REQUISIÇÃO
{
	"userId": 2,
	"name": "Sentinela",
	"idsAnime": [
		2,
		3
	],
	"quantidadeAnimes": 7
}

Caso dê tudo certo, a resposta será assim:
POST /customlist - FORMATO DA REQUISIÇÃO – STATUS 201
{
	"userId": 2,
	"name": "Sentinela",
	"idsAnime": [
		2,
		3
	],
	"quantidadeAnimes": 7,
	"id": 6
}

EDITAR ITEM DA LISTA PERSONALIZADA (TOKEN)
PATCH /customlist/{Id de um item da lista} - FORMATO DA REQUISIÇÃO
{
	"name": "futebol"
}

Caso dê tudo certo, a resposta será assim:
PATCH /customlist/{ Id de um item da lista } - FORMATO DA REQUISIÇÃO – STATUS 200
{
	"userId": 2,
	"name": "futebol",
	"idsAnime": [
		2,
		3
	],
	"quantidadeAnimes": 7,
	"id": 6
}


DELETAR ITEM DA LISTA PERSONALIZADA (TOKEN)
DELETE /customlist/{Id de um item da lista } - FORMATO DA REQUISIÇÃO
Não é necessário um corpo da requisição.

Caso dê tudo certo, a resposta será assim:
DELETE /customlist/{Id de um item da lista }- FORMATO DA REQUISIÇÃO – STATUS 200
{ }


