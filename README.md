# Weslley Gonçalves

**Software Engineer** · IA generativa e backend · São Paulo, SP

Construo software que coloca IA generativa em produção: agentes, times
multi-agente, RAG e as ferramentas para operar tudo isso com segurança,
versionamento e custo à vista. Trabalho com **Python/FastAPI** e
**TypeScript/Next.js**.

Antes de escrever software, passei mais de uma década sustentando
infraestrutura, redes e segurança. Por isso deploy, observabilidade e dado
sensível entram no primeiro commit, não na última etapa.

[LinkedIn](https://linkedin.com/in/wellcod) · weslleygoncalves18@gmail.com

<details>
<summary><b>In English</b></summary>

<br>

Software Engineer focused on generative AI and backend, based in São Paulo, Brazil.

I build software that puts generative AI into production: agents, multi-agent
teams, RAG, and the tooling to operate them with versioning, safety and visible
cost. I work with **Python/FastAPI** and **TypeScript/Next.js**.

Before writing software I spent more than a decade running infrastructure,
networks and security, so deployment, observability and sensitive-data handling
are part of the first commit rather than a final step.

The projects below are my own work: a platform to operate AI agents in
production (versioned agents, multi-agent teams, workflows, RAG, MCP and
guardrails), an insurance multi-quoting platform integrating real insurer APIs,
and a fully local face authentication service with liveness detection.

</details>

---

## Projetos

### [Automata](https://github.com/WellCod/automata) — plataforma para operar agentes de IA em produção

Quem não programa cria, testa e publica agentes, times multi-agente e workflows.
Cada mudança vira uma versão imutável com rollback, e a API recusa na escrita o
que quebraria em produção. Por cima disso vêm bases de conhecimento (RAG),
ferramentas via MCP com confirmação humana, guardrails de dado pessoal e injeção
de prompt, e analytics de latência e custo por execução.

<a href="https://github.com/WellCod/automata"><img src="https://raw.githubusercontent.com/WellCod/automata/main/docs/img/workflow.png" alt="Editor de workflow do Automata" width="820"></a>

- **Multi-agente:** times que coordenam, roteiam (handoff) ou consultam
  especialistas, e workflows com etapas em paralelo, condições e repetição.
- **RAG:** pgvector no próprio Postgres, ingestão em background, uma busca por
  base e custo de embedding medido.
- **Engenharia:** 14 ADRs, ~270 testes contra Postgres real com testcontainers,
  evals de guardrails, workflows e recuperação no CI, e mypy strict.

`Python` · `FastAPI` · `Agno` · `PostgreSQL` · `pgvector` · `MCP` · `Next.js` · `TypeScript`

### [multi-K](https://github.com/WellCod/multi-k) — multicálculo e gestão de seguros

Plataforma que cota o mesmo risco em várias seguradoras e compara os resultados.
Cada seguradora entra como *adapter* isolado atrás de um contrato único, então
integrar a próxima não toca o domínio. A integração foi exercitada contra a API
real de uma seguradora: JWT ES256, fila de trabalho no próprio Postgres, RLS por
corretora e auditoria append-only.

`Python` · `FastAPI` · `PostgreSQL` · `React` · `TypeScript` · `Docker`

### [FaceGate](https://github.com/WellCod/face-gate) — autenticação facial com liveness

Reconhecimento facial com detecção de vivacidade por piscar, rodando **100%
local**. Sobe com um `docker compose up` e nenhum frame sai da máquina. Dado
biométrico é dado sensível, e tratar assim é requisito, não enfeite.

`Python` · `FastAPI` · `DeepFace/ArcFace` · `MediaPipe` · `Docker`

---

## Como eu trabalho

- **Decisão escrita.** Cada escolha relevante vira um ADR com as alternativas
  descartadas e o que faria voltar atrás.
- **Teste contra o banco de verdade.** Integração com Postgres em container, sem
  mock de banco; com LLM, eval que mede comportamento e não só se o código roda.
- **Segurança desde o primeiro commit.** Segredo fora do bundle, dado pessoal
  tratado na entrada, proteção contra SSRF e falha visível em vez de silenciosa.
- **Leio log antes de chutar.** Penso em *failure mode* e trato credencial como
  responsabilidade, não como detalhe de configuração.

---

## Stack

| | |
|---|---|
| **IA generativa** | Agno · Anthropic e OpenAI · RAG com pgvector · embeddings (Voyage, OpenAI) · MCP · evals |
| **Backend** | Python · FastAPI · SQLAlchemy · Alembic · Node.js · Express |
| **Frontend** | TypeScript · React · Next.js · Tailwind CSS · TanStack Query |
| **Dados** | PostgreSQL · pgvector · Redis · SQLite · MongoDB |
| **Infra e DevOps** | Docker · Docker Compose · Nginx · Linux · GitHub Actions |
| **Fundamentos** | Redes (TCP/IP, DNS, VPN) · Segurança da informação · LGPD |
