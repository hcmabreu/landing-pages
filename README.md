# landing-pages

Skills de Claude Code para produção de landing pages e material visual cinematográfico.

## Como as skills são instaladas

Quase tudo é gerenciado pelo CLI [`skills`](https://www.npmjs.com/package/skills):
as pastas reais ficam em `.agents/skills/` (formato multi-agente, que serve também
Amp, Codex, Cline e outros) e `.claude/skills/` traz apenas symlinks. O
`skills-lock.json` registra origem, caminho e hash de cada skill, então
`npx skills install` reconstrói tudo.

**Exceção:** `scroll-world` é uma pasta real em `.claude/skills/`, copiada à mão do
repositório de origem, porque não é publicada num formato que o CLI resolva.

> Reinstalar uma skill pelo CLI **substitui a pasta inteira** em `.agents/skills/`.
> Não edite nada lá dentro nem adicione arquivos — some na próxima reinstalação.
> Por isso as licenças de terceiros ficam em `licenses/`, fora do alcance do CLI.

## As skills

### Principal

| Skill | O que faz |
| --- | --- |
| `scroll-world` | Landing page "fly through the world" com scroll-scrub: a câmera mergulha de fora para dentro de cada cena e flui para a próxima sem cortes. Entrevista o usuário (tema, brand kit, budget tier, mobile tier), gera cenas + clipes com Higgsfield atrás de gates de aprovação, verifica cada emenda por SSIM e monta um engine de scrub em JS puro. |

### Suíte Higgsfield

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
| `higgsfield` | Os mesmos modelos pelo **MCP** em vez da CLI. |

### Design e frontend

| Skill | O que faz |
| --- | --- |
| `frontend-design` | Direção estética, tipografia e escolhas visuais que não parecem template padrão. |
| `high-end-visual-design` | Fontes, espaçamento, sombras, cards e animações que fazem um site parecer caro; bloqueia os defaults que denunciam design gerado por IA. |
| `web-design-guidelines` | Auditoria de UI contra as Web Interface Guidelines (acessibilidade, UX). |
| `vercel-react-best-practices` | Performance em React/Next.js pela engenharia da Vercel — 76 regras sobre re-render, bundle, async e server. |
| `shadcn` | Componentes e registries shadcn/ui: adicionar, buscar, compor, depurar, aplicar presets. |

## Origens e licenças

| Origem | Skills | Licença |
| --- | --- | --- |
| [cth9191/scroll-world](https://github.com/cth9191/scroll-world) (fork de [oso95](https://github.com/oso95/scroll-world)) | `scroll-world` | MIT — `.claude/skills/scroll-world/LICENSE` |
| [higgsfield-ai/skills](https://github.com/higgsfield-ai/skills) | as 8 `higgsfield-*` | MIT — `licenses/higgsfield-ai-skills.LICENSE` |
| [robonuggets/higgsfield-skill](https://github.com/robonuggets/higgsfield-skill) | `higgsfield` | CC BY 4.0, © 2026 RoboLabs — `.claude/skills/higgsfield/LICENSE` |
| [anthropics/skills](https://github.com/anthropics/skills) | `frontend-design` | Apache 2.0 — `licenses/anthropics-skills.LICENSE` |
| [leonxlnx/taste-skill](https://github.com/leonxlnx/taste-skill) | `high-end-visual-design` | MIT — `licenses/leonxlnx-taste-skill.LICENSE` |
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | `shadcn` | MIT — `licenses/shadcn-ui-ui.LICENSE` |
| [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | `vercel-react-best-practices`, `web-design-guidelines` | **sem licença declarada** |

O repositório da vercel-labs não declara licença. Sem licença, o padrão legal é
"todos os direitos reservados" — vale resolver antes de tornar este repo público.

## Duas interfaces para o Higgsfield

A suíte `higgsfield-*` e o `scroll-world` falam com a **CLI** (`higgsfield …`).
A skill `higgsfield` fala com o **MCP**. São caminhos distintos para o mesmo serviço;
os gatilhos se sobrepõem para pedidos genéricos de gerar imagem ou vídeo.

## Pré-requisitos para rodar `scroll-world`

- **Higgsfield CLI** autenticado (`higgsfield auth login`) com créditos.
- **ffmpeg / ffprobe** no `$PATH` (extração de frames e encode).
- **Python 3 + Pillow** (opcional — só para o knockout de fundo das cenas flutuantes).

`higgsfield-brandkit` e `higgsfield-websites` trazem scripts Python próprios em
`scripts/`, invocados via `$SKILL_ROOT`.

## Uso

Peça uma landing page scroll-through, ou invoque `/scroll-world`.
