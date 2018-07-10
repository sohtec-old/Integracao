## Integração
Repositório com exemplos de integração com as APIs da SOHTEC.
Veja abaixo exemplos de integração.

### Login
Url: https://sohtec.com.br/services/api/login

Enviar o json abaixo:
```javascript {.line-numbers}
{
  "key":"KEY_DO_CLIENTE"
}
```

Você receberá um retorno de um token, ele tem validade de 10 minutos a partir da obtenção do mesmo, ou seja, sempre que for necessário repita a chamada no Login para renovar o token.
```javascript {.line-numbers}
{
    "token": "xxxxxxxxxxxxxxxxx"
}
```

### Carregar clientes
Url: https://sohtec.com.br/services/api/getclients

Enviar no Header da chamada os seguintes parametros:
```javascript {.line-numbers}
Content-Type: application/json
Authorization: Bearer AQUI_VAI_O_TOKEN
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




