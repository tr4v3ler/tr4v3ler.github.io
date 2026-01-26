## Blog setup (Hydejack)

This repository is configured to use the **Hydejack** Jekyll theme via
`remote_theme`. GitHub Pages will build the site automatically when you
push changes to the default branch.

### Update site metadata
Edit `_config.yml` and set:
- `title`
- `description`
- `url` (your GitHub Pages URL)
- `author.name` and `author.email`
- `author.picture` and `author.social`

### Publish a new post
1. Create a Markdown file under `_posts/`:
   - Naming format: `YYYY-MM-DD-title.md`
2. Use a front matter block like:

```
---
layout: post
title: "Your Post Title"
date: 2026-01-26 00:00:00 +0000
description: "One-line summary."
tags: [security, writeup]
---
```

3. Commit and push. GitHub Pages will rebuild automatically.

### Add an avatar
1. Add an image file at `assets/img/avatar.jpg` (or `.png`).
2. Set `author.picture` in `_config.yml` to match the path, e.g.:
   - `/assets/img/avatar.jpg`
3. Commit and push the image with your post updates.

### Remove the placeholder post
Delete `_posts/2026-01-26-welcome.md` when you are ready to publish real
content.
