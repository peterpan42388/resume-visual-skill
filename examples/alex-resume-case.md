# Real Case Study — Alex Zhang / 张明远

This documents the actual production session that this skill was built from.
Use as a reference for quality bar, content depth, and design decisions.

---

## User Profile

- **Name**: 张明远 (Alex / Mingyuan Zhang), 35岁
- **Target role**: AI Agent Engineer | Full-Stack Agent Developer | Multi-Agent System Architect
- **Location**: 深圳 / Remote
- **Salary**: 35–65K
- **Experience**: 14年全栈（iOS → AI Agent）

## Materials Provided

1. **PDF resume** (5 pages, Chinese) — extracted with pdftotext
2. **NovaMind about page** — HTML scraped, text extracted via Python HTMLParser
3. **GitHub**: github.com/alex-mingyuan
4. **Websites**: novamind.co, world.novamind.co
5. **Photos**:
   - `avatar_01.JPG` → avatar (coffee shop working photo, very effective)
   - `life_photo.png` → sidebar (teaching/life collage photo)
   - `education_photo.png` → original sidebar (replaced in iteration)

## Art Direction Chosen

**Dark Tech Blue** (preset 1) — user accepted suggestion, no custom reference provided.

## Content Extraction Notes

### From PDF resume — key data points
- 2025.08: Founded NovaMind Ltd (UK registered)
- Human Design algorithm reverse-engineered from NASA JPL ephemeris data
- NeuroClaw desktop installer: 0 CLI, for non-technical users
- EOW (Edge Open World): multi-agent social framework, Cloudflare edge
- 2023–2025: Computer dept head, vocational school — exam avg 380/490, grew from 3→10 classes
- 2020–2022: 中海庭 — solo delivered ¥1M iOS/Android smart port project in one quarter
- 2017–2020: 网幂 — ad SDK boosted revenue 30–50%, re-launched 49 apps in 2 months
- 2015–2017: 亲密圈 — Life360-style app, peak ~1M users
- Started programming 2012, promoted to team lead within months

### From NovaMind website
- Mission: "help everyone deeply understand their own essence"
- Key quote: "I realized we are entering a future of inward exploration"
- EOW is the "shared world framework for people, agents, projects"
- NeuroClaw installer is standard Step 02 for EOW onboarding

### From GitHub search (alex-mingyuan + neuroclaw ecosystem)
- NeuroClaw: personal AI assistant, any OS/platform, "the lobster way 🦞"
- Supports 20+ messaging channels (WhatsApp, Telegram, Slack, Discord, iMessage...)
- Multi-agent routing, voice wake, live canvas, companion apps
- Active development, production-grade

## Stats Chosen

| Number | Label | Source |
|--------|-------|--------|
| 14 | 年全栈经验 | Resume: started 2012 |
| 3 | Agent产品落地 | NeuroClaw installer + EOW + NovaMind platform |
| 20+ | 独立项目经验 | Counted across full resume |

## Project Cards (P1–P6) with Color Coding

| ID | Name | Color | Key Proof Point |
|----|------|-------|-----------------|
| P1 | NeuroClaw 桌面安装器 | #0A66C2 blue | 0-CLI, standard EOW Step 02 |
| P2 | EOW 多智能体框架 | #00a8cc cyan | Live, Agent Motivation Bridge, self-deploy |
| P3 | NovaMind 人格平台 | #6366f1 indigo | NASA JPL algorithm, global rarity |
| P4 | 智慧港口系列 | #f59e0b amber | 5 subprojects, solo, ¥1M in one quarter |
| P5 | 广告聚合 SDK | #10b981 green | 30–50% revenue lift, 49 apps |
| P6+P7 | 蜂行动+亲密圈 | #8b5cf6 purple | Solo full-stack + ~1M users |

## Iteration History

### Round 1 → Round 2 (image swap)
- Changed avatar from `life_photo.png` to `avatar_01.JPG` (better professional look)
- Changed sidebar photo from `education_photo.png` to `life_photo.png` (more personal/warm)
- Changed stat "49款App 2月上架" → "20+ 独立项目经验" (more accurate, more impressive)
- Added Qt/PyQt to desktop tech stack

### Round 2 → Round 3 (page size trim)
- User requested: remove right-side blank, unify height to page 1
- Measurement: content right edge ~161mm, right blank ~49mm
- Trimmed to: 166mm × 234mm (both pages identical)
- Method: pypdf MediaBox + CropBox adjustment

## Export Method

**Best result**: FireShot Chrome extension → "Capture Entire Page" → "Save as PDF"
- Preserves all gradients, shadows, colors
- No white strips or missing backgrounds
- User confirmed this as final method

## File Output

- `张明远_AI-Agent-Engineer_视觉优化版_2026.html` — primary deliverable
- `张明远_AI-Agent-Engineer_视觉优化版_2026.pdf` — trimmed via pypdf

## Lessons Learned

1. **Coffee shop working photo** as avatar is highly effective — authentic, memorable, tech vibe
2. **Base64 all images** — single-file HTML is the right target for FireShot
3. **Dark first page + light second page** is the winning formula for 2-page resumes
4. **Right-side blank** comes from content not filling full A4 width — always trim
5. **stat-num** with large numbers (14, 3, 20+) creates instant credibility in the hero
6. **Color-coded project cards** makes Page 2 scannable — each project has a distinct identity
7. **NASA JPL algorithm** framing for the Human Design work is dramatically more impressive
   than "personality analysis platform" — always find the most technical framing
