# API Endpoints

Este documento define os endpoints da API do Weather Dashboard. Todos os endpoints, exceto os de autenticação, requerem um Bearer Token no header `Authorization`.

---

## Autenticação (`/auth`)

### 1. Registrar Usuário

- **Endpoint:** `POST /auth/register`
- **Descrição:** Cria um novo usuário no sistema.
- **Autenticação:** Não requerida.

**Request Body:**
```json
{
  "name": "João Silva",
  "email": "joao.silva@example.com",
  "password": "strongPassword123"
}
```

**Response (201 Created):**
```json
{
  "id": 1,
  "name": "João Silva",
  "email": "joao.silva@example.com"
}
```

### 2. Login

- **Endpoint:** `POST /auth/login`
- **Descrição:** Autentica um usuário e retorna um token JWT.
- **Autenticação:** Não requerida.

**Request Body:**
```json
{
  "email": "joao.silva@example.com",
  "password": "strongPassword123"
}
```

**Response (200 OK):**
```json
{
  "access_token": "ey..."
}
```

### 3. Obter Perfil do Usuário

- **Endpoint:** `GET /auth/me`
- **Descrição:** Retorna os dados do usuário autenticado.
- **Autenticação:** Requerida (Bearer Token).

**Response (200 OK):**
```json
{
  "id": 1,
  "name": "João Silva",
  "email": "joao.silva@example.com"
}
```

---

## Localidades (`/locations`)

### 1. Buscar Localidades

- **Endpoint:** `GET /locations/search?q={query}`
- **Descrição:** Busca por cidades usando um serviço externo. O backend faz o repasse da chamada.
- **Autenticação:** Requerida.

**Exemplo de chamada:** `GET /locations/search?q=London`

**Response (200 OK):**
```json
[
  {
    "id": 2643743,
    "name": "London",
    "region": "City of London, Greater London",
    "country": "United Kingdom",
    "lat": 51.51,
    "lon": -0.12
  }
]
```

---

## Localidades Salvas do Usuário (`/me/locations`)

### 1. Listar Localidades Salvas

- **Endpoint:** `GET /me/locations`
- **Descrição:** Retorna a lista de localidades salvas pelo usuário.
- **Autenticação:** Requerida.

**Response (200 OK):**
```json
[
  {
    "id": 2643743,
    "name": "London",
    "country": "United Kingdom"
  }
]
```

### 2. Adicionar Localidade

- **Endpoint:** `POST /me/locations`
- **Descrição:** Adiciona uma localidade à lista do usuário.
- **Autenticação:** Requerida.

**Request Body:**
```json
{
  "locationId": 2643743
}
```

**Response (201 Created):**
```json
{
  "id": 2643743,
  "name": "London",
  "country": "United Kingdom"
}
```

### 3. Remover Localidade

- **Endpoint:** `DELETE /me/locations/{locationId}`
- **Descrição:** Remove uma localidade da lista do usuário.
- **Autenticação:** Requerida.

**Exemplo de chamada:** `DELETE /me/locations/2643743`

**Response (204 No Content)**

---

## Dados Meteorológicos (`/weather`)

### 1. Obter Clima por Localidade

- **Endpoint:** `GET /weather/{locationId}`
- **Descrição:** Retorna os dados de clima (atuais e previsão) para uma localidade específica. O backend é responsável por buscar os dados de uma API externa e gerenciá-los em cache.
- **Autenticação:** Requerida.

**Exemplo de chamada:** `GET /weather/2643743`

**Response (200 OK):**
```json
{
  "location": {
    "name": "London",
    "region": "City of London, Greater London",
    "country": "United Kingdom"
  },
  "current": {
    "temp_c": 15,
    "condition": {
      "text": "Partly cloudy",
      "icon": "//cdn.weatherapi.com/weather/64x64/day/116.png"
    },
    "wind_kph": 22.2,
    "humidity": 77
  },
  "forecast": [
    {
      "date": "2025-08-11",
      "day": {
        "maxtemp_c": 20.3,
        "mintemp_c": 12.8,
        "condition": {
          "text": "Sunny"
        }
      }
    }
  ]
}
```