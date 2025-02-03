# API de Games
Esta API foi desenvolvida para gerenciar um catálogo de jogos, permitindo a autenticação de usuários e a manipulação dos dados dos games. Com ela, é possível cadastrar, listar, atualizar e deletar jogos, além de realizar login para acessar endpoints protegidos.


## Endpoints
### POST /auth
Este endpoint é responsável por realizar o processo de Autenticação/Login.
#### Parâmetros
email: E-mail do usuário cadastrado no sistema.

password: Senha do usuário cadastrado no sistema.
Exemplo:
```
{
    "email": "lucas.ferreira@email.com",
    "password": "senha123"
}
```

#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá o token JWT para conseguir acessar endpoints protegidos na API.

Exemplo de resposta:
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJsdWNhcy5mZXJyZWlyYUBlbWFpbC5jb20iLCJpYXQiOjE3MzgxNDAzOTgsImV4cCI6MTczODMxMzE5OH0.bGi4c-elkIZq1paTxrCwDHyXXax47R2EvcTrQG4dUQA"
}
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Senha ou E-mail incorretos.

Exemplo de resposta:
```
{ "err": "Credenciais inválidas!" }
```

### GET /games
Este endpoint retorna a lista completa de jogos cadastrados no banco de dados, que é simulado por um objeto JSON contendo coleções de jogos e usuários.
#### Parâmetros
Nenhum.
#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá a listagem completa de todos os games.

Exemplo de resposta:
```
[
    {
        "id": 101,
        "title": "The Witcher 3: Wild Hunt",
        "year": 2015,
        "price": 50
    },
    {
        "id": 102,
        "title": "Red Dead Redemption 2",
        "year": 2018,
        "price": 70
    },
    {
        "id": 103,
        "title": "Elden Ring",
        "year": 2022,
        "price": 80
    }
]
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido ou Token expirado.

Exemplo de resposta:
```
{
    "err": "Token inválido!"
}
```

### POST /game
Este endpoint cadastra um novo jogo na lista, adicionando-o ao banco de dados simulado com base nas informações enviadas no corpo da requisição.
#### Parâmetros
id = ID do jogo a ser cadastrado.

title = Nome do jogo a ser cadastrado.

price =  Preço do jogo.

year = Ano de lançamento do jogo.

#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá o jogo específico, com base no id informado na URL.

Exemplo de resposta:
```
{
    "id": 103,
    "title": "Elden Ring",
    "year": 2022,
    "price": 80
}
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido ou Token expirado.

Exemplo de resposta:
```
{
    "err": "Token inválido!"
}
```

### GET /game/:id
Este endpoint retorna um jogo específico, com base no id informado na URL.
#### Parâmetros
:id = ID do jogo cadastrado no sistema (informado na URL).
#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá o jogo específico, com base no id informado na URL.

Exemplo de resposta:
```
{
    "id": 103,
    "title": "Elden Ring",
    "year": 2022,
    "price": 80
}
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido ou Token expirado.

Exemplo de resposta:
```
{
    "err": "Token inválido!"
}
```

### DELETE /game/:id
Este endpoint deleta um jogo específico da lista, com base no id informado na URL.
#### Parâmetros
:id = ID do jogo cadastrado no sistema (informado na URL).
#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá a mensagem informando que o jogo foi deletado com sucesso.

Exemplo de resposta:
```
{
    "Resposta": "Ok! Jogo deletado com sucesso"
}
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido ou Token expirado.

Exemplo de resposta:
```
{
    "err": "Token inválido!"
}
```

### PUT /game/:id
Este endpoint altera um campo de algum jogo específico da lista, com base no id informado na URL.
#### Parâmetros
:id = ID do jogo cadastrado no sistema (informado na URL).
#### Respostas
##### Ok! 200
Se esta resposta for retornada, você receberá a mensagem informando que o jogo foi alterado com sucesso.

Exemplo de resposta:
```
{
    "Resposta": "Ok! Jogo alterado com sucesso"
}
```
##### Falha na autenticação | 401
Se esta resposta for retornada, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido ou Token expirado.

Exemplo de resposta:
```
{
    "err": "Token inválido!"
}
```
##### Id inválido | 400
Se esta resposta for retornada, indica que você tentou passar um ID em um formato inválido, contendo letras em vez de números.

Exemplo de resposta:
```
{
    "Resposta": "Id inválido!"
}
```
