# Arquitetura do Projeto

## Visão Geral

Este documento descreve a arquitetura geral do projeto, sua estrutura de diretórios e os componentes principais.

## Estrutura de Diretórios

```
/ (raiz do projeto)
├── .github/                   # Configurações do GitHub
│   ├── ISSUE_TEMPLATE/        # Templates para novas tarefas (bug, feature)
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   ├── PULL_REQUEST_TEMPLATE.md # Template para pull requests
│   └── workflows/             # Automações (GitHub Actions)
│
├── /docs                      # Documentação detalhada
│   ├── architecture.md        # Estrutura do projeto (este arquivo)
│   ├── branch-policy.md       # Padrão de Branch
│   └── commit-policy.md       # Padrão de Commit
│
├── CONTRIBUTING.md            # Guia do Desenvolvedor
├── README.md                  # Apresentação do projeto
└── LICENSE                    # Licença do projeto
```

## Componentes Principais

### `.github/`
Centraliza toda a configuração do GitHub, incluindo:
- **ISSUE_TEMPLATE/**: Templates padronizados para reportar bugs e sugerir features
- **PULL_REQUEST_TEMPLATE.md**: Template para pull requests
- **workflows/**: GitHub Actions para CI/CD e automações

### `docs/`
Documentação técnica detalhada:
- **architecture.md**: Descrição da arquitetura (este arquivo)
- **branch-policy.md**: Convenções para branches
- **commit-policy.md**: Padrões de commits

### Raiz do Projeto
- **CONTRIBUTING.md**: Guia completo para contribuidores
- **README.md**: Visão geral e quick start
- **LICENSE**: Licença do projeto

## Fluxo de Desenvolvimento

```
1. Criar Issue (bug ou feature)
   ↓
2. Criar Branch (seguindo branch-policy)
   ↓
3. Desenvolver com commits (seguindo commit-policy)
   ↓
4. Abrir Pull Request
   ↓
5. Code Review
   ↓
6. Merge para main
```

## Padrões de Qualidade

O projeto segue padrões rigorosos para manter a qualidade:

- **Commits**: Mensagens semânticas (feat, fix, docs, etc.)
- **Branches**: Nomes descritivos (feature/, bugfix/, etc.)
- **Pull Requests**: Descrição clara do que foi mudado e por quê
- **Documentação**: Mantida sempre atualizada

## Próximos Passos

- Leia [branch-policy.md](./branch-policy.md) para aprender sobre convenções de branches
- Leia [commit-policy.md](./commit-policy.md) para aprender sobre padrões de commits
- Consulte [CONTRIBUTING.md](../CONTRIBUTING.md) para o guia completo
