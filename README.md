# Weslley Gonçalves

**Engenheiro de IA** · agentes de IA em produção, LLM, RAG e MCP · São Paulo, SP

Trabalho com **Python/FastAPI** e **TypeScript/Next.js**. No trabalho, opero dezenas
de agentes em produção que atendem milhares de conversas no WhatsApp e por voz.
Com o time, construí a plataforma interna que substituiu um fornecedor externo a
cerca de um décimo do custo. Também integrei o time de tecnologia de um projeto
reconhecido pela Meta como case global de soluções via WhatsApp.

Antes de escrever software, passei mais de uma década em infraestrutura, redes e segurança.

[LinkedIn](https://linkedin.com/in/wellcod) · weslleygoncalves18@gmail.com

<details>
<summary><b>In English</b></summary>

<br>

AI Engineer in São Paulo, Brazil. I work with Python/FastAPI and TypeScript/Next.js.
I operate dozens of production AI agents that handle thousands of conversations over
WhatsApp and voice. The platform I built with my team replaced an external vendor at
about one tenth of the cost. I also worked on a project Meta recognized as a global
WhatsApp case study.

My portfolio includes Automata for operating AI agents, Pixelwork for real-time
collaboration with a local Portuguese-speaking AI receptionist, multi-K for insurance
quoting, and k-voice for GPU-streamed speech synthesis.

</details>

---

## Projetos

### [Automata](https://github.com/WellCod/automata) — plataforma para operar agentes de IA em produção

Plataforma para equipes criarem e operarem agentes sem programar. As versões são
imutáveis, com auditoria, implantação gradual e rollback.

- **Agentes e workflows.** Handoff entre especialistas, etapas paralelas, revisão
  humana e ferramentas MCP com confirmação.
- **RAG e governança.** Busca no pgvector, conectores para GitHub, S3,
  SharePoint e Google Drive, SSO por OIDC, guardrails de dados pessoais e controles
  de custo por execução e usuário.
- **Qualidade e operação.** Suítes por agente com juiz por LLM podem bloquear a
  publicação. O canário compara erros, latência e custo, com traces OpenTelemetry
  sem o texto da conversa.
- **Engenharia.** 43 ADRs, ~1.280 testes com PostgreSQL via Testcontainers, fila
  durável e rotação de chaves durante a sessão.

`Python` · `FastAPI` · `Agno` · `PostgreSQL` · `pgvector` · `MCP` · `OpenTelemetry` · `Next.js` · `TypeScript`

### [Pixelwork](https://github.com/WellCod/Pixelwork) — coworking virtual em pixel art

Escritório 2D com mídia por proximidade, reuniões privadas, editor de mapas e
minijogos. O servidor valida movimentos e acesso às salas, e o cliente prevê os
passos e interpola os avatares.

- **Prévia antes do login.** A tela de entrada mostra a Sala Aurora, o lounge e a área de jogos.
- **Recepcionista com voz local.** Atende em português e destaca rotas no mapa.
  Faster Whisper, Qwen e Piper rodam na máquina da demo, sem chave de API.
- **Aquário e corrida multiplayer.** Alimente os animais do aquário interativo ou
  dispute uma corrida 1x1 com um jogador em cada fliperama.
- **Compartilhamento de tela.** Apresente uma janela, aba ou tela em salas de reunião e chamadas privadas. Quem recebe pode ver a apresentação em tela cheia.

`TypeScript` · `React` · `Phaser` · `Fastify` · `WebSocket` · `PostgreSQL` · `LiveKit`

[Telas da demo](https://github.com/WellCod/Pixelwork#telas) · [Configuração e medições de voz local](https://github.com/WellCod/Pixelwork#recepcionista-com-voz-local)

### [multi-K](https://github.com/WellCod/multi-k) — multicálculo e gestão de seguros

Plataforma que cota o mesmo risco em várias seguradoras e compara os resultados.
Cada seguradora entra como *adapter* isolado atrás de um contrato único, então
integrar a próxima não toca o domínio. A integração foi exercitada contra a API
real de uma seguradora: JWT ES256, fila de trabalho no próprio Postgres, RLS por
corretora e auditoria append-only.

`Python` · `FastAPI` · `PostgreSQL` · `React` · `TypeScript` · `Docker`

### [k-voice](https://github.com/WellCod/k-voice) — servidor de síntese de voz com streaming em GPU

Servidor Qwen3-TTS para chamadas via LiveKit/SIP e áudios de WhatsApp. A adoção
no atendimento aguarda o teste cego e a medição de latência em GPU.

- **Streaming.** Sintetiza enquanto recebe texto do LLM, permite interrupção
  e reutiliza falas frequentes em cache. O fallback para ElevenLabs cobre fila cheia.
- **Português do Brasil.** Normalização determinística e dicionário por cliente.
  A transcrição automática mediu 1,7% de WER nas frases de referência.
- **Vozes e integração.** Clonagem com consentimento e referências cifradas, plugin
  LiveKit, síntese em lote, MCP e API compatível com ElevenLabs.
- **Engenharia.** 8 ADRs, 329 testes com PostgreSQL via Testcontainers e mypy strict.

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
| **Infra e DevOps** | AWS (EC2, S3) · Docker · Docker Compose · Nginx · Linux · GitHub Actions · Datadog |
| **Fundamentos** | Redes (TCP/IP, DNS, VPN) · Segurança da informação · LGPD |

