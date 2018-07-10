# Integração
Repositório com exemplos de integração com as APIs da SOHTEC

Veja abaixo exemplos de integração.

# Login
https://sohtec.com.br/services/api/Login

Enviar o json abaixo:

```
{
  "key":"KEY_DO_CLIENTE"
}
```
Você receberá um retorno de um token, ele tem validade de 10 minutos a partir da obtenção do mesmo, ou seja, sempre que for necessário repita a chamada no Login para renovar o token.
```
{
    "token": "xxxxxxxxxxxxxxxxx"
}
```


