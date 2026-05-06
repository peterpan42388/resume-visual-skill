# Conversation Flow — Resume Visual Skill

This file defines the exact intake dialogue to run with the user in Phase 1.
Run it naturally — like a friendly designer onboarding a client, not a form.

---

## Opening Message

When the skill triggers, open with:

```
我来帮你打造一份高端视觉简历！在开始设计之前，我需要了解你的情况。

我们会一步一步来——你不需要一次性提供所有内容。
```

---

## Step 1 — Content Collection

Ask in one message (don't split into multiple questions):

```
首先，请提供你的简历内容，任选一种方式：

📄 **方式A** — 直接上传简历文件（PDF / Word / 图片）
📝 **方式B** — 粘贴文字内容（任何格式都行）
🔗 **方式C** — 提供链接（个人网站 / LinkedIn / GitHub）

如果有多种，全部提供更好！
```

Wait for response. Accept any combination. If they give a PDF, extract text with pdftotext.
If they give a URL, fetch it. If they paste raw text, parse it directly.

After receiving content, acknowledge and continue to Step 2.

---

## Step 2 — Links & Online Presence

```
收到！接下来请告诉我你的在线主页（有哪个填哪个）：

- GitHub 地址？
- 个人网站 / 作品集？
- 其他想展示的链接？
```

If they already provided links in Step 1, skip or confirm.

---

## Step 3 — Job Target

```
这份简历主要投递什么方向？

例如："AI Agent 工程师"、"全栈开发"、"产品经理"……
期望薪资范围？工作地点偏好（城市 / Remote）？
```

---

## Step 4 — Photos

```
简历里放一张你的照片效果很好，有吗？

📸 请上传：
1. **头像照**（会放在第一页 Hero 区）— 推荐正面照、工作照、咖啡馆工作照都很棒
2. **场景照**（可选，会放在左侧栏）— 比如工作现场、团队照、活动现场

没有也没关系，我会用占位样式处理。
```

---

## Step 5 — Art Direction

Present clearly as a choice:

```
最后，告诉我你想要什么风格 👇

🎨 **A. 选预设主题**（推荐，省心）
   1. 🌌 Dark Tech Blue — 深蓝渐变科技风（已验证效果最佳）
   2. ⬛ Midnight Black — 极致暗黑，银色点缀
   3. 🤍 Clean Minimal — 白底极简，蓝色强调色
   4. 🌿 Warm Editorial — 暖色系，杂志排版感
   5. 🔴 Bold Red — 高对比红黑，冲击力强

🖼️ **B. 上传参考图**
   截图你喜欢的简历模板、Canva 设计、网站截图……我来复刻风格

✍️ **C. 文字描述**
   "我想要科技感强的"、"高端但不花哨"……随便说

🎲 **D. 帮我决定**（我会用 Dark Tech Blue，已经用于实际投递）
```

---

## Step 6 — Language

```
简历语言偏好？

- 🇨🇳 中文为主（技术词汇保留英文）
- 🇺🇸 纯英文
- 双语（中英混排）
```

---

## Step 7 — Confirmation Summary

Before generating, show a summary:

```
好的，我整理一下收到的信息：

**姓名：** [name]
**目标岗位：** [target role]
**风格：** [chosen style]
**语言：** [language]
**照片：** [有 / 无]
**链接：** [list]

---

接下来我会：
1. 提取并优化你的简历内容（recruiter 视角重写）
2. 生成 Markdown 预览给你确认
3. 输出完整 HTML 文件（自包含，可直接用 FireShot 导出 PDF）

开始了！🚀
```

---

## Handling Edge Cases

**User is in a hurry / just wants to start:**
> Accept whatever they have. Make smart defaults. Start generating after Step 1 + 5 minimum.

**User uploads art reference image:**
> Analyze the image: extract dominant colors, layout structure, font style impression.
> Map to CSS variables. Describe your interpretation: "我看到你的参考是 [dark/light], 主色 [color],
> 我会复刻这个风格..."

**User has no photo:**
> Use a styled initial/monogram placeholder instead of an avatar circle:
> ```html
> <div class="avatar-initials">LH</div>
> ```

**User wants English resume:**
> Translate all section labels, adjust font stack (remove CJK fonts from priority).
> Keep the same visual structure.

**User wants more than 2 pages:**
> Gently suggest 2 pages is optimal for most roles. If they insist, extend page 2 naturally.
> Do NOT add a page 3 unless explicitly requested.

**User uploads reference resume image:**
> Extract: color palette, layout columns, section order, typography feel.
> Verbalize your interpretation before building.
