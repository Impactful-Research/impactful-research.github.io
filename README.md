# impactful-research.github.io

Organization website / blog for Impactful Research. Built with [Jekyll](https://jekyllrb.com/) using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme, hosted on [GitHub Pages](https://pages.github.com/).

Live site: https://impactful-research.github.io

## Local Preview

```bash
bundle install                # first time only — installs Ruby gems
bundle exec jekyll serve      # starts local server at http://localhost:4000
```

Most file changes auto-reload in the browser. **Exception:** `_config.yml` changes require stopping the server (Ctrl-C) and re-running `bundle exec jekyll serve`.

If `bundle install` fails, check `ruby -v`. GitHub Pages uses Jekyll 3.9, which requires Ruby 3.x (not 4.0+). On macOS, install via `brew install ruby@3.3` — the system Ruby (2.6) is too old and Ruby 4.0 is too new.

## Key Files

| File | What to edit |
|------|-------------|
| `_config.yml` | Site settings, author bio, social links |
| `_pages/index.md` | Homepage |
| `_pages/about.md` | About page (mission, team, QR) |
| `_pages/year-archive.md` | `/year-archive/` (chronological browse) |
| `_pages/category-archive.md` | `/categories/` (browse by series) |
| `_pages/tag-archive.md` | `/tags/` (browse by area) |
| `_posts/` | Blog posts (filename format: `YYYY-MM-DD-slug.md`) |
| `_data/navigation.yml` | Top navigation menu |
| `_data/labels.yml` | Bilingual labels for series & areas (see below) |
| `assets/` | Images, PDFs, CSS |

## Editorial taxonomy · 编辑分类

Every post is classified along two dimensions, both stored in front matter:

- **Series** (`categories:`) — exactly one per post — the *interview format*.
- **Areas** (`tags:`) — one or more per post — the *research field(s)*, mapped to the JEL broad-letter classification.

Bilingual display labels for both live in [`_data/labels.yml`](_data/labels.yml). Slugs (the front-matter values) stay ASCII English so URLs and Liquid lookups remain stable; the YAML maps each slug to its `en` and `zh` display strings, which appear bilingually on the `/categories/` and `/tags/` pages.

### Series · 系列

| Slug | English | 中文 | What it covers |
|------|---------|------|----------------|
| `featured` | Featured | 影响力之作 | Interviews with established researchers about a specific high-impact paper |
| `jmp` | JMP | 就业市场论文 | Interviews with junior researchers about their job-market paper |
| `wisdom` | Research Insights | 做研究心得 | Field-level reflections from established scholars (not anchored to one paper) |
| `essays` | Essays | 随笔 | One-off contributed essays / op-eds (not interviews) |
| `pioneer` | Pioneer | 开拓者 | Interviews with researchers carving out new field areas |

### Areas · 领域 (JEL broad letters)

| Slug | English | 中文 | JEL |
|------|---------|------|-----|
| `econometrics` | Econometrics | 计量经济学 | C |
| `micro` | Microeconomics | 微观经济学 | D |
| `macro` | Macroeconomics | 宏观经济学 | E |
| `international` | International Economics | 国际经济学 | F |
| `finance` | Finance | 金融经济学 | G |
| `public` | Public Economics | 公共经济学 | H |
| `health-education` | Health & Education | 健康与教育 | I |
| `labor` | Labor Economics | 劳动经济学 | J |
| `law-econ` | Law & Economics | 法律与经济学 | K |
| `io` | Industrial Organization | 产业组织 | L |
| `business` | Business Administration | 工商管理 | M |
| `econ-history` | Economic History | 经济史 | N |
| `development` | Development Economics | 发展经济学 | O |
| `environment` | Environmental Economics | 环境经济学 | Q |
| `urban-regional` | Urban & Regional | 城市与区域经济学 | R |
| `culture` | Cultural Economics | 文化经济学 | Z |

## Adding a new post

Each post lives in `_posts/YYYY-MM-DD-<slug>.md` and needs front matter like:

```yaml
---
title: "教授姓名 谈 [paper] 创作心得"
date: 2026-04-28 09:00:00 +0800
author: "Interviewer name"
excerpt: "One-line teaser shown on listing pages."
categories:
  - featured                      # one of: featured | jmp | wisdom | essays | pioneer
tags:
  - macro                         # one or more slugs from the Areas table above
  - labor
original_url: https://mp.weixin.qq.com/s/...
---
```

If a post needs a new tag (e.g., a JEL area not yet in the Areas table), add an entry to `_data/labels.yml` with `en` and `zh` labels — the per-area archive page will pick it up automatically on the next build.

The first content block of each post should be the bilingual mirror note (one paragraph in Chinese, one in English) crediting the WeChat official account; see any existing post in `_posts/` for the exact template.
