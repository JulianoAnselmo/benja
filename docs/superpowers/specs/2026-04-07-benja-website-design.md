# BENJA Eletrica, Hidraulica e Iluminacao — Website Design Spec

**Data:** 2026-04-07
**Status:** Aprovado
**Tipo:** Site institucional/comercial de alta conversao (single-page)

---

## 1. Visao Geral

Site premium para a BENJA Eletrica, Hidraulica e Iluminacao, empresa de Taquaritinga-SP. Objetivo: vitrine digital de alto nivel que fortalece a marca, gera contatos no WhatsApp, passa confianca e melhora presenca no Google.

**Nao e:** e-commerce, marketplace ou catalogo de produtos com precos.
**E:** site institucional comercial de alta conversao com foco em geracao de contato via WhatsApp.

---

## 2. Stack Tecnica

- **HTML5 semantico** — arquivo unico `index.html`
- **Tailwind CSS via CDN** — estilizacao utilitaria, responsiva, sem build
- **JavaScript vanilla** — interacoes, scroll, menu mobile, animacoes
- **Zero dependencias de build** — sem Node, sem framework, sem bundler
- **Hospedagem estatica** — Vercel, Netlify, GitHub Pages ou qualquer servidor

**Justificativa:** Performance maxima, SEO nativo, manutencao simples, deploy trivial.

---

## 3. Identidade Visual

### 3.1 Logo
- Mascote: personagem cartoon de eletricista (jovem, simpatico, macacão azul, camisa laranja, bone com "B", segurando lampada)
- Texto: "BENJA" em bold azul metalico + subtitulo "Eletrica, Hidraulica e Iluminacao."

### 3.2 Paleta de Cores

| Token | Hex | Uso |
|-------|-----|-----|
| `navy-900` | `#060D18` | Footer, fundos mais escuros |
| `navy-800` | `#0D1B2E` | Hero, secoes dark |
| `navy-700` | `#132E54` | Gradientes dark |
| `blue-600` | `#0A4DA0` | Azul institucional, barra confianca |
| `blue-500` | `#1A6FD9` | Azul principal, links, destaques |
| `blue-400` | `#1A8FFF` | Azul claro, logo no dark |
| `orange-500` | `#E8751A` | CTA principal, acentos |
| `orange-600` | `#D4600A` | CTA hover/gradiente |
| `amber-400` | `#F5B731` | Destaques, badges, estrelas |
| `gray-50` | `#F5F7FA` | Fundo secoes claras |
| `gray-100` | `#E8ECF0` | Bordas, divisores |
| `gray-500` | `#6B7B8D` | Texto secundario light |
| `dark-text` | `#0D1B2E` | Titulos em fundo claro |
| `white` | `#FFFFFF` | Cards, fundo principal claro |

### 3.3 Direcao Visual: Hybrid Dark/Light
- Hero e header: fundo dark navy
- Secoes de conteudo: alternam entre fundo claro e dark para criar ritmo visual
- Sequencia: dark (hero) → azul (confianca) → claro (categorias) → dark (diferenciais) → claro (quem compra) → gradiente (promo) → claro (depoimentos) → dark (institucional) → claro (contato) → dark (footer)

### 3.4 Tipografia
- Font principal: `Inter` (Google Fonts) — limpa, moderna, excelente legibilidade
- Fallback: `-apple-system, 'Segoe UI', sans-serif`
- Headlines: `font-weight: 800-900`, tracking tight
- Body: `font-weight: 400-500`, line-height 1.6-1.8
- Labels/badges: `font-weight: 600`, letter-spacing 2-3px, uppercase

---

## 4. Dados da Empresa

| Campo | Valor |
|-------|-------|
| Nome | BENJA Eletrica, Hidraulica e Iluminacao |
| Endereco | Rua Da Republica, 409 — Centro, Taquaritinga - SP, 15900-011 |
| Telefone | (16) 3253-1567 |
| Email | benja.eletricahidraulica@gmail.com |
| WhatsApp | wa.me/5516XXXXXXXXX (numero completo a confirmar com o cliente — usar o mesmo do perfil comercial) |
| Instagram | @benja.eletricahidraulica |
| Facebook | facebook.com/p/Benja-Eletrica-e-Hidraulica-100040646449109 |
| Horario | Seg-Sex 7h-18h30, Sab 8h-16h, Dom 8h-12h |

---

## 5. Estrutura da Home — 10 Secoes

### 5.1 Hero Section — "Split Impact"

**Layout:** Dividido — conteudo a esquerda (60%), espaco para imagem a direita (40%)
**Fundo:** Dark navy com gradiente (#070E1A → #0D1B2E)
**Imagem direita:** Area com overlay sutil para foto real da loja ou composicao de produtos

**Barra superior (top bar):**
- Esquerda: horario de funcionamento
- Direita: telefone em laranja, clicavel

**Navegacao:**
- Logo BENJA (mascote reduzido + texto) a esquerda
- Links: Inicio, Categorias, Diferenciais, Sobre, Contato
- Mobile: hamburger menu

**Conteudo hero:**
- Eyebrow: "REFERENCIA EM TAQUARITINGA" (letter-spacing 3px, cor cinza claro)
- Headline (3 linhas):
  ```
  Construir com
  confianca comeca
  aqui.
  ```
  - "aqui." em gradiente laranja→ambar (background-clip text)
- Subtitulo: "A maior variedade em eletrica, hidraulica e iluminacao de Taquaritinga. Atendimento especializado para quem constroi, reforma ou instala."
- CTA primario: "CHAMAR NO WHATSAPP" (fundo laranja, sombra, icone chat)
- CTA secundario: "PECA SEU ORCAMENTO" (borda branca translucida)
- Trust badges inline: "✓ Atendimento especializado" + "✓ Variedade completa"

**Imagem sugerida:** Foto da fachada da loja, ou composicao de produtos (luminarias, fios, ferramentas) em fundo escuro controlado.

---

### 5.2 Barra de Confianca Imediata

**Fundo:** Gradiente azul (#0A3D7A → #0A4DA0)
**Layout:** 4 colunas horizontais, centralizadas
**Mobile:** 2x2 grid

| Icone | Titulo | Subtitulo |
|-------|--------|-----------|
| 🏪 | Loja Fisica Completa | No centro de Taquaritinga |
| 👷 | Atendimento Tecnico | Equipe que entende de obra |
| 📦 | Variedade Real | De fios a placas solares |
| ⚡ | Agilidade | Compre rapido, resolva rapido |

**Nota:** Icones serao SVG refinados na implementacao (nao emoji).

---

### 5.3 Categorias — Vitrine Premium

**Fundo:** Claro (gradiente #F5F7FA → #FFFFFF)
**Eyebrow:** "O QUE VOCE ENCONTRA"
**Titulo:** "Solucoes para cada etapa da sua obra"
**Layout:** Grid 4x2 (desktop), 2x4 (mobile)

**Cards (8 categorias):**

| Icone | Categoria | Descricao |
|-------|-----------|-----------|
| ⚡ | Eletrica | Fios, cabos, disjuntores, quadros e componentes |
| 💧 | Hidraulica | Tubos, conexoes, registros, valvulas e acessorios |
| 💡 | Iluminacao | Luminarias, lampadas, spots, fitas LED e pendentes |
| 🔧 | Ferramentas | Ferramentas manuais e eletricas para instalacao |
| 🧱 | Obra e Reforma | Materiais essenciais para construcao e acabamento |
| 🔥 | Boiler | Aquecedores a gas, eletricos e acessorios |
| ☀️ | Energia Solar | Placas solares, inversores e kits completos |
| 🌡️ | Conforto | Ventilacao, climatizacao e solucoes de economia |

**Cada card:**
- Icone em container colorido (40x40px, border-radius 10px)
- Titulo em bold (13px)
- Descricao curta (10px, cinza)
- Hover: elevacao + borda azul
- Click: abre WhatsApp com mensagem pre-preenchida: "Ola, tenho interesse em produtos de [categoria]"

---

### 5.4 Diferenciais — "Por que Taquaritinga confia na BENJA"

**Fundo:** Dark navy (#070E1A → #0D1B2E) com glow sutil azul
**Eyebrow:** "DIFERENCIAIS"
**Titulo:** "Por que Taquaritinga confia na BENJA"
**Layout:** 3 colunas iguais
**Mobile:** Stack vertical

| Icone | Diferencial | Texto |
|-------|-------------|-------|
| 🎯 | Atendimento que Orienta | Nao vendemos so produtos. Ajudamos voce a escolher a solucao certa para cada situacao da sua obra. |
| 📦 | Tudo em Um So Lugar | Eletrica, hidraulica, iluminacao, ferramentas, boiler e energia solar. Voce resolve toda a obra em uma unica visita. |
| ⏱️ | Agilidade que Resolve | Sabemos que obra nao espera. Atendimento rapido, estoque preparado e equipe pronta para ajudar. |

**Destaque:** Card central ("Tudo em Um So Lugar") com badge "PRINCIPAL" e borda laranja sutil.

---

### 5.5 Quem Compra na BENJA

**Fundo:** Branco
**Eyebrow:** "PARA QUEM E"
**Titulo:** "A BENJA e para quem faz acontecer"
**Subtitulo:** "Do profissional experiente ao cliente que esta reformando pela primeira vez"
**Layout:** Grid 2x2
**Mobile:** Stack vertical

| Icone | Perfil | Descricao |
|-------|--------|-----------|
| 🏗️ | Quem esta construindo | Material completo do inicio ao acabamento |
| 🔨 | Quem esta reformando | Solucoes praticas para trocar e melhorar |
| 👷 | Profissionais da area | Eletricistas, encanadores, instaladores e pedreiros |
| 🏠 | Quem quer praticidade | Comprar com orientacao, sem complicacao |

---

### 5.6 Area Promocional Editavel

**Fundo:** Gradiente azul→laranja (#0A4DA0 → #1A6FD9 → #E8751A)
**Layout:** Conteudo a esquerda (60%), area para imagem a direita (40%)

**Estrutura:**
- Badge: "🔥 PROMOCAO DA SEMANA" (ou texto editavel)
- Titulo: "Condicoes especiais para sua obra" (editavel)
- Subtitulo: "Parcele em ate 10x sem juros no cartao. Descontos exclusivos para profissionais. Aproveite." (editavel)
- CTA: "QUERO APROVEITAR →" (fundo branco, texto azul)

**Nota de implementacao:** Todos os textos desta secao devem estar em variaveis/constantes faceis de localizar no HTML para atualizacao rapida sem dev. Comentarios no codigo indicando onde trocar.

---

### 5.7 Prova Social — Depoimentos

**Fundo:** Cinza claro (#F5F7FA)
**Eyebrow:** "DEPOIMENTOS"
**Titulo:** "O que nossos clientes dizem"
**Badge Google:** Nota 4.9 + estrelas + "no Google"
**Layout:** 3 cards lado a lado
**Mobile:** Carrossel horizontal com swipe (JS)

**Cada card:**
- 5 estrelas amarelas
- Texto do depoimento (italico, 11px)
- Nome do cliente
- Bairro ou profissao

**Nota:** Depoimentos sao placeholder. Substituir por avaliacoes reais do Google Meu Negocio.

---

### 5.8 Institucional — Sobre a BENJA

**Fundo:** Dark navy
**Layout:** Imagem/mascote a esquerda + texto a direita
**Mobile:** Mascote acima, texto abaixo

**Conteudo:**
- Eyebrow: "SOBRE NOS"
- Titulo: "Mais que uma loja. Uma referencia."
- Texto: "A BENJA nasceu com um proposito claro: ser o lugar onde Taquaritinga encontra tudo para eletrica, hidraulica e iluminacao com atendimento de verdade. Nao somos apenas uma loja de materiais — somos parceiros de quem constroi, reforma e instala. Nossa equipe entende de obra e esta pronta para ajudar voce a fazer a escolha certa."
- CTA: "Visite nossa loja no centro" (badge estilo)

---

### 5.9 Contato e Conversao

**Fundo:** Branco
**Eyebrow:** "VENHA NOS VISITAR"
**Titulo:** "Estamos prontos para atender voce"
**Layout:** 2 colunas — info a esquerda, Google Maps embed a direita
**Mobile:** Stack vertical, botoes de acao rapida em destaque

**Informacoes (esquerda):**
- Endereco: Rua Da Republica, 409 — Centro, Taquaritinga - SP
- Telefone: (16) 3253-1567 (clicavel tel:)
- WhatsApp: link direto
- Horario: Seg a Sex 7h–18h30, Sab 8h–16h, Dom 8h–12h
- Botao: "WHATSAPP" (laranja)
- Botao: "TRACAR ROTA" (azul)

**Mapa (direita):**
- Google Maps embed com pin no endereco
- Lazy loading para performance

---

### 5.10 Rodape Premium

**Fundo:** Navy mais escuro (#060D18) com borda superior laranja (3px)
**Layout:** 4 colunas

| Coluna 1 (2fr) | Coluna 2 | Coluna 3 | Coluna 4 |
|-----------------|----------|----------|----------|
| Logo + resumo institucional + icones redes sociais | Links de navegacao | Categorias | Contato |

**CTA final:** "Precisa de orcamento? Fale com a gente agora." + botao WhatsApp
**Copyright:** "© 2026 BENJA Eletrica, Hidraulica e Iluminacao. Todos os direitos reservados."

---

## 6. Elementos Globais

### 6.1 WhatsApp Flutuante
- Botao fixo canto inferior direito (position fixed)
- Icone WhatsApp em circulo verde (#25D366)
- Pulso sutil com animation (scale pulse)
- Z-index alto para ficar acima de tudo
- Abre chat com mensagem: "Ola! Vim pelo site da BENJA. Gostaria de mais informacoes."

### 6.2 Header Mobile
- Sticky no scroll (position sticky top 0)
- Logo reduzido + hamburger menu
- Menu aberto: overlay escuro + links + botao WhatsApp + telefone clicavel
- Transicao suave (slideDown ou fadeIn)

### 6.3 Back to Top
- Botao discreto (circulo azul com seta)
- Aparece apos 400px de scroll
- Smooth scroll para o topo

### 6.4 Smooth Scroll
- Todos os links internos (#secao) com scroll suave
- `scroll-behavior: smooth` + JS fallback

### 6.5 Animacoes de Entrada
- Intersection Observer para revelar secoes no scroll
- Fade-in + slide-up sutil (translateY 20px → 0)
- Stagger nos cards de categoria (delay escalonado)
- Sem bibliotecas — CSS transitions + JS nativo

---

## 7. SEO Local

### 7.1 Meta Tags
```html
<title>BENJA — Eletrica, Hidraulica e Iluminacao em Taquaritinga-SP</title>
<meta name="description" content="Loja de materiais eletricos, hidraulicos e iluminacao em Taquaritinga-SP. Atendimento especializado para construcao e reforma. Fios, cabos, luminarias, tubos, boiler, placa solar e mais.">
```

### 7.2 Schema Markup (JSON-LD)
- Tipo: `LocalBusiness` / `ElectricalStore`
- Nome, endereco, telefone, horario, coordenadas GPS
- Nota de avaliacao agregada

### 7.3 Open Graph
- og:title, og:description, og:image (preview do site)
- og:type: website
- og:locale: pt_BR

### 7.4 Keywords Alvo
- eletrica em Taquaritinga
- hidraulica em Taquaritinga
- iluminacao em Taquaritinga
- loja de materiais eletricos em Taquaritinga
- materiais para reforma em Taquaritinga
- materiais para construcao em Taquaritinga
- boiler em Taquaritinga
- placa solar em Taquaritinga

### 7.5 Heading Hierarchy
- h1: headline da hero (unico)
- h2: titulo de cada secao
- h3: subtitulos e cards

---

## 8. UX e Performance

### 8.1 Responsividade
- Mobile-first com Tailwind breakpoints (sm, md, lg, xl)
- Breakpoints chave: 640px (sm), 768px (md), 1024px (lg), 1280px (xl)
- Grids adaptam: 4col → 2col → 1col
- Imagens com srcset e sizes para performance
- Touch targets minimo 44x44px no mobile

### 8.2 Performance
- Tailwind via CDN (play CDN para simplicidade, ou build otimizado depois)
- Imagens em WebP com fallback JPG
- Google Maps com lazy loading (iframe loading="lazy")
- Font Inter via Google Fonts com display=swap
- Minificacao manual do JS inline
- Sem bibliotecas externas alem de Tailwind e Google Fonts

### 8.3 Acessibilidade
- Contraste WCAG AA em todos os textos
- aria-labels nos botoes de acao
- Skip navigation link
- Focus styles visiveis
- Semantica HTML5 (header, nav, main, section, footer)

---

## 9. Copywriting Completo

### 9.1 Headlines Principais (5)
1. "Construir com confianca comeca aqui."
2. "Solucoes para cada etapa da sua obra"
3. "Por que Taquaritinga confia na BENJA"
4. "A BENJA e para quem faz acontecer"
5. "Mais que uma loja. Uma referencia."

### 9.2 Subtitulos (5)
1. "A maior variedade em eletrica, hidraulica e iluminacao de Taquaritinga."
2. "Do profissional experiente ao cliente que esta reformando pela primeira vez"
3. "Nao vendemos so produtos. Ajudamos voce a escolher a solucao certa."
4. "Voce resolve toda a obra em uma unica visita."
5. "Estamos prontos para atender voce"

### 9.3 CTAs (10)
1. "CHAMAR NO WHATSAPP"
2. "PECA SEU ORCAMENTO"
3. "COMO CHEGAR"
4. "QUERO APROVEITAR"
5. "TRACAR ROTA"
6. "FALE COM A GENTE"
7. "VER CATEGORIAS"
8. "PEDIR ORCAMENTO NO WHATSAPP"
9. "VISITE NOSSA LOJA"
10. "CONHECA NOSSOS PRODUTOS"

---

## 10. Sitemap Futuro (expansao)

```
/                     → Home (este spec)
/eletrica             → Pagina de categoria com subcategorias
/hidraulica           → Pagina de categoria
/iluminacao           → Pagina de categoria
/energia-solar        → Landing page especifica
/boiler               → Landing page especifica
/sobre                → Pagina institucional expandida
/contato              → Pagina de contato dedicada
/blog                 → Conteudo SEO (dicas de obra, reforma, instalacao)
/orcamento            → Formulario de orcamento detalhado
```

---

## 11. Estrutura de Arquivos

```
benja/
├── index.html          → Pagina unica com todas as secoes
├── assets/
│   ├── images/
│   │   ├── logo.png
│   │   ├── logo-white.png
│   │   ├── hero-bg.webp
│   │   ├── mascote.png
│   │   └── og-image.jpg
│   ├── icons/          → SVGs das categorias e diferenciais
│   └── favicon.ico
├── .gitignore
└── README.md           → (se solicitado)
```

---

## 12. Resumo: Por que este site fica acima da concorrencia local

1. **Identidade visual premium** — paleta sofisticada, tipografia moderna, ritmo dark/light que nenhum concorrente local tem
2. **Foco total em conversao** — cada secao direciona para WhatsApp, sem distracao
3. **SEO local estruturado** — Schema markup, meta tags, heading hierarchy, keywords naturais
4. **Copywriting profissional** — tom de marca consolidada, sem cliches, sem exagero
5. **Performance nativa** — HTML puro carrega em <1s, sem framework pesado
6. **Mobile-first** — experiencia pensada primeiro para smartphone, onde 70%+ do trafego chega
7. **Preparado para crescer** — estrutura permite adicionar paginas de categoria, blog e formularios depois
8. **Prova social integrada** — depoimentos e nota Google reforçam confiança imediata
