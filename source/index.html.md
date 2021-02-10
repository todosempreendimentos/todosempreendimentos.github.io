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
var client = new RestClient("https://minhaconta.sistematodos.com.br/connect/token");

var request = new RestRequest(Method.POST);

request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("grant_type", "client_credentials");
request.AddParameter("scope", "apifiliado apifiliado:baixa");
request.AddParameter("client_id", "{SeuClientID}");
request.AddParameter("client_secret", "{SeuClientSecret}");

IRestResponse response = client.Execute(request);

```

```javascript
var http = require('https');

var fs = require('fs');

var qs = require('querystring');

var options = {
  'method': 'POST',
  'hostname': '{endpoint da api}',
  'path': '/sso2/connect/token',
  'headers': {
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  'maxRedirects': 20
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });
  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);

    console.log(body.toString());
  });
  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = qs.stringify({
  'client_id': '{SeuClientID}',
  'client_secret': '{SeuClientSecret}',
  'grant_type': 'client_credentials',
  'scope': 'openid apifiliado ctn apifiliado:baixa'
});

req.write(postData);
req.end();

```

```py
import http.client
import mimetypes
conn = http.client.HTTPSConnection("{endpoint da api}")
payload = 'client_id={client Id}}'\
            'client_secret={secret}'\
            '&grant_type=client_credentials'\
            '&scope=openid apifiliado ctn apifiliado:baixa'
headers = {
    'Content-Type': 'application/x-www-form-urlencoded'
}
conn.request("POST", "/sso2/connect/token", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
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

id | SERVIÇO | IDENTIFICAÇÃO DE ARRECADAÇÃO 
--------- | --------- | ----------- 
1   | `Mensalidade`   | mensalidade     
4   | `Adesão`        | adesão  

<br>

**Forma de Pagamento Colômbia**

ID | FORMA DE PAGAMENTO 
--------- | ----------- 
`5301083`   | PAYVALIDA - BALOTO     
`5301085`   | PAYVALIDA - EFECTY  

<br>

**idTipoFormaPagamento - Forma de Pagamento**

id | FORMA DE PAGAMENTO 
--------- | ----------- 
1  | BOLETO     
2  | CARNE  
3  | CARTÃO DE CRÉDITO 
4  | CONCESSIONÁRIA ENERGIA  
5  | DÉBITO BANCÁRIO  
7  | DIRETO NO CARTÃO

<br>

**idFormaPagamento - Forma de Pagamento**

### BOLETOS

id | FORMA DE PAGAMENTO 
--------- | ----------- 
5300067	  | BOLETO BRADESCO
5300069	  | BOLETO SANTANDER
5300114	  | BOLETO CAIXA

### CARNÊS

id | FORMA DE PAGAMENTO 
--------- | ----------- 
23	      | CARNÊ - SANTANDER
5300077	  | BOLETO SANTANDER - CORPORATIVO

### CONCESSIONÁRIAS DE ENERGIA

id | FORMA DE PAGAMENTO
--------- | ----------- 
2	      | ESCELSA
3	      | SANTA MARIA
4	      | CPFL PAULISTA
5	      | CPFL PIRATININGA
6	      | ENERGISA
7	      | CPFL SUL
5300001 |	BANDEIRANTES SP
5300002	| ENEL DISTRIBUIÇÃO
5300003	| AMPLA RJ
5300004	| RGE
5300007	| COELCE
5300058	| CPFL SANTA CRUZ
5300061	| AES SUL
5300113	| CELG
5300121	| RGE SUL
5300137	| NEOENERGIA COELBA
5301126	| NEOENERGIA CELPE
5301127	| NEOENERGIA COSERN

### DÉBITOS BANCÁRIOS

id | FORMA DE PAGAMENTO 
--------- | ----------- 
14	    | BANCO DO BRASIL
15	    | CAIXA ECONOMICA FEDERAL
18	    | BRADESCO
5300083	| SANTANDER
5300088	| ITAU
5300115	| SICOOB

### DIRETO NO CARTÃO

id | FORMA DE PAGAMENTO 
--------- | ----------- 
22	      | DIRETO NO CARTÃO - DINHEIRO
5300009	  | DIRETO NO CARTÃO - CIELO/MASTER
5300010	  | DIRETO NO CARTÃO - MASTER
5300011	  | DIRETO NO CARTÃO - CHEQUE
5300013	  | DIRETO NO CARTÃO - DÉBITO
5300070	  | DIRETO NO CARTÃO - PAG SEGURO
5300081	  | DIRETO NO CARTÃO - REDE PAY
5300082	  | DIRETO NO CARTÃO - DEPOSITO BANCÁRIO
5300104	  | DIRETO NO CARTÃO - PAGTODOS

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


## Pessoa

No aplicativo vendedores é realizado validações de algumas informações do cliente, como por exemplo:
  <ul>
    <li>CPF</li>
    <li>E-mail</li>
    <li>Telefone</li>
  </ul>

As principais validações realizadas são:

<b>CPF:</b> Verifica se já existe cadastro em nosso banco de dados.

Abaixo veremos a operação realizada para cada situação:
<ul>
  <li><b>Titular ativo:</b> Não será possível prosseguir pois o cliente já possuí uma matrícula ativa.</li>
  <li><b>Titular desfiliado:</b> Será informado em tela se deseja realizar a refiliação do mesmo.</li>
  <li><b>Dependente ativo:</b> Pode ser efetuado a filiação</li>
  <li><b>Dependente inativo:</b> Pode ser efetuado a filiação</li>
  <li><b>Responsável Financeiro:</b> Pode ser efetuado a filiação</li>
</ul>

<b>Email:</b> Verifica se o email já se encontra cadastrado no sistema para outro CPF.

<b>Telefone:</b> Verifica se o telefone já se encontra cadastrado no sistema para outro CPF.

### Pessoa/{documento}

**Requisição HTTP** 

Ao acessar a rota `GET Pessoa/{documento}` será realizada a validação do documento de identificação <b>(CPF)</b> informado.

`GET Pessoa/{documento}`

`Exemplo: GET Pessoa/XXXXXXXXXXX`


> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": {
    "titularAtivo": true,
    "idFiliado": 0,
    "titular": true,
    "idFranquia": 0,
    "pessoa": {
      "nome": "string",
      "dataNascimento": "2020-12-29T14:34:14.773Z",
      "documentoIdentificacao": "string",
      "identidade": "string",
      "genero": 0,
      "estadoCivil": 0,
      "email": "string",
      "telefones": [
        {
          "numero": "string",
          "tipo": 0
        }
      ]
    }
  }
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success`                 | Boolean | - | Sucesso da requisição.
`message`                 | String  | - | Mensagem de retorno.
`titularAtivo`            | Boolean | - | Retorno do status do filiado (Caso o CPF informado esteja cadastrado no sistema).
`idfiliado`               | Int     | - | Id do filiado, caso possua cadastro como filiado.
`titular`                 | Boolean | - | Informação se encontra cadastrado como titular.
`idFranquia`              | Int     | - | Id da franquia que ele está cadastro, caso esteja cadastrado.
`nome`                    | String  | - | Nome.
`dataNascimento`          | Int     | - | Data de nascimento.
`documentoIdentificacao`  | String  | - | CPF.
`identidade`              | String  | - | RG.
`genero`                  | Int     | - | Gênero.
`estadoCivil`             | Int     | - | Estado civil.
`email`                   | String  | - | E-mail.
`numero`                  | String  | - | Numero.
`tipo`                    | Int     | - | Tipo do número, se é Celular ou Telefone fixo.

### Pessoa/{documento}/{email}

**Requisição HTTP** 

Ao acessar a rota `GET Pessoa/{documento}/{email}` será realizada a validação do email que está sendo cadastrado para <b>(CPF)</b> informado.

`GET Pessoa/{documento}/{email}`

`Exemplo: GET Pessoa/XXXXXXXXXXX/emailexemplo@provedor.com.br`

<aside class="notice">
Caso o email já esteja cadastrado para outro CPF, não será permitido o prosseguimento do cadastro com esse email.
</aside>

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": "string"
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success` | Boolean | - | Sucesso da requisição.
`message` | String  | - | Mensagem de retorno.
`data`    | String  | - | Informação se o email já se encontra cadastrado.

### Pessoa/{documento}/telefone/{telefone}

**Requisição HTTP** 

Ao acessar a rota `GET Pessoa/{documento}/telefone/{telefone}` será realizada a validação do telefone que está sendo cadastrado para <b>(CPF)</b> informado.

`GET Pessoa/{documento}/telefone/{telefone}`

`Exemplo: GET Pessoa/XXXXXXXXXXX/telefone/31999999999`

<aside class="notice">
Caso o telefone já esteja cadastrado para outro CPF, não será permitido o prosseguimento do cadastro com esse número.
</aside>

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": "string"
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success` | Boolean | - | Sucesso da requisição.
`message` | String  | - | Mensagem de retorno.
`data`    | String  | - | Informação se o telefone já se encontra cadastrado.

## Filiação

**Requisição HTTP** 

`POST /filiacao`

> A requisição irá retornar o seguinte JSON:

```json
{
  "idProduto": 0,
  "idFranquia": 0,
  "idPv": "string",
  "idPromotorVendas": 0,
  "titular": {
    "nome": "string",
    "dataNascimento": "2020-12-28T17:07:55.119Z",
    "documentoIdentificacao": "string",
    "identidade": "string",
    "genero": 0,
    "estadoCivil": 0,
    "email": "string",
    "telefones": [
      {
        "numero": "string",
        "tipo": 0
      }
    ],
    "endereco": {
      "codigoPostal": "string",
      "logradouro": "string",
      "numero": "string",
      "complemento": "string",
      "bairro": "string",
      "cidade": "string",
      "uf": "string"
    }
  },
  "responsavelFinanceiro": {
    "nome": "string",
    "dataNascimento": "2020-12-28T17:07:55.119Z",
    "documentoIdentificacao": "string",
    "identidade": "string",
    "genero": 0,
    "estadoCivil": 0,
    "email": "string",
    "telefones": [
      {
        "numero": "string",
        "tipo": 0
      }
    ],
    "endereco": {
      "codigoPostal": "string",
      "logradouro": "string",
      "numero": "string",
      "complemento": "string",
      "bairro": "string",
      "cidade": "string",
      "uf": "string"
    }
  },
  "responsavelFinanceiroMesmoTitultar": true,
  "formasPagamento": [
    {
      "id": "string",
      "idTipoFormaPagamento": 0,
      "idFormaPagamento": 0,
      "dados": {}
    }
  ],
  "servicos": [
    {
      "id": 0,
      "parcelas": 0,
      "formaPagamento": "string"
    }
  ],
  "termoAceite": true,
  "voucher": "string"
}
```

### Entrada

As tabelas a seguir são descrições de toda a estrutura Json exibida ao lado.

Os três primeiros dados que teremos no Json são:

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`idProduto`             | Int    | -  | Identificação do produto.
`idFranquia`            | String | -  | Identificação da franquia.
`idPv`                  | Int    | -  | Identificação do Promotor de Vendas.
`idPromotorVendas`      | Int    | -  | Identificação do Promotor de Vendas.

<br>

A tabela a seguir é descritiva ao objeto <code>titular</code> e também <code>responsavelFinanceiro</code>. 

<aside class="notice">
O objeto <code>responsavelFinanceiro</code> só será preenchido caso o responsável financeiro esteja com o retorno <code>false</code> em <code>responsavelFinanceiroMesmoTitultar</code>. Caso o contrário, ficará em branco.
</aside>

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`nome`                    | String  | - | Nome do titular do contrato e/ou responsável financeiro.
`dataNascimento`          | Int     | - | Data de nascimento do titular do contrato e/ou responsável financeiro.
`documentoIdentificacao`  | String  | - | CPF do titular do contrato e/ou responsável financeiro.
`identidade`              | String  | - | RG do titular do contrato e/ou responsável financeiro.
`genero`                  | Int     | - | Gênero do titular do contrato e/ ou responsável financeiro.
`estadoCivil`             | Int     | - | Estado civil do titular do contrato e/ ou responsável financeiro.
`email`                   | String  | - | E-mail do titular do contrato e/ou responsável financeiro.
`numero`                  | String  | - | Numero do telefone ou celular do titular do contrato e/ ou responsável financeiro.
`tipo`                    | Int     | - | Tipo do número, se é Celular ou Telefone fixo.
`codigoPostal`            | String  |    | Código postal do titular do contrato e/ou responsável financeiro.
`logradouro`              | String  |    | Endereço do titular do contrato e/ou responsável financeiro.
`numero`                  | String  |    | Número da casa do titular do contrato e/ou responsável financeiro.
`complemento`             | String  |    | Complemento do endereço do titular do contrato e/ou responsável financeiro.
`bairro`                  | String  |    | Bairro do titular do contrato e/ou responsável financeiro.
`cidade`                  | String  |    | Cidade do titular do contrato e/ou responsável financeiro.
`uf`                      | String  |    | Estado do titular do contrato e/ou responsável financeiro.

<br>

A tabela a seguir contém o identificador chave que retornará se o responsável financeiro será o mesmo que o titular ou não. 

<aside class="notice">
Caso o mesmo retorne **VERDADEIRO**, não será necessário o preenchimento do objeto <code>responsavelFinanceiro</code>, caso retorne **FALSO**, esse objeto é obrigatório.
</aside>

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`responsavelFinanceiroMesmoTitultar`  | Boolean  |    | Identificador se o responsável financeiro é diferente ou igual ao titular do contrato.

<br>

A tabela a seguir é descritiva ao objeto de <code id='forma_pgto'>formasPagamento</code>.

<aside class="notice">
A estrutura do objeto <code>formasPagamento</code> dependerá da forma de pagamento escolhida pelo cliente.
</aside>

Abaixo veremos a estrutura geral que será requerida em todas as formas de pagamento e logo depois, as particularidades de cada um.

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`id`                      | String  |    | Identificação da forma de pagamento relacionada com os serviços que serão informados. <a href='#relacionamento'>(Exemplo)</a>
`idTipoFormaPagamento`    | String  |    | Identificação do idTipoFormaPagamento. Conforme o <a href='#dicionario-de-dados'>dicionário de dados</a>.
`idFormaPagamento`        | String  |    | Identificação do idFormaPagamento. Conforme o <a href='#dicionario-de-dados'>dicionário de dados</a>.
`dados`                   | object  |    | As informações contidade nesse objeto dependerá do retorno da forma de pagamento escolhida pelo cliente.

<br>

<span id="estru-forma-pgto">Abaixo veremos as estruturas de cada forma de pagamento.</span>

<aside class="notice">
Para cobranças no Direto no Cartão, Boleto ou Carnê é necessário apenas as informações da estrutura geral.
</aside>

### Concessionária de Energia

> Estrutura JSON dos dados da concessionária de energia

```json
{
   "uc":"00000000000",
   "contaContrato":"000000000000",
   "pn":"000000"
}
```

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`uc`                      | String  |    | Número da UC (Unidade consumidora) da conta do cliente.
`contaContrato`           | String  |    | No grupo NeoEnergia, ao invés da cobrança ser realizada pela instalação/uc é realizada pela conta contrato. **Campo exclusivo da NeoEnergia.**
`pn`                      | String  |    | Part number/ Numero de peça. **Exclusivo do grupo CPFL.**



### Cartão de Crédito

> Estrutura JSON dos dados do cartão de crédito

```json
   "dados":{
      "mes":1,
      "ano":2021,
      "numero":"2222.2222.2222.2222",
      "nome":"John Doe",
      "bandeira":"master",
      "codigoSeguranca":"361",
      "criptografiaAdyen":"",
      "metodo":0,
      "dadosAutenticacao":{
         "cavv":null,
         "xid":null,
         "eci":null,
         "version":null,
         "referenceId":null,
         "autenticado":false
      }
   }
```

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`mes`                  | Int     |    | Informação do mês da data de válidade do cartão do cliente.
`ano`                  | Int     |    | Informação do ano da data de válidade do cartão do cliente.
`numero`               | String  |    | Número do cartão do cliente.
`nome`                 | String  |    | Nome conforme cartão do cliente.
`bandeira`             | String  |    | Bandeira do cartão do cliente.
`codigoSeguranca`      | String  |    | CVC do cartão do cliente.
`criptografiaAdyen`    | String  |    | 
`metodo`               | Int     |    | Identificador se o cartão é crédito ou débito. 0 = Cartão crédito / 1 = Cartão de Débito
`cavv`                 | String  |    | 
`xid`                  | String  |    |
`eci`                  | String  |    | 
`version`              | String  |    | 
`referenceId`          | String  |    | 
`autenticado`          | Boolean |    | 

### Débito Bancário

> Estrutura JSON dos dados do débito bancário

```json
{
    "agencia": "0000",
    "digitoVerificadorAgencia": "0",
    "conta": "000000",
    "digitoVerificadorConta": "0",
    "diaVencimento": 1,
    "codigoOperacao": "000",
    "nomeCorrentista": "Nome do Correntista"
}
```

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`agencia`                  | String  |    | Número da agência do cliente.
`digitoVerificadorAgencia` | String  |    | Dígito verificador da agência se houver.
`conta`                    | String  |    | Número da conta.
`digitoVerificadorConta`   | String  |    | Dígito verificador da conta.
`diaVencimento`            | String  |    | Dia em que será realizado a tentativa de cobrança.
`codigoOperacao`           | String  |    | Código de operação da conta.
`nomeCorrentista`          | String  |    | Nome do titular da conta.


<br>

A tabela a seguir é descritiva do objeto <code>servicos</code>.

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`id`              | Int      |    | id será informado de acordo com o serviço escolhido. O mesmo pode ser verificado no <a href='#dicionario-de-dados'>dicionário de dados</a>.
`formaPagamento`  | String   |    | O <code>id</code> informado no objeto <a href='#forma_pgto'><code>formaPagamento</code></a>.
`parcelas`        | Int      |    | Esse campo só será informado se o id do serviço for correspondente ao serviço de **Adesão**.

<br>

Por fim teremos os dois ultimos campos do Json

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`Voucher`      | String   |    | Nome do Voucher (caso o cliente possuir) para desconto da mensalidade e/ou adesão.
`termoAceite`  | Boolean  |    | Identificador da confirmação do cliente.

### Relacionamento - Formas de Pagamento x Serviços 

> JSON  do Exemplo 1

```json
    "formasPagamento": [
        {​​​​​
            "id": "fp_1",
            "idTipoFormaPagamento": 4,
            "idFormaPagamento": 456,
            "dados": {​​​​​
                "uc": "123456789",
                "pn": "123456789",
                "contraContrato": "123456789"
            }​​​​​
        }​​​​​
    ],
 
    "servicos": [
        {​​​​​
            "id": 1,
            "parcelas": 1,
            "formaPagamento": "fp_1"
        }​​​​​,
        {​​​​​
            "id": 4,
            "formaPagamento": "fp_1"
        }​​​​​,
    ],
```
 
> JSON  do Exemplo 2

```json
 "formasPagamento": [
        {​​​​​
            "id": "fp_1",
            "idTipoFormaPagamento": 7,
            "idFormaPagamento": 22,
            "dados": {​​​​​ }​​​​​
        }​​​​​,
        {​​​​​
            "id": "fp_2",
            "idTipoFormaPagamento": "id_debito_bancario",
            "idFormaPagamento": "id_debito_bancario_x",
            "dados": {​​​​​
                "estrutura dos dados do debito bancario aqui"
            }​​​​​
        }​​​​​
    ],
 
    "servicos": [
        {​​​​​
            "id": 1,
            "parcelas": 1,
            "formaPagamento": "fp_2"
        }​​​​​,
        {​​​​​
            "id": 4,
            "formaPagamento": "fp_1"
        }​​​​​,
    ],
```

Ao informar os serviços a serem inclusos e as formas de pagamento que serão utilizadas, deve-se informar uma chave em cada objeto em <code id='relacionamento'>formasPagamento</code> para identificar e relacionar com os respectivos serviços que serão cobrados por ela.
 
**Exemplo 1:**
 
Será feita uma filiação com os serviços 1 (Adesão) e 4 (Mensalidade), a filiação será feita feita pela concessionária de energia XXXXX.
 
O payload ficará da seguinte forma:
 
A forma de pagamento foi identificada como `fp_1` e relacionada com os dois serviços (campo `id` do objeto do Serviço),
Desta forma, será vinculado e executado os dois serviços na forma de pagamento especificada.
 
**Exemplo 2:**
 
No segundo exemplo, será feita uma filiação onde o serviço de Adesão (4) será feito com a forma de pagametno Direto no Cartão, e a mensalidade será feita com o serviço de Débito Bancário, a estrutura ficará da seguinte forma:
 
O serviço de Mensalidade (1) está vinculado à forma de pagamento Débito Bancário através da chave `fp_2`
 
e o serviço de adesão (4) está vinculado à forma de pagamento Direto no Cartão através da chave `fp_1`.

## Refiliação

**Requisição HTTP** 

`POST /refiliacao`

> A requisição irá retornar o seguinte JSON:

```json
  {
    "idProduto": 0,
    "idFranquia": 0,
    "idPv": "string",
    "idPromotorVendas": 0,
    "idFiliado": 0,
    "responsavelFinanceiro": {
      "nome": "string",
      "dataNascimento": "2020-12-21T12:03:46.110Z",
      "documentoIdentificacao": "string",
      "identidade": "string",
      "genero": 0,
      "estadoCivil": 0,
      "email": "string",
      "telefones": [
        {
          "numero": "string",
          "tipo": 0
        }
      ],
      "endereco": {
        "codigoPostal": "string",
        "logradouro": "string",
        "numero": "string",
        "complemento": "string",
        "bairro": "string",
        "cidade": "string",
        "uf": "string"
      }
    },
    "responsavelFinanceiroMesmoTitultar": true,
    "formasPagamento": [
      {
        "id": "string",
        "idTipoFormaPagamento": 0,
        "idFormaPagamento": 0,
        "dados": {}
      }
    ],
    "servicos": [
      {
        "id": 0,
        "parcelas": 0,
        "formaPagamento": "string"
      }
    ],
    "termoAceite": true
}
```

### Entrada

As tabelas a seguir são descrições de toda a estrutura Json exibida ao lado.

<aside class="notice">
Ressaltamos que na fase de refiliação não possuímos o processo de preenchimento dos dados do titular pois, como o mesmo já se encontra cadastrado no sistema, esses dados já existem. Por esse motivo, o retorno não possui nenhum dado do filiado.
</aside>

Os seis primeiros dados que teremos no Json são:

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`idProduto`             | Int    | -  | Identificação do produto.
`idFranquia`            | String | -  | Identificação da franquia.
`idPv`                  | Int    | -  | Identificação do Promotor de Vendas.
`idPromotorVendas`      | Int    | -  | Identificação do Promotor de Vendas.
`idFiliado`             | Int    | -  | Identificação do filiado.

<br>

A tabela a seguir é descritiva ao objeto <code>responsavelFinanceiro</code>. 

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`nome`                    | String  | - | Nome do responsável financeiro.
`dataNascimento`          | Int     | - | Data de nascimento do responsável financeiro.
`documentoIdentificacao`  | String  | - | CPF do responsável financeiro.
`identidade`              | String  | - | RG do responsável financeiro.
`genero`                  | Int     | - | Gênero do responsável financeiro.
`estadoCivil`             | Int     | - | Estado civil do responsável financeiro.
`email`                   | String  | - | E-mail do titular do responsável financeiro.
`numero`                  | String  | - | Numero do telefone ou celular do responsável financeiro.
`tipo`                    | Int     | - | Tipo do número, se é Celular ou Telefone fixo.
`codigoPostal`            | String  |    | Código postal.
`logradouro`              | String  |    | Endereço.
`numero`                  | String  |    | Número da casa.
`complemento`             | String  |    | Complemento.
`bairro`                  | String  |    | Bairro.
`cidade`                  | String  |    | Cidade.
`uf`                      | String  |    | Estado.

<br>

A tabela a seguir contém o identificador chave que retornará se o responsável financeiro será o mesmo que o titular ou não. 

<aside class="notice">
Caso o mesmo retorne **VERDADEIRO**, não será necessário o preenchimento dos objetos <code>responsavelFinanceiro</code>, caso retorne **FALSO**, esse objeto é obrigatório.
</aside>

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`responsavelFinanceiroMesmoTitultar`  | Boolean  |   | Identificador se o responsável financeiro é diferente ou igual ao titular do contrato.

<br>

A tabela a seguir é descritiva ao objeto de <code id='forma_pgto_refiliacao'>formasPagamento</code>.

<aside class="notice">
A estrutura do objeto <code>formasPagamento</code> dependerá da forma de pagamento escolhida pelo cliente.
</aside>

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`id`                      | String  |    | Identificação da forma de pagamento relacionada com os serviços que serão informados. <a href='#relacionamento'>(Exemplo)</a>
`idTipoFormaPagamento`    | String  |    | Identificação do idTipoFormaPagamento. Conforme o <a href='#dicionario-de-dados'>dicionário de dados</a>.
`idFormaPagamento`        | String  |    | Identificação do idFormaPagamento. Conforme o <a href='#dicionario-de-dados'>dicionário de dados</a>.
`dados`                   | object  |    | As informações contidade nesse objeto dependerá do retorno da forma de pagamento escolhida pelo cliente.

<br>

As estruturas do retorno das formas de pagamento são as mesmas apresentdas no processo de filiação.<a href='#estru-forma-pgto'>Você pode ver clicando aqui.</a>

<br>

A tabela a seguir é descritiva do objeto <code>servicos</code>.

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`id`              | Int      |    | id será informado de acordo com o serviço escolhido. O mesmo pode ser verificado no <a href='#dicionario-de-dados'>dicionário de dados</a>.
`parcelas`        | Int      |    | Esse campo só será informado se o id do serviço for correspondente ao serviço de **Adesão**.
`formaPagamento`  | String   |    | O <code>id</code> informado no objeto <a href='#forma_pgto_refiliacao'><code>formaPagamento</code></a>.

<br>

Por fim teremos os dois ultimos campos do Json

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`termoAceite`  | Boolean  |    | Identificador da confirmação do cliente.

## Voucher

### GET /Voucher/identificador/{identificador}

<aside class="notice">
O endpoint <strong>/Voucher/identificador/{identificador}</strong> deve ser utilizado para obter as informações a respeito do voucher informado de uma forma resumida e assim entender qual finalidade ele será utilizado, quantos estão disponíveis e também o valor de desconto, bem como outras informações complementares.
</aside>

**Requisição HTTP** 

`GET /Voucher/identificador/{identificador}`

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "requestId": "string",
  "data": {
    "limite": 0,
    "possuiLimiteDisponivel": true,
    "porcentagem": 0,
    "servicos": [],
    "valido": true,
    "valorTotal": 0,
    "descontoTotal": 0,
    "valorComDescontoTotal": 0
  }
}
```

### Entrada

A tabela a seguir são descrições de toda a estrutura Json exibida ao lado.

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`success`                 | Boolean | -  | Sucesso da requisição.
`message`                 | String  | -  | Mensagem de retorno.
`requestId`               | Int     | -  | Só será retornado em caso de erro.
`limite`                  | Int     | -  | Quantidade de voucher disponibilizados para a campanha.
`possuiLimiteDisponivel`  | Int     | -  | Caso a utilização do voucher exceda o limite de utilização, esse campo é preenchido com a informação de que o voucher não possui limite disponível.
`porcentagem`             | Int     | -  | Porcentagem de desconto do voucher.
`valido`                  | Int     | -  | Informação referente a disponibilidade do voucher. Ex.: Se ultrapassado o limite; se ultrapassado a data de validade; se o voucher informado é realmente válido.
`valorTotal`              | Int     | -  | Valor original do serviço sem o desconto fornecido pelo voucher.
`descontoTotal`           | Int     | -  | Valor do desconto do voucher.
`valorComDescontoTotal`   | Int     | -  | Valor total do serviço com o desconto aplicado.


### GET Voucher/servicos/identificador/{identificador}

<aside class="notice">
O endpoint <strong>Voucher/servicos/identificador/{identificador}</strong> deve ser utilizado para obter as informações se o voucher informado encontra-se disponível para o serviço que deseja buscar. Também trará as informações resumidas do voucher bem como endpoint anterior.
</aside>

**Requisição HTTP** 

`GET /Voucher/servicos/identificador/{identificador}`

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "requestId": "string",
  "data": {
    "limite": 0,
    "possuiLimiteDisponivel": true,
    "porcentagem": 0,
    "servicos": [
      {
        "id": 0,
        "valorMensal": 0,
        "possuiDesconto": true,
        "desconto": 0,
        "valorComDesconto": 0
      }
    ],
    "valido": true,
    "valorTotal": 0,
    "descontoTotal": 0,
    "valorComDescontoTotal": 0
  }
}
```

### Entrada

A tabela a seguir são descrições de toda a estrutura Json exibida ao lado.

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- | ----------- | ------ | ---------- 
`success`                 | Boolean | -  | Sucesso da requisição.
`message`                 | String  | -  | Mensagem de retorno.
`requestId`               | Int     | -  | Só será retornado em caso de erro.
`limite`                  | Int     | -  | Quantidade de voucher disponibilizados para a campanha.
`possuiLimiteDisponivel`  | Int     | -  | Caso a utilização do voucher exceda o limite de utilização, esse campo é preenchido com a informação de que o voucher não possui limite disponível.
`porcentagem`             | Int     | -  | Porcentagem de desconto do voucher.
`id`                      | Int     | -  | Id do serviço.
`valorMensal`             | Int     | -  | Valor mensal do serviço.
`possuiDesconto`          | Int     | -  | Se possui desconto para o serviço.
`desconto`                | Int     | -  | Qual o valor que será aplicado de desconto.
`valorComDesconto`        | Int     | -  | Valor total do serviço com o desconto aplicado.
`valido`                  | Int     | -  | Informação referente a disponibilidade do voucher. Ex.: Se ultrapassado o limite; se ultrapassado a data de validade; se o voucher informado é realmente válido.
`valorTotal`              | Int     | -  | Valor original do serviço sem o desconto fornecido pelo voucher.
`descontoTotal`           | Int     | -  | Valor do desconto do voucher.
`valorComDescontoTotal`   | Int     | -  | Valor total do serviço com o desconto aplicado.

# API Franquia

## Introdução

O objetivo desta documentação é orientar o desenvolvedor sobre como integrar com a **API Franquia Cartão de TODOS**, descrevendo as funcionalidades, os métodos a serem utilizados, listando informações a serem enviadas e recebidas, e provendo exemplos.

Nesse manual você encontrará a referência sobre todas as operações disponíveis na API REST Franquia Cartão de TODOS. Estas operações devem ser executadas utilizando seu token específico nos respectivos endpoints dos ambientes:

SANDBOX | PRODUÇÃO
------------ | -------------
https://homologacao.sistematodos.com.br/api.franquias | https://franquia.sistematodos.com.br

## Autenticação

> Para autorização, use este código:



```csharp
var client = new RestClient("https://minhaconta.sistematodos.com.br/connect/token");

var request = new RestRequest(Method.POST);

request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("grant_type", "client_credentials");
request.AddParameter("scope", "franquias:franq franquias:contas {sistema}");
request.AddParameter("client_id", "{SeuClientID}");
request.AddParameter("client_secret", "{SeuClientSecret}");

IRestResponse response = client.Execute(request);

```

```javascript
var http = require('https');

var fs = require('fs');

var qs = require('querystring');

var options = {
  'method': 'POST',
  'hostname': '{endpoint da api}',
  'path': '/sso2/connect/token',
  'headers': {
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  'maxRedirects': 20
};

var req = http.request(options, function (res) {
  var chunks = [];
  res.on("data", function (chunk) {
    chunks.push(chunk);
  });
  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = qs.stringify({
  'client_id': '{SeuClientID}',
  'client_secret': '{SeuClientSecret}',
  'grant_type': 'client_credentials',
  'scope': 'openid franquias:franq {sistema} franquias:contas'
});

req.write(postData);
req.end();

```

```py
import requests;

payload = {'client_id' : '{client Id}}', 'client_secret' : '{client secret}',  'grant_type' : 'client_credentials', 'scope' : 'openid franquias:franq ctn franquias:contas'}    

res = requests.post("{endpoint do SSO}/sso2/connect/token")
print res.content
```

> A requisição irá retornar o seguinte JSON:

```json
{
  "access_token": "{SeuAccess_token}",
  "expires_in": 3600,
  "token_type": "Bearer",
  "scope": "franquias:franq franquias:contas"
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

<aside class="notice">
Os escopos devem ser solicitados de acordo com as informações que se deseja
</aside>

Veremos abaixo os métodos para consulta na API Franquias, seus parâmetros e rotas.

<aside class="notice">
Em todas as requisições deve ser informado o <code>Produto</code> para que possamos identificar o sistema que está sendo requisitado a pesquisa. Caso este não seja informado, tentaremos identificar pelo scope. Caso nenhum dos anteriores sejam identificados, será adotado como default o CTN.
</aside>

SISTEMA | CÓDIGO | IDENTIFICAÇÃO
--------- | ----------- | -----------
`CTN`     | 1    | Sistema do Cartão de TODOS
`CVF`     | 2    | Sistema do Clube de Vantagens da Família

## Franquias/promotor

**Requisição HTTP** 

Ao acessar a rota `GET /v2/Franquias/promotor` será listado o id da franquia a qual o promotor pertence.

<aside class="notice">
O promotor será identificado pelo <code>access_token</code> passado na requisição.
</aside>

`GET /v2/Franquias/promotor`


> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": 0
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success` | Boolean | - | Sucesso da requisição.
`message` | String  | - | Mensagem de retorno.
`data`    | Int     | - | Id da franquia a qual o promotor pertence.

## Perfis

Ao acessar a rota `GET /v2/Perfis` será listado o perfil em todas as franquias que está vinculado.

**Requisição HTTP** 

`GET /v2/Perfis`

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": [
    {
      "id": 0,
      "nome": "string",
      "idFranquia": 0
    }
  ]
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success`     | Boolean | - | Sucesso da requisição.
`message`     | String  | - | Mensagem de retorno.
`id`          | Int     | - | Id do perfil.
`nome`        | String  | - | Nome do perfil
`idFranquia`  | Int     | - | Id da franquia.

## Perfis/franquia/{idFranquia} 

Ao acessar a rota `GET Perfis/franquia/{idFranquia}` serão listados os id's dos perfis que estão vinculados a franquia informada.

**Requisição HTTP** 

`GET Perfis/franquia/{idFranquia}`

`Exemplo: GET Perfis/franquia/46`

**•	idFranquia:** Id da franquia que deseja realizar a pesquisa. 

> A requisição irá retornar o seguinte JSON:

```json
{
  "success": true,
  "message": "string",
  "data": [
    {
      "id": 0,
      "nome": "string",
      "idFranquia": 0
    }
  ]
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`success`     | Boolean | - | Sucesso da requisição.
`message`     | String  | - | Mensagem de retorno.
`id`          | Int     | - | Id do perfil.
`nome`        | String  | - | Nome do perfil.
`idFranquia`  | Int     | - | Id da franquia.

## Franquias/mais-proxima

Ao acessar a rota `GET Franquias/mais-proxima` será informado qual a franquia mais próxima do endereço pesquisado.

**Requisição HTTP** 

`Exemplo: GET /Franquias/mais-proxima?cep={cep}&logradouro={logradouro}&numero={numero}&bairro={bairro}&cidade={cidade}&uf={uf}`

> A requisição irá retornar o seguinte JSON:

```json
{
  "id": 0,
  "idRegional": 0,
  "unidade": "string",
  "nome": "string",
  "cnpj": "string",
  "ativo": true,
  "permiteGerarCobranca": true,
  "email": "string",
  "telefone": "string",
  "uf": "string",
  "cidade": "string",
  "bairro": "string",
  "cep": "string",
  "endereco": "string",
  "numero": 0,
  "complemento": "string",
  "latitude": 0,
  "longitude": 0,
  "permiteFiliar": true,
  "distanciaKM": 0
}
```

**Retorno**

PROPRIEDADE | TIPO | TAMANHO | DESCRIÇÃO
--------- |  ----------- | ------ | ---------- 
`id`                    | Boolean | - | Id da franquia.
`idRegional`            | String  | - | Id da regional da franquia.
`unidade`               | Int     | - | Unidade da franquia.
`nome`                  | String  | - | Nome da franquia.
`cnpj`                  | Int     | - | CNPJ da franquia.
`ativo`                 | Int     | - | Status da franquia. (Ativa ou Inativa)
`permiteGerarCobranca`  | Int     | - | Se a franquia está permitida a gerar cobrança para seus clientes ou não.
`email`                 | Int     | - | Email da franquia.
`telefone`              | Int     | - | Telefone da franquia.
`uf`                    | Int     | - | Estado da franquia.
`cidade`                | Int     | - | Cidade da franquia.
`bairro`                | Int     | - | Bairro da franquia.
`cep`                   | Int     | - | Cep da franquia.
`endereco`              | Int     | - | Endereço da franquia.
`numero`                | Int     | - | Número da franquia.
`complemento`           | Int     | - | Complemento da franquia.
`latitude`              | Int     | - | Latitude do endereço da franquia.
`longitude`             | Int     | - | Longitude do endereço da franquia.
`permiteFiliar`         | Int     | - | Id da franquia.
`distanciaKM`           | Int     | - | Distancia entre a franquia e o endereço do cliente.
