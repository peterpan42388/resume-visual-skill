# Design System — Resume Visual Skill

Full CSS token set, color presets, layout rules, and component specs.

---

## CSS Variables (Base)

```css
:root {
  /* ── Spacing ── */
  --gap-xs: 3px;
  --gap-sm: 6px;
  --gap-md: 12px;
  --gap-lg: 20px;
  --gap-xl: 28px;

  /* ── Border radius ── */
  --radius-sm: 3px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --radius-full: 999px;

  /* ── Typography ── */
  --font-main: 'Helvetica Neue', 'PingFang SC', 'Noto Sans CJK SC',
               'Microsoft YaHei', sans-serif;
  --font-size-base: 9.2pt;
  --font-size-sm:   7.8pt;
  --font-size-xs:   7pt;
  --font-size-h1:   28pt;
  --font-size-h2:   11pt;
  --font-size-sec:  7pt;
  --line-height:    1.45;
}
```

---

## Color Presets

### 1. Dark Tech Blue (Default — proven in production)

```css
:root {
  --p1-bg-start:   #061529;
  --p1-bg-mid:     #0a2540;
  --p1-bg-end:     #112a5e;
  --accent-bar:    linear-gradient(90deg, #0A66C2, #00c6ff, #38bdf8);
  --primary:       #0A66C2;
  --primary-light: #38bdf8;
  --primary-glow:  rgba(56,189,248,0.18);
  --text-hero:     #ffffff;
  --text-main:     #c8d8ec;
  --text-muted:    #9bb8d8;
  --text-dim:      #6a8aaa;
  --tag-bg:        rgba(255,255,255,0.07);
  --tag-border:    rgba(255,255,255,0.12);
  --tag-hot-bg:    rgba(10,102,194,0.3);
  --tag-hot-color: #7ed4fa;
  --sidebar-bg:    rgba(255,255,255,0.03);
  --divider:       rgba(255,255,255,0.06);
  --stat-num:      #38bdf8;
  --p2-bg:         #f7f9fc;
  --p2-topbar:     linear-gradient(90deg, #0a2540, #0A66C2);
  --card-border:   #0A66C2;
  --card-shadow:   rgba(10,38,80,0.07);
  --edu-bg:        linear-gradient(135deg, #e8f0fc, #f0f4ff);
  --links-bg:      linear-gradient(135deg, #0a2540, #0A66C2);
}
```

### 2. Midnight Black

```css
:root {
  --p1-bg-start:   #050505;
  --p1-bg-mid:     #0f0f0f;
  --p1-bg-end:     #1a1a1a;
  --accent-bar:    linear-gradient(90deg, #888, #fff, #888);
  --primary:       #e0e0e0;
  --primary-light: #ffffff;
  --primary-glow:  rgba(255,255,255,0.1);
  --text-hero:     #ffffff;
  --text-main:     #cccccc;
  --text-muted:    #999999;
  --text-dim:      #666666;
  --tag-bg:        rgba(255,255,255,0.05);
  --tag-border:    rgba(255,255,255,0.15);
  --tag-hot-bg:    rgba(255,255,255,0.12);
  --tag-hot-color: #ffffff;
  --stat-num:      #ffffff;
  --p2-bg:         #f5f5f5;
  --p2-topbar:     linear-gradient(90deg, #111, #333);
  --card-border:   #333333;
  --links-bg:      linear-gradient(135deg, #111, #333);
}
```

### 3. Clean Minimal

```css
:root {
  --p1-bg-start:   #ffffff;
  --p1-bg-mid:     #f8faff;
  --p1-bg-end:     #eef2ff;
  --accent-bar:    linear-gradient(90deg, #2563eb, #60a5fa);
  --primary:       #2563eb;
  --primary-light: #60a5fa;
  --text-hero:     #0f172a;
  --text-main:     #334155;
  --text-muted:    #64748b;
  --tag-bg:        #f1f5f9;
  --tag-border:    #cbd5e1;
  --tag-hot-bg:    #dbeafe;
  --tag-hot-color: #1d4ed8;
  --stat-num:      #2563eb;
  --p2-bg:         #ffffff;
  --p2-topbar:     linear-gradient(90deg, #1e40af, #2563eb);
  --card-border:   #2563eb;
}
```

### 4. Warm Editorial

```css
:root {
  --p1-bg-start:   #1c0f05;
  --p1-bg-mid:     #2d1a08;
  --p1-bg-end:     #3d2510;
  --accent-bar:    linear-gradient(90deg, #c2410c, #fb923c, #fbbf24);
  --primary:       #ea580c;
  --primary-light: #fb923c;
  --text-hero:     #fef3c7;
  --text-main:     #fed7aa;
  --text-muted:    #d97706;
  --stat-num:      #fb923c;
  --p2-bg:         #fffbf7;
  --p2-topbar:     linear-gradient(90deg, #7c2d12, #ea580c);
  --card-border:   #ea580c;
}
```

### 5. Bold Red

```css
:root {
  --p1-bg-start:   #1a0000;
  --p1-bg-mid:     #2d0000;
  --p1-bg-end:     #1a0000;
  --accent-bar:    linear-gradient(90deg, #dc2626, #ef4444, #f87171);
  --primary:       #dc2626;
  --primary-light: #f87171;
  --text-hero:     #ffffff;
  --text-main:     #fecaca;
  --text-muted:    #f87171;
  --stat-num:      #f87171;
  --p2-bg:         #fff5f5;
  --p2-topbar:     linear-gradient(90deg, #7f1d1d, #dc2626);
  --card-border:   #dc2626;
}
```

---

## Layout Specs

### Page dimensions
- **Width**: A4 = 210mm, but content typically 160–170mm (right blank trimmed via pypdf)
- **Height**: Fit to content (bottom blank trimmed via pypdf)
- **Both pages**: same width + same height (measured from page 1)

### Page 1 — 2-column layout
```
┌─────────────────────────────────────────────────────┐
│  ACCENT BAR (4px gradient)                          │
├─────────────────────────────────────────────────────┤
│  HERO: [avatar] [name + title + meta]               │
├─────────────────────────────────────────────────────┤
│  BADGE STRIP (tech keywords, pill style)            │
├──────────────────┬──────────────────────────────────┤
│  SIDEBAR (72mm)  │  MAIN COLUMN (flex: 1)           │
│  • Contact       │  • Professional Summary          │
│  • Stats (3)     │  • Experience (4–5 entries)      │
│  • Skills        │                                  │
│  • Photo         │                                  │
├──────────────────┴──────────────────────────────────┤
│  FOOTER BAR                                         │
└─────────────────────────────────────────────────────┘
```

### Page 2 — 2-column layout
```
┌─────────────────────────────────────────────────────┐
│  TOP BAR (dark gradient, name + links)              │
├───────────────────────────────────┬─────────────────┤
│  MAIN (flex: 1)                   │  SIDEBAR (58mm) │
│  Project cards (P1–P6)            │  Earlier exp    │
│                                   │  Education      │
│                                   │  Links box      │
└───────────────────────────────────┴─────────────────┘
```

---

## Component Specs

### Avatar
```css
.avatar-wrap {
  width: 90px; height: 90px;
  border-radius: 50%;
  border: 2.5px solid var(--primary-light);
  overflow: hidden;
  box-shadow: 0 0 0 4px var(--primary-glow), 0 8px 24px rgba(0,0,0,0.4);
}
```

### Badge (pill)
```css
.badge-item {
  background: rgba(56,189,248,0.12);
  border: 1px solid rgba(56,189,248,0.3);
  border-radius: 20px;
  padding: 2px 10px;
  font-size: 7.5pt;
  font-weight: 600;
}
```

### Stats row
- 3 items in a flex row
- Large number (16pt bold, primary-light color)
- Label below (6.5pt, muted)
- Separated by 1px dividers

### Project card (Page 2)
```css
.proj-card {
  background: #ffffff;
  border-radius: 8px;
  padding: 10px 12px;
  margin-bottom: 8px;
  border-left: 3px solid [color-coded per project];
  box-shadow: 0 2px 8px var(--card-shadow);
}
```
Suggested color coding (left border):
- P1: #0A66C2 (blue)
- P2: #00a8cc (cyan)
- P3: #6366f1 (indigo)
- P4: #f59e0b (amber)
- P5: #10b981 (green)
- P6: #8b5cf6 (purple)

### Section title (Page 1)
```css
.sec-title {
  font-size: 7pt;
  font-weight: 800;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--primary-light);
  border-bottom: 1px solid rgba(56,189,248,0.25);
  padding-bottom: 4px;
  margin-bottom: 7px;
}
```

### Section title (Page 2)
```css
.sec2-title {
  font-size: 7pt;
  font-weight: 800;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--primary);
  border-bottom: 2px solid var(--primary);
  /* with ::before blue-cyan gradient bar */
}
```

---

## Art Reference Interpretation

When user provides a reference image, extract and map:

| Observed in image | Map to |
|-------------------|--------|
| Dark/light overall | `--p1-bg-*` scheme |
| Dominant accent color | `--primary` + `--accent-bar` |
| Font weight feel | `font-weight` in hero |
| Card style (flat/shadow/border) | `.proj-card` style |
| Layout (1-col/2-col) | Adjust `.p1-body` flex |
| Photo placement | Sidebar vs. hero |

Always verbalize your interpretation: "我从参考图中提取到：深色背景 #1a1a2e，强调色橙红 #e94560，
卡片用微弱阴影无边框……我会按这个风格来。"

---

## Print Optimization

Always add to `<style>`:
```css
body {
  -webkit-print-color-adjust: exact;
  print-color-adjust: exact;
}
.page {
  page-break-after: always;
}
```

All images MUST be base64-inlined. No `<link>` or external `<script>` tags.
Tailwind CDN is OK for development preview but NOT for final HTML (use inline CSS instead).
