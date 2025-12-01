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

---

## 🚀 Como Rodar o Projeto

```bash
python -m venv .venv
source .venv/bin/activate       # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

---

## 📌 Principais Endpoints

### 🔐 Autenticação
- POST /auth/signup – cria usuário  
- POST /auth/login – retorna JWT  

### 👥 Pacientes (JWT obrigatório)
- POST /pacientes – criar paciente  
- GET /pacientes – listar  
- GET /pacientes/{id} – buscar por ID  
- PUT /pacientes/{id} – atualizar  
- DELETE /pacientes/{id} – excluir  

### 📅 Consultas (JWT obrigatório)
- POST /consultas – criar  
- GET /consultas – listar  

### ❤️ Saúde
- GET /health – verifica funcionamento  

---

## 🔧 Variáveis de Ambiente (.env)

```
SECRET_KEY=uma_chave_segura
ACCESS_TOKEN_EXPIRE_MINUTES=60
```

---

## 🧪 Como Testar no Postman

1. Criar *environment* com:  
   - base_url = http://localhost:8000  

2. Criar usuário:  
```
POST {{base_url}}/auth/signup
{
  "nome": "Admin Teste",
  "email": "admin@example.com",
  "senha": "Senha123",
  "perfil": "ADMIN"
}
```

3. Login para obter token:  
```
POST {{base_url}}/auth/login
{
  "email": "admin@example.com",
  "senha": "Senha123"
}
```

4. Configurar Bearer Token nas rotas protegidas.  
5. CRUD de pacientes e consultas normalmente.  

---

## 🗂️ Importando Environment e Collection no Postman

Para facilitar os testes, você pode fornecer ao time (ou utilizar você mesma) um **Environment** e uma **Collection** com todas as rotas já configuradas no Postman.

---

## 🌐 1. Importar Environment (Variáveis Globais)

O Environment geralmente contém:

- `base_url`  
- `jwt_token` (armazenado automaticamente após o login)  
- Outras variáveis úteis para testes  

### ➤ Como importar

1. Abra o **Postman**  
2. Vá em **Environments**  
3. Clique em **Import**  
4. Selecione o arquivo:

```
SGHSS.postman_environment.json
```

5. Clique em **Set Active** para ativá-lo  
6. Agora você pode usar:

```
{{base_url}}
```

em todas as requisições.

---

## 📁 2. Importar Collection (Rotas da API)

A Collection contém:

- Rotas de autenticação  
- Rotas protegidas já configuradas com Bearer  
- CRUD completo de Pacientes  
- CRUD de Consultas  
- Rota Health  

### ➤ Como importar

1. No Postman, abra **Collections**  
2. Clique em **Import**  
3. Selecione o arquivo:

```
SGHSS.postman_collection.json
```

4. A Collection aparecerá automaticamente com todas as requisições organizadas.

---

## 🔑 3. Após fazer Login

O token JWT ficará salvo automaticamente na variável:

```
{{jwt_token}}
```

E todas as rotas protegidas já utilizarão:

```
Authorization: Bearer {{jwt_token}}
```

---

## 📚 Observações LGPD

- Senhas com hash BCrypt  
- Uso de Bearer Token  
- Banco SQLite apenas para fins acadêmicos  

---

## ✔ Status

Projeto básico funcionando para testes, estudos e evolução futura.
