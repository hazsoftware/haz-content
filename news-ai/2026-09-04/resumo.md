# Resumo IA para Devs — 04/09/2026

**📰 Novidades para Devs**

**Modelos e APIs**
- Anthropic lançou **Fable 5.1** (uso geral) e o **Mythos 5.1** (acesso restrito a pesquisadores/defensores), com janela de contexto de 1M tokens e corte de 75% no preço de leitura de cache de prompt — reduz bastante o custo de sessões longas de agentes.
- Google lançou o **Gemini 3.8 Flash** ao mesmo preço do 3.7 Flash, com variante "Cyber" restrita (Fairwind-gated); a empresa está realocando mais compute para melhorar desempenho em coding.
- **DeepSeek V4 Flash**: modelo de coding que chega perto do Claude Opus 4.8 em qualidade custando ~99% menos por output comparável — pressão forte em preço para tarefas de codegen.
- **Qwen 3.6-Plus**: modelo agentic-first, 1M de contexto, coding em nível de repositório inteiro e uso de ferramentas nativo via MCP.

**Ferramentas e Frameworks**
- **Microsoft Agent Framework 1.0**: APIs estáveis, compromisso de LTS, suporte completo a MCP embutido, e um DevUI no navegador que visualiza execução do agente e chamadas de tools em tempo real.
- **MCP (Model Context Protocol)** — spec 2026-07-28 trouxe núcleo stateless, Multi Round-Trip Requests, roteamento por headers, resultados de listagem cacheáveis, endurecimento de autorização e um framework formal de extensões. SDKs TS e Python já passaram de 1 bilhão de downloads cada.
- Novo roadmap do MCP publicado em 22/08; entraram novos mantenedores (Clare Liguori no Core, Den Delimarsky como Lead Maintainer), sinal de maturidade crescente do protocolo como camada padrão de interoperabilidade agente↔ferramenta.

**Agentes e Automação**
- `anthropics/commerce-agents`: blueprint oficial da Anthropic para agentes de compra/venda com Claude (varejo, telecom, entretenimento).
- `reef` (Human-Agent-Society): infraestrutura de aprendizado contínuo para agentes que se auto-aprimoram sem re-treino completo.
- `reverify`: servidor MCP que faz verificação determinística (anti-alucinação) de claims de agentes que leem binários — cada afirmação é VERIFICADA ou REFUTADA contra os bytes reais.
- `useagent`: "coworker" de IA open-source que roda Claude Code, Codex e OpenCode sobre sua própria assinatura, entregando PRs, planilhas e relatórios prontos.

**Infraestrutura e Deploy**
- Coding virou o principal campo de batalha entre labs — Google, Anthropic e OpenAI redirecionando compute e pesquisa especificamente para modelos de codegen.
- Anthropic revelou ~US$ 71 bilhões em compromissos de compute, sinal de aposta pesada em capacidade para os próximos ciclos de modelos.
- Custo de inferência caindo rápido em modelos de coding (ex. DeepSeek V4 Flash), o que empurra mais workloads de produção para modelos abertos/baratos com fallback para modelos de ponta em tarefas críticas.

**🔥 Repositórios em Alta no GitHub**
- **anthropics/commerce-agents** (Python, ⭐ 1.8k desde 01/09) — blueprint de referência da própria Anthropic para construir agentes de compras/vendas com Claude.
- **2akouwu/reverify** (Python, ⭐ 843) — servidor MCP + CLI de anti-alucinação: agente propõe, tooling determinístico confirma ou refuta contra os dados reais (análise de binários/reverse engineering).
- **Ryze-AI-Adgent/open-seo-mcp-skills** (Shell, ⭐ 432) — skills de SEO/GEO open-source para Claude via MCP, integrando Search Console, GA4 e DataForSEO.
- **Human-Agent-Society/reef** (Python, ⭐ 351) — infra de continual learning para agentes autônomos que melhoram com o uso, sem retraining completo.
- **useagenthq/useagent** (TypeScript, ⭐ 284) — coworker de IA open-source que orquestra Claude Code/Codex/OpenCode com sandbox próprio e integrações Slack/Postgres.
- **op7418/guizang-yingzao-skill** (Python, ⭐ 292) — skill para Claude Code/Codex que transforma fotos em pôsteres editoriais com direção de arte via GPT Image.

**🛠️ Técnicas e Skills em Alta**
- **Orquestração multiagente**: coordenar vários modelos/agentes especializados (ex. um modelo "orquestrador" delegando para modelos de execução) virou padrão de arquitetura, não exceção.
- **Prompt engineering estruturado**: papéis explícitos, few-shot e formatos de saída bem definidos superam instruções vagas; profissionais com essa skill têm prêmio salarial de até 56%.
- **RAG agentic**: em vez de retrieval estático, agentes decidem dinamicamente estratégia de busca, refletem sobre resultados e re-consultam — inclui abordagens baseadas em grafo (entidades/causalidade) em vez de chunking simples.
- **Evals e observabilidade como padrão**: guardrails, testes automatizados de qualidade de output e verificação de uso de tools entram na checklist básica de qualquer pipeline de agente em produção.
- **MCP como camada de integração padrão**: cada vez mais ferramentas, skills e serviços internos são expostos via servidores MCP em vez de integrações ad-hoc.
- **Memória procedural de agentes**: agentes salvando "como fiz da última vez" (skills/procedimentos reutilizáveis) para não repetir erros nem retreinar do zero.

**📄 Papers em Tendência**
- **Fine-tuning with RAG for Improving LLM Learning of New Skills** (arXiv 2510.01375) — converte retrieval em tempo de inferência em competência aprendida via destilação de dicas extraídas de falhas do agente; generaliza entre escalas de modelo (7B/14B) e arquiteturas (ReAct/StateAct).
- **SoK: Agentic RAG** (arXiv 2603.07379) — taxonomia sistemática de arquiteturas, avaliação e direções de pesquisa para RAG agentic, útil como mapa de referência para quem está desenhando pipelines.
- **Towards Agentic RAG with Deep Reasoning** (arXiv 2507.09477) — survey sobre como combinar reasoning profundo com estratégias de retrieval dinâmico.
- **Agentic Retrieval-Augmented Generation: A Survey** (arXiv 2501.09136) — survey fundacional sobre como padrões de reflexão, planejamento e uso de ferramentas embutidos no pipeline de RAG superam o RAG tradicional.
- **SOPRAG** — proposta para substituir RAG baseado em chunks planos por "graph experts" que entendem relações entre entidades, causalidade e fluxos de processo em documentos estruturados.
- **ProcMEM** — investiga agentes salvando habilidades procedurais passo a passo de execuções anteriores para reuso, sem necessidade de retreinamento.

**🔗 Fontes**
- [AI Tools for Developers 2026 — Cortex](https://www.cortex.io/post/the-engineering-leaders-guide-to-ai-tools-for-developers-in-2026)
- [AI Agents News — Week of September 4, 2026](https://aiagentstore.ai/ai-agent-news/this-week)
- [Releases · microsoft/agent-framework](https://github.com/microsoft/agent-framework/releases)
- [Top AI Skills for Developers 2026 — CreateBytes](https://createbytes.com/insights/future-proof-developer-career-ai-skills)
- [awesome-ai-agent-papers — VoltAgent](https://github.com/VoltAgent/awesome-ai-agent-papers)
- [Fine-tuning with RAG (arXiv 2510.01375)](https://arxiv.org/abs/2510.01375)
- [SoK: Agentic RAG (arXiv 2603.07379)](https://arxiv.org/pdf/2603.07379)
- [Towards Agentic RAG with Deep Reasoning (arXiv 2507.09477)](https://arxiv.org/pdf/2507.09477)
- [Agentic RAG: A Survey (arXiv 2501.09136)](https://arxiv.org/abs/2501.09136)
- [New AI Model Releases — Local AI Zone](https://local-ai-zone.github.io/blog/September_2026_AI_Model_Updates.html)
- [Google's new Gemini AI could beat OpenAI, Anthropic in coding — The Hans India](https://www.thehansindia.com/technology/tech-news/googles-new-gemini-ai-could-beat-openai-anthropic-in-coding-1116974)
- [The 2026-07-28 Specification — MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [The New MCP Roadmap — MCP Blog](https://blog.modelcontextprotocol.io/posts/mcp-roadmap/)
- [GitHub Trending, AI/ML](https://github.com/trending?since=daily&spoken_language_code=en)
- [anthropics/commerce-agents](https://github.com/anthropics/commerce-agents)
- [2akouwu/reverify](https://github.com/2akouwu/reverify)
- [Ryze-AI-Adgent/open-seo-mcp-skills](https://github.com/Ryze-AI-Adgent/open-seo-mcp-skills)
- [Human-Agent-Society/reef](https://github.com/Human-Agent-Society/reef)
- [useagenthq/useagent](https://github.com/useagenthq/useagent)
- [op7418/guizang-yingzao-skill](https://github.com/op7418/guizang-yingzao-skill)
