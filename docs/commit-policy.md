# Política de Commits

## Visão Geral

Este documento define o padrão para mensagens de commit no projeto, baseado em "Conventional Commits". Isso garante legibilidade, facilita automação e permite gerar changelogs automaticamente.

## Formato de Commit

```
<tipo>(<escopo>): <assunto>

<corpo>

<rodapé>
```

## Componentes

### Tipo (obrigatório)

O tipo deve ser um dos seguintes:

| Tipo | Descrição | Exemplo |
|------|-----------|----------|
| `feat` | Uma nova funcionalidade | `feat: add user authentication` |
| `fix` | Correção de bug | `fix: resolve login validation error` |
| `docs` | Mudanças apenas na documentação | `docs: update API documentation` |
| `style` | Mudanças que não afetam o código (formatação, etc.) | `style: remove unused imports` |
| `refactor` | Refatoração sem mudar funcionalidade | `refactor: optimize database queries` |
| `perf` | Melhorias de performance | `perf: improve image loading speed` |
| `test` | Adição ou correção de testes | `test: add unit tests for auth` |
| `chore` | Tarefas de manutenção, build, deps | `chore: update dependencies` |
| `ci` | Mudanças em CI/CD | `ci: add GitHub Actions workflow` |

### Escopo (opcional)

O escopo especifica qual parte do projeto foi afetada:

```
feat(auth): add login form
feat(api): add user endpoint
fix(database): resolve connection leak
docs(readme): update installation steps
```

### Assunto (obrigatório)

- Use imperativo, modo presente: "add" em vez de "added" ou "adds"
- Não comece com letra maiúscula: "add feature" em vez de "Add feature"
- Sem ponto final no final
- Máximo 50 caracteres
- Descreva o QUÊ foi feito, não o POR QUÊ

### Corpo (opcional, mas recomendado para mudanças complexas)

- Explique o QUÊ e o POR QUÊ, não o COMO
- Use imperativo
- Separe do assunto com uma linha em branco
- Máximo 72 caracteres por linha

### Rodapé (opcional)

Use para referênciar issues ou breaking changes:

```
feat: add user authentication

Implement login and registration flow with email verification.

Closes #123
Refs #456
BREAKING CHANGE: removed deprecated API endpoint /api/v1/users
```

## Exemplos

### Commit Simples

```
feat: add user registration form
```

### Commit com Escopo

```
feat(auth): implement OAuth2 authentication
```

### Commit com Corpo

```
feat(api): add pagination to user list

Implement offset and limit parameters in the user list endpoint.
This allows clients to fetch users in batches, improving performance
for large datasets.

Closes #234
```

### Commit com Breaking Change

```
refactor(api): redesign API response format

Change the response structure to match REST standards.

BREAKING CHANGE: API responses now return data in 'payload' field instead of root
```

### Commit de Bug Fix

```
fix(login): resolve incorrect error message on failed authentication

The error message was showing "Username not found" instead of
"Invalid credentials" for security reasons.

Fixes #345
```

## Boas Práticas

### 1. Commits Atômicos

Cada commit deve representar uma mudança lógica única:

```bash
# ❌ Ruim: múltiplas mudanças não relacionadas
git commit -m "feat: add auth and update database schema"

# ✅ Bom: commits separados
git commit -m "feat(auth): add login form"
git commit -m "refactor(db): update schema to support new fields"
```

### 2. Mensagens Descritivas

```bash
# ❌ Ruim
git commit -m "fix: stuff"

# ✅ Bom
git commit -m "fix(auth): resolve token expiration validation bug"
```

### 3. Referenciar Issues

```bash
# ✅ Bom
git commit -m "feat: add email verification

Closes #123"
```

### 4. Rebase Antes de Merge

```bash
git fetch origin
git rebase origin/main
git push origin feature/my-feature --force-with-lease
```

## Configurar Template Local (Opcional)

Crie um arquivo `.gitmessage` na raiz do projeto:

```
# <tipo>(<escopo>): <assunto>
#
# <corpo>
#
# <rodapé>
#
# Tipos permitidos:
# feat, fix, docs, style, refactor, perf, test, chore, ci
#
# Escopo: especifique a área afetada (auth, api, db, etc)
#
# Assunto: use imperativo, modo presente, sem ponto final
#
# Corpo: explique o QUÊ e POR QUÊ, não o COMO
#
# Rodapé: Closes #issue, Refs #issue, BREAKING CHANGE: ...
```

Configure git para usar:

```bash
git config commit.template .gitmessage
```

## Ferramentas Recomendadas

- **commitizen**: Interactive commit CLI
- **husky**: Git hooks para validar commits
- **conventional-changelog**: Gerar changelogs automaticamente

## Troubleshooting

### Corrigir Última Mensagem de Commit

```bash
git commit --amend -m "feat: corrected message"
```

### Corrigir Mensagem de Commit Antigo

```bash
git log --oneline  # Find commit hash
git rebase -i <hash>^  # Interactive rebase
# Change 'pick' to 'reword' para o commit que quer editar
```
