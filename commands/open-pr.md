---
description: Criar e abrir um pull request com resumo completo e plano de testes
argument-hint: [título do pr]
allowed-tools: Bash(git:*), Bash(gh:*)
---

# Abrir Pull Request

Criar PR: $ARGUMENTS

## Processo

### 1. Pré-voo

```bash
git status
git log --oneline main..HEAD
git diff main...HEAD --stat
```

### 2. Commitar Alterações

Se houver alterações não commitadas:

```bash
git add -A
git commit -m "<tipo>: <descrição>"
```

Tipos de commit: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`

### 3. Enviar Branch

```bash
git push -u origin HEAD
```

### 4. Criar PR

```bash
gh pr create --title "<título>" --body "$(cat <<'EOF'
## Resumo
- [Alteração principal 1]
- [Alteração principal 2]

## Notas
[Quaisquer notas de deploy ou migração]
EOF
)"
```

## Saída

Retornar a URL do PR para revisão.
