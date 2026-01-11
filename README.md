# Carlos Mora - Portfolio Website

Personal portfolio and blog showcasing multi-cloud platform engineering, SRE expertise, and data platform governance work.

## Tech Stack

- **Jekyll**: Static site generator
- **GitHub Pages**: Hosting
- **Markdown**: Content writing
- **HTML/CSS**: Custom layouts and styling

## Local Development

### Prerequisites

- Ruby 2.7+ (check with `ruby --version`)
- Bundler (install with `gem install bundler`)

### Setup

1. **Clone the repository:**
```bash
git clone https://github.com/yourusername/carlos-mora-portfolio.git
cd carlos-mora-portfolio
```

2. **Install dependencies:**
```bash
bundle install
```

3. **Run local server:**
```bash
bundle exec jekyll serve
```

4. **View in browser:**
Open http://localhost:4000

The site will auto-reload when you make changes to files.

## Project Structure

```
carlos-mora-portfolio/
├── _config.yml              # Site configuration
├── Gemfile                  # Ruby dependencies
├── index.md                 # Home page
├── about.md                 # About page
├── projects.md              # Projects index
├── blog.md                  # Blog index
├── _layouts/                # Page templates
│   ├── default.html         # Base layout
│   ├── home.html            # Home layout
│   ├── page.html            # Page layout
│   ├── project.html         # Project layout
│   └── post.html            # Blog post layout
├── _includes/               # Reusable components
│   ├── header.html          # Site header
│   └── footer.html          # Site footer
├── _projects/               # Project case studies
│   └── snowflake-governance.md
├── _posts/                  # Blog posts (YYYY-MM-DD-title.md format)
├── assets/
│   ├── css/                 # Stylesheets
│   │   ├── style.css
│   │   └── syntax.css
│   └── diagrams/            # Architecture diagrams
└── .gitignore
```

## Adding Content

### Add a New Project

Create a new file in `_projects/` directory:

```markdown
---
title: "Your Project Title"
description: "Short description"
tags: ["tag1", "tag2"]
tech_stack: "Python, AWS, GCP"
impact: "Key metric or result"
---

## The Challenge

Describe the problem...

## The Solution

Describe your approach...

## Results

Show the impact...
```

### Add a New Blog Post

Create a new file in `_posts/` directory with format `YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: "Your Post Title"
date: 2026-01-10
tags: ["multi-cloud", "automation"]
author: "Carlos Mora"
---

Your content here...
```

### Add Images/Diagrams

1. Place images in `assets/diagrams/`
2. Reference in markdown:
```markdown
![Architecture diagram](/assets/diagrams/your-diagram.png)
```

## Configuration

### Update Site Settings

Edit `_config.yml`:

```yaml
title: Your Name
url: "https://yourusername.github.io"

author:
  name: Your Name
  email: your.email@example.com
  github: yourusername
  linkedin: yourlinkedin
```

### Customize Styling

Edit `assets/css/style.css` for visual customization.

## Deployment

### Deploy to GitHub Pages

1. **Create a GitHub repository:**
   - Name it: `yourusername.github.io` (for user site)
   - Or any name for a project site

2. **Initialize git and push:**
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git push -u origin main
```

3. **Enable GitHub Pages:**
   - Go to repository Settings → Pages
   - Source: Deploy from branch `main` / root
   - Save

4. **View your site:**
   - User site: `https://yourusername.github.io`
   - Project site: `https://yourusername.github.io/repo-name`

The site will automatically rebuild and deploy when you push changes to the main branch.

### Deploy to Netlify (Alternative)

1. Push your code to GitHub
2. Sign up at [Netlify](https://netlify.com)
3. New site from Git → Choose your repository
4. Build command: `jekyll build`
5. Publish directory: `_site`
6. Deploy

## Content Strategy

### Phase 1: MVP (Week 1)
- [x] Home page with hero section
- [x] About page
- [x] 1 featured project (Snowflake Governance)
- [ ] Deploy to GitHub Pages

### Phase 2: Content Expansion (Week 2-3)
- [ ] Add 2 more projects (Zero Trust Automation, IAM Audit Tool)
- [ ] Write first 2 blog posts
- [ ] Add architecture diagrams

### Phase 3: Enhancement (Week 4+)
- [ ] Add more blog posts (aim for 8-10 articles)
- [ ] Add certifications section details
- [ ] Consider newsletter signup
- [ ] Analytics integration (Google Analytics or Plausible)

## Sanitization Checklist

Before publishing any content, ensure:

- [ ] No client names (use "healthcare company", "data platform organization")
- [ ] No company names (Source Meridian → "consulting team" or omit)
- [ ] No AWS Account IDs, GCP Project IDs, or Snowflake account identifiers
- [ ] No URLs, IPs, or resource names
- [ ] No colleague or client contact names
- [ ] Metrics are percentages or ranges (not absolute numbers revealing client scale)
- [ ] Code examples are synthetic (not production code)
- [ ] Architecture diagrams are generic patterns (not real infrastructure)

## Writing Tips

1. **Focus on value**: What problem did you solve? What was the impact?
2. **Be specific about tech**: AWS services used, Python libraries, architectural patterns
3. **Show results**: Percentages, efficiency gains, scale improvements
4. **Tell a story**: Challenge → Solution → Results
5. **Code examples**: Short, illustrative snippets (not full production code)
6. **Diagrams help**: Visual architecture representations are powerful

## License

Content: © 2026 Carlos Mora. All rights reserved.
Code: MIT License (Jekyll templates and structure)

## Contact

Questions or suggestions? Reach out:
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourlinkedin)
- Email: your.email@example.com
