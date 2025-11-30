# SGHSS – FastAPI (Python)

Back-end mínimo para testes no Postman com **autenticação JWT** e CRUD de **pacientes**.

## Como rodar

```bash
# 1) (opcional) criar venv
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 2) instalar deps
pip install -r requirements.txt

# 3) rodar a API
uvicorn app.main:app --reload
```

A API estará em: `http://127.0.0.1:8000`

## Endpoints principais

- `POST /auth/signup` – cria usuário
- `POST /auth/login` – retorna `{ "token": "<jwt>" }`
- `POST /pacientes` – criar paciente (Bearer)
- `GET /pacientes` – listar (Bearer)
- `GET /pacientes/{id}` – buscar por id (Bearer)
- `PUT /pacientes/{id}` – atualizar (Bearer)
- `DELETE /pacientes/{id}` – excluir (Bearer)

## Variáveis de Ambiente

- `SECRET_KEY` – opcional (string); se não setar, será usado um default inseguro apenas para testes.
- `ACCESS_TOKEN_EXPIRE_MINUTES` – opcional (inteiro, padrão 60).

## Observações (LGPD)

- Senhas armazenadas com hash (BCrypt).
- Rotas protegidas exigem `Authorization: Bearer <token>`.
- Banco local SQLite apenas para fins acadêmicos.
