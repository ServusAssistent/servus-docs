# backend.md

# Backend Architecture

## Objetivo

O backend do Servus será responsável por:

* atendimento WhatsApp
* automações
* workflows ministeriais
* processamento IA
* pipelines
* campanhas
* multi-tenancy
* APIs administrativas

A arquitetura deve priorizar:

* simplicidade operacional
* escalabilidade pragmática
* baixo acoplamento
* modularidade
* velocidade de desenvolvimento
* facilidade de manutenção

---

# Stack

## Core

* Node.js
* NestJS
* TypeScript

---

## Banco de Dados

* PostgreSQL
* pgvector

---

## ORM

* Prisma

---

## Filas e Cache

* Redis
* BullMQ

---

## IA

* OpenAI API

---

## Integrações

* Meta WhatsApp Cloud API

---

## Storage

* S3 Compatible Storage
* Cloudflare R2 inicialmente

---

# Arquitetura Geral

A aplicação seguirá:

# Monólito Modular

Não serão utilizados microserviços inicialmente.

A separação será feita por módulos internos desacoplados.

Objetivo:

* reduzir complexidade
* acelerar desenvolvimento
* facilitar deploy
* permitir escalabilidade futura sem reescrita completa

---

# Estrutura de Pastas

```txt
src/

  common/
  config/
  database/
  queue/

  modules/

    auth/
    tenants/
    users/

    whatsapp/
    conversations/
    messages/

    ai/
    rag/

    workflows/
    pipelines/
    campaigns/

    scheduler/
    notifications/

    analytics/
```

---

# Estrutura Interna dos Módulos

Padrão:

```txt
module/

  controllers/
  services/
  repositories/
  dto/
  entities/
  interfaces/
  types/
```

---

# Princípios Arquiteturais

## Controllers

Controllers devem ser finos.

Responsabilidade:

* receber request
* validar entrada
* chamar services
* retornar resposta

Toda regra de negócio deve ficar nos services.

---

## Services

Services concentram:

* regras de negócio
* orquestração
* integrações
* workflows

---

## Repositories

Repositories isolam:

* Prisma
* queries
* persistência

Objetivo:

* reduzir acoplamento
* facilitar manutenção
* padronizar acesso a dados

---

## DTOs

Toda entrada deve usar DTOs.

Validação:

* class-validator
* class-transformer

---

# Multi-Tenancy

## Estratégia

O sistema será:

# multi-tenant compartilhado

Todas as tabelas devem possuir:

```txt
tenant_id
```

---

# Isolamento

Toda query deve obrigatoriamente filtrar:

```txt
tenant_id
```

---

# Contexto Tenant

O tenant será identificado via:

* JWT
* contexto da requisição

---

# Objetivos

* isolamento lógico
* simplicidade operacional
* escalabilidade
* baixo custo inicial

---

# Banco de Dados

## Banco Principal

PostgreSQL será o banco principal.

---

# Motivos da escolha

* forte modelagem relacional
* joins complexos
* analytics
* workflows
* consistência
* escalabilidade
* maturidade

---

# Vetores IA

Será utilizado:

```txt
pgvector
```

Objetivo:

* embeddings
* busca vetorial
* RAG

---

# ORM

Prisma será utilizado como ORM oficial.

---

# Convenções Prisma

* migrations obrigatórias
* schema centralizado
* nomes padronizados
* timestamps em todas entidades

---

# Convenções de Entidades

Toda entidade deve possuir:

```txt
id
created_at
updated_at
tenant_id
```

Quando necessário:

```txt
deleted_at
```

---

# Redis

Redis será utilizado para:

* filas
* cache
* rate limiting
* sessões temporárias
* scheduler

---

# BullMQ

BullMQ será utilizado para:

* envio mensagens
* retries
* mensagens agendadas
* workflows assíncronos
* IA assíncrona

---

# Filas Principais

```txt
whatsapp-send
whatsapp-retry
workflow-events
scheduled-messages
ai-processing
```

---

# WhatsApp

Integração oficial via:

# Meta Cloud API

---

# Fluxo WhatsApp

```txt
Webhook Meta
    ↓
Controller
    ↓
Queue
    ↓
Processor
    ↓
Workflow ou IA
    ↓
Response
```

---

# Regra Importante

Webhook nunca deve executar processamento pesado diretamente.

Tudo deve passar por filas.

---

# IA

## Estratégia

A IA será:

* contextual
* limitada
* assistiva

---

# Fluxos Críticos

Fluxos críticos NÃO devem depender de IA livre.

Exemplos:

* apresentação crianças
* campanhas
* integração PG
* formulários

Esses fluxos serão estruturados.

---

# Uso da IA

IA será utilizada para:

* FAQ
* dúvidas gerais
* contexto igreja
* suporte atendimento
* recuperação informações

---

# RAG

Arquitetura RAG:

```txt
Documentos
    ↓
Embeddings
    ↓
pgvector
    ↓
Retrieval
    ↓
Prompt Context
```

---

# Fontes de Contexto

* PDFs
* FAQs
* horários
* ministérios
* documentos internos

---

# Segurança

## Autenticação

JWT será utilizado inicialmente.

---

# Regras

* senhas com hash bcrypt
* rotas protegidas
* guards obrigatórios
* validação global
* sanitização entrada

---

# Proteções

* rate limiting
* tenant isolation
* logs estruturados
* tratamento erros
* retries controlados

---

# Logs

Pino será utilizado como logger oficial.

Objetivos:

* observabilidade
* debugging
* rastreabilidade

---

# Escalabilidade

## Fase Inicial

* monólito modular
* 1 instância backend
* Redis compartilhado
* PostgreSQL único

---

# Escala Futura

Quando necessário:

* múltiplas instâncias API
* workers separados
* read replicas
* filas distribuídas
* particionamento tenant

---

# Deploy

## Frontend

* Vercel

---

## Backend

* Railway inicialmente
  ou
* VPS Hetzner

---

## Banco

* Neon
  ou
* Supabase

---

## Redis

* Upstash

---

# Docker

Toda aplicação deve ser dockerizada.

---

# Ambientes

```txt
development
staging
production
```

---

# Variáveis de Ambiente

```txt
DATABASE_URL
REDIS_URL

OPENAI_API_KEY

META_TOKEN
META_WEBHOOK_SECRET

JWT_SECRET

S3_ENDPOINT
S3_BUCKET
S3_ACCESS_KEY
S3_SECRET_KEY
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

Pipeline backend:

```txt
Install
↓
Lint
↓
Tests
↓
Build
↓
Docker Build
↓
Deploy
```

---

# Objetivo Final da Arquitetura

A arquitetura deve permitir:

* milhares de igrejas
* baixo custo operacional
* alta velocidade desenvolvimento
* integração IA
* escalabilidade horizontal
* simplicidade de manutenção
* rápida evolução produto
