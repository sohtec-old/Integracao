 ## Serviços de Integração ##


1. [Login](#login)
2. [Carregar Clientes](#carregar-clientes)
3. [Carregar Agendas de Visitas a Imóveis](#carregar-agendas-de-visitas-a-imóveis)
4. [Carregar dados de usuários das modalidades de garantia](#carregar-dados-de-usuários-das-modalidades-de-garantia)
5. [Carregar Garantias](#carregar-garantias)
6. [Carregar Empresas](#carregar-empresas)
7. [Bloquear data para visitação de um imóvel dentro da plataforma SOHTEC](#bloquear-data-para-visitação-de-um-imóvel-dentro-da-plataforma-sohtec)
8. [Indicar uma preferência de um imóvel](#indicar-uma-preferência-de-um-imóvel)
9. [Obter url para acessar área administrativa](#obter-url-para-acessar-área-administrativa)
10. [Inserir um Lead](#inserir-um-lead)


## Integração
Repositório com exemplos de integração com as APIs da SOHTEC.
Veja abaixo exemplos de integração.

### Login
Url: https://sohtec.com.br/services/api/Login

Com a **chave(key)** do cliente fornecida pela SOHTEC siga os passos abaixo.

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
```

Enviar o json abaixo:
```javascript {.line-numbers}
{
  "key":"KEY_DO_CLIENTE"
}
```

Você receberá um retorno de um token, ele tem validade de **10 minutos** a partir da obtenção do mesmo, ou seja, sempre que for necessário repita a chamada no Login para renovar o token.
```javascript {.line-numbers}
{
    "token": "xxxxxxxxxxxxxxxxx"
}
```

### Carregar Clientes
Url: https://sohtec.com.br/services/api/GetClients

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar via **POST** no **BODY** o json abaixo:
```javascript {.line-numbers}
{
    "DataInicio" : "10/10/2019",
    "DataFim" : "10/11/2019"
}
```

OU

Enviar via **POST** no **BODY** o json abaixo:
```javascript {.line-numbers}
{    
    "Email" : "fulano@dominio.com"
}
```

Você receberá como retorno um array com os dados dos clientes que se cadastraram ou utilizaram a plataforma de um determinado cliente.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": [
        {
            "Email": "fulano@xxxxxx.com",
            "Nome": "Fulano",
            "Telefone": "99 9 9999-9999"
        },
        {
            "Email": "siclano@xxxxxx.com",
            "Nome": "Siclano",
            "Telefone": "99 9 9999-9999"
        }
    ]
}
```
### Carregar Agendas de Visitas a Imóveis
Url: https://sohtec.com.br/services/api/GetSchedule

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```

Enviar via **POST** no **BODY** o json abaixo:
```javascript {.line-numbers}
{
    "DataInicio" : "10/10/2019",
    "DataFim" : "10/11/2019"    
}
```

Você receberá como retorno um array com os dados das visitas dos clientes que fizeram um agendamento para visitar um imóvel de um determinado cliente.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": [
        {
            "Id": 0,
            "EmpresaId": 0,
            "EmpresaNome": "",
            "ClienteEmail": "",
            "ImovelId": "0",
            "ImovelUrl": "",
            "ImovelEndereco": "",
            "ImovelDormitorios": 0,
            "ImovelVagas": 1,
            "ImovelCep": "",
            "ImovelNumero": "0",
            "ImovelComplemento": "",
            "ImovelBairro": "",
            "ImovelCidade": "",
            "ImovelEstado": "",
            "ImovelAluguel": 0,
            "ImovelCondominio": 0,
            "ImovelIptu": 0,
            "Confirmada": true,
            "Cancelada": false,
            "StatusId": 4,
            "DataAgendamento": "2018-06-13T10:45:00",            
            "VisitaAcampanhada": false
        }
    ]
}
```
### Carregar dados de usuários das modalidades de garantia

Passe junto da url o CODIGO_DA_FICHA que deseja carregar os dados.

Url: https://api.sohtec.com.br/CarregaFicha/CODIGO_DA_FICHA

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```

Resposta:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": {
    	"Id": 6240,
        "TipoPessoa": "PF",
        "ClienteEmail": "le.fonseca@gmail.com",
        "ClienteNome": "LEANDRO SOHTEC",
        "DataCadastro": "2021-12-22T16:40:17.513",
	...
    }
}
```

### Carregar Garantias
Url: https://sohtec.com.br/services/api/GetAssurances

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Você receberá como retorno um array de garantias de imóveis aceitas pela SOHTEC.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": [
        {
            "Id": 3,
            "Nome": "Fiador"
        },
        {
            "Id": 1,
            "Nome": "Seguro Fiança"
        },
        {
            "Id": 2,
            "Nome": "Título de Capitalização"
        }
    ]
}
```
### Carregar Empresas
Url: https://sohtec.com.br/services/api/GetCompanies

Com a **chave(key)** do **parceiro** fornecida pela SOHTEC siga os passos abaixo.

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```

Enviar o json abaixo:
```javascript {.line-numbers}
{
  "key":"KEY_DO_PARCEIRO"
}
```

Você receberá como retorno um array de empresas.<br>
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": [
        {
            "Id": 0,
            "Nome": "",
            "Chave": "",
            "ParceiroCodigoAuxiliar": ""
        }
    ]
}
```

### Bloquear data para visitação de um imóvel dentro da plataforma SOHTEC.
Url: https://sohtec.com.br/services/api/BlockScheduling

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar o json abaixo:
```javascript {.line-numbers}
{	
	"PropertyCode" : "CODIGO_DO_IMOVEL",
	"DateHour" : "2018-08-01 10:00" //A data seve ser enviada no formato (yyyy-MM-dd HH:mm)
}
```

Se os dados estiverem ok o sistema retornará o seguinte JSON.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": null
}
```

### Indicar uma preferência de um imóvel.
Url: https://sohtec.com.br/services/api/SetPreference

Enviar no **Header** da chamada os seguintes parametros:
```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```
Enviar o json abaixo:
```javascript {.line-numbers}
{
	"PropertyCode" : "CODIGO_DO_IMOVEL",
	"ValidateDate" : "2018-09-01 10:00" //Informe a data limite em que a mensagem de prefência do imóvel deve aparecer na plataforma SOH.
}
```

Se os dados estiverem ok o sistema retornará o seguinte JSON.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": null
}
```


### Obter url para acessar área administrativa 
Url: https://sohtec.com.br/services/api/GetUrlAccess

Enviar no **Header** da chamada os seguintes parametros:

```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```

Enviar o json abaixo:
```javascript {.line-numbers}
{	
	"email" : "EMAIL_DO_USUARIO",
	"senha" : "SENHA_DO_USUARIO"
}
```

Você receberá como retorno uma url com um validade de utilização de 24h.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": "https://imob.sohtec.com.br/redir?hash=uasx9cr9Uo2jdSQCoL5pXfgnj9Q2%2fD4KJWei9oTU5vFQpix6G%2b5%2fEg%3d%3d"
}
```

### Inserir um Lead
Url: https://sohtec.com.br/services/api/AddLead

Enviar no **Header** da chamada os seguintes parametros:

```javascript {.line-numbers}
HTTP Verb: POST
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
```

Enviar o json abaixo:
```javascript {.line-numbers}
{	
	"ClienteEmail" : "",
	"ClienteNome" : "",
	"ClienteTelefone" : "",
	"ImovelCodigo" : "",
	"ClienteNome" : "",
	"Modulo" : "", //LOCACAO ou VENDAS
	"ClienteMensagem" : "",
	"CorretorEmail" : "",
	"Midia":""// Veja lista de mídias abaixo
}
```


**Mídias**
- AGENTE_IMOVEIS
- ATTRIA
- AVALIACAO
- CAPTACAO_LOCACAO
- CAPTACAO_VENDAS
- CASAMINEIRA
- CHAT
- CHAVES_NA_MAO
- DREAMCASA
- EI_IMOVEIS
- EMAIL_MKT
- FACEBOOK
- GOOGLE
- I123
- IMOVELWEB
- IMOVMAP
- INDICACAO
- INDICACAO_CONDOMINIO
- INDICACAO_CREDPAGO
- INDICACAO_LOCACAO
- INSTAGRAM
- LIGACAO
- LINKEDIN
- LOJA
- MERCADO_LIVRE
- NET_IMOVEIS
- OLX
- OUTROS
- PARCERIA
- PASSAGEM
- PLACA
- PORTAL_MEGA_REDE
- RDSTATION
- RECEPCAO
- REDES_SOCIAIS
- RGI
- SITE
- START
- TIKTOK
- TV
- VIVAREAL
- WHATSAPP
- ZAP


Se os dados estiverem ok o sistema retornará o seguinte JSON.
Exemplo de retorno:
```javascript {.line-numbers}
{
    "Code": 0,
    "Message": "OK",
    "Data": null
}
```
