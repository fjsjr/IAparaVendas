# UX Layout — Site "IA para Vendas"

> **Data:** 2026-04-10
> **Autor:** UX Designer (Design Squad) via Morgan (PM)
> **Input:** `docs/prd.md` + `docs/brief.md`
> **Tipo:** Wireframe textual + especificacoes de layout mobile-first

---

## Design Principles Aplicados

1. **Content first** — layout desenhado ao redor do conteudo real, nao de placeholders
2. **Progressive disclosure** — cada scroll revela um novo passo, sem sobrecarregar
3. **Consistency** — todas as 5 secoes seguem o mesmo padrao visual
4. **Mobile-first** — tudo desenhado para 375px primeiro, expandido para desktop depois

---

## Paleta de Cores (Fallback — Dark Theme)

```
--bg-primary:      #0A0A0F        (fundo principal — quase preto)
--bg-section:      #12121A        (fundo das secoes de passos)
--bg-card:         #1A1A2E        (cards e destaques)
--text-primary:    #F5F5F7        (texto principal — branco suave)
--text-secondary:  #A1A1AA        (texto de apoio — cinza claro)
--accent-1:        #6C63FF        (roxo — Planejamento)
--accent-2:        #00D4AA        (verde-agua — Captacao)
--accent-3:        #FF6B6B        (coral — Conversao)
--accent-4:        #FFD93D        (amarelo — Vendas)
--accent-5:        #4ECDC4        (teal — Pos-Venda)
--accent-gradient:  linear-gradient(135deg, #6C63FF, #00D4AA)
--border-subtle:   rgba(255,255,255,0.08)
```

**Rationale:** Dark theme transmite tecnologia/inovacao. Cada passo tem uma cor de acento propria para criar identidade visual distinta mas coesa. Gradiente nos elementos hero para impacto.

---

## Tipografia

```
--font-heading:    'Inter', system-ui, sans-serif
--font-body:       'Inter', system-ui, sans-serif

Heading 1 (Hero):     clamp(2.5rem, 6vw, 4.5rem)  / 700 / -0.02em
Heading 2 (Passos):   clamp(2rem, 4vw, 3rem)       / 700 / -0.01em
Heading 3 (Subtit):   clamp(1.25rem, 2.5vw, 1.5rem)/ 600
Body:                  clamp(1rem, 1.8vw, 1.125rem) / 400 / 1.7 line-height
Small/Caption:         0.875rem                      / 400 / 1.5 line-height
Step Number:           clamp(4rem, 10vw, 8rem)       / 800 / opacity 0.1
```

---

## Layout Grid

```
Mobile (375px):     padding inline 24px, single column
Tablet (768px):     padding inline 48px, max-width 720px centered
Desktop (1024px+):  padding inline 64px, max-width 1120px centered
```

---

## Wireframe por Secao

### HERO SECTION (100vh)

```
Mobile (375px)                         Desktop (1024px+)
┌─────────────────────┐                ┌──────────────────────────────────────┐
│                     │                │                                      │
│                     │                │                                      │
│   [badge pequeno]   │                │         [badge pequeno]              │
│   "Palestra 2026"   │                │         "Palestra 2026"              │
│                     │                │                                      │
│   IA para Vendas    │                │      IA para Vendas                  │
│   ───────────────   │                │      ─────────────────────           │
│   Subtitulo com 2   │                │      Subtitulo com 2 linhas max     │
│   linhas max        │                │      explicando os 5 passos         │
│                     │                │                                      │
│   [ Conheca os 5 ]  │                │      [ Conheca os 5 passos ↓ ]      │
│   [    passos ↓   ] │                │                                      │
│                     │                │                                      │
│   scroll indicator   │                │          scroll indicator            │
│        ↓            │                │               ↓                      │
└─────────────────────┘                └──────────────────────────────────────┘
```

**Specs:**
- Fundo: `--bg-primary` com sutil pattern ou gradient overlay
- Titulo: `--text-primary`, gradient text opcional
- Badge: pill shape, border `--accent-gradient`, font small
- CTA: botao pill, background gradient, hover glow effect
- Scroll indicator: chevron animado bouncing sutil
- Centrado verticalmente com flexbox

---

### STICKY NAV (aparece apos hero)

```
Mobile (375px)
┌─────────────────────────────────┐
│  01  02  03  04  05             │
│  ●   ○   ○   ○   ○             │
└─────────────────────────────────┘

Desktop (1024px+)
┌──────────────────────────────────────────────────────┐
│  01 Planejamento  02 Captacao  03 Conversao  04 Vendas  05 Pos-Venda │
│  ────────         ─────────   ──────────    ───────   ──────────     │
└──────────────────────────────────────────────────────┘
```

**Specs:**
- Fundo: `--bg-primary` com blur backdrop (glassmorphism sutil)
- Mobile: apenas numeros + dot indicator do ativo
- Desktop: numeros + nomes abreviados
- Ativo: cor de acento do passo + underline ou dot preenchido
- Transicao suave ao mudar de passo
- Height: 48px mobile, 56px desktop
- `position: sticky; top: 0; z-index: 100`
- Aparece com fade-in quando hero sai da viewport

---

### STEP SECTION (padrao para todos os 5 passos)

```
Mobile (375px)
┌─────────────────────────────┐
│                             │
│         01                  │   ← numero gigante, opacity 0.08
│                             │
│   PLANEJAMENTO              │   ← titulo do passo em accent color
│                             │
│   "Quem eu quero            │   ← pergunta-ancora (heading 3)
│    atingir?"                │
│                             │
│   ┌───────────────────────┐ │
│   │ ◉ Definicao de ICP    │ │   ← topico 1
│   │   com IA              │ │
│   └───────────────────────┘ │
│   ┌───────────────────────┐ │
│   │ ◉ Qualificacao        │ │   ← topico 2
│   │   automatica de leads │ │
│   └───────────────────────┘ │
│   ┌───────────────────────┐ │
│   │ ◉ Analise de mercado  │ │   ← topico 3
│   │   e concorrencia      │ │
│   └───────────────────────┘ │
│                             │
│   ┌─────────────────────┐   │
│   │ ✦ RESULTADO:        │   │   ← card destaque
│   │ "Voce para de       │   │
│   │  atirar no escuro"  │   │
│   └─────────────────────┘   │
│                             │
│   📊 60% do tempo com       │   ← insight/dado
│   leads que nunca compram   │
│                             │
└─────────────────────────────┘


Desktop (1024px+)
┌──────────────────────────────────────────────────────┐
│                                                      │
│   01                                                 │
│                    PLANEJAMENTO                       │
│   "Quem eu quero atingir?"                           │
│                                                      │
│   ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ │
│   │ ◉ Definicao  │ │ ◉ Qualific.  │ │ ◉ Analise de │ │
│   │   de ICP     │ │   automatica │ │   mercado e  │ │
│   │   com IA     │ │   de leads   │ │   concorr.   │ │
│   └──────────────┘ └──────────────┘ └──────────────┘ │
│                                                      │
│   ┌────────────────────────────────────────────────┐ │
│   │ ✦ "Voce para de atirar no escuro e comeca a    │ │
│   │    mirar no alvo certo"                        │ │
│   └────────────────────────────────────────────────┘ │
│                                                      │
│   📊 "A maioria gasta 60% do tempo com leads errados"│
│                                                      │
└──────────────────────────────────────────────────────┘
```

**Specs por elemento:**

| Elemento | Mobile | Desktop | Style |
|----------|--------|---------|-------|
| Numero grande | `4rem`, opacity 0.08, absolute | `8rem`, opacity 0.05 | `--accent-N` color, font-weight 800 |
| Titulo passo | `1.5rem`, bold, `--accent-N` | `2rem` | uppercase, letter-spacing 0.1em |
| Pergunta-ancora | `1.25rem`, italic, `--text-primary` | `1.5rem` | aspas decorativas opcionais |
| Topicos | cards empilhados, gap 12px | 3 colunas, gap 24px | bg `--bg-card`, border-left 3px `--accent-N`, padding 16px, border-radius 12px |
| Resultado tangivel | card destaque, bg gradient sutil | full-width card | border `--accent-N`, padding 24px, font-size 1.1rem, font-weight 600 |
| Insight/dado | texto + emoji, `--text-secondary` | mesmo | font-size 0.875rem, margin-top 16px |

**Spacing:**
- Secao padding: `80px 24px` mobile, `120px 64px` desktop
- Gap entre elementos internos: `32px` mobile, `48px` desktop
- Separacao entre secoes: `--bg-section` alternando com `--bg-primary` para ritmo visual

**Animacoes de entrada (por secao):**
1. Numero grande: fade-in (0ms delay)
2. Titulo: slide-up + fade-in (100ms delay)
3. Pergunta: slide-up + fade-in (200ms delay)
4. Topicos: stagger slide-up, 100ms entre cada (300ms start)
5. Resultado: slide-up + fade-in (600ms delay)
6. Insight: fade-in (800ms delay)

---

### COR DE ACENTO POR PASSO

| Passo | Nome | Cor | Hex |
|-------|------|-----|-----|
| 01 | Planejamento | Roxo | `#6C63FF` |
| 02 | Captacao | Verde-agua | `#00D4AA` |
| 03 | Conversao | Coral | `#FF6B6B` |
| 04 | Vendas | Amarelo | `#FFD93D` |
| 05 | Pos-Venda | Teal | `#4ECDC4` |

---

### TIMELINE RECAP SECTION

```
Mobile (375px) — vertical
┌─────────────────────────┐
│                         │
│   OS 5 PASSOS           │
│                         │
│   ● 01 Planejamento     │
│   │                     │
│   ● 02 Captacao         │
│   │                     │
│   ● 03 Conversao        │
│   │                     │
│   ● 04 Vendas           │
│   │                     │
│   ● 05 Pos-Venda        │
│                         │
└─────────────────────────┘

Desktop (1024px+) — horizontal
┌──────────────────────────────────────────────────────┐
│                                                      │
│                    OS 5 PASSOS                        │
│                                                      │
│   ●──────────●──────────●──────────●──────────●      │
│   Plan.      Capt.      Conv.      Vendas    Pos.    │
│                                                      │
└──────────────────────────────────────────────────────┘
```

**Specs:**
- Dots: 16px, cor do acento de cada passo
- Linha conectora: 2px, `--border-subtle`
- Labels: font small, `--text-secondary`
- Animacao: dots aparecem sequencialmente (stagger 200ms), linha "desenha" entre eles
- Fundo: `--bg-primary`

---

### CTA FINAL SECTION

```
Mobile (375px)
┌─────────────────────────┐
│                         │
│   Pronto para vender    │
│   mais com IA?          │
│                         │
│   Receba o material     │
│   completo dos 5 passos │
│                         │
│   ┌───────────────────┐ │
│   │  Fale comigo no   │ │
│   │  WhatsApp →       │ │
│   └───────────────────┘ │
│                         │
│   ─── ou ───            │
│                         │
│   ┌───────────────────┐ │
│   │ seu@email.com     │ │
│   │ [ Quero receber ] │ │
│   └───────────────────┘ │
│                         │
│   ┌───────────────────┐ │
│   │ 👤 [Foto]         │ │
│   │ Nome Palestrante  │ │
│   │ Descricao breve   │ │
│   │ 📱 🔗 📸          │ │
│   └───────────────────┘ │
│                         │
└─────────────────────────┘
```

**Specs:**
- Headline: heading 2, `--text-primary`
- Subtitulo: `--text-secondary`
- Botao WhatsApp: verde (#25D366), full-width mobile, icone WhatsApp
- Formulario: input com borda `--border-subtle`, botao com `--accent-gradient`
- Card palestrante: `--bg-card`, border-radius 16px, foto circular 80px
- Redes sociais: icones 24px, gap 16px

---

### FOOTER

```
┌──────────────────────────────────────┐
│   © 2026 · Feito com IA ❤           │
└──────────────────────────────────────┘
```

**Specs:**
- Fundo: `--bg-primary`
- Texto: `--text-secondary`, font small
- Padding: `24px`
- Centrado

---

## Interaction Specs

### Scroll Behavior
- `scroll-behavior: smooth` no html
- `scroll-snap-type: y proximity` opcional (testar em mobile)
- `scroll-padding-top: 56px` (compensar sticky nav)

### Sticky Nav Trigger
- Nav aparece quando hero sai da viewport (IntersectionObserver no hero)
- Transicao: `transform: translateY(-100%)` → `translateY(0)` com `transition: 0.3s ease`

### Active Step Detection
- IntersectionObserver com `threshold: 0.3` em cada step section
- Quando secao entra em 30% na viewport → atualiza nav highlight

### Reduced Motion
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Checklist de Acessibilidade

- [ ] Contraste 4.5:1 em todo texto sobre fundo
- [ ] Contraste 3:1 em elementos graficos (icones, bordas)
- [ ] Focus visible em todos os links e botoes
- [ ] Tab order logico (hero → nav → secoes → CTA → footer)
- [ ] Alt text descritivo em imagens/icones decorativos (aria-hidden)
- [ ] Landmark roles (header, nav, main, footer)
- [ ] Skip-to-content link (hidden, visivel no focus)
- [ ] Labels em campos de formulario
- [ ] Botao CTA com texto descritivo (nao apenas "Clique aqui")

---

## Handoff para @dev

Este layout esta pronto para implementacao direta. O @dev deve:

1. Comecar pelo HTML semantico (Story 1.1)
2. Aplicar CSS com as custom properties definidas aqui
3. Conteudo real do `docs/brief.md` (Story 1.2)
4. Animacoes como progressive enhancement (Story 1.5)
5. Testar mobile-first em 375px antes de expandir

**Arquivos de referencia:**
- `docs/brief.md` — conteudo dos 5 passos
- `docs/prd.md` — requisitos funcionais e nao-funcionais
- `docs/ux-layout.md` — este documento (layout e specs)

---

> UX Designer — Design for the user, not for the screen.
