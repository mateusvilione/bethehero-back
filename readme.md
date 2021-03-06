# 🦸‍♀️ Be The Hero 🦸‍♂️

Projeto desenvolvido na 11° semana OmniStack da  [RocketSeat](https://rocketseat.com.br/) com o objetivo desenvolver uma aplicação utilizando as tecnologias:

- [React](https://reactjs.org);
- [React Native](https://facebook.github.io/react-native/);
- [Node.js](https://nodejs.org/en/);
- [Expo](https://expo.io/).

---

Projeto

O projeto `Be the Hero` tem como objetivo conectar pessoas a instituições.

---

## API

HOST: https://bethehero.herokuapp.com/

## Ongs [/ongs]

### Cadastrar uma ong [POST]

- Request (application/json)
    - Attributes (Ong)
```json
{
	"name": "APAD",
	"email": "apad@gmail.com",
	"whatsapp": 13998989898,
	"city": "Rio do Sul",
	"uf": "SC"
}
```

- Response 200 (application/json)
    - Attributes (OngInstance)
```json
{
    "id": "8d4f46b9"
}
```

### Listar todas as ongs [get]

- Response 200 (application/json)
    - Attributes
        - data (array[Ong])
```json
[
    {
        "id": "8d577961",
        "name": "APAD",
        "email": "apad@gmail.com",
        "whatsapp": "13998989898",
        "city": "Rio do Sul",
        "uf": "SC"
    },
    {
        "id": "8d4f46b9",
        "name": "AACD",
        "email": "aacd@gmail.com",
        "whatsapp": "13998989898",
        "city": "São Paulo",
        "uf": "SP"
    }
]
```

### Data Structures

#### Ong (Object)

- name: "APAD" (string, required)
- email: "apad@gmail.com" (string, required)
- whatsapp: 13998989898 (number, required)
- city: "Rio do Sul" (string, required)
- uf: "SC" (string, required)

#### OngInstance (Ong)

- id: "8d4f46b9" (string, required)

-------------------------------------------------------

## Incidentes [/incidents]

### Cadastrar um incidentes [POST]

- Request (application/json)
    - Header (Authorization)
    - Attributes (Incident)
```json
{
	"title": "Caso 34",
	"description": "Detalhes do caso - 8d577961",
	"value": 302
}
```

- Response 200 (application/json)
    - Attributes (IncidentInstance)
```json
{
    "id": 35
}
```    

### Listar todos os incidentes [GET ? {page=1}]

- Response 200 (application/json)
    - Attributes
        - data (array[IncidentesInstance])
```json
[
    {
        "id": 16,
        "title": "Caso 1",
        "description": "Detalhes do caso - 8d577961",
        "value": "400.00",
        "ong_id": "8d577961",
        "name": "APAD",
        "email": "apad@gmail.com",
        "whatsapp": "13998989898",
        "city": "Rio do Sul",
        "uf": "SC"
    },
    .
    .
    .,
    {
        "id": 20,
        "title": "Caso 2",
        "description": "Detalhes do caso - 8d577961",
        "value": "100.00",
        "ong_id": "8d577961",
        "name": "APAD",
        "email": "apad@gmail.com",
        "whatsapp": "13998989898",
        "city": "Rio do Sul",
        "uf": "SC"
    }
]
```

### Deletar um incidente [delete /{id}]

- Parameters
    - Header (Authorization)
    - id (string)

- Response 204

- Response 401 (application/json)
```json
{
    "error": "Operation not permitted."
}
```

### Data Structures

#### Incident (Object)

- title: "Caso 34" (string, required)
- description: "Detalhes do caso - 8d577961" (string, required)
- value: 302 (number, required)

#### Authorization (Ong)

- Authorization: 8d577961 (number, required)

#### IncidentInstance (Incident)

- id: "32" (string, required)

#### IncidentsInstance (Incident)

- id: 20 (number, required)
- title: "Caso 2" (string, required)
- description: "Detalhes do caso - 8d577961" (string, required)
- value: "100.00" (string, required)
- ong_id: "8d577961" (string, required)
- name: "APAD" (string, required)
- email: "apad@gmail.com" (string, required)
- whatsapp: "13998989898" (string, required)
- city: "Rio do Sul" (string, required)
- uf: "SC" (string, required)

---

## Sessão [/sessions]

### Login [POST]

- Request (application/json)
    - Attributes (OngInstance)
```json
{
	"id": "8d577961"
}
```

- Response 200 (application/json)
    - Attributes (NameOng)
```json
{
    "name": "APAD"
}
```

- Response 400 (application/json)
```json
{
    "error": "No ONG found with this ID"
}
```

### Data Structures

#### OngInstance (Object)

- id: "8d577961" (string, required)

#### NameOng (Object)

- name: "APAD" (string, required)

--- 

## Perfil das Ongs [/profile]

### Listar todos os incidentes de uma ong [GET]

- Parameters
    - Header (Authorization)

- Response 200 (application/json)
    - Attributes
        - data (array[IncidentesInstance])
```json
[
    {
        "id": 17,
        "title": "Caso 1",
        "description": "Detalhes do caso - 8d577961",
        "value": "400.00",
        "ong_id": "8d577961"
    },
    .
    .
    .,
    {
        "id": 35,
        "title": "Caso 34",
        "description": "Detalhes do caso - 8d577961",
        "value": "302.00",
        "ong_id": "8d577961"
    }
]
```

### Data Structures

#### Authorization (Ong)

- Authorization: 8d577961 (number, required)

#### IncidentsInstance (Incident)

- id: 20 (number, required)
- title: "Caso 2" (string, required)
- description: "Detalhes do caso - 8d577961" (string, required)
- value: "100.00" (string, required)
- ong_id: "8d577961" (string, required)