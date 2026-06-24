# Exercício 4.1 — API REST de Tarefas

API REST mínima construída com FastAPI para o Módulo 3, Aula 6.

## Como rodar

```bash
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

## Endpoints

| Método | Rota              | Descrição                        |
|--------|-------------------|----------------------------------|
| GET    | `/health`         | Verificação de saúde             |
| POST   | `/tarefas`        | Cria uma tarefa (201)            |
| GET    | `/tarefas`        | Lista todas as tarefas           |
| GET    | `/tarefas/{id}`   | Busca tarefa por ID (404 se não existe) |
| PUT    | `/tarefas/{id}`   | Atualiza tarefa por ID (404 se não existe) |

## Exemplos de uso

```bash
# Criar tarefa
curl -X POST http://localhost:8000/tarefas -H "Content-Type: application/json" -d '{"titulo":"Estudar APIs"}'

# Listar tarefas
curl http://localhost:8000/tarefas

# Atualizar tarefa
curl -X PUT http://localhost:8000/tarefas/1 -H "Content-Type: application/json" -d '{"titulo":"Estudar APIs","concluida":true}'
```

## Contrato

**POST /tarefas**
```json
// body
{ "titulo": "Estudar APIs" }
// response 201
{ "id": 1, "titulo": "Estudar APIs", "concluida": false }
```

**PUT /tarefas/{id}**
```json
// body
{ "titulo": "Estudar APIs", "concluida": true }
// response 200
{ "id": 1, "titulo": "Estudar APIs", "concluida": true }
```
