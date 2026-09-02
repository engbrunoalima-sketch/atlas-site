# ATLAS — Site institucional (GitHub Pages)

Site público do produto ATLAS, montado a partir do pitch/deck
`ATLAS_Biomechanical_Performance.pdf`. Scroll narrativo em tela cheia,
15 seções (uma por slide) + formulário de contato real no final.

**Este site é totalmente independente do firmware do ESP8266.** A
página de controle (BRAÇO/TELA) continua embutida no `.ino` e roda
100% local, sem depender de internet nem deste repositório.

## Estrutura

```
├── index.html                        ← página principal
├── css/
│   ├── landing.css                    ← estilo do site institucional
│   └── style-painel-controle.css      ← CSS do painel do dispositivo
│                                         (não usado por este site;
│                                         guardado aqui só de referência,
│                                         caso decida reaproveitar depois)
└── assets/slides/                     ← 15 imagens extraídas do PDF
```

## Publicando

```bash
git init
git add .
git commit -m "Site ATLAS v1"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/bvl-atlas-site.git
git push -u origin main
```

No GitHub: `Settings` → `Pages` → branch `main`, pasta `/ (root)` → Save.
URL final: `https://SEU-USUARIO.github.io/bvl-atlas-site/`

## Antes de publicar, edite

1. **Formulário de contato** (`index.html`, seção `#contato`):
   ```html
   <form class="contact-form" action="mailto:contato@SEU-DOMINIO.com" ...>
   ```
   Troque pelo seu e-mail real. **Atenção**: `mailto` em formulário abre
   o cliente de e-mail do visitante (Outlook, Gmail app, etc.) — funciona,
   mas é rústico e alguns navegadores mobile bloqueiam. Se quiser algo
   mais profissional, troque por um serviço tipo Formspree ou Google
   Forms (envio direto, sem abrir app externo) — me avisa se quiser
   ajuda com isso depois.

2. **Domínio nos links** — não há links externos fixos além do
   Google Fonts (CDN), então não tem mais nada pra trocar além do
   formulário.

## Sobre as imagens

As 15 imagens em `assets/slides/` foram extraídas diretamente do PDF
(cada slide já vem com o texto "assado" na própria arte, gerado pela
ferramenta que criou o deck). Isso significa:

- ✅ Fidelidade visual 100% igual ao pitch original
- ✅ Site simples de manter — trocar uma seção é só trocar a imagem
- ⚠️ Texto dentro das imagens não é selecionável nem indexável por
  buscadores. Descrevi o conteúdo de cada slide no `alt` de cada
  imagem (bom pra acessibilidade e SEO básico), mas se quiser um site
  com texto "de verdade" (selecionável, editável sem precisar gerar
  imagem nova), me avisa — dá pra reconstruir cada seção em HTML/CSS
  puro depois, mantendo a mesma identidade visual.

## Performance

Site pesa ~1.7MB no total (15 imagens JPEG otimizadas). Carregamento:
primeira imagem (`01-hero.jpg`) é `eager`, as demais são `lazy` —
carregam conforme o visitante rola a página.
