# Contexto do Projeto: Sistema de Gerenciamento de Usuários e Contatos

## Visão Geral

Este é um projeto Laravel 12 desenvolvido para gerenciamento de usuários e seus contatos associados. O sistema permite o cadastro e gerenciamento completo de usuários com seus dados básicos, além de gerenciar múltiplos contatos (e-mail e telefone celular) vinculados a cada usuário.

## Stack Tecnológica

### Backend
- **Framework:** Laravel 12
- **Linguagem:** PHP 8.4.16
- **Banco de Dados:** MySQL (gerenciado via HerdMCP)
- **ORM:** Eloquent
- **Arquitetura:** MVC padrão do Laravel

### Frontend
- **Framework de Interface:** Filament PHP (a ser implementado)
- **Build Tool:** Vite 7
- **CSS Framework:** Tailwind CSS 4
- **JavaScript:** Vanilla JS com Axios

### Ferramentas de Desenvolvimento
- **Testes:** Pest PHP 4
- **Formatação de Código:** Laravel Pint
- **Análise Estática:** PHPStan
- **Git Hooks:** Husky (a ser configurado)
- **MCP Tools:** Laravel Boost MCP, HerdMCP

## Estrutura do Projeto

### Modelo de Dados

#### Entidade: Usuário (User)
- ID (chave primária)
- Nome (name)
- E-mail (email) - único
- Senha (password) - hasheada
- Email verificado (email_verified_at)
- Remember token
- Timestamps (created_at, updated_at)
- **Relacionamento:** Um usuário possui muitos contatos (1:N)

#### Entidade: Contato (Contact) - A ser implementado
- ID (chave primária)
- Tipo (type) - E-mail ou Telefone Celular
- Valor (value) - conteúdo do contato
- Usuário ID (user_id) - chave estrangeira
- Timestamps
- **Relacionamento:** Muitos contatos pertencem a um usuário (N:1)

## Funcionalidades Principais

### Gerenciamento de Usuários (CRUD)
- Criar novos usuários
- Listar todos os usuários
- Visualizar detalhes de um usuário
- Atualizar informações de usuários
- Excluir usuários

### Gerenciamento de Contatos (CRUD) - A ser implementado
- Criar novos contatos vinculados a usuários
- Listar todos os contatos
- Visualizar detalhes de um contato
- Atualizar informações de contatos
- Excluir contatos
- Suporte para dois tipos de contato:
  - E-mail
  - Telefone celular

### Dashboard - A ser implementado
- Visão geral do sistema
- Informações relevantes e estatísticas

## Estado Atual do Projeto

### Implementado
- ✅ Estrutura base do Laravel 12
- ✅ Modelo User com autenticação básica
- ✅ Migrations para tabela de usuários
- ✅ Factory para User
- ✅ Configuração de testes com Pest
- ✅ Configuração de Vite com Tailwind CSS 4
- ✅ Estrutura de rotas básica

### Em Desenvolvimento / Planejado
- ⏳ Configuração completa de QA (Laravel Pint, PHPStan, Husky)
- ⏳ Modelo Contact e migration
- ⏳ Relacionamento User-Contact
- ⏳ Instalação e configuração do Filament PHP
- ⏳ Resources do Filament para Usuários
- ⏳ Resources do Filament para Contatos
- ⏳ Dashboard com Filament
- ⏳ Validações de formulários
- ⏳ Testes completos (Feature e Unit)

## Estrutura de Diretórios

```
user-contact/
├── app/
│   ├── Http/
│   │   └── Controllers/
│   ├── Models/
│   │   └── User.php
│   └── Providers/
├── database/
│   ├── factories/
│   ├── migrations/
│   └── seeders/
├── docs/
│   └── PRD.md
├── resources/
│   ├── css/
│   ├── js/
│   └── views/
├── routes/
│   ├── web.php
│   └── console.php
└── tests/
    ├── Feature/
    └── Unit/
```

## Fases de Desenvolvimento

### Fase 1: Configuração de QA (Prioridade Alta)
- Configurar Laravel Pint
- Configurar PHPStan
- Criar script "Quality Check" no composer.json
- Instalar e configurar Husky
- Criar hooks pre-commit e pre-push

### Fase 2: Desenvolvimento do Backend
- Criar migration para tabela de contatos
- Criar modelo Contact com relacionamentos
- Criar factories e seeders
- Implementar validações

### Fase 3: Desenvolvimento do Frontend com Filament
- Instalar e configurar Filament PHP
- Criar Resource para Usuários
- Criar Resource para Contatos
- Criar Dashboard básico
- Configurar relacionamentos no Filament

### Fase 4: Testes e Validação
- Criar testes para models
- Criar testes para relacionamentos
- Criar testes para Resources do Filament
- Validar todas as funcionalidades

## Convenções e Padrões

- Seguir as convenções do Laravel
- Utilizar as melhores práticas do PHP 8.4
- Seguir os padrões definidos pelo Laravel Pint
- Utilizar migrations do Laravel para versionamento do banco
- Implementar relacionamentos através do Eloquent ORM
- Garantir integridade referencial
- Implementar validação adequada em todos os formulários

## Documentação de Referência

- **PRD:** `docs/PRD.md` - Documento completo de requisitos do produto
- **Laravel Boost MCP:** Utilizado para buscar informações sobre implementação e melhores práticas
- **HerdMCP:** Utilizado para gerenciamento do banco de dados MySQL

## Scripts Disponíveis

- `composer run dev` - Inicia servidor, queue e Vite simultaneamente
- `composer run test` - Executa os testes com Pest
- `npm run build` - Compila assets para produção
- `npm run dev` - Inicia Vite em modo desenvolvimento

## Ambiente de Desenvolvimento

- **Servidor Web:** Laravel Herd
- **URL Base:** `https://user-contact.test` (via Herd)
- **Banco de Dados:** MySQL (via HerdMCP)
- **Ambiente:** Desenvolvimento local

## Notas Importantes

- O projeto está em estágio inicial de desenvolvimento
- A interface será completamente desenvolvida com Filament PHP (sem frameworks frontend adicionais)
- O foco inicial está na configuração de ferramentas de QA antes do desenvolvimento das funcionalidades principais
- Todos os detalhes de implementação devem seguir as melhores práticas do Laravel e PHP 8.4
