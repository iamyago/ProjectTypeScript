# 📌 Voll - API de Avaliações

API desenvolvida em **Node.js + TypeScript**, responsável por gerenciar **autenticação** e **avaliações** dentro da plataforma Voll.  
Ela permite que usuários autenticados enviem feedback/avaliações e que administradores possam gerenciar esses registros.

---

## 🚀 Tecnologias Utilizadas

| Tecnologia | Descrição |
|-----------|-----------|
| Node.js | Ambiente de execução |
| TypeScript | Tipagem estática para JavaScript |
| Express | Framework para criação da API |
| JWT (JSON Web Token) | Autenticação e autorização |
| Docker (opcional) | Contêinerização do ambiente |
| Banco de Dados | Pode ser configurado (PostgreSQL, MySQL, MongoDB, etc.) |

---

## 📂 Estrutura do Projeto

```
server/
  src/
    auth/
      login.ts
      authRoutes.ts
      verificaTokenJWT.ts
      roles.ts
      authEntity.ts
      IAutencavel.ts
    avaliacoes/
      avaliacoesController.ts
      avaliacoesRoutes.ts
      avaliacoesEntity.ts
  package.json
  Dockerfile
  docker-compose.yml
```

---

## 🔐 Autenticação & Autorização

A API utiliza:

- **JWT** para autenticação
- **Roles** para definição de permissões

Fluxo de login:

1. Usuário envia email e senha → `/login`
2. Se credenciais forem válidas → API gera **token JWT**
3. O token deve ser enviado no **header Authorization** em todas as rotas protegidas:

```
Authorization: Bearer SEU_TOKEN_AQUI
```

---

## 📝 Rotas Principais

### **Autenticação**

| Método | Rota     | Descrição |
|--------|---------|-----------|
| POST   | `/login` | Gera token JWT para acesso às rotas protegidas |

**Exemplo de requisição:**

```bash
curl -X POST http://localhost:3000/login   -H "Content-Type: application/json"   -d '{"email": "usuario@teste.com", "senha": "123456"}'
```

---

### **Avaliações**

| Método | Rota                     | Descrição |
|--------|--------------------------|-----------|
| GET    | `/avaliacoes`            | Lista todas as avaliações |
| POST   | `/avaliacoes`            | Cria uma nova avaliação |
| PUT    | `/avaliacoes/:id`        | Atualiza uma avaliação existente |
| DELETE | `/avaliacoes/:id`        | Remove uma avaliação |

**Exemplo de criação de avaliação:**

```bash
curl -X POST http://localhost:3000/avaliacoes   -H "Authorization: Bearer SEU_TOKEN"   -H "Content-Type: application/json"   -d '{"nota": 4, "descricao": "Atendimento excelente"}'
```

---

## 🏗 Banco de Dados

O projeto **ainda não possui** banco configurado.

Opções recomendadas:

| Banco | Por quê? |
|------|----------|
| PostgreSQL | Seguro, robusto, usado em produção |
| MySQL/MariaDB | Popular e fácil de configurar |
| MongoDB | Flexível para modelos não relacionais |

Se quiser, posso **configurar automaticamente o banco + ORM + migrations**.  
Basta responder:

```
Escolho: PostgreSQL
```

ou

```
Escolho: MongoDB
```

---

## ▶️ Como Executar

### Usando Node

```bash
cd server
npm install
npm run dev
```

### Usando Docker

```bash
docker-compose up --build
```

---

## 🤝 Contribuição

1. Faça um fork
2. Crie uma branch: `git checkout -b minha-modificacao`
3. Commit: `git commit -m "Minha alteração"`
4. Push: `git push origin minha-modificacao`
5. Abra um Pull Request

---

## Autor

Baseado no curso e projeto de TypeScript da Alura.

