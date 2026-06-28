# 📚 Miniguia de Estudos — Backend com Node.js

Projeto desenvolvido como parte do desafio da DIO, utilizando o NotebookLM como ferramenta de aprendizagem ativa para consolidar conhecimentos fundamentais de desenvolvimento back-end.

---

## 🎯 Contexto e Objetivos

O tema escolhido foi **Back-end com Node.js**, com foco nos conceitos mais cobrados no mercado para desenvolvedores back-end. Os objetivos de estudo são:

- Entender como REST APIs se comunicam via HTTP
- Compreender o papel do middleware no Express.js
- Aprender autenticação stateless com JWT
- Conhecer o conceito de ORM e as vantagens do Prisma
- Diferenciar arquitetura monolítica de microsserviços

---

## 🔗 Curadoria de Fontes

| # | Tema | Fonte |
|---|------|-------|
| 1 | REST API e HTTP | [MDN — An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) |
| 2 | Middleware no Express | [Express.js — Writing Middleware](https://expressjs.com/en/guide/writing-middleware.html) |
| 3 | Autenticação com JWT | [jwt.io — Introduction](https://jwt.io/introduction) |
| 4 | ORM e Prisma | [Prisma Docs — What is an ORM](https://www.prisma.io/dataguide/types/relational/what-is-an-orm) |
| 5 | Arquitetura Backend | [roadmap.sh — Backend Roadmap](https://roadmap.sh/backend) |

---

## 🧪 Engenharia de Prompts e Cicatrizes

### Prompt 1
**Pergunta:** O que é uma REST API e quais são os métodos HTTP mais usados?

**Resposta:** Uma REST API é um estilo de arquitetura que permite a comunicação entre front-end e servidor via HTTP. Os métodos mais usados são GET (buscar), POST (criar), PUT (atualizar por completo), PATCH (atualizar parcialmente) e DELETE (remover). Além desses, HEAD e OPTIONS também fazem parte da especificação HTTP.

**Fonte citada:** MDN — An overview of HTTP

**Observação:** Resposta clara e completa na primeira tentativa. Boa porta de entrada para o tema.

---

### Prompt 2
**Pergunta:** O que é middleware no Express e qual é o papel da função `next()`?

**Resposta:** Middlewares são funções que têm acesso ao `req`, `res` e `next`, funcionando como camadas de processamento pelas quais uma requisição passa antes de chegar à rota final. A função `next()` é responsável por passar o controle para o próximo middleware — se não for chamada e nenhuma resposta for enviada, a requisição fica travada. Middlewares podem executar código, modificar req/res, encerrar o ciclo ou delegar para o próximo. A ordem de carregamento importa: o que é definido primeiro, executa primeiro.

**Fonte citada:** Express.js — Writing Middleware

**Observação:** Resposta completa. Vale destacar o comportamento do `next()` com erros: qualquer valor passado para `next(valor)` aciona o tratamento de erro, pulando middlewares comuns.

---

### Prompt 3
**Pergunta:** Como funciona autenticação com JWT? O que contém um token?

**Resposta:** JWT é um mecanismo de autenticação stateless composto por três partes separadas por ponto: Header (tipo e algoritmo), Payload (claims com dados do usuário como id e expiração) e Signature (garante integridade). O fluxo é: usuário faz login → servidor gera o token → cliente armazena e envia em todas as requisições no header `Authorization: Bearer <token>` → servidor valida a assinatura sem consultar o banco de dados.

**Fonte citada:** jwt.io/introduction

**Observação:** Ponto importante documentado — o Payload é apenas codificado em Base64Url, não criptografado. Qualquer pessoa pode lê-lo, então **nunca coloque senhas ou dados sensíveis dentro do token**.

---

### Prompt 4
**Pergunta:** O que é um ORM e qual a vantagem de usar o Prisma?

**Resposta:** ORM é uma camada de abstração que traduz dados do banco para objetos da aplicação, eliminando a necessidade de escrever SQL repetitivo. O Prisma é um ORM focado em Node.js e TypeScript com vantagens como: type-safety (evita erros em tempo de execução), schema migration (gerencia mudanças na estrutura do banco) e abstração eficiente para focar na lógica de negócio.

**Fonte citada:** Prisma Docs — What is an ORM

**Observação:** Ponto de atenção documentado — ORM é uma escolha estratégica. O alto nível de abstração pode dificultar a depuração e esconder detalhes internos do banco. Em projetos que exigem queries muito otimizadas, SQL puro pode ser mais adequado.

---

### Prompt 5
**Pergunta:** Qual a diferença entre arquitetura monolítica e microsserviços?

**Resposta:** Na arquitetura monolítica, toda a lógica da aplicação está em um único bloco de código — simples de iniciar, mas difícil de escalar. Nos microsserviços, a aplicação é dividida em serviços independentes que se comunicam via API, permitindo escalar apenas o que for necessário e atualizar partes isoladas sem derrubar o sistema inteiro.

| Característica | Monolítica | Microsserviços |
|----------------|------------|----------------|
| Desenvolvimento | Simples e centralizado | Complexo e distribuído |
| Escalabilidade | Escala a aplicação inteira | Escala serviços específicos |
| Implantação | Uma única unidade | Múltiplas unidades independentes |
| Manutenção | Risco de afetar todo o sistema | Alterações são isoladas por serviço |

**Fonte citada:** roadmap.sh — Backend Roadmap

**Observação:** A escolha entre as duas depende do tamanho e maturidade do projeto. Para projetos iniciais, monolito é recomendado. Microsserviços agregam complexidade e devem ser adotados quando há necessidade real de escala.

---

## 📖 Miniguia de Estudo

### Resumos Estruturados

**REST API**
APIs REST usam o protocolo HTTP para comunicação entre cliente e servidor. Cada operação é representada por um verbo HTTP: GET para buscar, POST para criar, PUT/PATCH para atualizar e DELETE para remover.

**Middleware no Express**
Middlewares são funções intermediárias que processam a requisição antes de ela chegar à rota. São encadeados via `next()` e podem fazer autenticação, logging, validação e tratamento de erros.

**JWT**
JSON Web Token é um padrão para autenticação stateless. O token carrega as informações do usuário de forma assinada, dispensando consultas ao banco a cada requisição. É composto por Header, Payload e Signature.

**ORM e Prisma**
ORMs abstraem o banco de dados, permitindo trabalhar com objetos em vez de SQL. O Prisma adiciona type-safety e migrations ao ecossistema Node.js/TypeScript.

**Arquitetura Backend**
Monolito é ideal para projetos menores e times pequenos. Microsserviços são mais adequados para sistemas com alta demanda de escala e times distribuídos.

---

### 📝 Glossário

| Termo | Definição |
|-------|-----------|
| REST | Estilo arquitetural para APIs que usa HTTP como protocolo de comunicação |
| HTTP | Protocolo de transferência de hipertexto usado na comunicação web |
| Middleware | Função intermediária que processa req/res antes da rota final |
| `next()` | Função do Express que passa o controle para o próximo middleware |
| JWT | JSON Web Token — padrão para autenticação stateless via token assinado |
| Payload | Parte do JWT que contém as claims (dados do usuário) |
| Signature | Parte do JWT que garante a integridade do token |
| Stateless | Sem estado — o servidor não armazena sessão, cada requisição é independente |
| ORM | Object Relational Mapper — camada de abstração entre código e banco de dados |
| Schema Migration | Controle de versão da estrutura do banco de dados |
| Type-safety | Garantia de tipos em tempo de compilação, evitando erros em execução |
| Monolito | Arquitetura onde toda a aplicação é uma única unidade |
| Microsserviços | Arquitetura onde a aplicação é dividida em serviços independentes |
| Bearer Token | Esquema de autenticação HTTP onde o token é enviado no header Authorization |

---

### 🔁 Prompts Reutilizáveis para Revisão

```
1. "Explique o ciclo completo de uma requisição HTTP em uma REST API, do cliente ao servidor."

2. "Descreva o fluxo de middlewares no Express e o que acontece se next() não for chamado."

3. "Quais são as três partes de um JWT e qual a função de cada uma?"

4. "Quais as principais vantagens do Prisma em relação a escrever SQL puro?"

5. "Em qual cenário é mais recomendado usar microsserviços em vez de monolito?"

6. "O que são claims em um JWT e qual a diferença entre claims registradas e privadas?"

7. "Como o Express trata erros passados para a função next()?"

8. "O que significa dizer que JWT é stateless e por que isso é uma vantagem?"
```

---

*Projeto desenvolvido para o Desafio de Projeto da DIO — Caderno Temático com NotebookLM.*
