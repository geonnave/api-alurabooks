![Integrando seu projeto React com APIs](thumbnail.png)

# AluraBooks

O AluraBooks é uma loja virtual que vende livros da Casa do Código. 
É um MVP que tá só começando e ainda tem muitas funcionalidades novas para serem desenvolvidas.

# JSONServer + JWT Auth

Essa é ma API Rest mockada, utilizando json-server e JWT.

## 🛠️ Instalação

### Configurando o HTTP/2

Essa versão já vem com HTTP/2 habilitado através da biblioteca [spdy](https://www.npmjs.com/package/spdy).
Como o HTTP/2 requer uso de TLS, precisamos gerar um certificado self-signed.
Faça isso antes de executar o servidor, com o seguinte comando:

```bash
$ openssl req -x509 -sha256 -nodes -days 365 -newkey ec -pkeyopt ec_paramgen_curve:secp256k1 -keyout server.key -out server.crt
```

### Instalando dependências e executando o servidor

```bash
$ npm install
$ npm run start-auth
```

## 🛠️ Como se registrar?

Você pode fazer isso efetuando uma requisição post para:

```
POST http://localhost:8000/public/registrar
```

Com os seguintes dados:


```
{
    "nome": "vinicios neves",
    "email": "vinicios@alura.com.br",
    "senha": "123456",
    "endereco": "Rua Vergueiro, 3185",
    "complemento": "Vila Mariana",
    "cep": "04101-300"
}
```

Repare que o e-mail é um campo único e usuários com e-mails duplicados não serão persistidos.

## 🛠️ Como fazer login?

Você pode fazer isso efetuando uma requisição post para:

```
POST http://localhost:8000/public/login
```

Com os seguintes dados:


```
{
  "email": "vinicios@alura.com.br",
  "senha":"123456"
}
```

Você vai receber um token no seguinte formato:

```
{
   "access_token": "<ACCESS_TOKEN>",
   "user": { ... dados do usuário ... }
}
```

## Autenticar próximas requests?

E então, adicionar este mesmo token ao header das próximas requisições:

```
Authorization: Bearer <ACCESS_TOKEN>
```

## 📚 Mais informações do curso

O AluraBooks é o projeto utilizado durante toda a formação, e essa API será utilizada em vários cursos diferentes :)
