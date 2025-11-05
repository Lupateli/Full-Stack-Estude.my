# 🎓 EstudeMy - Backend


O EstudeMy é uma plataforma de estudos gamificada, criada para tornar o aprendizado mais dinâmico e envolvente para jovens e estudantes.
Professores podem disponibilizar seus cursos, aulas e conteúdos personalizados, enquanto alunos exploram diferentes trilhas de aprendizado, acumulam pontos, conquistas e medalhas conforme avançam nos estudos.

---

## 🔗 Índice

- [🎓 EstudeMy - Backend](#-estudemy---backend)
  - [🔗 Índice](#-índice)
  - [📝 Sobre o Projeto](#-sobre-o-projeto)
  - [🏗️ Arquitetura do Sistema](#️-arquitetura-do-sistema)
  - [📋 Casos de uso](#-casos-de-uso)
  - [⚙️ Tecnologias Utilizadas](#️-tecnologias-utilizadas)
    - [Backend](#backend)
    - [DevOps](#devops)
  - [🚀 Como Executar Localmente](#-como-executar-localmente)
    - [Pré-requisitos](#pré-requisitos)
    - [1️⃣ Clone o repositório](#1️⃣-clone-o-repositório)
    - [2️⃣ Configure as variáveis de ambiente](#2️⃣-configure-as-variáveis-de-ambiente)
    - [3️⃣ Instale as dependências](#3️⃣-instale-as-dependências)
    - [4️⃣ Execute o servidor](#4️⃣-execute-o-servidor)
    - [5️⃣ Acesse a documentação](#5️⃣-acesse-a-documentação)
  - [📡 Endpoints da API](#-endpoints-da-api)
  - [🔐 Autenticação](#-autenticação)
    - [🔑 API Key (entre microsserviços)](#-api-key-entre-microsserviços)
    - [🧩 JWT (para endpoints protegidos)](#-jwt-para-endpoints-protegidos)
  - [📋 Variáveis de Ambiente](#-variáveis-de-ambiente)
  - [📅 Planejamento e Sprints](#-planejamento-e-sprints)
  - [👨‍💻 Colaboradores](#-colaboradores)
  - [📝 Licença](#-licença)

---

## 📝 Sobre o Projeto

O **EstudeMy** é uma plataforma de estudos gamificada, desenvolvida para incentivar o aprendizado de forma interativa e divertida.
A aplicação fornece uma API RESTful completa que gerencia usuários, cursos, progresso e interações entre alunos e professores.

O backend garante segurança, escalabilidade e integração simples com o frontend desenvolvido em React/Next.js, permitindo que o sistema evolua continuamente com novas funcionalidades educacionais.

Principais recursos:

- Cadastro e autenticação de usuários (alunos e professores)
- CRUD de cursos, aulas e trilhas de aprendizado
- Sistema de pontuação e conquistas gamificadas
- Monitoramento de progresso e desempenho dos alunos
- Integração com banco de dados MongoDB
- Documentação interativa via Swagger UI
- Hospedagem e deploy automatizado em nuvem

---

## 🏗️ Arquitetura do Sistema

```
┌───────────────────┐        ┌───────────────────┐
│   Auth Controller │◄──────►│  User Controller  │
└────────┬──────────┘        └────────┬──────────┘
         │                             │
         └──────────────┬──────────────┘
                        │
               ┌────────▼────────┐
               │    MongoDB      │
               └─────────────────┘
```

**Padrão utilizado:** Arquitetura MVC (Model - View - Controller)

## 📋 Casos de uso

![Casos de uso](https://github.com/EstudeMy/EstudeMyBackendNode/blob/main/image.png)

---

📋 Requisitos do Sistema
⚙️ Requisitos Funcionais

👤 Gestão de Usuários

RF01 – Cadastrar Usuário

Validar o formato do e-mail;
Verificar se o e-mail já está cadastrado.
Ações pós-cadastro:
Enviar e-mail de confirmação;
Redirecionar para a página de login;
Exibir mensagem de sucesso.

RF02 – Autenticar Usuário

Redirecionar para a página principal;

Iniciar uma sessão de usuário.
RF03 – Gerenciar Perfil

Detalhes: Permitir que usuários visualizem e editem seus dados pessoais (nome, e-mail, senha, foto de perfil etc.).
Validações: Validar os novos dados (formato de e-mail, critérios de senha, etc.).
Ações pós-atualização: Exibir mensagem de sucesso e atualizar os dados no banco de dados.

RF04 – Recuperar Senha

Detalhes: Permitir que os usuários recuperem suas senhas caso as tenham esquecido.
Fluxo: Enviar um e-mail com link para redefinição de senha.

RF05 – Desativar Conta

Detalhes: Permitir que os usuários desativem suas contas.
Confirmação: Solicitar confirmação antes da desativação.

📚 Gestão de Conteúdo
RF06 – Cadastrar Trilha

Detalhes: Professores podem cadastrar trilhas de aprendizado com nome, descrição, nível, categoria e outros atributos relevantes.

RF07 – Cadastrar Curso

Detalhes: Professores podem cadastrar cursos dentro de uma trilha com nome, descrição, carga horária e outros atributos.

RF08 – Cadastrar Lição

Detalhes: Professores podem cadastrar lições dentro de um curso, definindo título, conteúdo (texto, vídeo, quiz, etc.) e outros atributos.

RF09 – Visualizar Trilha

Detalhes: Alunos podem visualizar as trilhas disponíveis na plataforma.

RF10 – Visualizar Curso

Detalhes: Alunos podem visualizar os cursos dentro de uma trilha.

RF11 – Visualizar Lição

Detalhes: Alunos podem visualizar as lições dentro de um curso.

🏆 Gamificação
RF12 – Sistema de Pontuação

Detalhes: Atribuir pontos aos alunos por completar lições, cursos, trilhas, participar de desafios, etc.

RF13 – Sistema de Badges

Detalhes: Conceder badges aos alunos por conquistas e marcos de progresso.

RF14 – Ranking

Detalhes: Exibir ranking dos alunos com maiores pontuações.

RF15 – Desafios

Detalhes: Permitir que professores criem desafios com recompensas em pontos e badges.

💬 Interação e Comunicação
RF16 – Notificações

Detalhes: Enviar notificações sobre novas trilhas, cursos, lições, desafios e mensagens.

RF17 – Comentários

Detalhes: Permitir que alunos e professores comentem em lições, cursos e trilhas.

📈 Relatórios
RF18 – Relatórios de Progresso

Detalhes: Gerar relatórios de progresso dos alunos, mostrando desempenho em trilhas, cursos e lições.

RF19 – Relatórios de Desempenho

Detalhes: Gerar relatórios de desempenho dos professores, mostrando engajamento dos alunos em suas trilhas e cursos.

🔒 Requisitos Não Funcionais
⚡ Desempenho

RNF01: O sistema deve carregar as páginas em no máximo 3 segundos.

RNF02: Suportar até 1000 usuários simultâneos.

🔐 Segurança

RNF03: As senhas devem ser armazenadas de forma criptografada.

RNF04: Proteger dados contra acesso não autorizado.

RNF05: Implementar prevenção contra SQL Injection e XSS.

📈 Escalabilidade

RNF06: O sistema deve suportar crescimento de usuários e conteúdo.

🌐 Compatibilidade

RNF07: Compatível com os principais navegadores (Chrome, Firefox, Safari, Edge).

♿ Acessibilidade

RNF08: Seguir diretrizes WCAG para acessibilidade.

🧭 Usabilidade

RNF09: Interface intuitiva e fácil de usar.

RNF10: Navegação consistente e eficiente.

RNF11: Elementos de gamificação devem ser motivadores e engajadores.

🧩 Manutenibilidade

RNF12: Arquitetura modular e organizada para facilitar manutenção.

RNF13: Código bem documentado e seguindo boas práticas.

📱 Portabilidade

RNF14: Acesso via dispositivos móveis (smartphones e tablets).

---

## ⚙️ Tecnologias Utilizadas

### Backend
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![Mongoose](https://img.shields.io/badge/Mongoose-800000?style=for-the-badge)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Bcrypt](https://img.shields.io/badge/Bcrypt-004085?style=for-the-badge)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
![CORS](https://img.shields.io/badge/CORS-00599C?style=for-the-badge&logo=cors&logoColor=white)


### DevOps
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

---

## 🚀 Como Executar Localmente

### Pré-requisitos
- Node.js 18+  
- MongoDB (local ou Atlas)  
- Git  

### 1️⃣ Clone o repositório
```bash
git clone https://github.com/EstudeMy/EstudeMyBackendNode.git
cd EstudeMyBackendNode
```

### 2️⃣ Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto:

```env
PORT=5000
MONGO_URL=mongodb+srv://usuario:senha@cluster.mongodb.net/estudemy
JWT_SECRET=chave_super_segura_aqui
API_KEY=estudemy_api_key_2025
```

### 3️⃣ Instale as dependências
```bash
npm install
```

### 4️⃣ Execute o servidor
```bash
node src/server.js
```

### 5️⃣ Acesse a documentação
A documentação Swagger estará disponível em:  
👉 http://localhost:5000/api-docs

---

## 📡 Endpoints da API

| Método | Endpoint | Descrição | Autenticação |
|--------|----------|-----------|--------------|
| POST | `/api/auth/register` | Cadastrar novo usuário | ❌ |
| POST | `/api/auth/login` | Login (gera token JWT) | ❌ |
| GET | `/api/users` | Listar todos os usuários | ✅ |
| GET | `/api/users/:id` | Buscar usuário por ID | ✅ |
| PUT | `/api/users/:id` | Atualizar dados do usuário | ✅ |
| DELETE | `/api/users/:id` | Deletar usuário | ✅ |

---

## 🔐 Autenticação

### 🔑 API Key (entre microsserviços)
Adicione o header:
```http
x-api-key: estudemy_api_key_2025
```

### 🧩 JWT (para endpoints protegidos)
```http
Authorization: Bearer <seu_token_jwt>
```

---

## 📋 Variáveis de Ambiente

| Nome | Descrição | Exemplo |
|------|------------|---------|
| PORT | Porta de execução | 5000 |
| MONGO_URL | URL do banco MongoDB | mongodb+srv://usuario:senha@cluster.mongodb.net/estudemy |
| JWT_SECRET | Chave usada na geração dos tokens | super_secret_key |
| API_KEY | Chave de comunicação entre serviços | estudemy_api_key_2025 |

---

## 📅 Planejamento e Sprints

| 🏁 Sprint | 📆 Período | 🎯 Atividades | 📊 Status |
|:---------:|:-----------:|:--------------|:-----------:|
| **Sprint 1** | 15/09/2025 – 29/09/2025 | Criação do banco e autenticação inicial | ✅ Concluída |
| **Sprint 2** | 30/09/2025 – 13/10/2025 | CRUD de usuários e cursos | ✅ Concluída |
| **Sprint 3** | 14/10/2025 – 28/11/2025 | Integração com frontend e testes no Postman | 🕓 Em andamento |
| **Sprint 4** | 29/10/2025 – 12/11/2025 | Deploy, documentação e melhorias finais | 🚀 Planejada |

---

## 👨‍💻 Colaboradores

| Nome | Função |
|------|---------|
| João Milone | 💻 Frontend - Backend Developer |
| João Quaresma | 💻 Frontend - Backend Developer |
| Gabriel Lupateli | 👨‍💻 Product Owner|
| Beatriz Siqueira | 👩‍💻 Scrum Master|
| Wallacy José | 🧑‍💻 Frontend Devoloper |

---



## 📝 Licença

Este projeto está sob a licença **MIT** — veja o arquivo `LICENSE` para mais detalhes.

---

💙 Desenvolvido com dedicação pela equipe **EstudeMy**
