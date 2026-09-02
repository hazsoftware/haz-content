# news-ai

Notícias diárias de IA para devs, geradas pela rotina cloud "Noticias IA
diario" (`trig_01Ayf5Fg9fR24t3bcUe9wwVa`, cron `0 11 * * *` UTC). O mesmo
conteúdo é postado no Discord (#noticias-ia) e salvo aqui.

## Convenção

Uma subpasta por dia, nomeada `AAAA-MM-DD/`, contendo `resumo.md` com o
texto completo gerado naquele dia (todas as partes do envio ao Discord
concatenadas em um único arquivo).

```
news-ai/
  2026-09-03/
    resumo.md
  2026-09-04/
    resumo.md
  ...
```

## Histórico anterior a 2026-09-03

A rotina já rodava desde 2026-08-02 (ver `[[noticias-ia]]` na memória do
claude-os), mas só postava no Discord — nada era salvo em arquivo. O
histórico de execuções fica em `RemoteTrigger` (`list_runs`/`get_run_log`
sobre `trig_01Ayf5Fg9fR24t3bcUe9wwVa`), mas o log condensado só guarda
previews truncados de cada evento, não o texto completo — e a sessão em
`claude.ai/code/session_...` exige login que ferramentas de fetch não têm.
Ou seja, o conteúdo integral dos dias antigos só existe nas mensagens já
postadas no canal #noticias-ia do Discord. Não foi reconstruído.
