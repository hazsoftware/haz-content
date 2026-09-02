# usecases

Casos de uso diários de ferramentas de agentes de IA (Claude Code, OpenAI
Codex, Google Antigravity, Cursor, Claude in Chrome, Hermes Agent,
OpenClaw), gerados pela rotina cloud "Usecases ferramentas IA diario"
(`trig_01RRi1otVfvHJAoB6pk2pLzH`, cron `0 11 * * *` UTC). O mesmo conteúdo
é postado no Discord (#usecases) e salvo aqui.

## Convenção

Uma subpasta por dia, nomeada `AAAA-MM-DD/`, contendo `resumo.md` com o
texto completo gerado naquele dia (todas as partes do envio ao Discord
concatenadas em um único arquivo). Se nenhuma ferramenta teve novidade
relevante naquele dia, a rotina não posta nada — não existe pasta para
aquele dia.

```
usecases/
  2026-09-03/
    resumo.md
  2026-09-04/
    resumo.md
  ...
```

## Histórico anterior a 2026-09-03

A rotina já rodava antes disso, mas só postava no Discord — nada era
salvo em arquivo. O histórico de execuções fica em `RemoteTrigger`
(`list_runs`/`get_run_log` sobre `trig_01RRi1otVfvHJAoB6pk2pLzH`), mas o
log condensado só guarda previews truncados de cada evento, não o texto
completo — e a sessão em `claude.ai/code/session_...` exige login que
ferramentas de fetch não têm. Conteúdo integral dos dias antigos não foi
reconstruído (mesma situação de `news-ai/README.md`).

## Nota sobre push

Assim como `news-ai/`, o push automático da rotina pra este repositório
depende do GitHub App do Claude estar instalado pra org `hazsoftware`
(ver `news-ai/README.md`) — sem isso, a rotina posta no Discord
normalmente mas falha silenciosamente ao tentar salvar aqui (reporta o
403 no próprio resultado da tarefa).
