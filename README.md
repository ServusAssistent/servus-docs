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

# Objetivo Principal

Construir a infraestrutura operacional inteligente das igrejas.

Começando:

* simples
* extremamente útil
* operacional
* escalável
* orientado por IA

---

# Estrutura do Repositório

```txt id="0my3y6"
servus-docs/

├── architecture/
├── business/
├── decisions/
├── processes/
├── product/
├── roadmap/
```

---

# Diretórios

# architecture/

Documentação técnica da plataforma.

Inclui:

* backend
* frontend
* infraestrutura
* IA
* banco de dados
* escalabilidade

---

# business/

Documentação estratégica e comercial.

Inclui:

* pricing
* posicionamento
* aquisição
* ICP
* concorrência

---

# decisions/

Registro de decisões arquiteturais e estratégicas.

Objetivo:

* preservar contexto
* evitar retrabalho
* manter consistência

---

# processes/

Processos internos de desenvolvimento.

Inclui:

* branching
* padrões
* fluxo Git
* convenções

---

# product/

Definição do produto.

Inclui:

* visão
* MVP
* workflows
* funcionalidades
* pipelines

---

# roadmap/

Planejamento e evolução do projeto.

Inclui:

* backlog
* milestones
* roadmap geral

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

# Estratégia de Produto

O foco inicial NÃO é:

# construir ERP completo.

O foco é:

# resolver dores operacionais reais das igrejas via WhatsApp.

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

# Estratégia Comercial Inicial

Modelo:

# SaaS mensal

Aquisição inicial:

* networking
* igrejas piloto
* demonstrações
* implantação próxima
* indicação

---

# Objetivo do MVP

Validar:

* retenção
* uso recorrente
* valor percebido
* disposição de pagamento
* eficiência operacional

---

# Regras do Projeto

## Regra 1

Priorizar:

# execução

Não:

# perfeccionismo

---

## Regra 2

Toda decisão importante deve ser documentada.

---

## Regra 3

Evitar troca impulsiva de stack ou arquitetura.

---

## Regra 4

IA deve acelerar desenvolvimento, não substituir pensamento arquitetural.

---

## Regra 5

Complexidade só deve ser adicionada quando houver necessidade real.

---

# Convenções

## Branches

```txt id="56m6mk"
main
develop
feature/*
hotfix/*
```

---

# Commits

```txt id="7m9k4o"
feat:
fix:
chore:
refactor:
docs:
```

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
* provar valor operacional
