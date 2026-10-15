
# qsoft-frontend-design

Skill do Claude para criar, redesenhar e auditar interfaces web da QSOFT com padrão premium, identidade visual oficial e verificação automática em navegador.

## O que é

Uma skill (`SKILL.md` com materiais de apoio) que orienta o Claude a produzir sites, landing pages, dashboards web e componentes HTML/CSS/React sem a aparência genérica de interfaces geradas por IA. Ela combina cinco frentes em um fluxo único:

| Frente | O que entrega |
|---|---|
| Direção de design (taste) | Três dials de intensidade (variância de layout, movimento e densidade) e lista de padrões genéricos a evitar |
| Diretrizes de interface | Checklist de acessibilidade, formulários, foco, movimento, performance e SEO, com níveis de prioridade |
| Sistema visual da marca | `DESIGN.md` com tokens CSS, tipografia, componentes e regras de uso |
| Imagem para código | Fluxo para transformar screenshots e mockups em código, aplicando a identidade QSOFT |
| Verificação com Playwright | Script que captura screenshots em 375, 768 e 1440 px e roda checagens automáticas |

## Identidade aplicada

- Fundo branco `#FFFFFF` como padrão
- Laranja `#FF7900` como acento gráfico
- Preto `#1D1D1B` e grafite `#303030` para texto
- Orkney em títulos e Open Sans no corpo

**Nota de acessibilidade:** o laranja `#FF7900` sobre branco tem contraste de 2,63:1. A skill usa texto `#1D1D1B` em botões laranja e `#B04E00` para texto e links laranja. Esses tons funcionais são auxiliares e não fazem parte da paleta institucional.

## Estrutura

```
qsoft-frontend-design/
├── SKILL.md                      # Fluxo de trabalho e regras principais
├── assets/
│   └── template-pagina.html      # Página base com tokens, hero, cards, KPIs e formulário
├── references/
│   ├── DESIGN.md                 # Sistema visual QSOFT
│   ├── taste-dials.md            # Dials de direção criativa
│   ├── anti-slop.md              # Padrões genéricos a evitar
│   ├── interface-checklist.md    # Checklist de interface
│   ├── image-to-code.md          # Pipeline imagem para código
│   └── playwright-verify.md      # Guia da verificação visual
└── scripts/
    └── verify.py                 # Verificação com Playwright
```

## Instalação

### Claude (web e desktop)

1. Baixe o arquivo `qsoft-frontend-design.skill` na página de Releases, ou compacte a pasta `qsoft-frontend-design` em `.zip`.
2. Acesse **Configurações > Capacidades > Skills** e envie o arquivo.
3. Ative a skill.

Em contas de organização, o envio de skills pode depender de liberação do administrador.

### Claude Code

```bash
git clone https://github.com/<organizacao>/qsoft-frontend-design.git ~/.claude/skills/qsoft-frontend-design
```

## Uso

Peça ao Claude algo como:

- "Crie uma landing page para o serviço de Time sob Demanda da QSOFT."
- "Transforme este screenshot em uma página HTML com a identidade da QSOFT."
- "Audite este componente React contra o checklist de interface."
- "Monte um layout de dashboard web para indicadores operacionais."

A skill aciona o fluxo: ler o briefing, definir os dials, implementar, verificar no navegador e entregar com as pendências sinalizadas.

## Verificação visual

```bash
pip install playwright
playwright install chromium

python scripts/verify.py assets/template-pagina.html --out verify-out
```

Checagens automáticas: rolagem horizontal, fundo da página, meta viewport, texto branco sobre laranja, contraste de texto, imagens sem `alt`, campos sem rótulo, botões sem nome acessível, erros de console e fontes carregadas. As checagens complementam a revisão visual dos screenshots e não a substituem.

## Pendências de ativos

Este repositório **não inclui** o logotipo oficial nem os arquivos de fonte Orkney e Open Sans. O template usa fallback de fontes e um espaço reservado para o logo. Adicione os arquivos oficiais conforme as regras do BrandBook QSOFT.

## Privacidade e conformidade

Use apenas dados fictícios ou anonimizados em exemplos, páginas de teste e screenshots. Não inclua dados de clientes, contratos ou informações internas. Em caso de dúvida sobre conformidade de dados, consulte o responsável pela governança de dados da organização.

## Créditos de inspiração

Síntese original, escrita para a QSOFT, inspirada nas ideias de:

- [taste-skill](https://github.com/Leonxlnx/taste-skill) (Leonxlnx, MIT)
- [web-design-guidelines](https://github.com/vercel-labs/agent-skills) (Vercel Labs)
- [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) (VoltAgent, MIT)
- [Playwright](https://playwright.dev) para verificação em navegador

Nenhum texto dessas fontes foi copiado.

## Licença

[Definir antes de publicar]. A identidade visual, o logotipo e o BrandBook da QSOFT são propriedade da QSOFT e seguem suas regras de uso.
