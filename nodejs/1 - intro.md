# Introdução sobre Node.js
## O que é o Node.js?
É uma plataforma que permite a execução de javascript server side.

É composto pela v8 (motor javascript criado pela google) + libuv + módulos.

## O que o Node.js resolve?
Trabalha bem com I/O assíncrono. Na época do seu desenvolvimento, outras 
tecnologias não lidavam tão bem com isso.

## Características
- Tem a arquitetura de event loop (call stack)
- Single Thread (no event loop)
- Non-blocking I/O (multiplas funções/requisições sendo executadas ao mesmo tempo)
- Módulos próprios
  - http
  - dns
  - fs
  - buffer

### Event Loop
O event loop "observa" a call stack. A partir do momento que uma função da call 
stack é identificada no event loop, ele direciona aquela função para uma Thread.
Quando identificar a próxima função na call stack, manda pra outra Thread, e 
assim por diante. Por padrão, são 4 Threads disponíveis.

### Gerenciadores de pacotes
- Npm e Yarn
- Bibliotecas externas
- Disponibilização de bibliotecas para uso de terceiros

### Frameworks
- Express
- Egg.js
- Nest.js
- Adonis.js