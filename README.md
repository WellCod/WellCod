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
production (versioned agents with gradual rollout, multi-agent teams, workflows
with human review, RAG with source connectors, MCP, guardrails, cost controls,
an audit trail, SSO and per-agent test suites with an LLM judge that gate
publishing), an insurance multi-quoting platform integrating real insurer APIs,
a fully local face authentication service with liveness detection, and a
GPU-based streaming TTS server with LiveKit integration and pt-BR text normalization.

</details>

---

## Projetos

### [Automata](https://github.com/WellCod/automata) — plataforma para operar agentes de IA em produção

Quem não programa cria, testa e publica agentes, times multi-agente e workflows.
Cada mudança vira uma versão imutável com rollback, sai aos poucos para uma parte
das conversas (canário) e fica numa trilha de auditoria, e a API recusa na escrita
o que quebraria em produção. Cada agente tem uma suíte de testes, com juiz por LLM,
que pode travar a publicação e roda agendada, avisando no canal do time quando
algo regride. Por cima disso vêm bases de conhecimento (RAG) sincronizadas com
GitHub, S3, SharePoint e Google Drive, ferramentas via MCP com confirmação humana,
guardrails de dado pessoal e injeção de prompt, controle de custo por run e por
usuário, os direitos do titular da LGPD (exportar e apagar os dados de uma pessoa)
e login por SSO com o provedor de identidade da empresa.


- **Multi-agente:** times que coordenam, roteiam (handoff) ou consultam
  especialistas, e workflows com etapas em paralelo, condições, roteador,
  repetição e revisão humana com edição da saída.
- **Qualidade do agente:** suíte por agente com checagem de texto, de tools e de
  juiz por LLM, gate de publicação por suíte verde, regressão entre versões e
  caso de teste criado a partir de uma conversa real, com dados pessoais mascarados.
- **RAG:** pgvector no próprio Postgres, corte e estratégia de busca por base
  (MMR, recência, HyDE, cross-encoder), filtros por metadados escolhidos pelo
  modelo, conectores com webhook da origem e worker de ingestão separado.
- **Operação:** liberação gradual por sessão com comparação de erro, latência,
  custo e suíte entre as versões, trilha de auditoria com o antes e o depois das
  ações de produção e SSO por OIDC com o papel vindo do grupo.
- **Engenharia:** 42 ADRs, ~1.240 testes contra Postgres real com testcontainers,
  evals de guardrails, workflows, recuperação, custo e SSO no CI, fila durável
  para runs em background, rotação de chaves sem derrubar sessão e mypy strict.

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

### [k-voice](https://github.com/WellCod/k-voice) — servidor de síntese de voz com streaming em GPU

Servidor TTS próprio para tirar da ElevenLabs um agente de voz que atende
ligações (LiveKit/SIP) e as mensagens de áudio do WhatsApp. Roda o Qwen3-TTS,
modelo aberto com licença comercial, atrás de uma interface única de motor:
trocar de modelo não mexe em API, roteamento nem normalização. A fala começa
antes de a frase terminar de ser gerada, e com a fila do motor cheia o roteador
cai para a ElevenLabs em vez de atrasar a ligação. O serviço está pronto e
testado; a troca espera o teste cego e a medição de latência em GPU.

- **Streaming:** texto chegando em pedaços do LLM, cada frase completa vai para
  o motor na hora e, em GPU, o primeiro áudio sai antes do fim da frase
  (`faster-qwen3-tts`). Cancelamento imediato para quando a pessoa interrompe.
- **pt-BR:** normalização determinística testada por tabela (moeda, datas, CPF,
  telefone, siglas, anglicismos) e dicionário de pronúncia por cliente, que vale
  mesmo com o termo partido entre dois pedaços do LLM.
- **Vozes:** clonagem a partir de referência com consentimento registrado e
  áudio cifrado em repouso, além das vozes prontas do modelo.
- **Integração:** plugin LiveKit com fallback, lote em OGG/Opus com URL
  assinada, servidor MCP e API compatível com a ElevenLabs (troca só a URL e a chave).
- **Engenharia:** 8 ADRs, 176 testes com Postgres real via testcontainers,
  mypy strict, versões do modelo fixadas e latência afirmada só com medição no
  repositório.

`Python` · `FastAPI` · `PyTorch + CUDA` · `Qwen3-TTS` · `LiveKit Agents` · `PostgreSQL` · `S3` · `MCP` · `Docker`

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

