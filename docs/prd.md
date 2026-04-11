# IA para Vendas — Product Requirements Document (PRD)

> **Versao:** 1.0
> **Data:** 2026-04-10
> **Autor:** Morgan (PM Agent)
> **Briefing base:** `docs/brief.md`
> **Status:** Draft

---

## 1. Goals and Background Context

### Goals

- Entregar um site single-page scroll que apresente os 5 passos de vendas com IA de forma visual e impactante
- Servir como material de apoio ao vivo durante a palestra (2026-04-11)
- Funcionar como landing page pos-evento para captura de contatos via QR code
- Ser acessivel prioritariamente em dispositivos moveis
- Carregar em menos de 3 segundos em conexao 4G

### Background Context

Uma palestra presencial sobre "IA para Vendas" acontecera amanha (2026-04-11). O palestrante precisa de um site de apoio que funcione tanto como visual ao vivo quanto como material de referencia para os participantes levarem pra casa. O site segue a metodologia dos 5 passos: Planejamento, Captacao, Conversao, Vendas e Pos-Venda. O publico e composto por empreendedores e vendedores com nivel tecnico baixo a medio — precisam ver resultados praticos, nao teoria. O brainstorm e briefing ja foram produzidos pelo @analyst com insights do Hormozi Workshop framework.

### Change Log

| Data | Versao | Descricao | Autor |
|------|--------|-----------|-------|
| 2026-04-10 | 1.0 | Criacao inicial do PRD a partir do briefing | Morgan (PM) |

---

## 2. Requirements

### Functional

- **FR1:** O site deve exibir uma secao Hero com titulo, subtitulo e CTA de scroll para a primeira secao
- **FR2:** O site deve conter 5 secoes de conteudo, uma para cada passo do funil (Planejamento, Captacao, Conversao, Vendas, Pos-Venda)
- **FR3:** Cada secao deve exibir: numero do passo (01-05), pergunta-ancora, topicos principais, resultado tangivel destacado e insight/estatistica
- **FR4:** O site deve ter uma navegacao fixa (sticky nav) com links para cada secao e indicador visual do passo atual
- **FR5:** O site deve exibir uma timeline visual de recapitulacao dos 5 passos antes do CTA final
- **FR6:** O site deve ter uma secao de CTA final com formulario de captura de contato (e-mail ou link WhatsApp)
- **FR7:** O site deve exibir informacoes do palestrante (nome, bio resumida, contato, redes sociais) no footer ou CTA final
- **FR8:** Scroll animations devem ser aplicadas nas secoes ao entrar na viewport (fade-in, slide-up)
- **FR9:** A navegacao sticky deve destacar visualmente o passo atual conforme o usuario rola a pagina
- **FR10:** O site deve incluir um footer com creditos e ano

### Non Functional

- **NFR1:** Carregamento inicial < 3 segundos em conexao 4G
- **NFR2:** Lighthouse Performance score > 90
- **NFR3:** Site 100% estatico — zero dependencia de backend ou banco de dados
- **NFR4:** Mobile-first — layout otimizado para telas de 375px+ (prioridade absoluta)
- **NFR5:** Responsivo para tablet (768px+) e desktop (1024px+)
- **NFR6:** Textos legiveis sem zoom em dispositivos moveis
- **NFR7:** Area de toque minima de 44x44px em botoes e links interativos
- **NFR8:** Animacoes nao devem impactar performance (preferir CSS nativo ou IntersectionObserver)
- **NFR9:** Imagens otimizadas em formato WebP com lazy loading
- **NFR10:** Funcionar offline apos primeiro carregamento (service worker opcional, baixa prioridade)

---

## 3. User Interface Design Goals

### Overall UX Vision

Uma experiencia de scroll vertical imersiva que guia o visitante por uma jornada dos 5 passos de vendas com IA. Cada secao funciona como um "capitulo" visual — com identidade propria mas parte de uma narrativa coesa. O sentimento ao navegar deve ser de progressao e clareza: "estou aprendendo algo pratico a cada scroll."

### Key Interaction Paradigms

- **Scroll-driven storytelling:** A narrativa se desenrola conforme o usuario rola — cada secao revela um novo passo
- **Progress tracking:** Navegacao sticky mostra onde o usuario esta no funil (1/5, 2/5, etc.)
- **Snap sections:** Cada secao ocupa viewport completa ou quase completa, criando separacao clara entre passos
- **Reveal animations:** Conteudo aparece suavemente ao entrar na viewport, guiando o olhar

### Core Screens and Views

Este e um site single-page, entao "screens" sao secoes de scroll:

1. **Hero Section** — Primeiro impacto: titulo, subtitulo, CTA
2. **Step Sections (x5)** — Conteudo dos passos com layout padronizado
3. **Timeline Recap** — Visualizacao horizontal/vertical conectando os 5 passos
4. **CTA Section** — Captura de contato + info do palestrante
5. **Footer** — Creditos minimos

### Accessibility

WCAG AA basico:
- Contraste minimo 4.5:1 para texto
- Navegacao por teclado funcional
- Alt text em elementos visuais
- Focus visible em links/botoes

### Branding

- Paleta a definir pelo palestrante (fallback: dark theme com acentos em gradiente azul-roxo para transmitir tecnologia/inovacao)
- Tipografia moderna e impactante (sugestao: Inter ou similar sans-serif)
- Icones minimalistas para cada passo (line icons)
- Sem logo definida ainda — usar tipografia estilizada como placeholder

### Target Device and Platforms

**Mobile-first (Web Responsive)**
- Prioridade: iPhone/Android via QR code (375px - 428px)
- Secundario: Tablet landscape (768px+)
- Terciario: Desktop (1024px+)

---

## 4. Technical Assumptions

### Repository Structure

**Single file ou flat structure** — Nao e necessario monorepo nem polyrepo. Um unico diretorio com HTML, CSS e JS.

```
/
├── index.html
├── styles.css
├── script.js
└── assets/
    └── (icones, imagens)
```

### Service Architecture

**Site 100% estatico** — Zero backend, zero API, zero banco de dados. HTML + CSS + JS vanilla. Sem build step obrigatorio.

**Stack:**
- HTML5 semantico
- CSS3 com custom properties (variaveis CSS para temas)
- JavaScript vanilla (ES6+) — sem frameworks
- Animacoes: CSS nativo + IntersectionObserver API
- Opcional: Tailwind CSS via CDN para produtividade

### Testing Requirements

**Manual apenas** — dado o prazo de 1 dia:
- Teste visual em iPhone (Safari) e Android (Chrome)
- Teste de scroll e navegacao
- Teste de responsividade via DevTools
- Lighthouse audit para performance

### Additional Technical Assumptions

- Deploy em hosting estatico (Vercel, Netlify ou GitHub Pages)
- Sem necessidade de build pipeline
- Sem necessidade de minificacao na v1 (arquivos ja serao leves)
- Fontes carregadas via Google Fonts ou system fonts
- Icones via SVG inline ou biblioteca leve (Lucide, Phosphor)
- Formulario de captura pode ser link direto para WhatsApp (`https://wa.me/...`) ou form simples com Formspree/Google Forms embed

---

## 5. Epic List

Dado o escopo minimo (1 pagina estatica, prazo de 1 dia), o projeto inteiro cabe em **1 unico epic**:

### Epic 1: Site Single-Page "IA para Vendas"

**Goal:** Entregar o site completo com todas as secoes, navegacao, animacoes e CTA funcional, pronto para uso na palestra de amanha.

**Rationale:** Dividir em multiplos epics nao faz sentido — o escopo e pequeno, o prazo e de horas, e todas as partes dependem umas das outras para entregar valor. Um unico epic com stories focadas e a abordagem correta.

---

## 6. Epic 1: Site Single-Page "IA para Vendas"

**Goal:** Construir e deployar um site single-page scroll que apresente os 5 passos de vendas com IA, com navegacao fixa, animacoes de scroll, secao de captura de contato e design mobile-first profissional. O site sera usado ao vivo na palestra de 2026-04-11 e compartilhado via QR code.

---

### Story 1.1: Estrutura HTML e Hero Section

**Como** visitante do site,
**eu quero** ver uma pagina com estrutura semantica e uma Hero Section impactante,
**para que** eu entenda imediatamente do que se trata e queira continuar navegando.

**Acceptance Criteria:**

1. HTML5 semantico com sections, nav, header, main, footer
2. Meta tags de viewport, charset, title e description configuradas
3. Hero section ocupa viewport completa (100vh) com titulo, subtitulo e botao CTA
4. CTA do hero faz scroll suave ate a primeira secao de conteudo
5. Estrutura HTML das 5 secoes de passo ja criada (conteudo pode ser placeholder)
6. Arquivo CSS e JS linkados e funcionais
7. Fonte carregada (Inter via Google Fonts ou system font stack)

---

### Story 1.2: Secoes dos 5 Passos com Conteudo Real

**Como** visitante do site,
**eu quero** ver as 5 secoes de conteudo com informacoes reais dos passos de vendas com IA,
**para que** eu entenda o que fazer em cada etapa do funil.

**Acceptance Criteria:**

1. Cada secao exibe: numero grande (01-05), titulo do passo, pergunta-ancora
2. Cada secao lista os topicos principais do passo (conforme briefing)
3. Cada secao destaca visualmente o "resultado tangivel"
4. Cada secao exibe o insight/estatistica de apoio
5. Conteudo final extraido do briefing (docs/brief.md secoes 5.1 a 5.5)
6. Textos escritos em tom direto, pratico e conversacional ("voce")
7. Layout padronizado e consistente entre as 5 secoes

---

### Story 1.3: Design Visual e Estilizacao CSS

**Como** visitante do site,
**eu quero** ver um site visualmente profissional e moderno,
**para que** eu tenha confianca no conteudo e queira compartilhar.

**Acceptance Criteria:**

1. Paleta de cores definida com custom properties CSS (dark theme com acentos vibrantes como fallback)
2. Tipografia configurada: titulos impactantes (bold, grande), corpo legivel
3. Espacamento generoso entre elementos (padding/margin consistentes)
4. Cada secao de passo tem uma identidade visual sutil (cor de acento ou icone diferente)
5. Contraste minimo 4.5:1 em todo texto (WCAG AA)
6. Layout mobile-first: funciona perfeitamente em 375px
7. Responsivo para tablet (768px+) e desktop (1024px+)
8. Botoes e links com area de toque minima 44x44px

---

### Story 1.4: Navegacao Sticky e Indicador de Progresso

**Como** visitante do site,
**eu quero** ter uma navegacao fixa que me mostre onde estou e me permita pular entre secoes,
**para que** eu navegue facilmente pelos 5 passos.

**Acceptance Criteria:**

1. Nav fixa (sticky) no topo da pagina aparece apos scroll do hero
2. Nav exibe os 5 passos como links clicaveis
3. Clicar em um passo faz scroll suave ate a secao correspondente
4. O passo atual e destacado visualmente na nav (cor, peso, underline ou similar)
5. Deteccao do passo atual usa IntersectionObserver (sem scroll listeners pesados)
6. Nav e compacta no mobile (texto abreviado ou apenas numeros)
7. Nav nao bloqueia conteudo (z-index e espacamento adequados)

---

### Story 1.5: Animacoes de Scroll

**Como** visitante do site,
**eu quero** que o conteudo apareca suavemente conforme eu rolo a pagina,
**para que** a experiencia de navegacao seja fluida e envolvente.

**Acceptance Criteria:**

1. Elementos das secoes aparecem com animacao fade-in + slide-up ao entrar na viewport
2. Animacoes usam IntersectionObserver (nao scroll listener)
3. Animacoes sao suaves (duracao ~400-600ms, ease-out)
4. Elementos animam apenas uma vez (nao re-animam ao rolar para cima e voltar)
5. Animacoes respeitam `prefers-reduced-motion` — desativadas se usuario preferir
6. Performance: sem jank visivel durante scroll (60fps)

---

### Story 1.6: Timeline Visual e CTA Final

**Como** visitante do site,
**eu quero** ver uma recapitulacao visual dos 5 passos e um chamado para acao claro,
**para que** eu lembre do framework completo e saiba como dar o proximo passo.

**Acceptance Criteria:**

1. Secao de timeline exibe os 5 passos conectados visualmente (horizontal no desktop, vertical no mobile)
2. Cada passo na timeline tem icone/numero e titulo curto
3. Timeline usa animacao sequencial ao entrar na viewport
4. Secao de CTA final com headline de fechamento e campo de captura
5. Captura funcional: link WhatsApp (`wa.me/...`) ou formulario basico (Formspree/Google Forms)
6. Informacoes do palestrante visíveis (nome, contato, redes)
7. Footer com creditos e ano

---

### Story 1.7: Otimizacao e QR Code

**Como** palestrante,
**eu quero** que o site esteja otimizado e acessivel via QR code,
**para que** os participantes acessem facilmente durante a palestra.

**Acceptance Criteria:**

1. Lighthouse Performance > 90
2. Todas as imagens em formato WebP com lazy loading
3. CSS e JS minimos (sem codigo morto)
4. Fontes com `font-display: swap`
5. Site funciona sem JavaScript (conteudo visivel, animacoes como progressive enhancement)
6. QR code gerado apontando para a URL do site
7. Testado em iPhone Safari e Android Chrome
8. Testado em modo offline apos primeiro carregamento (conteudo visivel)

---

## 7. Checklist Results Report

_A ser preenchido apos revisao com `pm-checklist`._

---

## 8. Next Steps

### UX Expert Prompt

> **@ux-design-expert**: Revise o PRD em `docs/prd.md` e o briefing em `docs/brief.md`. Crie um layout detalhado (wireframe textual ou visual) para o site single-page "IA para Vendas" com foco mobile-first. O site tem: Hero, 5 secoes de passos, timeline de recap e CTA final. Priorize hierarquia visual, spacing e a experiencia de scroll. Output em `docs/ux-layout.md`.

### Architect Prompt

> **@architect**: Nao necessario para este projeto. Stack definida no PRD: HTML + CSS + JS vanilla, site estatico, sem build step. @dev pode implementar diretamente a partir do PRD e layout UX.

---

— Morgan, planejando o futuro
