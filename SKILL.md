---
name: resume-visual
description: >
  Build a stunning, visually designed HTML resume from raw user materials — and export it as a
  print-perfect PDF. Use this skill whenever a user wants to create, redesign, or visually upgrade a
  resume/CV, especially when they mention: "make my resume look good", "design a resume", "I want a
  beautiful resume", "upgrade my CV", "turn my resume into HTML", or "build a resume PDF". Also
  triggers when the user provides a resume file/text and asks for any kind of visual improvement or
  formatting. The skill runs a structured conversation to collect all necessary materials before
  generating output — never starts coding without first gathering inputs. Supports custom art
  direction (color scheme, style references, photo), multiple output formats (HTML + PDF via
  FireShot or wkhtmltopdf), and Chinese/English bilingual content.
---

# Resume Visual Skill

A conversation-driven workflow that transforms raw resume materials into a **stunning, high-end
HTML resume** — designed to be exported as PDF via FireShot (best quality) or wkhtmltopdf.

Modeled after a real production session that produced a 2-page AI Agent engineer resume with:
- Deep-blue gradient hero page (Page 1) + clean evidence page (Page 2)
- Live avatar photo embedded as base64
- Pill-style skill badges, card-style project sections, stat counters
- Strict 2-page layout, right-side blank trimmed

---

## Phase 0 — Read Before Doing Anything

Before writing a single line of HTML:

1. Read `references/design-system.md` for the full CSS token set and layout rules
2. Read `references/conversation-flow.md` for the exact intake dialogue to run with the user
3. Read `references/html-template.md` for the base HTML structure
4. Check `assets/` for any bundled example images or logo files

---

## Phase 1 — Conversation Intake (REQUIRED — never skip)

Run the intake dialogue defined in `references/conversation-flow.md`.

**Do not start generating HTML until you have collected:**
- [ ] Resume content (PDF upload, text paste, or URL)
- [ ] Target role / job title
- [ ] Key links (GitHub, personal site, portfolio)
- [ ] Contact info (location, phone, email, salary expectation)
- [ ] At least one photo (avatar for hero section)
- [ ] Art direction (style preference OR reference image — see below)
- [ ] Language preference (Chinese / English / bilingual)

**Art direction options** (present these to user):
- A) Choose a preset style → see `references/design-system.md#presets`
- B) Upload a reference image (screenshot, Canva template, another resume)
- C) Describe in words ("dark sci-fi", "minimal luxury", "warm editorial")
- D) "Surprise me" → use the Dark Tech Blue preset (proven effective)

If the user is in a hurry, accept partial info and make smart defaults.
Always confirm collected info before proceeding to Phase 2.

---

## Phase 2 — Content Extraction & Structuring

After intake, extract and organize all content into this canonical structure:

```
PERSON
  name_zh, name_en, age
  title_line (job title string for hero)
  location, phone, email, salary, work_mode

LINKS
  github, website, portfolio, other[]

SUMMARY (3–5 sentences, punchy)

SKILLS
  agent_tools[], languages[], deployment[], mobile[], desktop[]

EXPERIENCE[]
  company, role, date_range
  highlights[] (quantified bullets)

PROJECTS[]
  id, name, org, date_range, subtitle
  bullets[] (STAR format: background, approach, result)

EDUCATION[]
  school, degree, field, years

STATS[] (3 hero numbers, e.g. "14年 / 全栈经验")
```

Pull data from all provided sources: PDF text, website scrape, GitHub repos.
For GitHub: extract repo names, stars, tech stack, recent activity.
Synthesize — don't just copy-paste. Write punchy, recruiter-optimized bullets.

---

## Phase 3 — Design Execution

Read `references/design-system.md` for full CSS variables, color palettes, and layout specs.

### ⚠️ Page Width Rule — No Right Blank

**Always set `.page { width: 170mm }`, NOT `210mm` (full A4).**

The 2-column layout (72mm sidebar + flex main) only fills ~160–172mm of horizontal space.
Using 210mm leaves a 40–50mm white blank on the right — never acceptable in final output.

```css
/* CRITICAL: lock html AND body to page width — prevents right-side blank */
html {
  width: 170mm;
  max-width: 170mm;   /* required: 'width' alone is not enforced on root element */
  overflow-x: hidden;
  margin: 0; padding: 0;
}
body {
  width: 170mm;
  max-width: 170mm;
  overflow-x: hidden;
  margin: 0; padding: 0;
}

.page {
  width: 170mm;   /* NOT 210mm */
  /* NO min-height — let content drive height, zero bottom blank */
  position: relative;
  overflow: hidden;
  page-break-after: always;
}
```

**Rules:**
- `html`, `body`, and `.page` must all have **both `width: 170mm` AND `max-width: 170mm`**. Setting only `width` on `html` is not reliably enforced by browsers — `max-width` is required to cap it.
- Add `overflow-x: hidden` on both `html` and `body` to prevent any child element from expanding the scroll area beyond 170mm.
- **Never set `min-height`** on `.page`. A fixed min-height creates bottom blank when content is shorter. Height must be driven by content only.

If trimming a PDF after export, use the pypdf step in Phase 4.5.

**Page 1 — Hero / Ad Page:**
- Dark gradient background (configurable via preset)
- Large name + title in hero zone with circular avatar photo
- Badge strip with tech keywords
- 2-column layout: left sidebar (contact, stats, skills, photo) + right main (summary, experience)
- Footer bar with page indicator

**Page 2 — Evidence Page:**
- Light background for readability
- Top brand bar (matches Page 1 color)
- 2-column: main (project cards with color-coded left border) + sidebar (earlier exp, education, links)
- Each project card = white card, colored left accent, structured bullets

**Images:**
- Avatar and any photos must be base64-encoded and inlined into HTML (no external refs)
- Use PIL/Pillow to resize before encoding: avatar max 300×400px, sidebar photos max 280×380px
- Compress to JPEG quality 80–85

**Export note for user:**
> The recommended export method is **FireShot** (Chrome extension → "Capture entire page" → PDF).
> This preserves all gradients, shadows, and colors perfectly.
> Alternatively, wkhtmltopdf works but may lose some CSS features.

---

## Phase 4 — Output Delivery

> **Before delivery, always run Phase 4.5 — blank trim check (see below).**

Deliver in this order:

1. **Markdown preview** — show page 1 / page 2 content outline for user confirmation
2. **HTML file** — single self-contained file, all assets base64-inlined
   - Save to `/mnt/user-data/outputs/<name>_Resume_Visual_<year>.html`
3. **PDF** (optional, if user requests or if wkhtmltopdf is available):
   - Run wkhtmltopdf with `--margin-top 0 --margin-bottom 0 --margin-left 0 --margin-right 0`
   - Use pypdf to crop right-side blank and standardize page height
   - Save to `/mnt/user-data/outputs/<name>_Resume_Visual_<year>.pdf`
4. **FireShot instructions** — always include at end:

```
📤 最佳导出方式（FireShot）：
1. 在 Chrome 中打开 HTML 文件
2. 安装 FireShot 扩展（免费）
3. 点击 FireShot → "Capture Entire Page"
4. 选择 "Save as PDF"
→ 这是保留所有视觉效果的最佳方式
```

---

## Phase 4.5 — Blank Trim (Mandatory Finishing Step)

After generating the HTML, always perform the following checks before delivery:

### Step A — HTML page width check

Verify `.page { width }` is set to **170mm** (not 210mm).
If not, fix it before outputting the file.

### Step B — Bottom blank check

After the user views the HTML in browser, measure if Page 1 or Page 2 has excessive
bottom white space (more than ~8mm). If yes, either:
- Reduce `min-height` on `.page` in the HTML, or
- Use the pypdf crop after wkhtmltopdf export (see below)

### Step C — pypdf crop for PDF (if PDF is generated)

```python
from pypdf import PdfReader, PdfWriter
from pypdf.generic import RectangleObject

mm = lambda x: x * 2.8346          # mm → PDF points

reader = PdfReader("output_raw.pdf")
writer = PdfWriter()

TARGET_W = mm(170)   # match HTML .page width
TARGET_H = mm(234)   # measure content height; adjust per resume

for page in reader.pages:
    orig_h = float(page.mediabox.height)
    # keep bottom of content; crop from top to TARGET_H
    new_bottom = orig_h - TARGET_H
    rect = RectangleObject([0, new_bottom, TARGET_W, orig_h])
    page.mediabox = rect
    page.cropbox  = rect
    writer.add_page(page)

with open("output_trimmed.pdf", "wb") as f:
    writer.write(f)
```

**Rule: both pages must have identical dimensions.**
Measure Page 1 height first, then apply the same rect to Page 2.

---

## Phase 5 — Iteration

After delivery, offer these refinement options:
- Swap photos
- Adjust color scheme / style preset
- Add/remove/reorder sections
- Resize page (crop right blank, trim bottom)
- Language toggle (zh ↔ en)
- Update specific content

For photo swaps: re-encode the new image as base64 and do a targeted string replacement.
For color changes: only update CSS variable values, don't re-render the whole page.

---

## Key Technical Notes

### Image encoding
```python
from PIL import Image
import base64, io

def img_to_b64(path, max_size=(300, 400), quality=82):
    img = Image.open(path)
    img.thumbnail(max_size, Image.LANCZOS)
    buf = io.BytesIO()
    img.save(buf, format='JPEG', quality=quality)
    return base64.b64encode(buf.getvalue()).decode()
```

### PDF blank trimming (right side)
```python
from pypdf import PdfReader, PdfWriter
from pypdf.generic import RectangleObject

# Measure content width at 150dpi with PIL, then:
mm_to_pt = 2.8346
page.mediabox = RectangleObject([0, new_bottom, target_w_pt, orig_h])
page.cropbox  = RectangleObject([0, new_bottom, target_w_pt, orig_h])
```

### wkhtmltopdf command
```bash
wkhtmltopdf \
  --page-size A4 \
  --margin-top 0 --margin-bottom 0 --margin-left 0 --margin-right 0 \
  --enable-local-file-access --zoom 1.0 --dpi 150 --encoding utf-8 \
  input.html output.pdf
```

### Font stack (CJK-safe)
```css
font-family: 'Helvetica Neue', 'PingFang SC', 'Noto Sans CJK SC',
             'Microsoft YaHei', sans-serif;
```

---

## Reference Files

| File | When to read |
|------|-------------|
| `references/conversation-flow.md` | Phase 1 — always |
| `references/design-system.md` | Phase 3 — always |
| `references/html-template.md` | Phase 3 — base structure |
| `examples/leo-resume-case.md` | Anytime — real production example |
