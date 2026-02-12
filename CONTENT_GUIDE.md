# Content Creation Guide

Quick reference for adding new content to your website.

---

## 📝 Adding a New Note (Short Thought)

**Location**: `_notes/`

**File naming**: `your-note-title.md` (use lowercase and hyphens)

**Template**:

```markdown
---
layout: post
title: "Your Note Title Here"
date: 2026-02-12
inline: false
related_posts: false
tags: [iot, development, thoughts]
---

Your content here. Keep it short and focused (200-800 words).

You can use **markdown formatting**, lists, code blocks, etc.
```

**Example**:

```bash
# Create file
_notes/my-new-thought.md

# Add content, commit, push
git add _notes/my-new-thought.md
git commit -m "Add new note about X"
git push
```

---

## 📰 Adding a Blog Post

**Location**: `_posts/`

**File naming**: `YYYY-MM-DD-your-post-title.md` (date is required!)

**Template**:

```markdown
---
layout: post
title: Your Blog Post Title
description: A short description for SEO and previews
tags: [iot, tutorial, esp32]
categories: [tutorials]
giscus_comments: true
date: 2026-02-12
featured: false
---

Your full blog post content here.

## Section Headings

- Lists
- Code blocks
- Images
- Whatever you need!
```

**Example**:

```bash
# Create file (note the date format!)
_posts/2026-02-12-building-iot-dashboard.md

# Add content, commit, push
git add _posts/2026-02-12-building-iot-dashboard.md
git commit -m "Add blog post about IoT dashboards"
git push
```

---

## 🚀 Adding a Project

**Location**: `_projects/`

**File naming**: `number_project.md` (e.g., `6_project.md`)

**Template**:

```markdown
---
layout: page
title: Your Project Name
description: Brief description of the project
img: assets/img/your-image.jpg
importance: 1
category: work
related_publications: false
---

## Project Overview

Detailed description of your project.

## Technical Implementation

**Hardware**: ESP32, sensors, etc.
**Software**: MQTT, Python, etc.

## Results

- Metric 1
- Metric 2

## Technologies Used

`ESP32` `MQTT` `Python` `AWS IoT`
```

**Example**:

```bash
# Create file (use next number in sequence)
_projects/6_project.md

# Add image (optional)
assets/img/my-project.jpg

# Commit and push
git add _projects/6_project.md assets/img/my-project.jpg
git commit -m "Add new project: Smart Home System"
git push
```

---

## 🖼️ Adding Images

**Location**: `assets/img/`

**Usage in markdown**:

```markdown
![Alt text]({{ '/assets/img/your-image.jpg' | relative_url }})
```

**For projects**: Specify in front matter

```yaml
img: assets/img/project-image.jpg
```

---

## ⚡ Quick Workflow

### From VS Code or Any Editor:

1. **Create the file** in the right folder with proper naming
2. **Copy a template** (from this guide or an existing file)
3. **Write your content** in markdown
4. **Save the file**
5. **Commit and push**:
   ```bash
   git add <your-file>
   git commit -m "Add new <type>: <title>"
   git push
   ```
6. **Wait ~2 minutes** for GitHub Actions to deploy
7. **Visit your site** to see the changes live!

---

## 📂 File Structure Quick Reference

```
asimzulfiqar.github.io/
├── _notes/              # Short thoughts (Notes page)
│   └── *.md
├── _posts/              # Blog posts (Blog page)
│   └── YYYY-MM-DD-*.md
├── _projects/           # Portfolio projects (Projects page)
│   └── *_project.md
├── _pages/              # Static pages
│   ├── about.md
│   ├── services.md
│   ├── cv.md
│   └── notes.md
└── assets/
    └── img/             # All images
```

---

## 🎨 Front Matter Options

### Common Options (all content types):

- `layout: post` - The template to use
- `title: "Title"` - Page/post title
- `date: YYYY-MM-DD` - Publication date
- `description: "..."` - SEO description
- `tags: [tag1, tag2]` - Tags for categorization

### Blog Post Specific:

- `categories: [category1]` - Categories
- `featured: true` - Feature on homepage
- `giscus_comments: true` - Enable comments
- `thumbnail: path/to/image.jpg` - Thumbnail image

### Project Specific:

- `img: path/to/image.jpg` - Project image
- `importance: 1` - Sort order (1 = highest)
- `category: work` - work or fun
- `redirect: https://...` - Link to external project

---

## 💡 Tips

- **Commit often**: Small, focused commits are easier to track
- **Test locally** (optional): Run `bundle exec jekyll serve` to preview
- **Use drafts**: Create files but don't commit until ready
- **Copy existing files**: Easiest way to get the format right
- **Check the build**: Visit Actions tab to ensure deployment succeeds

---

## 🆘 Common Issues

**Q: My post doesn't appear on the blog**

- Check the filename starts with `YYYY-MM-DD-`
- Ensure the date isn't in the future
- Check front matter is valid YAML

**Q: Images don't load**

- Use correct path: `assets/img/filename.jpg`
- Ensure image is committed to git
- Check file extension matches (.jpg vs .jpeg)

**Q: Site not updating**

- Check GitHub Actions tab for build errors
- Wait 2-3 minutes for deploy to complete
- Hard refresh browser (Ctrl+Shift+R)

---

**Need help?** Check the [al-folio documentation](https://github.com/alshedivat/al-folio) or ask me!
