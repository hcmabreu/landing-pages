# landing-pages

Skills de Claude Code para produção de landing pages e material visual cinematográfico
com Higgsfield.

## Skills instaladas (`.claude/skills/`)

### A skill principal

| Skill | O que faz |
| --- | --- |
| `scroll-world` | Landing page "fly through the world" com scroll-scrub: a câmera mergulha de fora para dentro de cada cena e flui para a próxima sem cortes. Entrevista o usuário (tema, brand kit, budget tier, mobile tier), gera cenas + clipes com Higgsfield atrás de gates de aprovação, verifica cada emenda por SSIM e monta um engine de scrub em JS puro. |

Origem: [cth9191/scroll-world](https://github.com/cth9191/scroll-world) — fork endurecido de
[oso95/scroll-world](https://github.com/oso95/scroll-world). MIT (`scroll-world/LICENSE`).

### Suíte oficial Higgsfield

| Skill | O que faz |
| --- | --- |
| `higgsfield-generate` | Geração de imagem/vídeo/3D/áudio. Dependência declarada no Step 0 do `scroll-world`. |
| `higgsfield-brandkit` | Sistemas visuais completos: paletas, logo em SVG, tipografia, mockups, packaging, brandbook em PPTX/PDF. |
| `higgsfield-websites` | Sites, apps e jogos full-stack (React 19 + TanStack SSR em Cloudflare Worker), com deploy. Também cobre arte de jogo. |
| `higgsfield-product-photoshoot` | Fotos de produto e criativos de paid social. |
| `higgsfield-marketplace-cards` | Cards de listagem para marketplace e conteúdo A+. |
| `higgsfield-video-explainer` | Vídeo explicativo narrado, montado a partir de blocos de 10 s. |
| `higgsfield-youtube-thumbnail` | Thumbnails de YouTube e capas verticais. |
| `higgsfield-soul-id` | Treina um Soul Character para consistência de identidade em imagem e vídeo. |

Origem: [higgsfield-ai/skills](https://github.com/higgsfield-ai/skills).
MIT (`LICENSE.higgsfield-ai`).

### Alternativa via MCP

| Skill | O que faz |
| --- | --- |
| `higgsfield` | Acesso a 30+ modelos de imagem e vídeo pelo **MCP** do Higgsfield, sem a CLI. |

Origem: [robonuggets/higgsfield-skill](https://github.com/robonuggets/higgsfield-skill).
CC BY 4.0 — © 2026 RoboLabs (`higgsfield/LICENSE`).

### Design e frontend (via `npx skills add`)

Instaladas pelo CLI `skills`, que grava as skills em `.agents/skills/` (layout
multi-agente) e cria symlinks em `.claude/skills/`. O `skills-lock.json` na raiz
registra origem e hash de cada uma.

| Skill | O que faz | Origem | Licença |
| --- | --- | --- | --- |
| `frontend-design` | Direção estética, tipografia e escolhas visuais que não parecem template padrão. | `anthropics/skills` | Apache 2.0 |
| `high-end-visual-design` | Fontes, espaçamento, sombras, cards e animações que fazem um site parecer caro; bloqueia os defaults que denunciam design gerado por IA. | `leonxlnx/taste-skill` | MIT |
| `vercel-react-best-practices` | Performance em React/Next.js pela engenharia da Vercel — 76 regras sobre re-render, bundle, async e server. | `vercel-labs/agent-skills` | sem licença declarada |
| `web-design-guidelines` | Auditoria de UI contra as Web Interface Guidelines (acessibilidade, UX). | `vercel-labs/agent-skills` | sem licença declarada |

## Dois layouts de skill neste repo

As skills do Higgsfield e a `scroll-world` são pastas normais em `.claude/skills/`.
As quatro de design ficam em `.agents/skills/` com symlink a partir de `.claude/skills/`,
porque foi assim que o CLI `skills` as instalou. Ambos funcionam; a diferença importa
só se você for mover ou versionar as pastas à mão.

## Duas interfaces para o Higgsfield

A suíte `higgsfield-*` oficial e o `scroll-world` são escritos para a **CLI** (`higgsfield …`).
A skill `higgsfield` da robonuggets é escrita para o **MCP**. São caminhos distintos para o
mesmo serviço — escolha conforme o que estiver disponível na sessão.

## Pré-requisitos para rodar `scroll-world`

- **Higgsfield CLI** autenticado (`higgsfield auth login`) com créditos.
- **ffmpeg / ffprobe** no `$PATH` (extração de frames e encode).
- **Python 3 + Pillow** (opcional — só para o knockout de fundo das cenas flutuantes).

O `higgsfield-brandkit` e o `higgsfield-websites` também trazem scripts Python próprios
(`scripts/`), invocados via `$SKILL_ROOT`.

## Uso

Peça uma landing page scroll-through, ou invoque `/scroll-world`.
