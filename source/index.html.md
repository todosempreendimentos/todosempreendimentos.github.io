---
title: API Parceiros Cartão de TODOS

language_tabs: # must be one of https://git.io/vQNgJ
  - csharp
  - javascript
  - python

toc_footers:
  - <a href='mailto:suporte@cartaodetodos.com.br?Subject=Solicitação de Credenciamento'>Credenciamento</a>
  - <a href='#'>TODOS Empreendimentos</a>

includes:
  - errors

search: true
---

# Introdução

Bem-vindo ao portal de documentação das API's da TODOS Empreendimentos. O objetivo é você conseguir explorar as maneiras de utilização das API's disponibilizadas.

- <a href='#api-parceiros'>API Parceiros</a>
- <a href='#api-filiados'>API Filiados</a>

O mecanismo de integração com o Cartão de TODOS é simples, de modo que apenas conhecimentos intermediários em linguagem de programação para Web, requisições HTTP/HTTPS e manipulação de arquivos JSON, são necessários para implantar a solução Cartão de TODOS com sucesso.

# API Parceiros

## Introdução

O objetivo desta documentação é orientar o desenvolvedor sobre como integrar com a **API Parceiros Cartão de TODOS**, descrevendo as funcionalidades, os métodos a serem utilizados, listando informações a serem enviadas e recebidas, e provendo exemplos.

Nesse manual você encontrará a referência sobre todas as operações disponíveis na API REST de integração Cartão de TODOS. Estas operações devem ser executadas utilizando seu token específico nos respectivos endpoints dos ambientes:

SANDBOX | PRODUÇÃO
------------ | -------------
http://sandbox.sistematodos.com.br:81/integracao | https://api.cartaodetodos.com.br/

## Autenticação

> Para autorização, use este código:

```csharp
var client = new RestClient("http://sandbox.sistematodos.com.br:81/api/filiado/10669447684/ctn");

var request = new RestRequest(Method.GET);
request.AddHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891AC5CC59E0CC7A006888DF");

IRestResponse response = client.Execute(request);

```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://sandbox.sistematodos.com.br:81/api/filiado/10669447684/ctn");
xhr.setRequestHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891AC5CC59E0CC7A006888DF");

xhr.send(data);

```

>

Para realizar a autenticação você sempre deverá enviar seu token no cabeçalho em todas as suas requisições, conforme abaixo.

`Authorization: Bearer B4C7AB108191735504990B41D18F1EDBEC14891AC5CC59E0CC7A006888DF`

<aside class="notice">
Você deve substituir <code>B4C7AB108191735504990B41D18F1EDBEC14891AC5CC59E0CC7A006888DF</code> por seu token.
</aside>

## Consultas

Veremos abaixo os métodos para consulta na API Parceiros, seus parâmetros e rotas para os três sistemas do Cartão de TODOS: CartãoNet, Clube de Vantagens da família e IPS colômbia.

**Matrícula/CPF**

```csharp
var client = new RestClient("http://sandbox.sistematodos.com.br:81/integracao/api/filiado/60362238626/ctn");

var request = new RestRequest(Method.GET);
request.AddHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891AC5CC59E0CC7A006888DF");

IRestResponse response = client.Execute(request);
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://sandbox.sistematodos.com.br:81/integracao/api/filiado/60362238626/ctn");
xhr.setRequestHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891DC5CC59E0CC7D106888DF");

xhr.send(data);
```

> A requisição irá retornar o seguinte JSON:

```json
{
  "mensagem": "string",
  "dados": [
    {
      "idFiliado": 0,
      "idPessoa": 0,
      "matricula": "string",
      "nomeFiliado": "string",
      "dataNascimento": "2018-10-17T18:26:46.865Z",
      "cpf": "string",
      "idTipoSituacaoFinanceira": 0,
      "idStatusFiliado": 0,
      "nomeFranquia": "string",
      "endereco": "string",
      "numero": "string",
      "bairro": "string",
      "cidade": "string",
      "uf": "string",
      "telefone": "string",
      "celular": "string",      
      "sistema": 0,
      "idFranquia": 0,
      "idFiliadoPai": 0,
      "tipoSituacaoFinanceira": "string",
      "statusFiliado": "string",
      "tipoFiliado": "string",
      "permiteDesconto": true
    }
  ],
  "quantidade": 0
}
```

A rota da pesquisa por matrícula ou CPF é 

**Requisição HTTP** 

`GET /api/filiado/{matriculaCpf}/{sistema}`

`Exemplo Matrícula: GET /api/filiado/MG046049495/ctn`

`Exemplo CPF: GET /api/filiado/60362238626/ctn`

**•	MatriculaCPF:** Número da matrícula ou CPF do filiado. 

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
 `Mensagem` | String | - | Mensagem de retorno.
 `idFiliado` | Int | - | Número de identificação do filiado. 
 `idPessoa` | Int | - | Número de identificação da pessoa. 
 `matricula` | String | 12 | Matrícula ou CPF do filiado.
 `nomeFiliado` | String | - | Nome do filiado. Deve conter no mínimo 3 caracteres. A pesquisa por nome sempre irá retornar os primeiros 20 resultados. 
 `dataNascimento` | Datetime | yyyy-mm-dd | Data de nascimento do filiado.
 `cpf` | String | 11 | Número do CPF do filiado.
 `idTipoSituacaoFinanceira` | Int | - | Qual a situação financeira do filiado.
 `idStatusFiliado` | Int | - | Identificação do status do filiado.
 `nomeFranquia` | String | - | Nome da franquia em que o filiado esta cadastrado.
 `endereco` | String | - | Nome da rua do filiado.
 `numero` | String | - | Número do endereço do filiado.
 `bairro`| String | - | Nome do bairro do filiado.
 `cidade` | String | - | Nome da cidade do filiado.
 `uf` | String | 2 | Nome do estado do filiado.
 `telefone` | String | 10 | Número de telefone do filiado.
 `celular` | String | 11 | Número de celular do filiado. 
 `sistema` | Int | 3 | Sigla do sistema.
 `idFranquia` | Int | - | Número de identificação da franquia.
 `idFiliadoPai` | Int | - | Identificação do titular do contrato.
 `tipoSituacaoFinanceira` | String | - | Status da situação financeira do filiado (Adimplente, inadimplente etc).
 `statusFiliado` | String | - | Status do filiado (Ativo, desfiliado etc).
 `tipoFiliado` | String | - | Informa se é o titular ou dependente do contrato.
 `permiteDesconto` | Boolean | - | Se o desconto é permitido (true/false).
 `quantidade` | Int | - | Quantidade de itens dentro do array dados.


**Nome**

```csharp
var client = new RestClient("http://sandbox.sistematodos.com.br:81/integracao/api/filiado/pesquisa/lorenna/ctn");

var request = new RestRequest(Method.GET);
request.AddHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891BC5CC59E0CC7A106888DF");

IRestResponse response = client.Execute(request);
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://sandbox.sistematodos.com.br:81/integracao/api/filiado/pesquisa/lorenna/ctn");
xhr.setRequestHeader("authorization", "Bearer B4C7AB108191735504990B41D18F1EDBEC14891DC5CC59F0CC7D106888DF");

xhr.send(data);
```

> A requisição irá retornar o seguinte JSON:

```json
{
  "mensagem": "string",
  "dados": [
    {
      "idFiliado": 0,
      "idPessoa": 0,
      "matricula": "string",
      "nomeFiliado": "string",
      "dataNascimento": "2018-10-17T18:33:31.200Z",
      "cpf": "string",
      "idTipoSituacaoFinanceira": 0,
      "idStatusFiliado": 0,
      "nomeFranquia": "string",
      "endereco": "string",
      "numero": "string",
      "bairro": "string",
      "cidade": "string",
      "uf": "string",
      "telefone": "string",
      "celular": "string",      
      "sistema": 0,
      "idFranquia": 0,
      "idFiliadoPai": 0,
      "tipoSituacaoFinanceira": "string",
      "statusFiliado": "string",
      "tipoFiliado": "string",
      "permiteDesconto": true
    }
  ],
  "quantidade": 0
}
```

A rota da pesquisa por nome é 

**Requisição HTTP** 

`GET /api/filiado/pesquisa/{nome}/{sistema}`

`Exemplo: GET /api/filiado/pesquisa/lorenna/ctn`

**•	Nome:** Nome do filiado. 

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
 `Mensagem` | String | - | Mensagem de retorno.
 `idFiliado` | Int | - | Número de identificação do filiado.  
 `idPessoa` | Int | - | Número de identificação da pessoa. 
 `matricula` | String | 12 | Matrícula ou CPF do filiado.
 `nomeFiliado` | String | - | Deve conter no mínimo 3 caracteres. A pesquisa por nome sempre irá retornar os primeiros 20 resultados. 
 `dataNascimento` | Datetime | yyyy-mm-dd | Data de nascimento do filiado.
 `cpf` | String | 11 | Número do CPF do filiado.
 `idTipoSituacaoFinanceira` | Int | - | Qual a situação financeira do filiado.
 `idStatusFiliado` | Int | - | Identificação do status do filiado.
 `nomeFranquia` | String | - | Nome da franquia em que o filiado esta cadastrado.
 `endereco` | String | - | Nome da rua do filiado.
 `numero` | String | - | Número do endereço do filiado.
 `bairro` | String | - | Nome do bairro do filiado.
 `cidade` | String | - |  Nome da cidade do filiado.
 `uf` | String | 2 | Nome do estado do filiado.
 `telefone` | String | 10 | Número de telefone do filiado.
 `celular` | String | 11 | Número de celular do filiado. 
 `sistema` | Int | 3 | Sigla do sistema.
 `idFranquia` | Int | - | Número de identificação da franquia.
 `idFiliadoPai` | Int | - | Identificação do titular do contrato.
 `tipoSituacaoFinanceira` | String | - | Status da situação financeira do filiado (Adimplente, inadimplente etc).
 `statusFiliado` | String | - | Status do filiado (Ativo, desfiliado etc).
 `tipoFiliado` | String | - | Informa se é o titular ou dependente do contrato.
 `permiteDesconto` | Boolean | - | Se o desconto é permitido (true/false).
 `quantidade` | Int | - | Quantidade de itens dentro do array dados.

# API Filiados

## Introdução

O objetivo desta documentação é orientar o desenvolvedor sobre como integrar com a **API Filiado Cartão de TODOS**, descrevendo as funcionalidades, os métodos a serem utilizados, listando informações a serem enviadas e recebidas, e provendo exemplos.

Nesse manual você encontrará a referência sobre todas as operações disponíveis na API REST Filiado Cartão de TODOS. Estas operações devem ser executadas utilizando seu token específico nos respectivos endpoints dos ambientes:

SANDBOX | PRODUÇÃO
------------ | -------------
https://homologacao.sistematodos.com.br/api.filiado | https://filiado.sistematodos.com.br

### Identificação do produto

Todas as requisições devem conter a identificação do produto no cabeçalho. A identificação será efetuada da seguinte forma:

<code>Produto: 1</code>

PRODUTO | CÓDIGO
------------ | -------------
Cartão de TODOS               | 1
Clube de Vantagens da Família | 2
IPS de TODOS Colômbia         | 3

## Autenticação

> Para autorização, use este código:

```csharp
var client = new RestClient("https://login.cartaodetodos.com.br/connect/token");

var request = new RestRequest(Method.POST);

request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("grant_type", "client_credentials");
request.AddParameter("scope", "apifiliado apifiliado:baixa");
request.AddParameter("client_id", "{SeuClientID}");
request.AddParameter("client_secret", "{SeuClientSecret}");

IRestResponse response = client.Execute(request);

```

```javascript
var data = "grant_type=client_credentials&scope=apifiliado%20apifiliado%3Abaixa&client_id=&client_secret=";

var xhr = new XMLHttpRequest();

xhr.withCredentials = true;
xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
xhr.open("POST", "https://login.cartaodetodos.com.br/connect/token");
xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
xhr.send(data);

```

> A requisição irá retornar o seguinte JSON:

```json
{
    "access_token": "{SeuAccess_token}",
    "expires_in": 3600,
    "token_type": "Bearer",
    "scope": "apifiliado apifiliado:baixa"
}
```

>

A aplicação solicita um token de acesso enviando suas credenciais, seu <code>client_id</code> e <code>client_secret</code>, para o servidor de autorização. Um exemplo de solicitação POST poderia se parecer com o que se encontra ao lado:

Se as credenciais da aplicação forem verificadas, o servidor de autorização retorna um token de acesso para a aplicação. Agora a aplicação está autorizada a utilizar sua própria conta!

<aside class="notice">
Você deve substituir {SeuClientID} por seu <code>client_id</code> e {SeuClientSecret} por seu <code>client_secret</code>.
</aside>

Uma vez obtido o token de acesso, ele poderá ser utilizado para acesso à API, limitado ao escopo informado, até que o token expire ou seja revogado.

<aside class="notice">
Na chave {SeuAccess_token} no retorno será apresentado o seu Token.
</aside>

Para consumir a API é necessário informar o <code>access_token</code> no cabeçalho de **todas** as requisições.

## Dicionário de Dados

**Serviços**

SERVIÇO | IDENTIFICAÇÃO 
--------- | ----------- 
`Mensalidade`   | mensalidade     
`Adesão`        | adesão  

<br>

**Forma de Pagamento Colômbia**

ID | FORMA DE PAGAMENTO 
--------- | ----------- 
`5301083`   | PAYVALIDA - BALOTO     
`5301085`   | PAYVALIDA - EFECTY  


## Arrecadação de Lançamentos

```csharp
var client = new RestClient("https://homologacao.sistematodos.com.br/api.filiado/lancamentos/baixa");

var request = new RestRequest(Method.POST);

request.AddHeader("Produto", "1");
request.AddHeader("Authorization", "Bearer {Seu access_token}");
request.AddHeader("Content-Type", "application/json");
request.AddBody("application/json", new {
    valorDesconto: 10,
    idFiliado: 22916173,
    idFormaPagamento: 18,
    referencia: "2020/08",
    logUsuario: "log usuario",
    servico: "mensalidade"
});

IRestResponse response = client.Execute(request);

Console.WriteLine(response.Content);
```

```javascript
var data = JSON.stringify({"idLancamento":null,"valorDesconto":10,"historico":null,"idFiliado":22916173,"idFormaPagamento":18,"referencia":"2020/08","logUsuario":"maisTodos","servico":"mensalidade"});

var xhr = new XMLHttpRequest();

xhr.withCredentials = true;
xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
xhr.open("POST", "https://localhost:5001/lancamentos/baixa");
xhr.setRequestHeader("Produto", "1");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.send(data);

```

```py

import http.client
import mimetypes

conn = http.client.HTTPSConnection("localhost", 5001)

payload = "{\r\n  \"idLancamento\": null,\r\n  \"valorDesconto\":10,\r\n  \"historico\": null,\r\n  \"idFiliado\": 22916173,\r\n  \"idFormaPagamento\": 18,\r\n  \"referencia\": \"2020/08\",\r\n  \"logUsuario\" : \"maisTodos\",\r\n  \"servico\" : \"mensalidade\"\r\n}"

headers = 
  {
    'Produto': '1',
    'Content-Type': 'application/json'
  }

conn.request("POST", "/lancamentos/baixa", payload, headers)
res = conn.getresponse()

data = res.read()
print(data.decode("utf-8"))

```

> A requisição irá retornar o seguinte JSON caso  sucesso:

```json
{
    "success": true,
    "message": "Baixa armazenada para processamento.",
    "data": [
        "46_7cb053a67f1146ff9828b27fb052c4b0",
        "46_e55a4101accb4900bdf90f60c70f8681"
    ]
}
```

> A requisição irá retornar o seguinte JSON caso houver erro:

```json
{
    "success": false,
    "message": "Descrição do erro",
    "data": null
}
```

**Requisição HTTP** 

`POST /Lancamentos/baixa`

### Entrada

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`idFiliado`         | Int     | -  | Identificação do Filiado.
`referencia`        | String  | 7  | Referência do lançamento. Formato **yyyy/MM** (Ex.: 2020/10)
`servico`           | String  | 16 | Identificação do serviço. Conforme o <a href='#dicionario-de-dados'>dicionário de dados</a>.
`logusuario`        | String  | 56 | Nome a ser salvo no log do lançamento.
`idFormaPagamento`  | Int     | -  | Identificação da forma de pagamento.

### Retorno

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`success`        | Boolean   | - | Retorno de verdadeiro ou falso de acordo com a operação.
`message`        | String    | - | Mensagem de retorno.
`data`           | String    | - | Identificações dos lançamentos salvos para processamento. 
