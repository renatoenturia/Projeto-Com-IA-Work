# Lista de Tarefas - Sistema de Gerenciamento de Usuários e Contatos

**Projeto:** user-contact  
**Framework:** Laravel 12  
**Status Geral:** 🟡 Em Desenvolvimento

---

## 📋 Índice

- [Fase 1: Configuração de QA](#fase-1-configuração-de-qa-prioridade-alta)
- [Fase 2: Desenvolvimento do Backend](#fase-2-desenvolvimento-do-backend)
- [Fase 3: Desenvolvimento do Frontend com Filament](#fase-3-desenvolvimento-do-frontend-com-filament)
- [Fase 4: Testes e Validação](#fase-4-testes-e-validação)
- [Tarefas Adicionais](#tarefas-adicionais)

---

## 🎯 Fase 1: Configuração de QA (Prioridade Alta)

### 1.1 Laravel Pint
- [ ] Verificar se Laravel Pint está instalado (já está em `require-dev`)
- [ ] Configurar arquivo de configuração do Laravel Pint (`.pint.json` ou `pint.json`)
- [ ] Criar script no `composer.json` para executar o Pint
  - [ ] Script `pint` para formatação
  - [ ] Script `pint:test` para verificar sem modificar
- [ ] Executar Pint em todo o projeto e corrigir formatação
- [ ] Documentar uso do Pint no README

### 1.2 PHPStan
- [ ] Instalar PHPStan via Composer (`composer require --dev phpstan/phpstan`)
- [ ] Criar arquivo de configuração `phpstan.neon` ou `phpstan.dist.neon`
- [ ] Configurar níveis de análise apropriados
- [ ] Criar script no `composer.json` para executar o PHPStan
- [ ] Executar PHPStan e corrigir todos os problemas apontados
- [ ] Validar que não há erros antes de prosseguir

### 1.3 Script de Quality Check
- [ ] Criar script `quality-check` no `composer.json`
- [ ] O script deve executar em sequência:
  1. Laravel Pint (formatação)
  2. PHPStan (análise estática)
  3. Testes Pest (validação)
- [ ] Testar o script completo
- [ ] Documentar uso do script

### 1.4 Git Hooks com Husky
- [ ] Instalar Husky via npm (`npm install --save-dev husky`)
- [ ] Inicializar Husky (`npx husky init`)
- [ ] Criar hook `pre-commit`:
  - [ ] Executar Laravel Pint automaticamente antes do commit
  - [ ] Testar o hook
- [ ] Criar hook `pre-push`:
  - [ ] Executar script `quality-check` completo (Pint + PHPStan + Testes)
  - [ ] Testar o hook
- [ ] Documentar os hooks no README

**Status da Fase 1:** 🔴 Não Iniciada

---

## 🗄️ Fase 2: Desenvolvimento do Backend

### 2.1 Migrations
- [ ] Verificar migration de usuários existente
- [ ] Criar migration para tabela `contacts`:
  - [ ] Campo `id` (chave primária)
  - [ ] Campo `type` (enum: 'email', 'phone')
  - [ ] Campo `value` (string)
  - [ ] Campo `user_id` (foreign key para users)
  - [ ] Timestamps (`created_at`, `updated_at`)
  - [ ] Índices apropriados
- [ ] Executar migrations
- [ ] Verificar estrutura do banco de dados

### 2.2 Models e Relacionamentos
- [ ] Criar model `Contact`:
  - [ ] Definir `$fillable`
  - [ ] Definir `$casts` (se necessário)
  - [ ] Criar relacionamento `belongsTo(User::class)`
- [ ] Atualizar model `User`:
  - [ ] Adicionar relacionamento `hasMany(Contact::class)`
- [ ] Testar relacionamentos no Tinker

### 2.3 Factories e Seeders
- [ ] Criar `ContactFactory`:
  - [ ] Gerar dados aleatórios para `type` e `value`
  - [ ] Associar a usuários aleatórios
- [ ] Atualizar `UserFactory` se necessário
- [ ] Criar `ContactSeeder`:
  - [ ] Criar contatos de exemplo
- [ ] Atualizar `DatabaseSeeder`:
  - [ ] Chamar `ContactSeeder`
- [ ] Executar seeders e verificar dados

### 2.4 Validações
- [ ] Criar Form Request `StoreContactRequest`:
  - [ ] Validar `type` (required, in:email,phone)
  - [ ] Validar `value` (required, string)
    - [ ] Se `type` = email: validar formato de email
    - [ ] Se `type` = phone: validar formato de telefone
  - [ ] Validar `user_id` (required, exists:users,id)
- [ ] Criar Form Request `UpdateContactRequest`
- [ ] Criar Form Request `StoreUserRequest` (se necessário)
- [ ] Criar Form Request `UpdateUserRequest` (se necessário)

**Status da Fase 2:** 🔴 Não Iniciada

---

## 🎨 Fase 3: Desenvolvimento do Frontend com Filament

### 3.1 Instalação e Configuração do Filament
- [ ] Instalar Filament PHP (`composer require filament/filament:"^3.2"`)
- [ ] Publicar configurações do Filament
- [ ] Configurar painel administrativo
- [ ] Criar usuário administrador inicial
- [ ] Acessar painel e verificar funcionamento

### 3.2 Resource para Usuários
- [ ] Criar Resource `UserResource`:
  - [ ] Configurar tabela de listagem
  - [ ] Configurar formulário de criação
  - [ ] Configurar formulário de edição
  - [ ] Adicionar filtros (se necessário)
  - [ ] Adicionar ações em massa (se necessário)
- [ ] Testar CRUD completo de usuários
- [ ] Personalizar campos e validações

### 3.3 Resource para Contatos
- [ ] Criar Resource `ContactResource`:
  - [ ] Configurar tabela de listagem
  - [ ] Configurar formulário de criação
  - [ ] Configurar formulário de edição
  - [ ] Adicionar relacionamento com User (select/relationship)
  - [ ] Adicionar filtros (por usuário, por tipo)
  - [ ] Adicionar ações em massa (se necessário)
- [ ] Testar CRUD completo de contatos
- [ ] Personalizar campos e validações
- [ ] Implementar validação condicional (email vs telefone)

### 3.4 Dashboard
- [ ] Criar widget de estatísticas:
  - [ ] Total de usuários
  - [ ] Total de contatos
  - [ ] Contatos por tipo (email vs telefone)
- [ ] Criar gráficos (se necessário):
  - [ ] Distribuição de contatos por tipo
  - [ ] Usuários mais recentes
- [ ] Personalizar layout do dashboard
- [ ] Testar visualização do dashboard

### 3.5 Relacionamentos no Filament
- [ ] Configurar relacionamento User -> Contacts no UserResource:
  - [ ] Adicionar tabela de contatos na página de detalhes do usuário
  - [ ] Permitir criar contatos diretamente do usuário
- [ ] Configurar relacionamento Contact -> User no ContactResource:
  - [ ] Exibir informações do usuário relacionado
- [ ] Testar navegação entre recursos relacionados

**Status da Fase 3:** 🔴 Não Iniciada

---

## 🧪 Fase 4: Testes e Validação

### 4.1 Testes de Models
- [ ] Criar teste `UserTest`:
  - [ ] Testar criação de usuário
  - [ ] Testar relacionamento com contatos
  - [ ] Testar validações do model
- [ ] Criar teste `ContactTest`:
  - [ ] Testar criação de contato
  - [ ] Testar relacionamento com usuário
  - [ ] Testar validações do model
  - [ ] Testar validação de tipo (email vs telefone)

### 4.2 Testes de Relacionamentos
- [ ] Testar que um usuário pode ter múltiplos contatos
- [ ] Testar que um contato pertence a um usuário
- [ ] Testar exclusão em cascata (se configurado)
- [ ] Testar integridade referencial

### 4.3 Testes de Resources do Filament
- [ ] Criar testes para UserResource:
  - [ ] Testar listagem
  - [ ] Testar criação
  - [ ] Testar edição
  - [ ] Testar exclusão
- [ ] Criar testes para ContactResource:
  - [ ] Testar listagem
  - [ ] Testar criação
  - [ ] Testar edição
  - [ ] Testar exclusão
  - [ ] Testar validação de tipo
- [ ] Testar relacionamentos entre recursos

### 4.4 Validação Final
- [ ] Executar todos os testes e garantir 100% de aprovação
- [ ] Executar PHPStan e garantir sem erros
- [ ] Executar Laravel Pint e garantir formatação correta
- [ ] Testar todas as funcionalidades manualmente:
  - [ ] CRUD de usuários
  - [ ] CRUD de contatos
  - [ ] Dashboard
  - [ ] Relacionamentos
  - [ ] Validações
- [ ] Verificar responsividade da interface
- [ ] Verificar acessibilidade básica

**Status da Fase 4:** 🔴 Não Iniciada

---

## 📝 Tarefas Adicionais

### Documentação
- [ ] Atualizar README.md com instruções de instalação
- [ ] Documentar estrutura do banco de dados
- [ ] Documentar APIs/endpoints (se houver)
- [ ] Criar guia de contribuição (se necessário)
- [ ] Documentar variáveis de ambiente

### Melhorias Futuras
- [ ] Adicionar autenticação e autorização
- [ ] Implementar soft deletes
- [ ] Adicionar logs de auditoria
- [ ] Implementar exportação de dados (CSV, Excel)
- [ ] Adicionar busca avançada
- [ ] Implementar paginação otimizada
- [ ] Adicionar notificações
- [ ] Implementar cache para melhor performance

---

## 📊 Progresso Geral

| Fase | Status | Progresso |
|------|--------|-----------|
| Fase 1: QA | 🔴 Não Iniciada | 0% |
| Fase 2: Backend | 🔴 Não Iniciada | 0% |
| Fase 3: Frontend | 🔴 Não Iniciada | 0% |
| Fase 4: Testes | 🔴 Não Iniciada | 0% |

**Progresso Total:** 0%

---

## 🎯 Próximos Passos

1. **Iniciar Fase 1** - Configuração de QA (Prioridade Alta)
   - Começar pela configuração do Laravel Pint
   - Em seguida, configurar PHPStan
   - Finalizar com Git Hooks

2. **Após Fase 1** - Desenvolver Backend
   - Criar migrations e models
   - Implementar relacionamentos
   - Criar factories e seeders

3. **Após Fase 2** - Desenvolver Frontend
   - Instalar Filament
   - Criar Resources
   - Implementar Dashboard

4. **Após Fase 3** - Testes e Validação
   - Criar testes completos
   - Validar todas as funcionalidades

---

## 📌 Notas

- Todas as tarefas devem seguir as convenções do Laravel
- Utilizar PHP 8.4.16 e Laravel 12
- Seguir os padrões definidos pelo Laravel Pint
- Manter código testado e documentado
- Usar Laravel Boost MCP para buscar informações sobre implementação

---

**Última atualização:** 2024  
**Mantido por:** Equipe de Desenvolvimento
