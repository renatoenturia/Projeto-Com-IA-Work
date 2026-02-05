# Product Requirements Document (PRD)
## Sistema de Gerenciamento de Usuários e Contatos

**Versão:** 1.0  
**Data:** 2024  
**Status:** Em Desenvolvimento

---

## 1. Visão Geral

### 1.1. Descrição do Produto
Aplicação Fullstack para gerenciamento de usuários e seus contatos associados. O sistema permite o cadastro e gerenciamento de usuários com seus dados básicos, além de gerenciar contatos (e-mail e telefone celular) vinculados a cada usuário.

### 1.2. Objetivos
- Fornecer uma interface completa para gerenciamento de usuários
- Permitir o cadastro e gerenciamento de múltiplos contatos por usuário
- Oferecer uma experiência de usuário moderna e intuitiva através do Filament PHP
- Garantir qualidade de código através de ferramentas de QA automatizadas

---

## 2. Requisitos Funcionais

### 2.1. Gerenciamento de Usuários
- **RF-001:** O sistema deve permitir criar, ler, atualizar e excluir (CRUD) usuários
- **RF-002:** Cada usuário deve possuir dados básicos (nome, e-mail, etc.)
- **RF-003:** O sistema deve exibir uma listagem de todos os usuários cadastrados

### 2.2. Gerenciamento de Contatos
- **RF-004:** O sistema deve permitir criar, ler, atualizar e excluir (CRUD) contatos
- **RF-005:** Cada contato deve estar vinculado a um usuário específico
- **RF-006:** Um usuário pode ter múltiplos contatos associados
- **RF-007:** Os contatos devem suportar dois tipos:
  - E-mail
  - Telefone celular
- **RF-008:** O sistema deve exibir uma listagem de todos os contatos cadastrados

### 2.3. Dashboard
- **RF-009:** O sistema deve exibir um dashboard básico com informações relevantes
- **RF-010:** O dashboard deve fornecer visão geral do sistema

---

## 3. Requisitos Técnicos

### 3.1. Stack Tecnológico

#### Backend
- **Framework:** Laravel (versão mais recente)
- **Linguagem:** PHP 8.4.16
- **Banco de Dados:** MySQL
- **Instalação do Banco:** HerdMCP

#### Frontend
- **Framework de Interface:** Filament PHP
- **Interface:** Totalmente desenvolvida utilizando Filament PHP

### 3.2. Arquitetura
- Aplicação Laravel pura (sem frameworks frontend adicionais)
- Interface de usuário completamente desenvolvida com Filament PHP
- Arquitetura MVC padrão do Laravel

### 3.3. Modelo de Dados

#### Entidade: Usuário
- ID (chave primária)
- Nome
- E-mail
- Outros dados básicos conforme necessário
- Relacionamento: Um usuário possui muitos contatos (1:N)

#### Entidade: Contato
- ID (chave primária)
- Tipo (E-mail ou Telefone Celular)
- Valor (conteúdo do contato)
- Usuário ID (chave estrangeira)
- Relacionamento: Muitos contatos pertencem a um usuário (N:1)

---

## 4. Fase 1: Configuração de QA (Quality Assurance)

### 4.1. Laravel Pint
- **RT-001:** Laravel Pint deve estar instalado e configurado
- **RT-002:** Deve existir um script no `composer.json` para executar o Laravel Pint
- **RT-003:** O Pint deve formatar o código seguindo os padrões do Laravel

### 4.2. PHPStan
- **RT-004:** PHPStan deve estar instalado e configurado
- **RT-005:** Deve existir um script no `composer.json` para executar o PHPStan
- **RT-006:** Todos os problemas apontados pelo PHPStan devem ser corrigidos
- **RT-007:** O PHPStan deve ser executado e validado antes de prosseguir

### 4.3. Script de Quality Check
- **RT-008:** Deve ser criado um script geral chamado "Quality Check" no `composer.json`
- **RT-009:** O script deve executar, em sequência:
  1. Laravel Pint (formatação)
  2. PHPStan (análise estática)
  3. Testes (Pest)

### 4.4. Git Hooks com Husky
- **RT-010:** Husky deve ser instalado via npm
- **RT-011:** Deve ser criado um hook `pre-commit` que:
  - Executa o Laravel Pint para formatação automática antes do commit
- **RT-012:** Deve ser criado um hook `pre-push` que:
  - Executa o script geral de Quality Check (Pint + PHPStan + Testes)

---

## 5. Critérios de Aceitação

### 5.1. Fase 1 - QA
- [ ] Laravel Pint instalado, configurado e com script no `composer.json`
- [ ] PHPStan instalado, configurado e com script no `composer.json`
- [ ] Todos os problemas do PHPStan corrigidos
- [ ] Script "Quality Check" criado e funcional
- [ ] Husky instalado e configurado
- [ ] Hook `pre-commit` funcionando corretamente
- [ ] Hook `pre-push` funcionando corretamente

### 5.2. Funcionalidades Principais
- [ ] CRUD completo de usuários implementado e funcional
- [ ] CRUD completo de contatos implementado e funcional
- [ ] Dashboard básico implementado e exibindo informações relevantes
- [ ] Relacionamento usuário-contato funcionando corretamente
- [ ] Validação de tipos de contato (e-mail e telefone celular) implementada
- [ ] Interface desenvolvida completamente com Filament PHP

---

## 6. Ferramentas e Recursos

### 6.1. Ferramentas de Desenvolvimento
- **Laravel Boost MCP:** Utilizado para buscar informações sobre implementação, melhores práticas e documentação do Laravel
- **HerdMCP:** Utilizado para instalação e configuração do banco de dados MySQL
- **Laravel Pint:** Formatação automática de código
- **PHPStan:** Análise estática de código
- **Pest:** Framework de testes
- **Husky:** Gerenciamento de Git hooks

### 6.2. Documentação
- Para qualquer detalhe de implementação, melhores práticas ou dúvidas técnicas, utilizar o MCP Laravel Boost para buscar informações necessárias

---

## 7. Ordem de Implementação

### Fase 1: Configuração de QA (Prioridade Alta)
1. Verificar/Instalar Laravel Pint
2. Configurar Laravel Pint
3. Criar script no `composer.json` para Pint
4. Instalar PHPStan
5. Configurar PHPStan
6. Criar script no `composer.json` para PHPStan
7. Executar PHPStan e corrigir problemas
8. Criar script "Quality Check" no `composer.json`
9. Instalar Husky via npm
10. Criar hook `pre-commit`
11. Criar hook `pre-push`
12. Testar todos os hooks

### Fase 2: Desenvolvimento do Backend (Após Fase 1)
1. Criar migrations para tabelas de usuários e contatos
2. Criar models com relacionamentos
3. Criar factories e seeders
4. Implementar validações

### Fase 3: Desenvolvimento do Frontend com Filament (Após Fase 2)
1. Instalar e configurar Filament PHP
2. Criar Resource para Usuários
3. Criar Resource para Contatos
4. Criar Dashboard básico
5. Configurar relacionamentos no Filament

### Fase 4: Testes e Validação (Após Fase 3)
1. Criar testes para models
2. Criar testes para relacionamentos
3. Criar testes para Resources do Filament
4. Validar todas as funcionalidades

---

## 8. Notas Técnicas

### 8.1. Convenções de Código
- Seguir as convenções do Laravel
- Utilizar as melhores práticas do PHP 8.4
- Seguir os padrões definidos pelo Laravel Pint

### 8.2. Banco de Dados
- Utilizar migrations do Laravel para versionamento do banco
- Implementar relacionamentos através do Eloquent ORM
- Garantir integridade referencial

### 8.3. Segurança
- Implementar validação adequada em todos os formulários
- Proteger rotas conforme necessário
- Sanitizar dados de entrada

---

## 9. Definições e Glossário

- **CRUD:** Create, Read, Update, Delete (Criar, Ler, Atualizar, Excluir)
- **QA:** Quality Assurance (Garantia de Qualidade)
- **MCP:** Model Context Protocol
- **HerdMCP:** Ferramenta para gerenciamento de banco de dados MySQL
- **Filament PHP:** Framework de interface administrativa para Laravel
- **PHPStan:** Ferramenta de análise estática de código PHP
- **Husky:** Ferramenta para gerenciar Git hooks

---

## 10. Histórico de Versões

| Versão | Data | Descrição | Autor |
|--------|------|-----------|-------|
| 1.0 | 2024 | Versão inicial do PRD | - |

---

**Documento criado para:** Sistema de Gerenciamento de Usuários e Contatos  
**Última atualização:** 2024
