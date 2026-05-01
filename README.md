# Servus Docs

Documentação central do ecossistema Servus.

Este repositório concentra:

* arquitetura
* produto
* negócio
* infraestrutura
* roadmap
* decisões
* processos

O objetivo é manter:

* clareza
* alinhamento
* velocidade de execução
* contexto para IA
* rastreabilidade técnica e estratégica

---

# Visão do Projeto

O Servus é uma plataforma operacional inteligente para igrejas, focada em:

* WhatsApp
* automações
* IA contextual
* workflows ministeriais
* follow-up
* pipelines
* organização operacional

O produto nasce como:

# WhatsApp-first

Com foco em:

* redução trabalho manual
* integração visitantes
* campanhas
* automações
* atendimento inteligente

---

# Estrutura da Documentação

```txt
servus-docs/
│
├── architecture/
├── business/
├── decisions/
├── processes/
├── product/
└── roadmap/
```

---

# Navegação Rápida

# Architecture

Documentação técnica da plataforma.

## Arquivos

* [backend.md](./architecture/backend.md)
* [frontend.md](./architecture/frontend.md)
* [infrastructure.md](./architecture/infrastructure.md)

---

# Business

Documentação estratégica e comercial.

## Arquivos sugeridos

* [pricing.md](./business/pricing.md)
* [icp.md](./business/icp.md)
* [positioning.md](./business/positioning.md)
* [acquisition.md](./business/acquisition.md)
* [competitors.md](./business/competitors.md)

---

# Decisions

Registro de decisões arquiteturais e estratégicas.

## Arquivos

* [decisions.md](./decisions/decisions.md)

---

# Processes

Processos internos de desenvolvimento.

## Arquivos

* [branching.md](./processes/branching.md)

---

# Product

Definição do produto.

## Arquivos

* [mvp.md](./product/mvp.md)
* [vision.md](./product/vision.md)
* [workflows.md](./product/workflows.md)
* [pipelines.md](./product/pipelines.md)

---

# Roadmap

Planejamento e evolução do projeto.

## Arquivos

* [roadmap.md](./roadmap/roadmap.md)
* [milestones.md](./roadmap/milestones.md)
* [backlog.md](./roadmap/backlog.md)

---

# Filosofia do Projeto

O Servus deve priorizar:

* simplicidade
* velocidade
* clareza
* escalabilidade pragmática
* foco operacional
* validação rápida

Evitar:

* overengineering
* burocracia
* complexidade precoce
* arquitetura enterprise desnecessária

---

# Stack Principal

## Backend

* NestJS
* PostgreSQL
* Prisma
* Redis
* BullMQ

---

## Frontend

* Angular
* Angular Material

---

## Infraestrutura

* Docker
* Vercel
* Railway
* Cloudflare
* Neon/Supabase

---

## IA

* OpenAI
* RAG
* pgvector

---

# Estratégia Técnica

Arquitetura inicial:

# monólito modular

Objetivo:

* acelerar desenvolvimento
* reduzir complexidade
* simplificar deploy
* permitir evolução gradual

---

# Funcionalidades Principais do MVP

* chatbot WhatsApp
* IA contextual
* integração visitantes
* pedidos oração
* apresentação crianças
* pipelines kanban
* follow-up automático
* dashboard administrativo

---

# Convenções

## Branches

```txt
main
develop
feature/*
hotfix/*
```

---

# Commits

```txt
feat:
fix:
chore:
refactor:
docs:
```

---

# GitHub Pages

O projeto poderá ser publicado futuramente usando GitHub Pages.

## URL esperada

```txt
https://servusassistent.github.io/servus-docs/
```

---

# Como ativar GitHub Pages

## 1. Abrir o repositório

GitHub → Settings

---

## 2. Abrir seção

```txt
Pages
```

---

## 3. Configurar

### Source

```txt
Deploy from a branch
```

---

### Branch

```txt
main
```

---

### Folder

```txt
/ root
```

---

## 4. Save

Após alguns minutos o GitHub publicará o site.

---

# Objetivo da Documentação

Esta documentação existe para:

* alinhar desenvolvimento
* preservar contexto
* acelerar onboarding
* facilitar uso de IA
* manter consistência
* reduzir decisões impulsivas

---

# Integração com IA

Os documentos deste repositório servem como:

# contexto operacional e arquitetural

para:

* Claude
* Codex
* agentes IA
* automações futuras

---

# Visão de Longo Prazo

O Servus pode evoluir para um ecossistema completo contendo:

* CRM ministerial
* automações avançadas
* analytics
* multi-campus
* app mobile
* voice AI
* gestão operacional completa
* infraestrutura digital para igrejas

---

# Estado Atual

Fase:

# MVP

Objetivo atual:

* construir rápido
* validar mercado
* conseguir igrejas piloto
* gerar retenção
* pro
