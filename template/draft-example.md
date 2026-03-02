---
title: "Draft Example - Visible in dev only"
date: 2025-03-01
draft: true
description: "Posts with draft: true only show when using hugo server -D"
tags:
  - Draft
categories:
  - Notes
---

This is a **draft** post. With `draft: true`:

- `hugo server -D` → visible
- `hugo server` → hidden
- `hugo` production build → excluded

Set `draft` to `false` to publish.
