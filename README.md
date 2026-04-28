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
| `_pages/about.md` | About page |
| `_pages/year-archive.md` | Posts archive page |
| `_posts/` | Blog posts (filename format: `YYYY-MM-DD-slug.md`) |
| `_data/navigation.yml` | Top navigation menu |
| `assets/` | Images, PDFs, CSS |