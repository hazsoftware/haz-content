# Resumo IA para Devs — 06/09/2026

**📰 Novidades para Devs**

**Modelos e APIs**
- Claude Sonnet 4.5 segue como referência de custo-benefício em coding, com ~77% no SWE-bench Verified — ponto de comparação direto contra GPT-5.x e Gemini em tarefas de engenharia real.
- Guerra de preços entre Google, OpenAI e Anthropic: Google cortou o plano de entrada do Gemini (AI Plus) de US$7,99 para US$4,99/mês, e a OpenAI estuda reduzir bastante o preço por token para segurar clientes enterprise.
- ChatGPT ganhou suporte nativo a MCP, permitindo conectar servidores externos diretamente sem integrações customizadas — reduz atrito pra times que já padronizaram em MCP.

**Ferramentas e Frameworks**
- Cursor: Composer 2.5 (branch 3.7) virou o modo agressivo padrão para edições multi-arquivo — recebe instrução em linguagem natural, monta um plano inline editável antes de executar.
- Claude Code segue evoluindo o modelo de execução autônoma: effort level "xhigh", Task Budgets (limite de custo/tempo por tarefa) e Auto Mode para deixar o agente decidir quando parar.
- CodeRabbit levantou US$60M para expandir revisão de código via IA — sinal de que "AI code review" virou categoria própria, não só feature de IDE.
- astral-sh/ruff continua ganhando tração como linter/formatter Python em Rust, substituindo boa parte do stack flake8+black+isort em projetos novos.

**Agentes e Automação**
- Microsoft Agent Framework chegou à GA (1.0), unificando AutoGen e Semantic Kernel numa única plataforma suportada — chat clients, tools, integrações MCP e workflows multi-step em um SDK só.
- Google mantém seu agente de terminal open-source (loop ReAct, MCP nativo, contexto de 1M tokens, Apache 2.0) como opção viável a Claude Code/Codex CLI.
- Slack Code passou a embutir agentes de coding (Claude Code, Devin, GitHub Copilot, agente da Vercel) direto em canais dedicados, permitindo que o time inteiro acompanhe e revise em tempo real.
- n8n segue em alta como camada de orquestração no-code/low-code para conectar agentes e ferramentas em workflows de produção.

**Infraestrutura e Deploy**
- MCP consolidou a revisão de spec 2026-07-28: protocolo stateless (sem handshake de sessão), extensão de Tasks para chamadas assíncronas longas, MCP Apps para UIs interativas sandboxed, e cache determinístico de listagens de tools — tudo pensado pra escalar horizontalmente e melhorar hit-rate de prompt cache.
- OpenTelemetry avança nas semantic conventions para GenAI (spans de modelo/agente, tokens, custo, latência, TTFT), permitindo instrumentar com OpenInference e mandar pra Phoenix, Langfuse, Honeycomb ou Jaeger sem trocar de SDK.
- Observabilidade de vector DB virou requisito de produção: monitorar latência/recall de retrieval é tratado como parte do SLO de qualquer stack RAG, não mais opcional.

**🔥 Repositórios em Alta no GitHub**
- **huggingface/transformers** (Python, 🌟 ~42 hoje) — o framework de referência para modelos de texto, visão e áudio continua puxando tração diária mesmo maduro.
- **n8n-io/n8n** (TypeScript, 🌟 ~139 hoje) — automação visual+código com 400+ integrações, virou peça central para orquestrar agentes em produção.
- **f/prompts.chat** (HTML, 🌟 ~99 hoje) — plataforma self-hostable para compartilhar e descobrir prompts, alternativa aberta a serviços proprietários.
- **astral-sh/ruff** (Rust, 🌟 ~20 hoje) — linter/formatter Python ultrarrápido, consolidando o Rust como stack de tooling para Python.
- **codecrafters-io/build-your-own-x** (Markdown, 🌟 ~234 hoje) — recurso educacional pra recriar ferramentas conhecidas do zero, útil pra entender internals que agentes de IA hoje abstraem.
- **donnemartin/system-design-primer** (Python, 🌟 ~226 hoje) — referência de system design, cada vez mais relevante pra revisar arquiteturas geradas por agentes.
- **dgtlmoon/changedetection.io** (Python, 🌟 ~45 hoje) — monitoramento de mudanças em páginas web, útil como gatilho de automações e pipelines de dados para RAG.

**🛠️ Técnicas e Skills em Alta**
- **Orquestração de agentes + MCP**: coordenar múltiplos agentes especializados via protocolo padrão (em vez de integrações ad-hoc) é a habilidade mais cotada em vagas de engenharia com IA agora.
- **Eval design**: engenheiros estão investindo em benchmarks e avaliadores determinísticos próprios (LLM-as-judge + testes reproduzíveis) em vez de confiar só em benchmarks públicos.
- **Destilar RAG em fine-tuning**: internalizar conhecimento recuperado via fine-tuning para eliminar overhead de retrieval em produção, mantendo o ganho de qualidade do RAG só em tempo de treino.
- **Observabilidade GenAI com OpenTelemetry**: instrumentar spans de modelo/agente com custo, tokens e latência virou prática padrão antes mesmo do primeiro deploy.
- **Verificação de código gerado por IA**: revisão rigorosa (testes, análise estática, checagem de premissas) do output de agentes autônomos é tratada como etapa obrigatória do pipeline, não opcional.
- **Linguagens tipadas por padrão**: TypeScript, Python com type hints, Rust e Go seguem como escolha padrão para novos projetos justamente para dar mais grip sobre código gerado por IA.

**📄 Papers em Tendência**
- **Fine-tuning with RAG for Improving LLM Learning of New Skills** — mostra como converter retrieval em tempo de inferência em competência aprendida via destilação, eliminando overhead de RAG no deploy sem perder desempenho.
- **SoK: Agentic Retrieval-Augmented Generation (RAG)** — survey que organiza taxonomia, arquiteturas e direções de pesquisa para RAG agentic, útil como mapa de referência pra quem está desenhando pipelines novos.
- **Stable-RAG** — ataca alucinações causadas por permutação na ordem dos documentos recuperados, um problema prático comum em RAG de produção.
- **Agents' Last Exam (ALE)** — benchmark vivo com 300+ especialistas em 55 indústrias e 1.500+ tarefas reais, testando se agentes generalistas (GUI+CLI) fazem trabalho de nível profissional.
- **RealSWE** — benchmark com 381 famílias de tarefas multi-variante para avaliar agentes de coding sob pedidos realistas de usuário, mais próximo do dia a dia do que SWE-bench clássico.
- **AgenticDataBench** — benchmark para agentes de dados automatizando workflows de data science reais em 15 domínios, incluindo casos B2B fintech.

**🔗 Fontes**
- [Cortex — AI Tools for Developers 2026](https://www.cortex.io/post/the-engineering-leaders-guide-to-ai-tools-for-developers-in-2026)
- [Microsoft Agent Framework at BUILD 2026](https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/)
- [doit.software — Top 13 AI Developer Skills 2026](https://doit.software/blog/ai-developer-skills)
- [The New MCP Roadmap — MCP Blog](https://blog.modelcontextprotocol.io/posts/mcp-roadmap/)
- [The 2026-07-28 Specification — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [GitHub Trending (daily, EN)](https://github.com/trending?since=daily&spoken_language_code=en)
- [aiweekly.co — Anthropic News](https://aiweekly.co/ai-news-today/anthropic-news)
- [Sherwood News — OpenAI/Anthropic/Google price wars](https://sherwood.news/tech/openai-anthropic-google-price-wars-where-no-one-is-making-money/)
- [VentureBeat — AI category](https://venturebeat.com/category/ai)
- [andrew.ooo — Cursor/Windsurf/Claude Code comparativo](https://andrew.ooo/answers/cursor-3-7-vs-cursor-4-vs-windsurf-vs-claude-code-june-2026/)
- [arXiv 2510.01375 — Fine-tuning with RAG](https://arxiv.org/abs/2510.01375)
- [arXiv 2603.07379 — SoK Agentic RAG](https://arxiv.org/pdf/2603.07379)
- [arXiv 2601.02993 — Stable-RAG](https://arxiv.org/pdf/2601.02993)
- [Hugging Face Papers — Agents' Last Exam](https://huggingface.co/papers/2606.05405)
- [VoltAgent — awesome-ai-agent-papers](https://github.com/VoltAgent/awesome-ai-agent-papers)
- [InfoWorld — MCP going stateless](https://www.infoworld.com/article/4201254/model-context-protocol-is-going-stateless-to-make-scaling-simpler.html)
