# Estratégia de Autenticação

A autenticação da API é feita através de JSON Web Tokens (JWT) no formato Bearer Token.

## Fluxo de Autenticação

1.  O cliente envia as credenciais (email e senha) para o endpoint `POST /auth/login`.
2.  O servidor valida as credenciais.
3.  Se as credenciais forem válidas, o servidor gera um JWT assinado e o retorna no corpo da resposta.
4.  O cliente armazena o JWT de forma segura.
5.  Para acessar endpoints protegidos, o cliente envia o JWT no header `Authorization` com o prefixo `Bearer`.

**Exemplo de Header:**
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyLCJleHAiOjE1MTYyNDI2MjJ9.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

## Estrutura do Token (JWT)

O token é composto por três partes: Header, Payload e Signature.

### Header

Define o algoritmo de assinatura. Usaremos **HS256**.

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

### Payload (Claims)

Contém as informações (claims) sobre o usuário e o token.

- **`sub` (Subject):** O ID do usuário. Essencial para identificar o autor da requisição.
- **`iat` (Issued At):** Timestamp de quando o token foi criado.
- **`exp` (Expiration Time):** Timestamp de quando o token irá expirar.

**Exemplo de Payload:**
```json
{
  "sub": 101,
  "iat": 1660154400, 
  "exp": 1660158000
}
```

### Signature

A assinatura é usada para verificar que o token não foi alterado. É gerada a partir do header, payload e um segredo (`JWT_SECRET`).

## Considerações de Segurança

### 1. Segredo do JWT (`JWT_SECRET`)

O segredo usado para assinar o token é crítico para a segurança.

- **NUNCA** deve ser exposto no código-fonte.
- **DEVE** ser uma string longa, complexa e aleatória.
- **DEVE** ser gerenciado através de variáveis de ambiente no backend (`JWT_SECRET`).

### 2. Tempo de Expiração do Token

- O `access_token` deve ter um tempo de vida curto para mitigar o risco em caso de vazamento. Uma duração de **15 a 60 minutos** é recomendada.
- Uma estratégia de *refresh token* pode ser implementada no futuro para melhorar a experiência do usuário sem comprometer a segurança.

### 3. Armazenamento no Cliente

- O frontend deve armazenar o token em um local seguro. Evite `localStorage`. Prefira armazenar em memória ou, se necessário, em um `HttpOnly` cookie seguro.