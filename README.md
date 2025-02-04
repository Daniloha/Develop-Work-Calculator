# Develop-Work-Calculator

Calculadora de valores de projetos para desenvolvedores.

## 📂 Estrutura do Projetoprojeto.sln

```
calculator.sln
│── /calculator.Api           -> API e Configuração
│── /calculator.Application   -> Casos de Uso, Handlers, Perfis do AutoMapper, Serviços e DTOs
│── /calculator.Domain        -> Entidades, VOs, Repositórios (somente interfaces) e Regras de Negócio
│── /calculator.Infrastructure -> Contexto, Implementação dos Repositórios e Configuração do EF Core
│── /calculator.Shared        -> Enums, Requests, Responses, Paginação, etc.
│── /tests
│   │── /calculator.Api.Test        -> Testes da API
│   │── /calculator.Application.Test -> Testes de Casos de Uso e Serviços
│   │── /calculator.Domain.Test      -> Testes de Domínio (Entidades e VOs)
│   │── /calculator.Infrastructure.Test -> Testes do Repositório e Banco de Dados

```



## ✅ Checklist de Desenvolvimento

### 1️⃣ - Criar a Solução e Projetos
1. 🔲 **Criar a solução no .NET**
2. 🔲 **Adicionar os projetos à solução**
3. 🔲 **Configurar referências entre os projetos**

### 2️⃣ - Definir o Domínio (calculator.Domain)
1. 🔲 **Criar Entidades**<br>
2. 🔲 **Criar Value Objects (VOs) se necessário**
3. 🔲 **Criar Interfaces de Repositórios**
4. 🔲 **Criar Exceções de Domínio (DomainException)**
5. 🔲 **Criar Regras de Negócio dentro das entidades**

### 3️⃣ - Criar Casos de Uso (calculator.Application)
1. 🔲 **Criar DTOs**<br>
2. 🔲 **Criar Interfaces de Serviços**
3. 🔲 **Criar Implementação de Serviços**
4. 🔲 **Criar Handlers (se usar CQRS)**
5. 🔲 **Configurar AutoMapper para converter Entidades <-> DTOs**

### 4️⃣ - Implementar a Infraestrutura (calculator.Infrastructure)
1. 🔲 **Criar o DbContext com Entity Framework Core**
2. 🔲 **Criar a Configuração das Entidades com Fluent API**
3. 🔲 **Criar a Implementação dos Repositórios**
4. 🔲 **Criar Migrations e Atualizar o Banco**

### 5️⃣ - Criar a API e Configurar Dependências (calculator.Api)
1. 🔲 **Criar o Program.cs com Minimal API**
2. 🔲 **Configurar Injeção de Dependência (DI)**
3. 🔲 **Adicionar Swagger**
4. 🔲 **Criar Endpoints**
5. 🔲 **Criar Middlewares (tratamento de erro, logs, autenticação, etc.)**
6. 🔲 **Adicionar Autenticação e Autorização**

### 6️⃣ - Criar Testes
#### 🟠 Testes de Unidade
1. **🔲 Criar testes para Entidades e Regras de Negócio (calculator.Domain.Test)**
2. **🔲 Criar testes para Serviços e Casos de Uso (calculator.Application.Test)**

#### 🔵 Testes de Integração
1. 🔲 **Criar testes para Repositórios (calculator.Infrastructure.Test)**
2. 🔲 **Criar testes para Endpoints da API (calculator.Api.Test)**

### 7️⃣ - Configurar CI/CD e Publicação
1. 🔲 **Criar um Dockerfile**
2. 🔲 **Criar um pipeline CI/CD (GitHub Actions ou Azure DevOps)**
3. 🔲 **Publicar a API em um ambiente (ex: Railway, Azure, AWS, Render)**

---

##  Diagrama de Dependências

```
Projeto.Api        --->  Projeto.Application  --->  Projeto.Domain
       |                     |                     |
       v                     v                     v
 Projeto.Infrastructure  Projeto.Shared     Projeto.Shared

```
### Regra geral
* Camadas superiores podem depender de camadas inferiores.
* Camadas inferiores NÃO devem depender das camadas superiores.
* Projeto.Shared pode ser referenciado por qualquer camada, pois contém DTOs, Enums e VOs.

### Regras de dependências do projeto:
* **calculator.Api** depende de calculator.Application, calculator.Infrastructure e calculator.Shared
* **calculator.Application** depende de calculator.Domain e calculator.Shared
* **calculator.Infrastructure** depende de calculator.Domain e calculator.Shared
* **calculator.Domain** depende apenas de calculator.Shared
* **calculator.Shared** pode ser usado por todas as camadas
---
