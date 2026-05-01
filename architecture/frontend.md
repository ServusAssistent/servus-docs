# frontend.md

# Frontend Architecture

## Objetivo

O frontend do Servus será um painel administrativo operacional para igrejas.

Objetivos principais:

* simplicidade
* produtividade
* velocidade operacional
* experiência clara
* baixo atrito
* alta reutilização

---

# Stack

## Core

* Angular
* TypeScript

---

## UI

* Angular Material

---

## Estado

* Angular Signals
* RxJS

---

## Comunicação

* REST API
* WebSockets

---

# Objetivos Arquiteturais

A arquitetura frontend deve priorizar:

* modularidade
* desacoplamento
* reusabilidade
* produtividade
* facilidade manutenção
* escalabilidade futura

---

# Estrutura do Projeto

```txt
src/app/

  core/
  shared/

  auth/

  dashboard/

  conversations/
  pipelines/
  campaigns/

  settings/
  analytics/
```

---

# Core Module

Responsável por:

* interceptors
* guards
* auth
* websocket
* services globais
* configs

---

# Shared Module

Responsável por:

* componentes reutilizáveis
* pipes
* directives
* helpers
* layouts
* UI compartilhada

---

# Módulos Funcionais

Cada domínio deve possuir:

```txt
pages/
components/
services/
models/
store/
```

---

# Estrutura Exemplo

```txt
conversations/

  pages/
  components/
  services/
  models/
  store/
```

---

# Rotas Principais

```txt
/login

/dashboard

/conversations

/pipelines

/campaigns

/settings

/analytics
```

---

# Lazy Loading

Todos os módulos principais devem utilizar:

# lazy loading

Objetivo:

* melhorar performance
* reduzir bundle inicial

---

# Gerenciamento de Estado

## Estratégia Inicial

* Signals
* services locais
* RxJS

---

# Regra Importante

Evitar overengineering no MVP.

Não utilizar:

* NgRx inicialmente
* arquitetura excessivamente complexa

---

# Realtime

WebSockets serão utilizados para:

* mensagens
* notificações
* atualização pipelines
* status tempo real

---

# Comunicação Backend

## REST

Usado para:

* CRUD
* autenticação
* configurações
* pipelines

---

## WebSockets

Usado para:

* mensagens tempo real
* atualizações instantâneas
* eventos

---

# Auth

## Estratégia

JWT Authentication.

---

# Fluxo

```txt
Login
↓
JWT
↓
Storage seguro
↓
Interceptor
↓
Requests autenticadas
```

---

# Guards

Rotas privadas devem utilizar:

* AuthGuard
* Tenant Context

---

# UI Strategy

Angular Material será utilizado inicialmente.

Objetivos:

* velocidade
* consistência
* acessibilidade
* produtividade

---

# Design System

Inicialmente:

* design simples
* sem design system customizado complexo

Foco:

# funcionalidade

---

# Responsividade

O painel deve funcionar:

* desktop primeiro
* tablet funcional
* mobile administrativo básico

---

# Convenções de Componentes

## Smart Components

Responsáveis por:

* lógica
* estado
* chamadas API

---

## Dumb Components

Responsáveis por:

* UI
* apresentação
* eventos

---

# Estrutura Shared

```txt
shared/

  components/
  directives/
  pipes/
  services/
  layouts/
```

---

# Serviços

Regras:

* services isolados por domínio
* evitar services gigantes
* responsabilidade única

---

# Models

Todos os dados devem possuir:

* interfaces tipadas
* DTOs frontend
* contratos claros

---

# Naming Convention

## Componentes

```txt
conversation-list.component.ts
pipeline-board.component.ts
```

---

## Services

```txt
conversation.service.ts
campaign.service.ts
```

---

# Estrutura Visual do Produto

## Dashboard

* métricas
* status geral
* campanhas
* atividade recente

---

# Conversations

* lista conversas
* atendimento humano
* histórico mensagens
* status atendimento

---

# Pipelines

* kanban
* drag and drop
* cards
* responsáveis
* status

---

# Campaigns

* campanhas oração
* agendamentos
* automações
* templates

---

# Settings

* IA
* WhatsApp
* branding
* FAQs
* usuários

---

# Performance

Objetivos:

* baixo tempo carregamento
* atualização rápida
* poucos renders desnecessários

---

# Estratégias

* lazy loading
* trackBy
* signals
* componentes reutilizáveis

---

# Tratamento de Erros

Frontend deve possuir:

* interceptors globais
* tratamento centralizado
* feedback visual claro
* retry quando necessário

---

# Logs

Sentry poderá ser utilizado futuramente para:

* frontend errors
* monitoring
* tracing

---

# Deploy

## Frontend

* Vercel inicialmente

---

# Ambientes

```txt
development
staging
production
```

---

# Environment Variables

```txt
API_URL
WS_URL
ENVIRONMENT
```

---

# Git Flow

## Branches

```txt
main
develop
feature/*
hotfix/*
```

---

# Commits

Padrão:

```txt
feat:
fix:
chore:
refactor:
docs:
```

---

# GitHub Actions

Pipeline frontend:

```txt
Install
↓
Lint
↓
Tests
↓
Build Angular
↓
Deploy Vercel
```

---

# Objetivo Final da Arquitetura

A arquitetura frontend deve permitir:

* crescimento rápido do produto
* manutenção simples
* onboarding fácil
* experiência operacional eficiente
* alta produtividade
* escalabilidade futura
* integração realtime
* evolução gradual sem refatorações destrutivas
