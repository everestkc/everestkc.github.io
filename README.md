# Your Personal Website

A clean, minimal personal website built with [Astro](https://astro.build).

**Design:** Black, white, and grey only. No color — just typography and space.
**Fonts:** Cormorant Garamond (headings) + Outfit (body)
**Theme:** Light / Dark mode with system preference detection

---

## Pages

| Page | File | Description |
|------|------|-------------|
| Home | `src/pages/index.astro` | Hero + About section |
| Blog | `src/pages/blog/index.astro` | Post listing |
| Post | `src/pages/blog/[slug].astro` | Individual post |
| Talks | `src/pages/talks.astro` | Talks & presentations |
| Contact | `src/pages/contact.astro` | Contact form + links |

---

## Getting started

```bash
npm install
npm run dev
# Open http://localhost:4321
```

## Customising

### 1. Your name
Search for `Your Name` across all files and replace it with yours. Key spots:
- `src/layouts/Layout.astro` — nav logo and footer
- `src/pages/index.astro` — hero heading
- All `<title>` tags (via the layout's `title` prop)

### 2. Your photo
In `src/pages/index.astro`, replace the `<div class="photo-placeholder">` block with:
```html
<img src="/your-photo.jpg" alt="Your Name" />
```
Place the image file in `public/`.

### 3. About section
Edit the text in `src/pages/index.astro` — the bio paragraph, skills grid values, and eyebrow label.

### 4. Blog posts
Add `.md` or `.mdx` files to `src/content/blog/`. Each needs this frontmatter:
```yaml
---
title: "Your Post Title"
description: "One-sentence description shown in the listing."
pubDate: 2024-12-01
tags: ["tag1", "tag2"]
draft: false   # set true to hide from listing
---
```
Then write your post in Markdown below the `---`.

### 5. Talks
Edit the `talks` array in `src/pages/talks.astro`. Each entry:
```js
{
  title: "Talk Title",
  event: "Conference Name",
  location: "City",
  date: "Month Year",
  type: "Keynote" | "Talk" | "Workshop" | "Lightning Talk" | "Panel",
  slides: "https://...",   // leave "" if none
  video: "https://...",    // leave "" if none
  description: "Short description.",
}
```

### 6. Contact links
In `src/pages/contact.astro`, update the `href` values on each `.contact-channel` and the form `action` URL.

### 7. Contact form (Formspree)
1. Sign up at [formspree.io](https://formspree.io) (free tier: 50 submissions/month)
2. Create a new form and copy your Form ID
3. Replace `YOUR_FORM_ID` in `src/pages/contact.astro`

### 8. Social links in footer
Edit `src/layouts/Layout.astro` — the `.footer-links` section at the bottom.

---

## Adding new blog posts

```bash
# Create a new post
touch src/content/blog/my-new-post.md
```

Paste this starter:
```markdown
---
title: "Post Title"
description: "What this post is about."
pubDate: 2024-12-15
tags: ["tag"]
---

Your content here.
```

---

## Deploying

### Vercel (recommended — zero config)
```bash
npm i -g vercel
vercel
```

### Netlify
```bash
npm run build
# Drag the dist/ folder to app.netlify.com/drop
```

### GitHub Pages
Add to `astro.config.mjs`:
```js
export default defineConfig({
  site: 'https://yourusername.github.io',
  base: '/repo-name',  // if not deploying to root
  integrations: [mdx()],
});
```

---

## Project structure

```
src/
├── layouts/
│   └── Layout.astro          # Nav, footer, theme toggle, <head>
├── pages/
│   ├── index.astro            # Home (hero + about)
│   ├── talks.astro            # Talks & presentations
│   ├── contact.astro          # Contact form
│   └── blog/
│       ├── index.astro        # Blog listing
│       └── [slug].astro       # Individual post page
├── content/
│   ├── config.ts              # Blog collection schema
│   └── blog/                  # Your .md post files
│       ├── welcome.md
│       ├── things-i-learned.md
│       ├── designing-for-clarity.md
│       └── tools-i-use.md
└── styles/
    └── global.css             # All styles + CSS custom properties
public/
└── (your images go here)
```
