<div align="center">
  <h1>Teko</h1>
  <p><strong>Server-first UI engine for Node.js</strong></p>
  <p>Component-based SSR templates for modern web apps — with layouts, islands, and optional hydration.</p>
</div>

---

## O que é o Teko?

> **Teko é uma engine de frontend server-first com sintaxe de templates, componentes reutilizáveis e SSR nativo, com ilhas interativas quando necessário.**

Inspirado no [EdgeJS](https://edgejs.dev/), o Teko vai além de uma template engine tradicional: ele oferece um modelo completo de renderização server-side com suporte a componentes com props, slots, layouts e contexto compartilhado — e hidratação parcial no cliente apenas quando necessário.

---

## Visão

**Teko = runtime de frontend server-first**

| Pacote | Responsabilidade |
|--------|-----------------|
| `@teko/core` | Parser, compilador e renderer |
| `@teko/ssr` | Renderização server-side por rota |
| `@teko/components` | Componentes com props, slots e contexto |
| `@teko/client` | Hidratação opcional por ilha |
| `@teko/router` | Integração com Node/Fastify/Adonis/Express |
| `@teko/build` | Pré-compilação opcional para produção |

---

## Diferenciais

- ✅ **Edge-inspired** — sintaxe familiar, modelo mental simples
- 🖥️ **SSR como padrão** — HTML no servidor, performance e SEO de graça
- 🏝️ **Islands Architecture** — componentes que nascem no servidor e hidratam no cliente apenas quando necessário
- 🧩 **Componentes reutilizáveis** — props, slots nomeados, layouts e provide/inject
- ⚡ **Async templates** — suporte nativo a `async/await` dentro dos templates
- 🔒 **HTML escaping automático** — seguro por padrão
- 🪶 **Sem Virtual DOM** — renderização direta para string, simples e rápido

---

## Modos de Renderização

### 1. SSR Puro
Renderiza tudo no servidor e entrega HTML estático. Ideal para landing pages, blogs e dashboards.

### 2. SSR + Islands
A página nasce inteira no servidor, mas componentes específicos hidratam no cliente.

```
navbar         → SSR
conteúdo       → SSR
filtro tabela  → SSR + hidratação
modal          → SSR + hidratação
```

### 3. Client-only (opt-in)
Para componentes pesados como editores ricos, mapas ou widgets que só fazem sentido no navegador.

---

## Sintaxe

### Template básico

```teko
<h1>Olá, {{ user.name }}</h1>

@if(user.loggedIn)
  <p>Bem-vindo de volta</p>
@else
  <p>Faça login para continuar</p>
@end
```

### Loop

```teko
<ul>
  @each(post in posts)
    <li>{{ post.title }}</li>
  @end
</ul>
```

### Componentes com props e slots

```teko
@ui.card({ class: 'shadow-lg' })
  @slot('header')
    <h2>Título</h2>
  @end

  @slot('content')
    <p>Conteúdo do card</p>
  @end
@end
```

### Layouts

```teko
@layout.app({ title: 'Home' })
  @slot('meta')
    <meta name="description" content="Página inicial">
  @end

  @slot('main')
    <h1>Hello</h1>
  @end
@end
```

### Islands (hidratação parcial)

```teko
@islands.comments({ postId: post.id }, { hydrate: 'visible' })
@end
```

Estratégias de hidratação disponíveis: `load` · `idle` · `visible` · `interaction` · `media(query)`

---

## Arquitetura

```
Request
  → Router
  → Data Loader
  → Template Resolver
  → Compiler / Cache
  → SSR Renderer
  → Island Manifest
  → HTML Response
  → Client Hydration (opcional)
```

### Estrutura do Monorepo

```
teko/
├─ packages/
│  ├─ core/          # parser, AST, compiler
│  ├─ ssr/           # renderer HTTP/server
│  ├─ runtime/       # helpers, escaping, slots, context
│  ├─ client/        # hydration runtime
│  ├─ vite-plugin/   # integração com Vite
│  ├─ router/        # integração com frameworks
│  └─ create-teko/   # scaffolding CLI
│
├─ playground/
├─ examples/
└─ docs/
```

---

## Tipos de Componentes

| Tipo | Descrição | Exemplos |
|------|-----------|---------|
| **Server Components** | Nunca hidratam, geram apenas HTML | hero, footer, article-body |
| **Island Components** | SSR + hidratação no cliente | autocomplete, tabs, modal, data-table |
| **Client Components** | Apenas no navegador | editor rico, mapas, widgets pesados |

---

## Roadmap

### MVP 1
- [x] Parser + AST
- [ ] Expressões `{{ }}`
- [ ] Diretivas `@if`, `@else`, `@each`
- [ ] Componentes com props e slots
- [ ] Layouts
- [ ] SSR + cache

### MVP 2
- [ ] Provide/Inject
- [ ] Assets/Head manager
- [ ] Islands com hidratação parcial
- [ ] Data loaders por página

### MVP 3
- [ ] Streaming SSR
- [ ] Async blocks (suspense-like)
- [ ] Server actions / forms
- [ ] Plugin API

---

## Stack Técnica

| Decisão | Escolha |
|---------|---------|
| Linguagem | TypeScript |
| Runtime | Node.js |
| Parser | Custom tokenizer + recursive descent parser |
| SSR | String renderer |
| Client runtime | Vanilla TypeScript (pequeno e focado) |
| Build | Vite |
| HTML escaping | Obrigatório por padrão |
| Async templates | ✅ Sim |
| Virtual DOM | ❌ Não |

---

## Comunidade

Este repositório contém os arquivos de saúde padrão da organização **tekojs** no GitHub:

- [**SECURITY.md**](./SECURITY.md) — política de segurança e reporte de vulnerabilidades
- [**ISSUE_TEMPLATE/**](./ISSUE_TEMPLATE/) — templates para abertura de issues
- [**PULL_REQUEST_TEMPLATE.md**](./PULL_REQUEST_TEMPLATE.md) — template para pull requests

---

<div align="center">
  <sub>Teko — server-first, simples e rápido.</sub>
</div>