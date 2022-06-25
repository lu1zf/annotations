# O que é API?
Application Programming Interface. É um conjunto de especificações de possíveis
interações entre aplicações. É importante ter uma documentação, para que outros
desenvolvedores possam consumir os recursos da API (rotas, tipos de parâmetros, 
tipos de retornos).

# O que é REST?
É um acrônimo para Representation State Transfer. É um modelo de arquitetura, 
composto por 6 regras.

## 1. Client-Server
Cliente e servidor não precisam ter conhecimento do que está acontecendo do 
outro lado. A comunicação é independente.

## 2. Stateless
Nenhum estado é armazenado ao fim das requisições. A cada nova requisição, todas
as informações serão passadas novamente do servidor para o cliente.

## 3. Cache
A aplicação precisa ser construída de uma forma que seja possível (não 
necessariamente implementado logo de cara) implementar um cache dos dados.

## 4. Interface Uniforme
A interface é uma espécie de contrato, onde o cliente identifica e o servidor 
representa os recursos.
```
HOSTNAME/products
HOSTNAME/products/id
HOSTNAME/clients
```
Sobre a representação de recursos, isso se refere à forma (json, xml, etc) que o servidor envia
os dados para o cliente. Isso precisa ser feita de maneira uniforme.

Também é importante retornar mensagens auto-descritivas, para que o cliente 
identifique com facilidade erros que possam estar acontecendo.

HATEOAS: utilizar links que ligam pontos da api.

## 5. Camadas
A API deve permitir que existam camadas entre o client e o server, 
como load balancer e camadas de segurança, por exemplo.

## 6. Código Sob Demanda
Permitir que as funcionalidades do cliente sejam estendidas na forma de scripts ou
mini aplicações.

# Métodos de Requisições (HTTP Verbs)
- GET: leitura
- POST: criação
- PUT: atualização
- PATCH: atualização parcial
- DELETE: deleção

# Códigos HTTP
- 1XX: Informativo - a solicitação foi aceita ou o processo continua em andamento
- 2XX: Confirmação
  - 200: Requisição bem sucedida
  - 201: Created - geralmente utilizado após uma requisição POST ter criado um registro
- 3XX: Redirecionamento
  - 301: Movido permanentemente
  - 302: Movido
- 4XX: Erro do cliente
  - 400: Bad request
  - 401: Unauthorized
  - 403: Forbidden
  - 404: Not found
  - 422: Unprocessable Entity
- 5XX: O servidor falhou ao concluir a solicitação
  - 500: Internal server error
  - 502: Bad gateway

# Parâmetros
- Header Params
  - Token
  - Controle de sessão
- Query Params
  - Inseridos no final de uma url
  - Utiliza modelo de chave e valor, com um delimitador entre parâmetros: <code>HOSTNAME/users?page=2&limit=50</code>
- Route Params
  - Parâmetros que são passados na rota da requisição, por exemplo: <code>HOSTNAME/users/{id}</code>, id é um route param
- Body Params
  - Parâmetros que são passados no corpo de uma requisição

# Boas práticas
- Utilização correta dos métodos HTTP
- Utilização correta dos status de retorno das respostas
- Padrão de nomenclatura
  - Exemplo:
    - busca de usuários (GET): 
      - <code>HOSTNAME/v1/users</code>
    - busca de usuário por id (GET): 
      - <code>HOSTNAME/v1/users/1</code>
    - busca de endereço do usuário (GET): 
      - <code>HOSTNAME/v1/users/1/address</code>
    - deleção de um usuário (DELETE): 
      - <code>HOSTNAME/v1/users/1</code>
    - atualização do status de um usuário (PATCH): 
      - <code>HOSTNAME/v1/users/1/status</code>