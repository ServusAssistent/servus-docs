# branching.md

# Git Branching Strategy

## Objetivo

Definir um fluxo simples, consistente e escalável para desenvolvimento do Servus.

O objetivo do fluxo é:

* manter organização
* reduzir conflitos
* facilitar deploy
* permitir crescimento da equipe
* manter histórico limpo
* acelerar desenvolvimento

---

# Filosofia

O projeto deve priorizar:

# simplicidade operacional

Evitar:

* fluxos extremamente complexos
* excesso de branches
* burocracia desnecessária

---

# Estratégia Principal

Será utilizado um modelo baseado em:

* main
* develop
* feature branches
* hotfix branches

---

# Branches Oficiais

## main

Branch de produção.

Regra:

* sempre estável
* sempre deployável
* nunca quebrada

Tudo que estiver em:

```txt id="1if6tq"
main
```

deve poder ir para produção.

---

# develop

Branch principal de desenvolvimento.

Objetivo:

* integração features
* testes
* staging

---

# Fluxo

```txt id="zttk38"
feature/* → develop → main
```

---

# Feature Branches

Toda feature deve possuir branch própria.

---

# Padrão

```txt id="4v98uq"
feature/nome-feature
```

---

# Exemplos

```txt id="1bnjlwm"
feature/whatsapp-webhook
feature/auth-module
feature/pipeline-kanban
feature/visitor-workflow
feature/openai-service
```

---

# Regras

Feature branches:

* pequenas
* objetivas
* focadas
* curta duração

Evitar branches gigantes.

---

# Hotfix Branches

Correções urgentes de produção.

---

# Padrão

```txt id="j2l2ye"
hotfix/nome-fix
```

---

# Exemplos

```txt id="2a54it"
hotfix/fix-webhook-loop
hotfix/jwt-validation
hotfix/tenant-security
```

---

# Fluxo de Desenvolvimento

## 1. Atualizar develop

```bash id="i5f02k"
git checkout develop
git pull origin develop
```

---

## 2. Criar feature branch

```bash id="wg8vbv"
git checkout -b feature/whatsapp-webhook
```

---

## 3. Desenvolver

Realizar:

* código
* testes
* ajustes

---

## 4. Commitar

Seguir padrão commits.

---

## 5. Push

```bash id="n58thw"
git push origin feature/whatsapp-webhook
```

---

## 6. Pull Request

Abrir PR para:

```txt id="bx5v9w"
develop
```

---

## 7. Merge

Após:

* revisão
* CI verde
* testes

---

# Fluxo de Produção

Quando develop estiver estável:

```txt id="gwfaj9"
develop → main
```

---

# Deploy Produção

Toda atualização em:

```txt id="6iy15o"
main
```

gera:

* deploy produção

---

# Deploy Staging

Toda atualização em:

```txt id="c8lv7e"
develop
```

gera:

* deploy staging

---

# Regras de Commit

## Objetivo

Histórico claro e rastreável.

---

# Padrões

## feat

Nova funcionalidade.

```txt id="0yfj0r"
feat: add whatsapp webhook
```

---

## fix

Correção bug.

```txt id="97b1r5"
fix: resolve tenant validation
```

---

## chore

Infraestrutura ou manutenção.

```txt id="h69f5r"
chore: setup docker environment
```

---

## refactor

Refatoração sem alterar comportamento.

```txt id="g0qkz3"
refactor: simplify auth service
```

---

## docs

Documentação.

```txt id="7j4ltm"
docs: update architecture docs
```

---

# Regras Importantes

## Nunca commitar:

* secrets
* .env
* tokens
* credenciais
* arquivos sensíveis

---

# Commits Devem Ser

* pequenos
* claros
* focados
* descritivos

---

# Evitar

❌ commits gigantes
❌ “update”
❌ “fix stuff”
❌ “teste”
❌ múltiplas features no mesmo commit

---

# Pull Requests

## Objetivo

Garantir:

* qualidade
* rastreabilidade
* estabilidade

---

# Regras

PR deve:

* ser pequeno
* possuir objetivo claro
* passar CI
* compilar corretamente

---

# Nome PR

```txt id="ng4sv0"
feat: implement whatsapp webhook
```

---

# CI/CD

## GitHub Actions

Toda PR deve executar:

```txt id="yfybg4"
Install
↓
Lint
↓
Tests
↓
Build
```

---

# Merge Rules

Só realizar merge quando:

* build verde
* sem conflitos
* funcionalidade validada

---

# Estratégia Inicial da Equipe

Inicialmente:

* fluxo simplificado
* velocidade alta
* baixa burocracia

---

# Estratégia Futura

Quando equipe crescer:

* code owners
* approvals
* protected branches
* semantic release
* release automation

---

# Versionamento

Inicialmente:

# simples

Exemplo:

```txt id="6j3r9x"
v0.1.0
v0.2.0
v1.0.0
```

---

# Estratégia de Releases

## MVP

Deploy contínuo.

---

# Futuro

Possível adoção:

* changelogs
* releases automáticas
* release notes

---

# Objetivo Final do Fluxo

O fluxo de branching deve permitir:

* velocidade desenvolvimento
* organização
* estabilidade
* deploy contínuo
* escalabilidade futura
* colaboração eficiente
* histórico limpo
* integração fácil com IA e automações
