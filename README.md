# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Projetos Front-end.

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

### Adicionar aos favoritos

POST /favoriteIds <br/>

Voce precisa fornecer o tokem do usuario e o corpo da requisição com o seguinte padrão : 

{
	"favoriteObject":{"death":12},            <- favoriteObject representa a chave do objeto que iremos favoritar e {"death":12} representa o objeto favoritado <br/>
	"userId":1                                <-Presisamos pasar o id do usuario  com o a seguinte chave  "userId"
}

exemplo de resposta: 

{
	"favoriteObject": { 
		"death": 12
	},
	"userId": 1,
	"id": 7
}

### Pegar os favoritos do usuario 

GET /favoriteIds?userId=1  <-colocamos o id do usuario aqui  <br/>

Voce precisa fornecer o tokem do usuario e nao precisa de corpo 

exemplo de resposta: 

[{
	"favoriteObject": 
		"death": 12
	},
	"userId": 1,
	"id": 7
},{
	"favoriteObject": {
		"death": 13
	},
	"userId": 1,
	"id": 9
}]

### Deletar favoritos do usuario

DELETE/ favoriteIds/4  <- O numero 4 representa o id do objeto a ser deletado<br/>

Voce tambem precisa fornecer o tokem do usuario 