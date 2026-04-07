# BENJA Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a premium single-page institutional website for BENJA Eletrica, Hidraulica e Iluminacao (Taquaritinga-SP) — hybrid dark/light design, mobile-first, SEO local, WhatsApp conversion focus.

**Architecture:** Single `index.html` file with Tailwind CSS via CDN (play cdn) and inline vanilla JavaScript. No build step, no framework. Custom color tokens via Tailwind config. SVG icons inline. All sections in one file, ordered top to bottom matching the spec.

**Tech Stack:** HTML5 semantic, Tailwind CSS CDN, vanilla JS, Google Fonts (Inter)

**Spec:** `docs/superpowers/specs/2026-04-07-benja-website-design.md`

---

## File Structure

```
benja/
├── index.html              ← Single page with all 10 sections + JS
├── assets/
│   └── icons/              ← SVG icon files for categories/diferenciais
│       ├── eletrica.svg
│       ├── hidraulica.svg
│       ├── iluminacao.svg
│       ├── ferramentas.svg
│       ├── obra.svg
│       ├── boiler.svg
│       ├── solar.svg
│       ├── conforto.svg
│       ├── loja.svg
│       ├── atendimento.svg
│       ├── variedade.svg
│       ├── agilidade.svg
│       ├── orientacao.svg
│       ├── tudo-em-um.svg
│       ├── relogio.svg
│       ├── construindo.svg
│       ├── reformando.svg
│       ├── profissional.svg
│       ├── praticidade.svg
│       ├── whatsapp.svg
│       ├── facebook.svg
│       ├── instagram.svg
│       ├── phone.svg
│       ├── map-pin.svg
│       ├── clock.svg
│       ├── mail.svg
│       ├── menu.svg
│       ├── close.svg
│       ├── arrow-up.svg
│       └── check.svg
└── .gitignore
```

All code lives in `index.html`. Icons are separate SVG files in `assets/icons/` for maintainability. No images are included (placeholders used — real photos to be added by client).

---

### Task 1: HTML Boilerplate + Head + Tailwind Config

**Files:**
- Create: `index.html`

This task sets up the full `<head>` with SEO meta tags, Open Graph, Schema.org JSON-LD, Google Fonts, Tailwind CDN with custom color config, and the opening `<body>` tag. No visible content yet — just the foundation.

- [ ] **Step 1: Create index.html with complete head section**

Create `index.html` with this content:

```html
<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BENJA — Elétrica, Hidráulica e Iluminação em Taquaritinga-SP</title>
  <meta name="description" content="Loja de materiais elétricos, hidráulicos e iluminação em Taquaritinga-SP. Atendimento especializado para construção e reforma. Fios, cabos, luminárias, tubos, boiler, placa solar e mais.">
  <meta name="keywords" content="elétrica Taquaritinga, hidráulica Taquaritinga, iluminação Taquaritinga, materiais elétricos, materiais hidráulicos, reforma Taquaritinga, construção Taquaritinga, boiler Taquaritinga, placa solar Taquaritinga">
  <meta name="author" content="BENJA Elétrica, Hidráulica e Iluminação">
  <meta name="robots" content="index, follow">
  <link rel="canonical" href="https://www.benjaeletrica.com.br/">

  <!-- Open Graph -->
  <meta property="og:type" content="website">
  <meta property="og:locale" content="pt_BR">
  <meta property="og:title" content="BENJA — Elétrica, Hidráulica e Iluminação em Taquaritinga-SP">
  <meta property="og:description" content="Tudo para sua obra com atendimento especializado. Elétrica, hidráulica, iluminação, boiler e energia solar em Taquaritinga.">
  <meta property="og:url" content="https://www.benjaeletrica.com.br/">
  <meta property="og:site_name" content="BENJA Elétrica">
  <!-- <meta property="og:image" content="https://www.benjaeletrica.com.br/assets/images/og-image.jpg"> -->

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            navy: {
              700: '#132E54',
              800: '#0D1B2E',
              900: '#060D18',
            },
            blue: {
              400: '#1A8FFF',
              500: '#1A6FD9',
              600: '#0A4DA0',
              700: '#0A3D7A',
            },
            orange: {
              500: '#E8751A',
              600: '#D4600A',
            },
            amber: {
              400: '#F5B731',
            },
            gray: {
              50: '#F5F7FA',
              100: '#E8ECF0',
              500: '#6B7B8D',
            },
          },
          fontFamily: {
            sans: ['Inter', '-apple-system', 'Segoe UI', 'sans-serif'],
          },
        },
      },
    }
  </script>

  <!-- Custom styles (minimal — only what Tailwind can't do) -->
  <style>
    /* Gradient text for hero "aqui." */
    .text-gradient-orange {
      background: linear-gradient(135deg, #E8751A, #F5B731);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    /* WhatsApp pulse animation */
    @keyframes pulse-whatsapp {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.08); }
    }
    .animate-pulse-whatsapp {
      animation: pulse-whatsapp 2s ease-in-out infinite;
    }

    /* Scroll reveal animation */
    .reveal {
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Stagger delay for cards */
    .stagger-1 { transition-delay: 0.1s; }
    .stagger-2 { transition-delay: 0.2s; }
    .stagger-3 { transition-delay: 0.3s; }
    .stagger-4 { transition-delay: 0.4s; }
    .stagger-5 { transition-delay: 0.5s; }
    .stagger-6 { transition-delay: 0.6s; }
    .stagger-7 { transition-delay: 0.7s; }
    .stagger-8 { transition-delay: 0.8s; }
  </style>

  <!-- Schema.org JSON-LD -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "ElectricalStore",
    "name": "BENJA Elétrica, Hidráulica e Iluminação",
    "description": "Loja de materiais elétricos, hidráulicos e iluminação em Taquaritinga-SP. Atendimento especializado para construção e reforma.",
    "url": "https://www.benjaeletrica.com.br",
    "telephone": "+551632531567",
    "email": "benja.eletricahidraulica@gmail.com",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Rua Da República, 409",
      "addressLocality": "Taquaritinga",
      "addressRegion": "SP",
      "postalCode": "15900-011",
      "addressCountry": "BR"
    },
    "geo": {
      "@type": "GeoCoordinates",
      "latitude": -21.4053,
      "longitude": -48.5053
    },
    "openingHoursSpecification": [
      {
        "@type": "OpeningHoursSpecification",
        "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
        "opens": "07:00",
        "closes": "18:30"
      },
      {
        "@type": "OpeningHoursSpecification",
        "dayOfWeek": "Saturday",
        "opens": "08:00",
        "closes": "16:00"
      },
      {
        "@type": "OpeningHoursSpecification",
        "dayOfWeek": "Sunday",
        "opens": "08:00",
        "closes": "12:00"
      }
    ],
    "aggregateRating": {
      "@type": "AggregateRating",
      "ratingValue": "4.9",
      "reviewCount": "120"
    },
    "sameAs": [
      "https://www.instagram.com/benja.eletricahidraulica/",
      "https://www.facebook.com/p/Benja-El%C3%A9trica-e-Hidr%C3%A1ulica-100040646449109/"
    ]
  }
  </script>
</head>
<body class="font-sans antialiased">

  <!-- Skip navigation -->
  <a href="#conteudo" class="sr-only focus:not-sr-only focus:absolute focus:top-2 focus:left-2 focus:bg-orange-500 focus:text-white focus:px-4 focus:py-2 focus:rounded focus:z-50">
    Pular para o conteúdo
  </a>

  <main id="conteudo">
    <!-- Sections will be added in subsequent tasks -->
  </main>

</body>
</html>
```

- [ ] **Step 2: Verify the file opens in browser**

Run: `start "C:/dev/prototipos/benja/index.html"` (Windows) or open the file manually.
Expected: Blank white page, no console errors, Tailwind loaded (check network tab).

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add HTML boilerplate with SEO, Tailwind config, and Schema.org"
```

---

### Task 2: SVG Icons

**Files:**
- Create: `assets/icons/*.svg` (all 29 icons)

Create clean, minimal SVG icons. Each icon is 24x24 viewBox, single color using `currentColor` so they inherit text color from Tailwind classes.

- [ ] **Step 1: Create assets/icons directory and all SVG files**

Create `assets/icons/` directory. Then create each SVG file. All icons follow this pattern — 24x24 viewBox, stroke-based, `currentColor`:

**`assets/icons/eletrica.svg`** — Lightning bolt:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg>
```

**`assets/icons/hidraulica.svg`** — Water droplet:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2.69l5.66 5.66a8 8 0 11-11.31 0z"/></svg>
```

**`assets/icons/iluminacao.svg`** — Lightbulb:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 18h6"/><path d="M10 22h4"/><path d="M12 2a7 7 0 00-4 12.7V17h8v-2.3A7 7 0 0012 2z"/></svg>
```

**`assets/icons/ferramentas.svg`** — Wrench:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14.7 6.3a1 1 0 000 1.4l1.6 1.6a1 1 0 001.4 0l3.77-3.77a6 6 0 01-7.94 7.94l-6.91 6.91a2.12 2.12 0 01-3-3l6.91-6.91a6 6 0 017.94-7.94l-3.76 3.76z"/></svg>
```

**`assets/icons/obra.svg`** — Bricks/building:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="1" y="2" width="22" height="6" rx="1"/><rect x="1" y="10" width="10" height="6" rx="1"/><rect x="13" y="10" width="10" height="6" rx="1"/><rect x="1" y="18" width="22" height="4" rx="1"/></svg>
```

**`assets/icons/boiler.svg`** — Flame/heater:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 12c2-2.96 0-7-1-8 0 3.038-1.773 4.741-3 6-1.226 1.26-2 3.24-2 5a6 6 0 1012 0c0-1.532-1.056-3.94-2-5-1.786 3-2.791 3-4 2z"/></svg>
```

**`assets/icons/solar.svg`** — Sun:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/></svg>
```

**`assets/icons/conforto.svg`** — Thermometer:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 14.76V3.5a2.5 2.5 0 00-5 0v11.26a4.5 4.5 0 105 0z"/></svg>
```

**`assets/icons/loja.svg`** — Storefront:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
```

**`assets/icons/atendimento.svg`** — Headset/support:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 18v-6a9 9 0 0118 0v6"/><path d="M21 19a2 2 0 01-2 2h-1a2 2 0 01-2-2v-3a2 2 0 012-2h3zM3 19a2 2 0 002 2h1a2 2 0 002-2v-3a2 2 0 00-2-2H3z"/></svg>
```

**`assets/icons/variedade.svg`** — Package/box:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z"/><polyline points="3.27 6.96 12 12.01 20.73 6.96"/><line x1="12" y1="22.08" x2="12" y2="12"/></svg>
```

**`assets/icons/agilidade.svg`** — Zap/speed:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>
```

**`assets/icons/orientacao.svg`** — Target/aim:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="6"/><circle cx="12" cy="12" r="2"/></svg>
```

**`assets/icons/tudo-em-um.svg`** — Grid/boxes:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></svg>
```

**`assets/icons/relogio.svg`** — Clock:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
```

**`assets/icons/construindo.svg`** — Crane/construction:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 20h20"/><path d="M5 20V8l7-5v17"/><path d="M12 8h5l3 4v8"/><path d="M8 11h0"/><path d="M8 15h0"/></svg>
```

**`assets/icons/reformando.svg`** — Hammer:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15.12 7.88c1.14-1.12 1.3-2.88.56-4.2a1 1 0 00-1.56-.18L11.7 5.92a1 1 0 01-1.42 0L9 4.64a1 1 0 00-1.42 0L2 10.22a1 1 0 000 1.42l3.54 3.53a1 1 0 001.42 0l5.66-5.66z"/><path d="M14.5 17.5L21 11"/><path d="M15 10l-1 1"/></svg>
```

**`assets/icons/profissional.svg`** — Hard hat:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 18h20"/><path d="M4 18v-2a8 8 0 0116 0v2"/><path d="M12 2v6"/><path d="M9 6h6"/></svg>
```

**`assets/icons/praticidade.svg`** — Home:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
```

**`assets/icons/whatsapp.svg`** — WhatsApp logo:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
```

**`assets/icons/facebook.svg`** — Facebook logo:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
```

**`assets/icons/instagram.svg`** — Instagram logo:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
```

**`assets/icons/phone.svg`** — Phone:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07 19.5 19.5 0 01-6-6 19.79 19.79 0 01-3.07-8.67A2 2 0 014.11 2h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L8.09 9.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
```

**`assets/icons/map-pin.svg`** — Map pin:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
```

**`assets/icons/clock.svg`** — Clock:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
```

**`assets/icons/mail.svg`** — Email:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
```

**`assets/icons/menu.svg`** — Hamburger menu:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="18" x2="21" y2="18"/></svg>
```

**`assets/icons/close.svg`** — Close X:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
```

**`assets/icons/arrow-up.svg`** — Arrow up:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg>
```

**`assets/icons/check.svg`** — Checkmark:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
```

- [ ] **Step 2: Commit icons**

```bash
git add assets/icons/
git commit -m "feat: add SVG icon set for all sections"
```

---

### Task 3: Top Bar + Navigation + Hero Section

**Files:**
- Modify: `index.html` (add content inside `<main>`)

This builds the top bar with contact info, the sticky navigation, and the full hero section with Split Impact layout.

- [ ] **Step 1: Add top bar, navigation, and hero section inside `<main>`**

Replace the `<!-- Sections will be added in subsequent tasks -->` comment inside `<main>` with the full top bar + nav + hero HTML. The complete code:

```html
    <!-- ========== TOP BAR ========== -->
    <div class="bg-navy-900/80 border-b border-white/5">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 flex justify-between items-center py-2 text-xs text-white/40">
        <span class="hidden sm:inline">Seg a Sex: 7h–18h30 · Sáb: 8h–16h · Dom: 8h–12h</span>
        <span class="sm:hidden">Seg-Sex 7h–18h30</span>
        <a href="tel:+551632531567" class="text-orange-500 hover:text-orange-400 transition-colors font-semibold">
          📞 (16) 3253-1567
        </a>
      </div>
    </div>

    <!-- ========== NAVIGATION ========== -->
    <nav id="navbar" class="sticky top-0 z-40 bg-navy-800/95 backdrop-blur-md border-b border-white/5 transition-all duration-300">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 flex justify-between items-center h-16 lg:h-20">
        <!-- Logo -->
        <a href="#" class="flex items-center gap-3">
          <span class="text-blue-400 font-black text-2xl tracking-widest">BENJA</span>
          <span class="hidden md:inline text-white/30 text-xs border-l border-white/10 pl-3 leading-tight">Elétrica, Hidráulica<br>e Iluminação</span>
        </a>

        <!-- Desktop links -->
        <div class="hidden lg:flex items-center gap-8">
          <a href="#categorias" class="text-white/45 hover:text-white text-sm font-medium tracking-wide transition-colors">Categorias</a>
          <a href="#diferenciais" class="text-white/45 hover:text-white text-sm font-medium tracking-wide transition-colors">Diferenciais</a>
          <a href="#sobre" class="text-white/45 hover:text-white text-sm font-medium tracking-wide transition-colors">Sobre</a>
          <a href="#contato" class="text-white/45 hover:text-white text-sm font-medium tracking-wide transition-colors">Contato</a>
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20mais%20informações." target="_blank" rel="noopener" class="bg-gradient-to-r from-orange-500 to-orange-600 text-white px-5 py-2.5 rounded-lg text-sm font-bold hover:shadow-lg hover:shadow-orange-500/25 transition-all">
            Peça Orçamento
          </a>
        </div>

        <!-- Mobile hamburger -->
        <button id="menu-toggle" class="lg:hidden w-10 h-10 flex items-center justify-center text-white/60 hover:text-white transition-colors" aria-label="Abrir menu">
          <img src="assets/icons/menu.svg" alt="" class="w-6 h-6 invert opacity-60" id="menu-icon-open">
          <img src="assets/icons/close.svg" alt="" class="w-6 h-6 invert opacity-60 hidden" id="menu-icon-close">
        </button>
      </div>

      <!-- Mobile menu overlay -->
      <div id="mobile-menu" class="lg:hidden hidden bg-navy-800/98 backdrop-blur-md border-t border-white/5">
        <div class="max-w-7xl mx-auto px-4 py-6 flex flex-col gap-4">
          <a href="#categorias" class="text-white/60 hover:text-white text-base font-medium py-2 transition-colors mobile-menu-link">Categorias</a>
          <a href="#diferenciais" class="text-white/60 hover:text-white text-base font-medium py-2 transition-colors mobile-menu-link">Diferenciais</a>
          <a href="#sobre" class="text-white/60 hover:text-white text-base font-medium py-2 transition-colors mobile-menu-link">Sobre</a>
          <a href="#contato" class="text-white/60 hover:text-white text-base font-medium py-2 transition-colors mobile-menu-link">Contato</a>
          <div class="flex flex-col gap-3 pt-4 border-t border-white/10">
            <a href="tel:+551632531567" class="text-white/60 text-sm font-medium">📞 (16) 3253-1567</a>
            <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20mais%20informações." target="_blank" rel="noopener" class="bg-gradient-to-r from-orange-500 to-orange-600 text-white px-5 py-3 rounded-lg text-sm font-bold text-center">
              💬 Chamar no WhatsApp
            </a>
          </div>
        </div>
      </div>
    </nav>

    <!-- ========== SECTION 1: HERO ========== -->
    <section id="hero" class="relative bg-gradient-to-br from-[#070E1A] to-navy-800 overflow-hidden">
      <!-- Right side image area -->
      <div class="absolute right-0 top-0 bottom-0 w-2/5 hidden lg:block">
        <div class="absolute inset-0 bg-gradient-to-br from-blue-500/10 to-blue-500/5"></div>
        <!-- Replace with real photo: <img src="assets/images/hero-bg.webp" class="absolute inset-0 w-full h-full object-cover opacity-40"> -->
        <div class="absolute inset-0 flex items-center justify-center">
          <div class="text-center opacity-20">
            <div class="text-6xl mb-2">💡</div>
            <p class="text-white text-xs">Foto real aqui</p>
          </div>
        </div>
      </div>

      <!-- Ambient glow -->
      <div class="absolute -top-20 -right-20 w-80 h-80 bg-blue-500/10 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-10 left-1/4 w-48 h-48 bg-orange-500/5 rounded-full blur-3xl"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-28">
        <div class="max-w-xl lg:max-w-2xl">
          <!-- Eyebrow -->
          <p class="text-xs sm:text-sm tracking-[3px] text-white/30 font-medium mb-4 sm:mb-6">REFERÊNCIA EM TAQUARITINGA</p>

          <!-- Headline -->
          <h1 class="text-3xl sm:text-4xl lg:text-5xl xl:text-6xl font-black text-white leading-[1.1] mb-4 sm:mb-6 tracking-tight">
            Construir com<br>
            confiança começa<br>
            <span class="text-gradient-orange">aqui.</span>
          </h1>

          <!-- Subtitle -->
          <p class="text-sm sm:text-base text-white/50 leading-relaxed mb-8 max-w-lg">
            A maior variedade em elétrica, hidráulica e iluminação de Taquaritinga. Atendimento especializado para quem constrói, reforma ou instala.
          </p>

          <!-- CTAs -->
          <div class="flex flex-col sm:flex-row gap-3 sm:gap-4 mb-8">
            <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20mais%20informações." target="_blank" rel="noopener"
               class="inline-flex items-center justify-center gap-2 bg-gradient-to-r from-orange-500 to-orange-600 text-white px-6 sm:px-8 py-3.5 rounded-lg text-sm font-bold shadow-lg shadow-orange-500/30 hover:shadow-xl hover:shadow-orange-500/40 hover:-translate-y-0.5 transition-all">
              💬 CHAMAR NO WHATSAPP
            </a>
            <a href="#contato"
               class="inline-flex items-center justify-center gap-2 border border-white/15 text-white/65 hover:text-white hover:border-white/30 px-6 sm:px-8 py-3.5 rounded-lg text-sm font-medium transition-all">
              PEÇA SEU ORÇAMENTO
            </a>
          </div>

          <!-- Trust badges -->
          <div class="flex flex-wrap gap-4 sm:gap-6">
            <div class="flex items-center gap-2 text-xs sm:text-sm text-white/40">
              <img src="assets/icons/check.svg" alt="" class="w-4 h-4 invert opacity-60" style="filter: invert(55%) sepia(98%) saturate(1000%) hue-rotate(190deg);">
              <span>Atendimento especializado</span>
            </div>
            <div class="flex items-center gap-2 text-xs sm:text-sm text-white/40">
              <img src="assets/icons/check.svg" alt="" class="w-4 h-4 invert opacity-60" style="filter: invert(55%) sepia(98%) saturate(1000%) hue-rotate(190deg);">
              <span>Variedade completa</span>
            </div>
          </div>
        </div>
      </div>
    </section>
```

Note: All subsequent sections will be added after `</section>` of the hero, still inside `<main>`.

- [ ] **Step 2: Verify hero renders correctly**

Open `index.html` in browser. Expected: dark hero with headline "Construir com confiança começa aqui.", two CTA buttons, navigation at top.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add top bar, navigation, and hero section"
```

---

### Task 4: Trust Bar + Categories Section

**Files:**
- Modify: `index.html` (add sections 2 and 3 after hero `</section>`)

- [ ] **Step 1: Add trust bar and categories sections**

Add this HTML after the hero `</section>` closing tag:

```html
    <!-- ========== SECTION 2: TRUST BAR ========== -->
    <section class="bg-gradient-to-r from-blue-700 to-blue-600">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-8 sm:py-10">
        <div class="grid grid-cols-2 lg:grid-cols-4 gap-6 lg:gap-8 text-center">
          <div class="reveal">
            <div class="w-12 h-12 mx-auto mb-3 rounded-xl bg-white/10 flex items-center justify-center">
              <img src="assets/icons/loja.svg" alt="" class="w-6 h-6 invert">
            </div>
            <h3 class="text-white font-bold text-sm mb-1">Loja Física Completa</h3>
            <p class="text-white/50 text-xs">No centro de Taquaritinga</p>
          </div>
          <div class="reveal">
            <div class="w-12 h-12 mx-auto mb-3 rounded-xl bg-white/10 flex items-center justify-center">
              <img src="assets/icons/atendimento.svg" alt="" class="w-6 h-6 invert">
            </div>
            <h3 class="text-white font-bold text-sm mb-1">Atendimento Técnico</h3>
            <p class="text-white/50 text-xs">Equipe que entende de obra</p>
          </div>
          <div class="reveal">
            <div class="w-12 h-12 mx-auto mb-3 rounded-xl bg-white/10 flex items-center justify-center">
              <img src="assets/icons/variedade.svg" alt="" class="w-6 h-6 invert">
            </div>
            <h3 class="text-white font-bold text-sm mb-1">Variedade Real</h3>
            <p class="text-white/50 text-xs">De fios a placas solares</p>
          </div>
          <div class="reveal">
            <div class="w-12 h-12 mx-auto mb-3 rounded-xl bg-white/10 flex items-center justify-center">
              <img src="assets/icons/agilidade.svg" alt="" class="w-6 h-6 invert">
            </div>
            <h3 class="text-white font-bold text-sm mb-1">Agilidade</h3>
            <p class="text-white/50 text-xs">Compre rápido, resolva rápido</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== SECTION 3: CATEGORIES ========== -->
    <section id="categorias" class="bg-gradient-to-b from-gray-50 to-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <!-- Header -->
        <div class="text-center mb-12 sm:mb-16 reveal">
          <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">O QUE VOCÊ ENCONTRA</p>
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-navy-800">Soluções para cada etapa da sua obra</h2>
        </div>

        <!-- Cards grid -->
        <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-5">
          <!-- Elétrica -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20produtos%20de%20Elétrica." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-blue-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-1">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-blue-500/10 flex items-center justify-center">
              <img src="assets/icons/eletrica.svg" alt="" class="w-5 h-5 text-blue-500" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-blue-500 transition-colors">Elétrica</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Fios, cabos, disjuntores, quadros e componentes</p>
          </a>

          <!-- Hidráulica -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20produtos%20de%20Hidráulica." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-blue-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-2">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-blue-500/10 flex items-center justify-center">
              <img src="assets/icons/hidraulica.svg" alt="" class="w-5 h-5" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-blue-500 transition-colors">Hidráulica</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Tubos, conexões, registros, válvulas e acessórios</p>
          </a>

          <!-- Iluminação -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20produtos%20de%20Iluminação." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-amber-400/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-3">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-amber-400/10 flex items-center justify-center">
              <img src="assets/icons/iluminacao.svg" alt="" class="w-5 h-5" style="filter: invert(60%) sepia(98%) saturate(500%) hue-rotate(10deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-amber-500 transition-colors">Iluminação</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Luminárias, lâmpadas, spots, fitas LED e pendentes</p>
          </a>

          <!-- Ferramentas -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Ferramentas." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-orange-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-4">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-orange-500/10 flex items-center justify-center">
              <img src="assets/icons/ferramentas.svg" alt="" class="w-5 h-5" style="filter: invert(50%) sepia(98%) saturate(800%) hue-rotate(350deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-orange-500 transition-colors">Ferramentas</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Ferramentas manuais e elétricas para instalação</p>
          </a>

          <!-- Obra e Reforma -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20materiais%20para%20Obra%20e%20Reforma." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-blue-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-5">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-blue-500/10 flex items-center justify-center">
              <img src="assets/icons/obra.svg" alt="" class="w-5 h-5" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-blue-500 transition-colors">Obra e Reforma</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Materiais essenciais para construção e acabamento</p>
          </a>

          <!-- Boiler -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Boiler%20/%20Aquecedor." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-amber-400/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-6">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-amber-400/10 flex items-center justify-center">
              <img src="assets/icons/boiler.svg" alt="" class="w-5 h-5" style="filter: invert(60%) sepia(98%) saturate(500%) hue-rotate(10deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-amber-500 transition-colors">Boiler</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Aquecedores a gás, elétricos e acessórios</p>
          </a>

          <!-- Energia Solar -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Energia%20Solar." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-orange-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-7">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-orange-500/10 flex items-center justify-center">
              <img src="assets/icons/solar.svg" alt="" class="w-5 h-5" style="filter: invert(50%) sepia(98%) saturate(800%) hue-rotate(350deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-orange-500 transition-colors">Energia Solar</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Placas solares, inversores e kits completos</p>
          </a>

          <!-- Conforto -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20soluções%20de%20Conforto%20e%20Economia." target="_blank" rel="noopener"
             class="group bg-white border border-gray-100 rounded-xl p-5 sm:p-6 text-center shadow-sm hover:shadow-lg hover:border-blue-500/30 hover:-translate-y-1 transition-all duration-300 reveal stagger-8">
            <div class="w-11 h-11 mx-auto mb-3 rounded-lg bg-blue-500/10 flex items-center justify-center">
              <img src="assets/icons/conforto.svg" alt="" class="w-5 h-5" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <h3 class="font-bold text-sm text-navy-800 mb-1 group-hover:text-blue-500 transition-colors">Conforto</h3>
            <p class="text-xs text-gray-500 leading-relaxed">Ventilação, climatização e soluções de economia</p>
          </a>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Expected: Blue trust bar with 4 pillars below hero. Categories section with 8 white cards in a 4x2 grid (2x4 on mobile).

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add trust bar and categories sections"
```

---

### Task 5: Diferenciais + Quem Compra Sections

**Files:**
- Modify: `index.html` (add sections 4 and 5 after categories)

- [ ] **Step 1: Add diferenciais and quem compra sections**

Add after categories `</section>`:

```html
    <!-- ========== SECTION 4: DIFERENCIAIS ========== -->
    <section id="diferenciais" class="relative bg-gradient-to-br from-[#070E1A] to-navy-800 overflow-hidden">
      <!-- Ambient glow -->
      <div class="absolute -top-16 -right-16 w-64 h-64 bg-blue-500/10 rounded-full blur-3xl"></div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <!-- Header -->
        <div class="text-center mb-12 sm:mb-16 reveal">
          <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">DIFERENCIAIS</p>
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-white">Por que Taquaritinga confia na BENJA</h2>
        </div>

        <!-- 3 columns -->
        <div class="grid md:grid-cols-3 gap-5 sm:gap-6">
          <!-- Atendimento -->
          <div class="bg-white/[0.04] border border-white/[0.08] rounded-xl p-6 sm:p-8 text-center reveal">
            <div class="w-14 h-14 mx-auto mb-4 rounded-xl bg-blue-500/15 flex items-center justify-center">
              <img src="assets/icons/orientacao.svg" alt="" class="w-6 h-6" style="filter: invert(45%) sepia(98%) saturate(1000%) hue-rotate(190deg);">
            </div>
            <h3 class="text-white font-bold text-base sm:text-lg mb-3">Atendimento que Orienta</h3>
            <p class="text-white/45 text-sm leading-relaxed">Não vendemos só produtos. Ajudamos você a escolher a solução certa para cada situação da sua obra.</p>
          </div>

          <!-- Tudo em um (highlighted) -->
          <div class="relative bg-white/[0.04] border border-orange-500/20 rounded-xl p-6 sm:p-8 text-center reveal">
            <div class="absolute -top-px left-1/2 -translate-x-1/2 bg-orange-500 text-white text-[10px] font-bold px-4 py-1 rounded-b-lg tracking-wider">PRINCIPAL</div>
            <div class="w-14 h-14 mx-auto mb-4 rounded-xl bg-orange-500/15 flex items-center justify-center">
              <img src="assets/icons/tudo-em-um.svg" alt="" class="w-6 h-6" style="filter: invert(50%) sepia(98%) saturate(800%) hue-rotate(350deg);">
            </div>
            <h3 class="text-white font-bold text-base sm:text-lg mb-3">Tudo em Um Só Lugar</h3>
            <p class="text-white/45 text-sm leading-relaxed">Elétrica, hidráulica, iluminação, ferramentas, boiler e energia solar. Você resolve toda a obra em uma única visita.</p>
          </div>

          <!-- Agilidade -->
          <div class="bg-white/[0.04] border border-white/[0.08] rounded-xl p-6 sm:p-8 text-center reveal">
            <div class="w-14 h-14 mx-auto mb-4 rounded-xl bg-amber-400/15 flex items-center justify-center">
              <img src="assets/icons/relogio.svg" alt="" class="w-6 h-6" style="filter: invert(70%) sepia(98%) saturate(500%) hue-rotate(10deg);">
            </div>
            <h3 class="text-white font-bold text-base sm:text-lg mb-3">Agilidade que Resolve</h3>
            <p class="text-white/45 text-sm leading-relaxed">Sabemos que obra não espera. Atendimento rápido, estoque preparado e equipe pronta para ajudar.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== SECTION 5: QUEM COMPRA ========== -->
    <section class="bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <!-- Header -->
        <div class="text-center mb-12 sm:mb-16 reveal">
          <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">PARA QUEM É</p>
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-navy-800">A BENJA é para quem faz acontecer</h2>
          <p class="text-gray-500 text-sm sm:text-base mt-3 max-w-xl mx-auto">Do profissional experiente ao cliente que está reformando pela primeira vez</p>
        </div>

        <!-- 2x2 grid -->
        <div class="grid sm:grid-cols-2 gap-4 sm:gap-5 max-w-3xl mx-auto">
          <div class="flex items-center gap-4 bg-gray-50 border border-gray-100 rounded-xl p-5 reveal">
            <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center flex-shrink-0">
              <img src="assets/icons/construindo.svg" alt="" class="w-6 h-6" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <div>
              <h3 class="font-bold text-sm text-navy-800">Quem está construindo</h3>
              <p class="text-xs text-gray-500 mt-0.5">Material completo do início ao acabamento</p>
            </div>
          </div>

          <div class="flex items-center gap-4 bg-gray-50 border border-gray-100 rounded-xl p-5 reveal">
            <div class="w-12 h-12 rounded-xl bg-orange-500/10 flex items-center justify-center flex-shrink-0">
              <img src="assets/icons/reformando.svg" alt="" class="w-6 h-6" style="filter: invert(50%) sepia(98%) saturate(800%) hue-rotate(350deg);">
            </div>
            <div>
              <h3 class="font-bold text-sm text-navy-800">Quem está reformando</h3>
              <p class="text-xs text-gray-500 mt-0.5">Soluções práticas para trocar e melhorar</p>
            </div>
          </div>

          <div class="flex items-center gap-4 bg-gray-50 border border-gray-100 rounded-xl p-5 reveal">
            <div class="w-12 h-12 rounded-xl bg-amber-400/10 flex items-center justify-center flex-shrink-0">
              <img src="assets/icons/profissional.svg" alt="" class="w-6 h-6" style="filter: invert(60%) sepia(98%) saturate(500%) hue-rotate(10deg);">
            </div>
            <div>
              <h3 class="font-bold text-sm text-navy-800">Profissionais da área</h3>
              <p class="text-xs text-gray-500 mt-0.5">Eletricistas, encanadores, instaladores e pedreiros</p>
            </div>
          </div>

          <div class="flex items-center gap-4 bg-gray-50 border border-gray-100 rounded-xl p-5 reveal">
            <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center flex-shrink-0">
              <img src="assets/icons/praticidade.svg" alt="" class="w-6 h-6" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
            </div>
            <div>
              <h3 class="font-bold text-sm text-navy-800">Quem quer praticidade</h3>
              <p class="text-xs text-gray-500 mt-0.5">Comprar com orientação, sem complicação</p>
            </div>
          </div>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Expected: Dark diferenciais section with 3 cards (center one highlighted with orange border + "PRINCIPAL" badge). White "quem compra" section with 2x2 grid of persona cards.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add diferenciais and quem compra sections"
```

---

### Task 6: Promotional Banner + Testimonials + Institutional

**Files:**
- Modify: `index.html` (add sections 6, 7, 8 after quem compra)

- [ ] **Step 1: Add promotional, testimonials, and institutional sections**

Add after quem compra `</section>`:

```html
    <!-- ========== SECTION 6: PROMOTIONAL ========== -->
    <!-- === EDITABLE PROMO SECTION — Change texts below for each campaign === -->
    <section class="relative bg-gradient-to-r from-blue-600 via-blue-500 to-orange-500 overflow-hidden">
      <!-- Right side image area -->
      <div class="absolute right-0 top-0 bottom-0 w-1/3 hidden lg:block bg-white/5">
        <div class="absolute inset-0 flex items-center justify-center">
          <div class="text-center opacity-25">
            <div class="text-5xl mb-2">🏷️</div>
            <p class="text-white text-xs">Imagem promo</p>
          </div>
        </div>
      </div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 py-12 sm:py-16">
        <div class="max-w-xl lg:max-w-2xl">
          <!-- EDITABLE: Badge text -->
          <span class="inline-block bg-white/20 rounded-full px-4 py-1.5 text-xs font-semibold text-white mb-4">
            🔥 PROMOÇÃO DA SEMANA
          </span>

          <!-- EDITABLE: Main title -->
          <h2 class="text-2xl sm:text-3xl font-black text-white mb-3 reveal">
            Condições especiais para sua obra
          </h2>

          <!-- EDITABLE: Description -->
          <p class="text-white/70 text-sm sm:text-base leading-relaxed mb-6 max-w-md reveal">
            Parcele em até 10x sem juros no cartão. Descontos exclusivos para profissionais. Aproveite.
          </p>

          <!-- EDITABLE: CTA -->
          <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vi%20a%20promoção%20no%20site%20e%20gostaria%20de%20saber%20mais." target="_blank" rel="noopener"
             class="inline-flex items-center gap-2 bg-white text-blue-600 px-6 py-3 rounded-lg text-sm font-extrabold hover:bg-gray-50 hover:shadow-lg transition-all reveal">
            QUERO APROVEITAR →
          </a>
        </div>
      </div>
    </section>
    <!-- === END EDITABLE PROMO SECTION === -->

    <!-- ========== SECTION 7: TESTIMONIALS ========== -->
    <section class="bg-gray-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <!-- Header -->
        <div class="text-center mb-12 sm:mb-16 reveal">
          <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">DEPOIMENTOS</p>
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-navy-800">O que nossos clientes dizem</h2>
          <div class="inline-flex items-center gap-2 mt-4 bg-white border border-gray-100 rounded-full px-5 py-2 shadow-sm">
            <span class="text-lg font-extrabold text-orange-500">4.9</span>
            <span class="text-amber-400 text-sm">★★★★★</span>
            <span class="text-xs text-gray-500">no Google</span>
          </div>
        </div>

        <!-- Testimonial cards -->
        <div id="testimonials-container" class="grid md:grid-cols-3 gap-5 sm:gap-6">
          <!-- Testimonial 1 -->
          <div class="bg-white border border-gray-100 rounded-xl p-6 shadow-sm reveal">
            <div class="text-amber-400 text-xs mb-3 tracking-wider">★★★★★</div>
            <p class="text-sm text-gray-600 leading-relaxed italic mb-4">"Excelente atendimento, encontrei tudo que precisava para a reforma do banheiro. Equipe muito atenciosa e prestativa."</p>
            <div>
              <p class="text-sm font-bold text-navy-800">Maria C.</p>
              <p class="text-xs text-gray-500">Centro, Taquaritinga</p>
            </div>
          </div>

          <!-- Testimonial 2 -->
          <div class="bg-white border border-gray-100 rounded-xl p-6 shadow-sm reveal">
            <div class="text-amber-400 text-xs mb-3 tracking-wider">★★★★★</div>
            <p class="text-sm text-gray-600 leading-relaxed italic mb-4">"Melhor loja de materiais elétricos da cidade. Sempre tem o que preciso e o preço é justo. Recomendo para todos."</p>
            <div>
              <p class="text-sm font-bold text-navy-800">Carlos R.</p>
              <p class="text-xs text-gray-500">Eletricista</p>
            </div>
          </div>

          <!-- Testimonial 3 -->
          <div class="bg-white border border-gray-100 rounded-xl p-6 shadow-sm reveal">
            <div class="text-amber-400 text-xs mb-3 tracking-wider">★★★★★</div>
            <p class="text-sm text-gray-600 leading-relaxed italic mb-4">"Comprei toda a parte hidráulica da minha casa lá. Ótima variedade e me ajudaram a escolher tudo certinho."</p>
            <div>
              <p class="text-sm font-bold text-navy-800">Roberto S.</p>
              <p class="text-xs text-gray-500">Jd. América, Taquaritinga</p>
            </div>
          </div>
        </div>

        <!-- Mobile: swipe hint (hidden on desktop) -->
        <p class="md:hidden text-center text-xs text-gray-400 mt-4">Deslize para ver mais →</p>
      </div>
    </section>

    <!-- ========== SECTION 8: ABOUT ========== -->
    <section id="sobre" class="bg-gradient-to-br from-[#070E1A] to-navy-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <div class="flex flex-col md:flex-row items-center gap-8 md:gap-12 lg:gap-16">
          <!-- Mascot area -->
          <div class="w-32 h-32 sm:w-40 sm:h-40 rounded-2xl bg-blue-500/10 border border-blue-500/20 flex items-center justify-center flex-shrink-0 reveal">
            <!-- Replace with: <img src="assets/images/mascote.png" alt="Mascote BENJA" class="w-full h-full object-contain p-4"> -->
            <span class="text-white/30 text-xs text-center">MASCOTE<br>BENJA</span>
          </div>

          <!-- Text -->
          <div class="reveal">
            <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">SOBRE NÓS</p>
            <h2 class="text-2xl sm:text-3xl font-extrabold text-white mb-4">Mais que uma loja. Uma referência.</h2>
            <p class="text-white/50 text-sm sm:text-base leading-relaxed mb-6 max-w-xl">
              A BENJA nasceu com um propósito claro: ser o lugar onde Taquaritinga encontra tudo para elétrica, hidráulica e iluminação com atendimento de verdade. Não somos apenas uma loja de materiais — somos parceiros de quem constrói, reforma e instala. Nossa equipe entende de obra e está pronta para ajudar você a fazer a escolha certa.
            </p>
            <a href="#contato" class="inline-flex items-center gap-2 bg-orange-500/15 border border-orange-500/30 text-amber-400 px-5 py-2.5 rounded-lg text-sm font-semibold hover:bg-orange-500/25 transition-all">
              📍 Visite nossa loja no centro
            </a>
          </div>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Expected: Gradient promo banner, gray testimonials section with 3 cards + Google badge, dark about section with mascot placeholder.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add promotional, testimonials, and institutional sections"
```

---

### Task 7: Contact Section + Footer

**Files:**
- Modify: `index.html` (add sections 9, 10 after institutional)

- [ ] **Step 1: Add contact section and footer**

Add after institutional `</section>`:

```html
    <!-- ========== SECTION 9: CONTACT ========== -->
    <section id="contato" class="bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 py-16 sm:py-20 lg:py-24">
        <!-- Header -->
        <div class="text-center mb-12 sm:mb-16 reveal">
          <p class="text-xs tracking-[3px] text-orange-500 font-semibold mb-3">VENHA NOS VISITAR</p>
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-extrabold text-navy-800">Estamos prontos para atender você</h2>
        </div>

        <div class="grid lg:grid-cols-2 gap-8 lg:gap-12">
          <!-- Contact info -->
          <div class="reveal">
            <!-- Address -->
            <div class="flex items-center gap-4 py-4 border-b border-gray-100">
              <div class="w-10 h-10 rounded-lg bg-blue-500/10 flex items-center justify-center flex-shrink-0">
                <img src="assets/icons/map-pin.svg" alt="" class="w-5 h-5" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
              </div>
              <div>
                <p class="font-bold text-sm text-navy-800">Endereço</p>
                <p class="text-sm text-gray-500">Rua Da República, 409 — Centro, Taquaritinga - SP</p>
              </div>
            </div>

            <!-- Phone -->
            <div class="flex items-center gap-4 py-4 border-b border-gray-100">
              <div class="w-10 h-10 rounded-lg bg-blue-500/10 flex items-center justify-center flex-shrink-0">
                <img src="assets/icons/phone.svg" alt="" class="w-5 h-5" style="filter: invert(35%) sepia(98%) saturate(1000%) hue-rotate(200deg);">
              </div>
              <div>
                <p class="font-bold text-sm text-navy-800">Telefone</p>
                <a href="tel:+551632531567" class="text-sm text-gray-500 hover:text-blue-500 transition-colors">(16) 3253-1567</a>
              </div>
            </div>

            <!-- WhatsApp -->
            <div class="flex items-center gap-4 py-4 border-b border-gray-100">
              <div class="w-10 h-10 rounded-lg bg-orange-500/10 flex items-center justify-center flex-shrink-0">
                <img src="assets/icons/whatsapp.svg" alt="" class="w-5 h-5" style="filter: invert(50%) sepia(98%) saturate(800%) hue-rotate(350deg);">
              </div>
              <div>
                <p class="font-bold text-sm text-navy-800">WhatsApp</p>
                <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA." target="_blank" rel="noopener" class="text-sm text-gray-500 hover:text-orange-500 transition-colors">Clique para conversar</a>
              </div>
            </div>

            <!-- Hours -->
            <div class="flex items-center gap-4 py-4">
              <div class="w-10 h-10 rounded-lg bg-amber-400/10 flex items-center justify-center flex-shrink-0">
                <img src="assets/icons/clock.svg" alt="" class="w-5 h-5" style="filter: invert(60%) sepia(98%) saturate(500%) hue-rotate(10deg);">
              </div>
              <div>
                <p class="font-bold text-sm text-navy-800">Horário</p>
                <p class="text-xs text-gray-500 leading-relaxed">Seg a Sex: 7h–18h30 · Sáb: 8h–16h · Dom: 8h–12h</p>
              </div>
            </div>

            <!-- Action buttons -->
            <div class="flex gap-3 mt-6">
              <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20um%20orçamento." target="_blank" rel="noopener"
                 class="flex-1 bg-gradient-to-r from-orange-500 to-orange-600 text-white py-3 rounded-lg text-sm font-bold text-center hover:shadow-lg hover:shadow-orange-500/25 transition-all">
                💬 WHATSAPP
              </a>
              <a href="https://www.google.com/maps/dir/?api=1&destination=Rua+Da+República,+409,+Centro,+Taquaritinga+-+SP,+15900-011" target="_blank" rel="noopener"
                 class="flex-1 bg-blue-600 text-white py-3 rounded-lg text-sm font-bold text-center hover:bg-blue-700 transition-colors">
                📍 TRAÇAR ROTA
              </a>
            </div>
          </div>

          <!-- Map -->
          <div class="reveal">
            <div class="rounded-xl overflow-hidden border border-gray-100 shadow-sm h-72 sm:h-80 lg:h-full lg:min-h-[360px]">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3718.5!2d-48.5053!3d-21.4053!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2sRua+Da+Rep%C3%BAblica%2C+409%2C+Taquaritinga+-+SP!5e0!3m2!1spt-BR!2sbr!4v1"
                width="100%"
                height="100%"
                style="border:0; min-height: 100%;"
                allowfullscreen=""
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
                title="Localização BENJA Elétrica">
              </iframe>
            </div>
          </div>
        </div>
      </div>
    </section>

  </main>

  <!-- ========== SECTION 10: FOOTER ========== -->
  <footer class="bg-navy-900 border-t-[3px] border-orange-500">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 py-12 sm:py-16">
      <!-- 4-column grid -->
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-8 lg:gap-12 pb-10 border-b border-white/5">
        <!-- Col 1: Brand -->
        <div class="col-span-2 lg:col-span-1">
          <a href="#" class="text-blue-400 font-black text-2xl tracking-widest">BENJA</a>
          <p class="text-white/35 text-xs leading-relaxed mt-3 max-w-xs">
            Referência em elétrica, hidráulica e iluminação em Taquaritinga e região. Atendimento especializado para quem constrói e reforma.
          </p>
          <!-- Social -->
          <div class="flex gap-2 mt-4">
            <a href="https://www.facebook.com/p/Benja-El%C3%A9trica-e-Hidr%C3%A1ulica-100040646449109/" target="_blank" rel="noopener" aria-label="Facebook"
               class="w-9 h-9 rounded-lg bg-white/5 hover:bg-white/10 flex items-center justify-center transition-colors">
              <img src="assets/icons/facebook.svg" alt="" class="w-4 h-4 invert opacity-40">
            </a>
            <a href="https://www.instagram.com/benja.eletricahidraulica/" target="_blank" rel="noopener" aria-label="Instagram"
               class="w-9 h-9 rounded-lg bg-white/5 hover:bg-white/10 flex items-center justify-center transition-colors">
              <img src="assets/icons/instagram.svg" alt="" class="w-4 h-4 invert opacity-40">
            </a>
            <a href="https://wa.me/5516XXXXXXXXX" target="_blank" rel="noopener" aria-label="WhatsApp"
               class="w-9 h-9 rounded-lg bg-white/5 hover:bg-white/10 flex items-center justify-center transition-colors">
              <img src="assets/icons/whatsapp.svg" alt="" class="w-4 h-4 invert opacity-40">
            </a>
          </div>
        </div>

        <!-- Col 2: Navigation -->
        <div>
          <h4 class="text-white text-xs font-bold tracking-wider mb-4">NAVEGAÇÃO</h4>
          <ul class="space-y-2.5">
            <li><a href="#" class="text-white/35 text-xs hover:text-white transition-colors">Início</a></li>
            <li><a href="#categorias" class="text-white/35 text-xs hover:text-white transition-colors">Categorias</a></li>
            <li><a href="#diferenciais" class="text-white/35 text-xs hover:text-white transition-colors">Diferenciais</a></li>
            <li><a href="#sobre" class="text-white/35 text-xs hover:text-white transition-colors">Sobre</a></li>
            <li><a href="#contato" class="text-white/35 text-xs hover:text-white transition-colors">Contato</a></li>
          </ul>
        </div>

        <!-- Col 3: Categories -->
        <div>
          <h4 class="text-white text-xs font-bold tracking-wider mb-4">CATEGORIAS</h4>
          <ul class="space-y-2.5">
            <li><a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Elétrica." target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">Elétrica</a></li>
            <li><a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Hidráulica." target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">Hidráulica</a></li>
            <li><a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Iluminação." target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">Iluminação</a></li>
            <li><a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Ferramentas." target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">Ferramentas</a></li>
            <li><a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Tenho%20interesse%20em%20Energia%20Solar." target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">Energia Solar</a></li>
          </ul>
        </div>

        <!-- Col 4: Contact -->
        <div>
          <h4 class="text-white text-xs font-bold tracking-wider mb-4">CONTATO</h4>
          <ul class="space-y-2.5">
            <li><a href="tel:+551632531567" class="text-white/35 text-xs hover:text-white transition-colors">(16) 3253-1567</a></li>
            <li><a href="https://wa.me/5516XXXXXXXXX" target="_blank" rel="noopener" class="text-white/35 text-xs hover:text-white transition-colors">WhatsApp</a></li>
            <li><span class="text-white/35 text-xs">Rua Da República, 409</span></li>
            <li><span class="text-white/35 text-xs">Centro — Taquaritinga</span></li>
          </ul>
        </div>
      </div>

      <!-- Final CTA -->
      <div class="text-center py-8 border-b border-white/5">
        <p class="text-white/50 text-sm font-medium mb-4">Precisa de orçamento? Fale com a gente agora.</p>
        <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20um%20orçamento." target="_blank" rel="noopener"
           class="inline-flex items-center gap-2 bg-gradient-to-r from-orange-500 to-orange-600 text-white px-6 py-3 rounded-lg text-sm font-bold hover:shadow-lg hover:shadow-orange-500/25 transition-all">
          💬 PEDIR ORÇAMENTO NO WHATSAPP
        </a>
      </div>

      <!-- Copyright -->
      <div class="text-center pt-6">
        <p class="text-white/20 text-xs">© 2026 BENJA Elétrica, Hidráulica e Iluminação. Todos os direitos reservados.</p>
      </div>
    </div>
  </footer>
```

**Important:** Remove the closing `</main>` that was after `<!-- Sections will be added in subsequent tasks -->` — it's now placed right before the footer. The `</main>` tag goes after the contact section's `</section>`, before the `<footer>`.

- [ ] **Step 2: Verify in browser**

Expected: Contact section with info + map placeholder, dark footer with 4 columns, final CTA, and copyright.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add contact section and premium footer"
```

---

### Task 8: JavaScript — Mobile Menu, Scroll Reveal, WhatsApp FAB, Back to Top

**Files:**
- Modify: `index.html` (add `<script>` before `</body>`)

- [ ] **Step 1: Add JavaScript before closing body tag**

Add this right before `</body>`:

```html
  <!-- ========== WHATSAPP FLOATING BUTTON ========== -->
  <a href="https://wa.me/5516XXXXXXXXX?text=Olá!%20Vim%20pelo%20site%20da%20BENJA.%20Gostaria%20de%20mais%20informações." target="_blank" rel="noopener"
     aria-label="Conversar no WhatsApp"
     class="fixed bottom-5 right-5 z-50 w-14 h-14 bg-[#25D366] rounded-full flex items-center justify-center shadow-lg shadow-green-500/30 animate-pulse-whatsapp hover:scale-110 transition-transform">
    <img src="assets/icons/whatsapp.svg" alt="" class="w-7 h-7 invert">
  </a>

  <!-- ========== BACK TO TOP BUTTON ========== -->
  <button id="back-to-top" aria-label="Voltar ao topo"
          class="fixed bottom-5 right-24 z-50 w-11 h-11 bg-blue-600 rounded-full flex items-center justify-center shadow-lg opacity-0 invisible transition-all duration-300 hover:bg-blue-700">
    <img src="assets/icons/arrow-up.svg" alt="" class="w-5 h-5 invert">
  </button>

  <!-- ========== JAVASCRIPT ========== -->
  <script>
    // === Mobile Menu Toggle ===
    const menuToggle = document.getElementById('menu-toggle');
    const mobileMenu = document.getElementById('mobile-menu');
    const menuIconOpen = document.getElementById('menu-icon-open');
    const menuIconClose = document.getElementById('menu-icon-close');

    menuToggle.addEventListener('click', () => {
      const isOpen = !mobileMenu.classList.contains('hidden');
      mobileMenu.classList.toggle('hidden');
      menuIconOpen.classList.toggle('hidden');
      menuIconClose.classList.toggle('hidden');
      menuToggle.setAttribute('aria-label', isOpen ? 'Abrir menu' : 'Fechar menu');
    });

    // Close mobile menu when clicking a link
    document.querySelectorAll('.mobile-menu-link').forEach(link => {
      link.addEventListener('click', () => {
        mobileMenu.classList.add('hidden');
        menuIconOpen.classList.remove('hidden');
        menuIconClose.classList.add('hidden');
      });
    });

    // === Scroll Reveal (Intersection Observer) ===
    const revealElements = document.querySelectorAll('.reveal');
    const revealObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          revealObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

    revealElements.forEach(el => revealObserver.observe(el));

    // === Back to Top Button ===
    const backToTop = document.getElementById('back-to-top');

    window.addEventListener('scroll', () => {
      if (window.scrollY > 400) {
        backToTop.classList.remove('opacity-0', 'invisible');
        backToTop.classList.add('opacity-100', 'visible');
      } else {
        backToTop.classList.add('opacity-0', 'invisible');
        backToTop.classList.remove('opacity-100', 'visible');
      }
    }, { passive: true });

    backToTop.addEventListener('click', () => {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    });

    // === Mobile Testimonials Horizontal Scroll ===
    const testimonialsContainer = document.getElementById('testimonials-container');
    if (window.innerWidth < 768) {
      testimonialsContainer.classList.remove('grid', 'md:grid-cols-3', 'gap-5', 'sm:gap-6');
      testimonialsContainer.classList.add('flex', 'gap-4', 'overflow-x-auto', 'snap-x', 'snap-mandatory', 'pb-4', '-mx-4', 'px-4');
      testimonialsContainer.style.scrollbarWidth = 'none';
      testimonialsContainer.querySelectorAll(':scope > div').forEach(card => {
        card.classList.add('min-w-[280px]', 'snap-center', 'flex-shrink-0');
      });
    }
  </script>
```

- [ ] **Step 2: Verify all interactions work**

Open in browser and test:
- Mobile menu: resize to mobile, click hamburger — menu opens/closes
- Scroll reveal: scroll down — sections fade in
- WhatsApp FAB: green button visible bottom-right, pulses
- Back to top: scroll past hero — blue button appears bottom-right, clicking scrolls to top
- Smooth scroll: click nav links — smooth scroll to sections
- Testimonials on mobile: resize to <768px, refresh — horizontal scroll works

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add mobile menu, scroll reveal, WhatsApp FAB, and back-to-top"
```

---

### Task 9: Final Polish — Mobile Swipe Hint, Navbar Scroll Effect, Accessibility

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add navbar background darkening on scroll**

In the `<script>` section, add this after the back-to-top scroll listener code (before the mobile testimonials code):

```javascript
    // === Navbar scroll effect ===
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 50) {
        navbar.classList.add('shadow-lg', 'shadow-black/20');
      } else {
        navbar.classList.remove('shadow-lg', 'shadow-black/20');
      }
    }, { passive: true });
```

- [ ] **Step 2: Add custom scrollbar hide CSS**

In the `<style>` section, add:

```css
    /* Hide scrollbar for mobile carousels */
    .scrollbar-hide::-webkit-scrollbar { display: none; }
    .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }
```

- [ ] **Step 3: Update testimonials JS to use scrollbar-hide class**

In the mobile testimonials JS code, change `testimonialsContainer.style.scrollbarWidth = 'none';` to:

```javascript
      testimonialsContainer.classList.add('scrollbar-hide');
```

- [ ] **Step 4: Verify everything works end-to-end**

Full checklist:
- Top bar shows hours + phone
- Nav is sticky, links smooth-scroll, mobile menu works
- Hero: headline, gradient text, CTAs visible
- Trust bar: 4 columns with icons
- Categories: 8 cards, hover effects
- Diferenciais: 3 cards, center highlighted
- Quem compra: 4 persona cards
- Promo: gradient banner with CTA
- Testimonials: 3 cards (carousel on mobile)
- About: mascot placeholder + text
- Contact: info + map + buttons
- Footer: 4 columns + CTA + copyright
- WhatsApp FAB: fixed, pulses
- Back to top: appears after scroll
- Scroll reveal: all sections animate in
- Mobile: everything stacks properly, touch targets large enough

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: add scroll effects, accessibility polish, and final refinements"
```

---

### Task 10: Validation and Final Commit

**Files:**
- None new. Validation only.

- [ ] **Step 1: Check HTML validity**

Open `index.html` in browser. Open DevTools console. Confirm no errors. Check:
- All images load (SVG icons)
- No 404s in network tab
- No JS errors in console
- Tailwind classes applied correctly

- [ ] **Step 2: Test mobile responsiveness**

In browser DevTools, toggle device toolbar. Check at:
- 375px (iPhone SE)
- 390px (iPhone 14)
- 768px (iPad)
- 1024px (tablet landscape)
- 1440px (desktop)

Verify: no horizontal scroll, no overlapping text, CTAs are thumb-reachable, menu works.

- [ ] **Step 3: Final commit with all files**

```bash
git add -A
git commit -m "chore: final validation — site complete and tested"
```
