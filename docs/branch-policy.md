# Política de Branches

## Visão Geral

Este documento define o padrão para criação e nomeação de branches no projeto, garantindo organização e facilidade na identificação do tipo de trabalho.

## Nomes de Branches

Os branches devem seguir o padrão:

```
<tipo>/<descrição-do-trabalho>
```

### Tipos de Branch

| Tipo | Propósito | Exemplo |
|------|-----------|----------|
| `feature/` | Nova funcionalidade | `feature/user-authentication` |
| `bugfix/` | Correção de bug | `bugfix/login-validation` |
| `hotfix/` | Correção urgente em produção | `hotfix/critical-security-patch` |
| `docs/` | Atualizações de documentação | `docs/api-endpoints` |
| `refactor/` | Refatoração de código | `refactor/optimize-database-queries` |
| `chore/` | Tarefas de manutenção | `chore/update-dependencies` |
| `test/` | Adição ou melhoria de testes | `test/add-unit-tests` |

## Convenções de Nomenclatura

### Regras Gerais

1. **Usar kebab-case**: `feature/my-awesome-feature` ✅
2. **Não usar underscores**: `feature/my_awesome_feature` ❌
3. **Manter descritivo**: `feature/auth` ✅ vs `feature/wip` ❌
4. **Usar inglês**: `feature/adicionar-autenticacao` ❌ vs `feature/add-authentication` ✅
5. **Máximo 50 caracteres**: `feature/implement-oauth2-google-authentication-with-refresh-tokens` ❌

### Exemplos Válidos

```
feature/user-registration
feature/email-verification
bugfix/password-reset-token-expiry
hotfix/database-connection-leak
docs/installation-guide
refactor/api-response-handler
chore/update-npm-packages
test/add-integration-tests
```

## Boas Práticas

### 1. Criar Branch da Main

```bash
git checkout main
git pull origin main
git checkout -b feature/my-feature
```

### 2. Manter Branch Atualizado

Antes de fazer pull request:

```bash
git fetch origin
git rebase origin/main
```

### 3. Um Branch por Issue

Cada issue deve ter seu próprio branch. Se a issue é `#123`, o branch pode ser:

```
feature/123-user-authentication
```

### 4. Deletar Branches Merged

Após o merge, delete o branch local e remoto:

```bash
git branch -d feature/my-feature
git push origin --delete feature/my-feature
```

## Branch Protection Rules

A branch `main` é protegida com as seguintes regras:

- ✅ Requer pull request para merge
- ✅ Requer revisão aprovada
- ✅ Dismiss stale pull request approvals
- ✅ Requer status checks passar
- ✅ Requer commits atualizados antes do merge
- ✅ Requer branch estar atualizada com base antes do merge
- ✅ Deletar branch automáticamente após merge

## Fluxo Típico

```bash
# 1. Atualizar main
git checkout main
git pull origin main

# 2. Criar novo branch
git checkout -b feature/add-login

# 3. Fazer commits
git add .
git commit -m "feat: add login form component"

# 4. Push do branch
git push origin feature/add-login

# 5. Abrir Pull Request no GitHub
# 6. Após aprovação, merge via GitHub

# 7. Limpar branch local (opcional, GitHub deleta automático)
git branch -d feature/add-login
```

## Troubleshooting

### Branch está desatualizado

```bash
git fetch origin
git rebase origin/main
git push origin feature/my-feature --force-with-lease
```

### Criar branch a partir de outra branch

```bash
git checkout -b feature/sub-feature origin/feature/parent-feature
```

### Renomear branch local

```bash
git branch -m feature/old-name feature/new-name
git push origin --delete feature/old-name
git push origin feature/new-name
```
