# Personal Blog - Hugo + PaperMod

A static blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Features

| Feature | Description |
|---------|-------------|
| Blog publishing | Markdown + Front Matter, draft/publish, cover images |
| Comments | Giscus (GitHub Discussions) |
| Home page | Latest posts, pagination, excerpts |
| Categories/Tags | Taxonomy archives |
| Profile | About page |
| Search | Fuse.js (built into PaperMod) |
| Dark mode | Theme toggle |
| RSS | Auto-generated at `/index.xml` |
| CMS | Netlify CMS (optional) |

## Quick start

### 1. Install Hugo

```bash
brew install hugo
# Or: https://gohugo.io/installation/
```

Requires Hugo >= 0.146.0.

### 2. Local preview

```bash
# Include drafts
hugo server -D

# Published only
hugo server
```

Visit http://localhost:1313

### 3. Build

```bash
hugo
# Output in public/
```

## Configuration

### Basic

Edit `config.yaml`:

- `baseURL`: Site URL
- `title`: Site title
- `params.author`: Author name
- `params.socialIcons`: Social links

### Giscus comments

1. Create a **public repo** on GitHub and enable **Discussions**
2. Install [giscus](https://github.com/apps/giscus) and authorize the repo
3. Open [giscus.app](https://giscus.app) and generate config
4. Add `repo`, `repoId`, `categoryId` to `params.giscus` in `config.yaml`

### Netlify CMS (optional)

1. Deploy to Netlify
2. Enable Identity and GitHub OAuth
3. Visit `https://your-domain/admin` to publish via CMS

## Content structure

```
content/
├── about.md          # About page
└── posts/            # Posts
    ├── hello-world.md
    ├── sample-post-with-cover.md
    └── draft-example.md   # Draft example
```

### Front Matter example

```yaml
---
title: "Post title"
date: 2025-03-01
draft: false
description: "Summary"
tags: [tag1, tag2]
categories: [category]
cover:
  image: "Cover image URL"
  alt: "Alt text"
---
```

## Deployment

- **Netlify**: Connect GitHub repo, Build command: `hugo`, Publish directory: `public`
- **Vercel**: Same as Netlify
- **GitHub Pages**: Build with `hugo --baseURL "https://username.github.io/repo/"` and push to `gh-pages`

## References

- [Hugo docs](https://gohugo.io/documentation/)
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki)
- [Giscus](https://giscus.app)
