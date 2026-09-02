# gastos-ia

Snapshots semanais do dashboard de custo/tokens de uso do Claude Code
(`departments/it/workspaces/gastos-ia/`), gerados pela tarefa agendada
local `gastos-ia-weekly` (Windows Task Scheduler, segunda 08:00 local —
**não** é uma routine cloud, porque `collect.py` precisa ler os logs
locais em `~/.claude/projects/*/*.jsonl`).

## Convenção

Uma subpasta por execução, nomeada `AAAA-MM-DD/` (data da execução),
contendo:

- `resumo.md` — o mesmo texto enviado ao Discord (gasto do mês atual,
  total histórico acumulado, top 3 projetos do mês).
- `dashboard.html` — cópia completa e autocontida do dashboard daquela
  semana (gráficos inline, sem dependências externas), permitindo abrir o
  estado histórico de qualquer semana passada, não só o mais recente.

```
gastos-ia/
  2026-09-08/
    resumo.md
    dashboard.html
  2026-09-15/
    resumo.md
    dashboard.html
  ...
```

## Mecanismo de gravação (diferente de news-ai/ e usecases/)

`notify.py` (rodando localmente, não numa sandbox cloud) escreve os
arquivos e faz `git add`/`commit`/`push origin main` diretamente sobre o
clone local deste repositório, usando o remote SSH `github-empresa` já
configurado. **Isso não depende do GitHub App do Claude** (o bloqueio de
403 documentado em `news-ai/README.md` e `usecases/README.md` é
específico do mecanismo de routine cloud) — o push daqui já funciona
desde o primeiro run.

Se um snapshot não aparecer numa segunda-feira, o problema está na
Scheduled Task local (`gastos-ia-weekly`) ou no push local, não no GitHub
App — verifique antes de assumir que é o mesmo bloqueio das outras duas
pastas.

## Histórico anterior à automação

Snapshots de antes de 2026-09-02 não existem aqui — o dashboard sempre
existiu apenas como `dashboard.html` local (sobrescrito a cada execução),
sem histórico versionado até essa mudança.
