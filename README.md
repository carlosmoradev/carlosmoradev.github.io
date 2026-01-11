# carlosmora.dev

Personal portfolio and blog showcasing platform engineering, SRE expertise, and multi-cloud infrastructure work.

**Live site:** [carlosmora.dev](https://carlosmora.dev)

## Tech Stack

- **Jekyll** - Static site generator
- **GitHub Pages** - Hosting
- **BootstrapMade-inspired** - Custom responsive design

## Local Development

### Prerequisites

- Ruby 2.7+ (check with `ruby --version`)
- Bundler (install with `gem install bundler`)

### Clone the repository

**SSH (recommended):**
```bash
git clone git@mora-github.com:carlosmoradev/carlosmoradev.github.io.git
cd carlosmoradev.github.io
```

**HTTPS:**
```bash
git clone https://github.com/carlosmoradev/carlosmoradev.github.io.git
cd carlosmoradev.github.io
```

### Install dependencies

```bash
bundle install --path vendor/bundle
```

### Run local server

```bash
bundle exec jekyll serve --no-watch --host 0.0.0.0
```

**Note:** Using `--no-watch` to avoid inotify limits. You'll need to restart the server to see changes.

**Alternative port** (if 4000 is busy):
```bash
bundle exec jekyll serve --no-watch --host 0.0.0.0 --port 4001
```

Open http://localhost:4000 (or 4001) in your browser.

## Project Structure

```
carlosmora.dev/
├── _config.yml          # Site configuration
├── index.md             # Home page
├── about.md             # About page
├── projects.md          # Projects index
├── blog.md              # Blog index
├── _layouts/            # Page templates
├── _includes/           # Header/footer components
├── _projects/           # Project case studies
├── _posts/              # Blog posts (YYYY-MM-DD-title.md)
└── assets/css/          # Stylesheets
```

## Adding Content

### New Project

Create `_projects/project-name.md`:

```markdown
---
title: "Project Title"
description: "Short description"
tags: ["AWS", "Python", "Terraform"]
tech_stack: "AWS, GCP, Python"
impact: "95% reduction in manual work"
---

## The Challenge
...

## The Solution
...

## Results
...
```

### New Blog Post

Create `_posts/YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: "Post Title"
date: 2026-01-10
tags: ["multi-cloud", "automation"]
---

Your content here...
```

## Deployment

The site automatically deploys to GitHub Pages when you push to the `main` branch.

```bash
git add .
git commit -m "Your commit message"
git push
```

GitHub Pages will rebuild and deploy in 2-5 minutes.

## License

Content: © 2026 Carlos Mora. All rights reserved.
Code: MIT License

## Contact

- **Website:** [carlosmora.dev](https://carlosmora.dev)
- **Email:** hi@carlosmora.dev
- **GitHub:** [@carlosmoradev](https://github.com/carlosmoradev)
- **LinkedIn:** [carlosmoradev](https://linkedin.com/in/carlosmoradev)
