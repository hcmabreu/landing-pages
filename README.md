# landing-pages

Skills de Claude Code para produção de landing pages cinematográficas.

## Skills instaladas (`.claude/skills/`)

| Skill | O que faz | Origem |
| --- | --- | --- |
| `scroll-world` | Landing page "fly through the world" com scroll-scrub: a câmera mergulha de fora para dentro de cada cena e flui para a próxima sem cortes. Entrevista o usuário (tema, brand kit, budget tier, mobile tier), gera cenas + clipes com Higgsfield atrás de gates de aprovação, verifica cada emenda por SSIM e monta um engine de scrub em JS puro. | [cth9191/scroll-world](https://github.com/cth9191/scroll-world) (fork endurecido de oso95/scroll-world) — MIT |
| `higgsfield-generate` | Geração de imagem/vídeo/3D/áudio via Higgsfield. Dependência declarada no Step 0 de `scroll-world`. | [higgsfield-ai/skills](https://github.com/higgsfield-ai/skills) — MIT |

## Pré-requisitos para rodar `scroll-world`

- **Higgsfield CLI** autenticado (`higgsfield auth login`) com créditos.
- **ffmpeg / ffprobe** no `$PATH` (extração de frames e encode).
- **Python 3 + Pillow** (opcional — só para o knockout de fundo das cenas flutuantes).

## Uso

Peça uma landing page scroll-through, ou invoque `/scroll-world`.
