# Resumo IA para Devs — 03/09/2026

**📰 Novidades para Devs**

**Modelos e APIs**
- Anthropic tornou o **Claude Fable 5.1** GA em 1/set, mantendo preço ($10/$50), com janela de contexto de 1M tokens e corte de 75% no preço de cache-read de prompt; lançou também o **Mythos 5.1**, versão com salvaguardas extras e acesso restrito a pesquisadores/defensores vetados.
- Google lançou o **Gemini 3.8 Flash (Cyber)**, focado em descoberta autônoma de vulnerabilidades, superando modelos maiores da concorrência (Mythos 5, GPT-5.6 Sol/GPT-5.5-Cyber) em benchmarks de segurança ofensiva.
- Qwen lançou o **Qwen3.8-Max-0902** (2/set), reforçando a cadência agressiva de releases dos modelos abertos chineses.
- O **MCP (Model Context Protocol)** publicou novo roadmap (22/ago) após a spec de 28/jul trazer core stateless, multi round-trip requests, cache de list results e hardening de autorização (CIMD substituindo Dynamic Client Registration).

**Ferramentas e Frameworks**
- **LangGraph** ganhou timeouts por nó, handlers de erro por nó, shutdown gracioso cooperativo, `DeltaChannel` (menos overhead de checkpoint) e API de streaming tipada v2.
- **LlamaIndex Workflows 1.0** consolidou o modelo de orquestração baseado em eventos para pipelines de agentes.
- O repositório **anthropics/skills** (Agent Skills) segue em alta, junto com **Graphify**, que transforma qualquer codebase em um grafo de conhecimento consultável por Claude Code e outros agentes.

**Agentes e Automação**
- **AgentZ** (AccuKnox): plataforma agnóstica de modelo que empacota agentes, sandboxes, workflows, RBAC, injeção de credenciais em runtime e trilhas de auditoria — foco em levar agentes de experimento para produção (SaaS, on-prem ou air-gapped).
- **OpenClaw** é apontada como um dos projetos open-source de crescimento mais rápido do ano: agentes que navegam na web, executam código, gerenciam arquivos e orquestram workflows multi-etapas continuamente.
- Padrão **Agent Skills** (usado pelo Claude Code) ganha tração como forma de empacotar conhecimento reutilizável para agentes, com pesquisas como o Corpus2Skill compilando corpora inteiros em árvores de skills navegáveis.

**Infraestrutura e Deploy**
- **vLLM** segue como escolha padrão de facto para serving de inferência em escala.
- A arquitetura stateless do novo MCP permite distribuir requisições entre servidores via load balancer simples, sem estado compartilhado — facilita deploy de servidores MCP em produção.

**🔥 Repositórios em Alta no GitHub**
- **NousResearch/hermes-agent** — agente que "cresce com você"; forte tração em agentes personalizáveis de longo prazo.
- **anthropics/skills** — repositório oficial de Agent Skills para Claude, referência para quem quer empacotar workflows reutilizáveis.
- **jingyaogong/minimind** (Python) — treina um LLM de 64M parâmetros do zero em 2h; ótimo para entender o pipeline completo de pretraining sem custo de nuvem.
- **MakazhanAlpamys/Soup** — fine-tuning de LLMs a partir de um único YAML, com layer streaming permitindo treinar um modelo de 8B numa GPU de laptop de 4GB.
- **Graphify-Labs/graphify** — converte qualquer codebase em grafo de conhecimento consultável, pensado para uso com Claude Code e outros agentes de codificação.
- **google-research/timesfm** — modelo fundacional de séries temporais do Google Research para forecasting.
- **datacurve-ai/deep-swe** — benchmark para medir agentes de codificação de fronteira em tarefas de engenharia longas e realistas.

**🛠️ Técnicas e Skills em Alta**
- **Orquestração de múltiplos agentes**: coordenar vários agentes especializados (planner/coder/critic) virou habilidade central, não mais exceção — visto em frameworks como LangGraph e em papers como o OptimAI.
- **RAG + fine-tuning combinados**: em vez de só recuperar contexto em runtime, times estão destilando falhas de agentes em RAG para gerar trajetórias de treino melhores, reduzindo custo de inferência.
- **Agent Skills / packaging de conhecimento**: compilar conhecimento de domínio em "skills" navegáveis pelo agente (em vez de prompts gigantes) está virando padrão, inclusive fora do Claude Code.
- **Evals e observabilidade como parte do dia a dia**: guardrails automatizados, checagem de tool-use e testes de regressão para outputs de LLM entraram no checklist básico de qualquer pipeline de agente.
- **Linguagens tipadas por padrão**: TypeScript ultrapassou Python como linguagem mais usada no GitHub; times preferem TS, Python com type hints, Rust ou Go em projetos novos com geração de código por IA.
- **Fine-tuning leve e local**: técnicas de layer streaming e YAML-driven fine-tuning (ex. Soup) tornam viável treinar modelos de 7-8B em hardware de consumidor.

**📄 Papers em Tendência**
- **Fine-tuning with RAG for Improving LLM Learning of New Skills** — destila falhas recorrentes de agentes em RAG runtime para gerar trajetórias de professor melhores, convertendo retrieval em competência aprendida via fine-tuning.
- **SoK: Agentic RAG (Taxonomy, Architectures, Evaluation)** — mapeamento sistemático de como RAG agentic incorpora reflexão, planejamento e uso de ferramentas para gerenciar retrieval dinamicamente.
- **OptimAI** — pipeline de 4 agentes (Formulator, Planner, Coder, Critic) que transforma problemas de otimização em linguagem natural em código de solver funcional.
- **Corpus2Skill** — compila um corpus offline em uma árvore hierárquica de Agent Skills que o LLM navega em tempo de consulta, em vez de depender só de retrieval bruto.
- **ProgRouter** (EMNLP 2026) — orquestração online guiada por progresso para workflows multi-agente sob trade-off de qualidade vs. custo.
- **Safety Testing LLM Agents at Scale** — framework para descoberta de riscos e verificação com evidências em testes de segurança de agentes em larga escala.

**🔗 Fontes**
- [Top 10 AI Engineering Tools Everyone is Using in 2026](https://www.analyticsvidhya.com/blog/2026/06/ai-engineering-tools-everyone-is-using-in-2026/)
- [AI Agents News — Week of September 3, 2026](https://aiagentstore.ai/ai-agent-news/this-week)
- [Releases · microsoft/agent-framework](https://github.com/microsoft/agent-framework/releases)
- [New AI Model Releases News | September 2026](https://blog.mean.ceo/new-ai-model-releases-news-september-2026/)
- [AI Updates Today (September 2026) – LLM Stats](https://llm-stats.com/llm-updates)
- [Google, Anthropic, and OpenAI Unveil Cyber AI Models — The Hacker News](https://thehackernews.com/2026/09/google-anthropic-and-openai-unveil.html)
- [Latest AI Model Releases — AI Release Tracker](https://aireleasetracker.com/latest)
- [The 2026-07-28 Specification — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [The New MCP Roadmap — MCP Blog](https://blog.modelcontextprotocol.io/posts/mcp-roadmap/)
- [MCP protocol receives major update — ITdaily](https://itdaily.com/news/software/mcp-2026-update-specs/)
- [Top AI GitHub Repositories in 2026 — ByteByteGo](https://blog.bytebytego.com/p/top-ai-github-repositories-in-2026)
- [Trending AI Repositories — OSSInsight](https://ossinsight.io/trending/ai)
- [GitHub Trending (daily, EN)](https://github.com/trending?since=daily&spoken_language_code=en)
- [GitHub Trending Python (daily)](https://github.com/trending/python?since=daily)
- [Fine-tuning with RAG for Improving LLM Learning of New Skills — arXiv](https://arxiv.org/abs/2510.01375)
- [SoK: Agentic Retrieval-Augmented Generation — arXiv](https://arxiv.org/pdf/2603.07379)
- [awesome-ai-agent-papers — VoltAgent](https://github.com/VoltAgent/awesome-ai-agent-papers)
- [Safety Testing LLM Agents at Scale — arXiv](https://arxiv.org/abs/2607.01793)
- [Top AI Skills for Developers 2026 — HackerNoon](https://hackernoon.com/5-must-have-ai-skills-for-developers-in-2026-and-how-to-learn-them)
- [Developer AI Tooling in 2026 — platform.uno](https://platform.uno/blog/ai-tooling-trends-shaping-how-we-build/)
