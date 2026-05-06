# HTML Template — Resume Visual Skill

This is the annotated base HTML structure. Copy and adapt per user's content.
All `{{PLACEHOLDER}}` values must be replaced. Base64 image data goes in `{{AVATAR_B64}}` etc.

For full CSS variable definitions, see `design-system.md`.

---

## Shell Structure

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<style>
/* ── RESET ── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Helvetica Neue', 'PingFang SC', 'Noto Sans CJK SC',
               'Microsoft YaHei', sans-serif;
  font-size: 9.2pt;
  line-height: 1.45;
  color: #1a1a2e;
  background: #fff;
  -webkit-print-color-adjust: exact;
  print-color-adjust: exact;
}

/* ── PAGE ── */
.page {
  width: 210mm;
  min-height: 297mm;
  position: relative;
  overflow: hidden;
  page-break-after: always;
}

/* ── PASTE FULL CSS FROM design-system.md HERE ── */
/* (all component styles: .hero, .sidebar, .badge-item, .proj-card, etc.) */

</style>
</head>
<body>

<!-- ══════════════ PAGE 1 ══════════════ -->
<div class="page page1">

  <!-- Accent bar -->
  <div class="accent-bar"></div>

  <!-- Hero -->
  <div class="hero">
    <div class="avatar-wrap">
      <img src="data:image/jpeg;base64,{{AVATAR_B64}}" alt="{{NAME_EN}}">
    </div>
    <div class="hero-text">
      <div class="hero-name">{{NAME_ZH}}</div>
      <div class="hero-name-en">{{NAME_EN}} | {{TITLE_SHORT}}</div>
      <div class="hero-title">{{TITLE_FULL}}</div>
      <div class="hero-meta">
        <span><span class="dot"></span> {{LOCATION}}</span>
        <span><span class="dot"></span> {{PHONE}}</span>
        <span><span class="dot"></span> {{EMAIL}}</span>
        <span><span class="dot"></span> 期望薪资：<strong>{{SALARY}}</strong></span>
        <span><span class="dot"></span> {{WORK_MODE}}</span>
      </div>
    </div>
  </div>

  <!-- Badge strip -->
  <div class="badges-row">
    <!-- Repeat for each keyword -->
    <span class="badge-item">{{KEYWORD}}</span>
  </div>

  <!-- Body: sidebar + main -->
  <div class="p1-body">

    <!-- Left sidebar -->
    <div class="sidebar">

      <!-- Contact -->
      <div>
        <div class="sec-title">联系方式</div>
        <div class="contact-item">
          <div class="contact-icon">GH</div>
          <a class="contact-link" href="{{GITHUB_URL}}">{{GITHUB_DISPLAY}}</a>
        </div>
        <!-- Add more contact items -->
      </div>

      <!-- Stats (3 numbers) -->
      <div class="stats-row">
        <div class="stat-item">
          <span class="stat-num">{{STAT1_NUM}}</span>
          <span class="stat-label">{{STAT1_LABEL}}</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">{{STAT2_NUM}}</span>
          <span class="stat-label">{{STAT2_LABEL}}</span>
        </div>
        <div class="stat-item">
          <span class="stat-num">{{STAT3_NUM}}</span>
          <span class="stat-label">{{STAT3_LABEL}}</span>
        </div>
      </div>

      <!-- Skills -->
      <div>
        <div class="sec-title">核心技术</div>
        <!-- Repeat skill-block for each category -->
        <div class="skill-block">
          <div class="skill-label">▸ {{SKILL_CATEGORY}}</div>
          <div class="skill-tags">
            <span class="tag hot">{{HOT_SKILL}}</span>
            <span class="tag">{{SKILL}}</span>
          </div>
        </div>
      </div>

      <!-- Sidebar photo (optional) -->
      <div>
        <div class="sec-title">{{PHOTO_LABEL}}</div>
        <div class="photo-frame">
          <img src="data:image/jpeg;base64,{{PHOTO_B64}}" alt="photo">
        </div>
        <div class="photo-caption">{{PHOTO_CAPTION}}</div>
      </div>

    </div><!-- /sidebar -->

    <!-- Main column -->
    <div class="main-col">

      <!-- Summary -->
      <div>
        <div class="sec-title">Professional Summary</div>
        <div class="summary-text">
          {{SUMMARY_HTML}}
        </div>
      </div>

      <!-- Experience -->
      <div>
        <div class="sec-title">Experience</div>

        <!-- Repeat for each job -->
        <div class="job-entry">
          <div class="job-header">
            <div class="job-company">{{COMPANY}}</div>
            <div class="job-date">{{DATE_RANGE}}</div>
          </div>
          <div class="job-role">{{ROLE}}</div>
          <ul class="job-bullets">
            <li><strong>{{HIGHLIGHT}}</strong> rest of bullet</li>
          </ul>
        </div>

      </div>

    </div><!-- /main-col -->
  </div><!-- /p1-body -->

  <!-- Footer -->
  <div class="p1-footer">
    <div class="p1-footer-left">{{COMPANY_TAGLINE}}</div>
    <div class="p1-footer-right">→ 第 2 页：项目详情与证据</div>
  </div>

</div><!-- /page1 -->


<!-- ══════════════ PAGE 2 ══════════════ -->
<div class="page page2">

  <!-- Top bar -->
  <div class="p2-topbar">
    <div class="p2-topbar-name">{{NAME_ZH}} {{NAME_EN}} | {{TITLE_SHORT}}</div>
    <div class="p2-topbar-links">{{GITHUB_DISPLAY}} · {{WEBSITE_DISPLAY}}</div>
  </div>

  <!-- Body -->
  <div class="p2-body">

    <!-- Main: projects -->
    <div class="p2-main">
      <div class="sec2-title">Selected Projects &amp; Detailed Evidence</div>

      <!-- Repeat for each project (vary border-left-color) -->
      <div class="proj-card" style="border-left-color: #0A66C2">
        <div class="proj-header">
          <div class="proj-name">[P{{N}}] {{PROJECT_NAME}}</div>
          <span class="proj-tag">{{ORG}} · {{DATE}}</span>
        </div>
        <div class="proj-sub">{{PROJECT_SUBTITLE}}</div>
        <ul class="proj-bullets">
          <li><strong>背景：</strong>{{BACKGROUND}}</li>
          <li><strong>方案：</strong>{{APPROACH}}</li>
          <li><strong>成果：</strong>{{RESULT}}</li>
        </ul>
      </div>

    </div><!-- /p2-main -->

    <!-- Sidebar -->
    <div class="p2-sidebar">

      <!-- Earlier experience -->
      <div>
        <div class="sec2-title">Earlier Experience</div>
        <div class="prev-job">
          <div class="prev-job-name">{{COMPANY}}</div>
          <div class="prev-job-role">{{ROLE}}</div>
          <div class="prev-job-date">{{DATE_RANGE}}</div>
          <div class="prev-job-note">{{ONE_LINE_NOTE}}</div>
        </div>
      </div>

      <!-- Education -->
      <div>
        <div class="sec2-title">Education</div>
        <div class="edu-block" style="margin-bottom: 8px">
          <div class="edu-school">{{SCHOOL}}</div>
          <div class="edu-degree">{{DEGREE}} · {{LEVEL}}</div>
          <div class="edu-year">{{YEARS}}</div>
        </div>
      </div>

      <!-- Links box -->
      <div class="links-box">
        <div class="links-box-title">Links &amp; Open Source</div>
        <div class="link-row">
          <div class="link-icon">GH</div>
          <div class="link-text">{{GITHUB}}</div>
        </div>
        <!-- Add more links -->
        <div class="kw-row">
          <span class="kw-chip">{{KEYWORD}}</span>
        </div>
      </div>

    </div><!-- /p2-sidebar -->
  </div><!-- /p2-body -->

  <div class="page-num">Page 2 / 2</div>
</div><!-- /page2 -->

</body>
</html>
```

---

## Notes on Customization

- **No photo available**: Replace `<div class="avatar-wrap"><img ...></div>` with:
  ```html
  <div class="avatar-wrap avatar-initials">{{INITIALS}}</div>
  ```
  Add CSS: `.avatar-initials { display:flex; align-items:center; justify-content:center;
  font-size:28pt; font-weight:800; color: var(--primary-light); }`

- **English-only**: Change `lang="zh-CN"` to `lang="en"`, translate all section labels,
  remove CJK fonts from font-family stack priority.

- **Single page**: Remove `<!-- PAGE 2 -->` block entirely, remove `page-break-after: always`.

- **More than 6 projects**: Reduce padding on `.proj-card` to `8px 10px`, font-size to `7.5pt`.
