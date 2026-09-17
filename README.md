# Weslley Gonçalves

**Software Engineer** · Backend & Full Stack · São Paulo, SP

Mais de uma década sustentando infraestrutura, redes e segurança antes de
escrever software. Hoje construo aplicações em **Python/FastAPI** e
**TypeScript/React** — com deploy, observabilidade e tratamento de dado sensível
pensados desde a primeira linha, não como etapa final.

[LinkedIn](https://linkedin.com/in/wellcod) · weslleygoncalves18@gmail.com

---

## Projetos

### [multi-K](https://github.com/WellCod/multi-k) — multicálculo e gestão de seguros

Plataforma que cota o mesmo risco em várias seguradoras e compara os resultados.
Cada seguradora entra como *adapter* isolado atrás de um contrato único, então
integrar a próxima não toca o domínio. Integração real em produção com API
externa: JWT ES256, fila de trabalho no próprio Postgres, RLS por corretora e
auditoria append-only.

`Python` · `FastAPI` · `PostgreSQL` · `React` · `TypeScript` · `Docker`

### [FaceGate](https://github.com/WellCod/face-gate) — autenticação facial com liveness

Reconhecimento facial com detecção de vivacidade por piscar, rodando **100%
local**. Sobe com um `docker compose up` e nenhum frame sai da máquina — dado
biométrico é dado sensível, e tratar assim é requisito, não enfeite.

`Python` · `FastAPI` · `DeepFace/ArcFace` · `MediaPipe` · `Docker`

### [Automata](https://github.com/WellCod/automata) — painel para operar agentes de IA

Prompt versionado com rollback, troca de modelo sem reescrever instruções e custo
estimado antes de publicar. Nasceu de um incômodo concreto: agente em produção
costuma ser editado no escuro.

`Python` · `FastAPI` · `Next.js` · `TypeScript` · `PostgreSQL`

---

## Stack

| | |
|---|---|
| **Backend** | Python · FastAPI · Node.js · Express |
| **Frontend** | TypeScript · JavaScript · React · Next.js · Tailwind CSS |
| **Dados** | PostgreSQL · SQLite · MongoDB |
| **Infra & DevOps** | Docker · Docker Compose · Nginx · Linux · GitHub Actions |
| **Fundamentos** | Redes (TCP/IP, DNS, VPN) · Segurança da informação · LGPD |

---

## De infra para engenharia

Antes de escrever software, passei anos sustentando o que roda embaixo dele:
redes, servidores, DataCenter, telecom e segurança. Isso me deixou com hábitos
que costumam faltar — leio log antes de chutar, penso em *failure mode*, e trato
credencial e dado pessoal como responsabilidade, não como detalhe de
configuração.

É de onde vem o que faço hoje: sistema que alguém precisa manter de pé às três da
manhã.
