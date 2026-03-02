---
title: "Sample Post - With Cover and Tags"
date: 2025-03-01
draft: false
description: "Shows full Front Matter config: cover image, tags, categories."
tags:
  - Example
  - Tutorial
categories:
  - Tech
cover:
  image: "https://images.unsplash.com/photo-1499750310107-5fef28a66643?w=1200"
  alt: "Code"
  caption: "Unsplash"
  hidden: false
---

A sample post demonstrating complete Front Matter configuration.

## Front Matter Fields

| Field | Description |
|-------|-------------|
| title | Post title |
| date | Publish date |
| draft | true=draft, false=published |
| description | Summary (shown on list page) |
| tags | Array of tags |
| categories | Array of categories |
| cover | Cover image config |

## Draft vs Published

- `draft: true`: Only visible with `hugo server -D`, excluded from production build
- `draft: false`: Published normally

## Multiple Authors (Optional)

Add `author` in Front Matter for multi-author blogs.

<!--more-->

More content...
