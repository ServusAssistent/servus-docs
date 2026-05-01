# infrastructure.md

# Infrastructure Architecture

## Objetivo

A infraestrutura do Servus deve priorizar:

* baixo custo inicial
* simplicidade operacional
* alta confiabilidade
* escalabilidade gradual
* facilidade de manutenção
* deploy rápido
* observabilidade
* preparação para crescimento

A infraestrutura deve permitir:

* começar pequeno
* escalar rapidamente
* evitar reescrita arquitetural

---

# Filosofia da Infraestrutura

## Estratégia Inicial

A infraestrutura inicial deve ser:

# simples, barata e eficiente

Evitar:

* Kubernetes precoce
* microserviços desnecessários
* complexidade enterprise
* múltiplos providers sem necessidade

---

# Estratégia de Escalabilidade

A arquitetura deve permitir:

## Fase 1

MVP simples

## Fase 2

Escala horizontal API

## Fase 3

Workers separados

## Fase 4

Read replicas

## Fase 5

Infraestrutura distribuída

---

# Arquitetura Geral

```txt id="7d1m95"
                Users
                   ↓
             Cloudflare
                   ↓
               Frontend
                Vercel
                   ↓
                Backend
          Railway/VPS Docker
                   ↓
      +------------+------------+
      |                         |
 PostgreSQL               Redis/BullMQ
      |
   pgvector
      |
   OpenAI
      |
 Meta Cloud API
```

---

# Frontend Infrastructure

## Plataforma

Inicialmente:

* Vercel

---

# Motivos

* deploy simples
* integração GitHub
* preview deployments
* CDN global
* baixo custo inicial

---

# Estratégia

Cada push em:

```txt id="e4mibn"
main
```

deve gerar:

* deploy produção

Cada push em:

```txt id="j0nhbh"
develop
```

deve gerar:

* staging preview

---

# Backend Infrastructure

## Estratégia Inicial

Backend dockerizado.

---

# Opções iniciais

## Preferencial

* Railway

---

## Alternativa

* VPS Hetzner

---

# Objetivos

* deploy rápido
* custo baixo
* simplicidade operacional

---

# Docker

Toda aplicação backend deve possuir:

```txt id="8f0q5n"
Dockerfile
docker-compose.yml
```

---

# Containerização

Backend deve ser:

* stateless
* horizontalmente escalável

Nenhum dado persistente local.

---

# Banco de Dados

## Banco Principal

PostgreSQL

---

# Providers

## Inicial

* Neon
  ou
* Supabase

---

# Objetivos

* backups automáticos
* alta disponibilidade
* escalabilidade
* gerenciamento simples

---

# Extensões

Obrigatório:

```txt id="j8j3m0"
pgvector
```

---

# Estratégia de Crescimento

## Inicial

1 instância PostgreSQL.

---

# Futuro

* read replicas
* particionamento
* dedicated instances
* sharding tenant

---

# Redis Infrastructure

## Provider

Inicialmente:

* Upstash

---

# Uso

Redis será utilizado para:

* BullMQ
* cache
* sessões temporárias
* rate limiting
* realtime support

---

# Estratégia

Separar:

* queues críticas
* cache

quando necessário futuramente.

---

# Filas

## BullMQ

Filas principais:

```txt id="afw11s"
whatsapp-send
whatsapp-retry
scheduled-messages
workflow-events
ai-processing
```

---

# Objetivos

* evitar bloqueios
* processamento assíncrono
* retries automáticos
* desacoplamento

---

# Storage

## Estratégia

Todo arquivo deve ficar em:

# object storage

Nunca local filesystem.

---

# Provider Inicial

* Cloudflare R2

---

# Arquivos

* PDFs
* uploads
* mídia WhatsApp
* documentos IA

---

# CDN

Cloudflare será utilizado para:

* cache
* proteção
* performance
* SSL
* CDN

---

# Domínios

## Estrutura sugerida

```txt id="bhajy9"
app.servus.ai
api.servus.ai
admin.servus.ai
```

---

# SSL

SSL obrigatório em:

* frontend
* backend
* webhooks

---

# Ambientes

## Obrigatórios

```txt id="t5mptc"
development
staging
production
```

---

# Regras

## Development

ambiente local.

---

## Staging

testes reais.

---

## Production

produção clientes.

---

# Environment Variables

## Backend

```txt id="j5n5iu"
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

## Frontend

```txt id="i1fxzq"
API_URL
WS_URL
ENVIRONMENT
```

---

# CI/CD

## GitHub Actions

Toda aplicação deve possuir:

* CI
* CD
* testes automáticos
* build automático

---

# Backend Pipeline

```txt id="tq0kn0"
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

# Frontend Pipeline

```txt id="6g3j6y"
Install
↓
Lint
↓
Tests
↓
Angular Build
↓
Deploy Vercel
```

---

# Branch Strategy

## Branches principais

```txt id="kv1q4m"
main
develop
feature/*
hotfix/*
```

---

# Deploy Rules

## main

deploy produção.

---

## develop

deploy staging.

---

# Observabilidade

## Logs

Backend:

* Pino Logger

---

# Error Tracking

Inicialmente:

* Sentry

---

# Objetivos

* rastreamento erros
* debugging
* monitoramento

---

# Monitoramento Futuro

Quando necessário:

* Prometheus
* Grafana
* uptime monitoring
* métricas customizadas

---

# Segurança

## Obrigatório

* HTTPS
* JWT
* rate limiting
* tenant isolation
* validation pipes
* sanitização
* backups automáticos

---

# Webhooks

Webhooks devem:

* validar assinatura
* responder rápido
* processar async

---

# Estratégia de Backup

## Banco

Backups automáticos diários.

---

# Storage

Versionamento habilitado quando possível.

---

# Disaster Recovery

Objetivo:

* recuperação rápida
* mínima perda dados

---

# Escalabilidade

## Estratégia Inicial

1 instância backend.

---

# Escala Horizontal

Quando necessário:

```txt id="u08azx"
Load Balancer
      ↓
Multiple API Instances
      ↓
Redis Shared
      ↓
PostgreSQL
```

---

# Workers

Workers poderão ser separados futuramente:

```txt id="06vj7s"
API
Workers
Scheduler
Realtime
```

---

# Realtime Infrastructure

## Estratégia

WebSockets inicialmente integrados na API principal.

---

# Futuro

Separação realtime service se necessário.

---

# Custos

## Estratégia

Infraestrutura deve priorizar:

* eficiência
* baixo custo inicial
* crescimento gradual

---

# Regra Importante

Nunca antecipar infraestrutura enterprise sem necessidade real.

---

# Objetivo Final da Infraestrutura

A infraestrutura deve permitir:

* milhares de igrejas
* crescimento rápido
* deploy simples
* baixo custo operacional
* alta disponibilidade
* escalabilidade horizontal
* integração IA
* estabilidade operacional
* facilidade manutenção
* rápida evolução produto
