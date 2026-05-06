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

Posts come from one of two paths: **direct authoring** (write straight to this repo) or **WeChat porting** (import an existing 公众号 article via a converter that lives in the private `WeChat-blog-porting` repo). Both produce a file at `_posts/YYYY-MM-DD-<slug>.md` with the same front-matter shape.

### Path 1 — Writing a post directly

1. Pick a slug — `<firstname>-<lastname>` in pinyin, all-lowercase ASCII (e.g. `xiaobo-zhang`, `david-reeb`). For repeat interviewees append `-2`, `-3`.
2. Create `_posts/YYYY-MM-DD-<slug>.md` with the publish date as the filename prefix.
3. Use this front-matter template:

   ```yaml
   ---
   title: "中文标题<br>English title"   # bilingual: separate the two languages with <br>; single-language is fine
   date: 2026-04-28 09:00:00 +0800
   byline:
     - qinyu                          # one or more slugs from _data/authors.yml
     - tianyueruan                    # (or raw Chinese names for non-team contributors)
   excerpt: "中文摘要句子。 English excerpt sentence."   # bilingual: separate with a space (not <br>); single-language is fine
   categories:
     - featured                       # exactly one of: featured | jmp | wisdom | essays | pioneer
   tags:
     - macro                          # one or more slugs from the Areas table above
     - labor
   ---
   ```

   `original_url:` is optional and only relevant for posts mirrored from WeChat.

   **Bilingual title and excerpt.** Titles use `<br>` between the Chinese and English line — they render as two lines on listing pages and on the post page, and the `<br>` is stripped from `<title>` / OpenGraph tags so social previews stay clean. Excerpts use a single space (not `<br>`), because the archive listing pipes excerpts through `strip_html` to keep tag-truncation safe; both languages render on one wrapping line. Keep each language ≤ ~25 Chinese chars / ~60 English chars per side so listings stay tidy.

4. Write the body in markdown below the front matter. Use `_posts/` for examples — keep credit lines (`责任编辑 | …`) at the bottom if relevant.
5. Preview locally with `bundle exec jekyll serve` (`http://localhost:4000/YYYY/MM/DD/<slug>/`).
6. Commit and push.

### Path 2 — Porting from WeChat

The converter and the URL backlog live in a separate **private** repo (`Impactful-Research/WeChat-blog-porting`) so the scraping tool isn't trivially cloneable. Ask a maintainer for access if you need to import. That repo's README documents the full porting workflow; from this repo's perspective, a ported post arrives as a new file under `_posts/` plus images under `assets/images/posts/<slug>/`, and from there the review/commit steps are the same as Path 1.

## Adding a new team member

Edit `_data/authors.yml` — add an entry with the pinyin slug as key, plus `name` (Chinese display) and `home` (personal URL):

```yaml
newperson:
  name: "新人"                          # Chinese display name shown in bylines
  home: "https://example.com/"         # personal URL the byline links to
```

If the new member's name will appear in WeChat-mirrored posts, **also update the matching dicts (`NAME_TO_SLUG` and `CREDIT_NAME_TO_URL`) in the converter script** — the converter lives in the private `WeChat-blog-porting` repo and needs to know how to map the Chinese name to your new slug. See that repo's README for details.

## Adding a new research area (tag)

Edit `_data/labels.yml` under the `tags:` block — add an entry with the new slug as key, plus `en` and `zh` display labels:

```yaml
tags:
  ...
  newarea:
    en: "New Field Name"
    zh: "新领域名称"
```

The per-area archive at `/tags/#newarea` picks it up automatically on the next build. Match the slug to a JEL broad letter when one applies.

## Adding a new series (category)

Same pattern as a new tag, but under the `categories:` block of `_data/labels.yml`. Use sparingly — categories distinguish the *interview format* (Featured / JMP / Wisdom / Essays / Pioneer), not the topic.

## Sidebar identity

Every post's right-hand sidebar shows the site brand "Impactful Research" (configured under `author:` in `_config.yml`), not per-post authors. This is intentional — per-post author info appears in the byline meta line, while the sidebar carries the publication identity. If you need to change avatar / bio / social links, edit `_config.yml`.
