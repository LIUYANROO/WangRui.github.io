# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based academic personal homepage for 刘彦汝 (Rui Wang), a Master's student at Shenzhen University. The site uses GitHub Pages and supports bilingual content (Chinese and English).

## Build Commands

- **Start local server**: `bash run_server.sh` — runs `bundle exec jekyll liveserve` with live reload
- **Build for production**: `bundle exec jekyll build`
- **Serve locally**: `bundle exec jekyll serve`

## Key Dependencies

- **github-pages** gem (from Gemfile) — includes Jekyll, plugins, and dependencies for GitHub Pages compatibility
- **Plugins**: jekyll-feed, jekyll-sitemap, jekyll-gist, jekyll-redirect-from

## Site Architecture

### Content Structure
- `_pages/about.md` — English homepage content
- `_pages/about-cn.md` — Chinese homepage content
- `_data/navigation.yml` — navigation menu configuration
- `_config.yml` — site-wide settings (title, author info, SEO, Google Analytics, bilingual config)

### Layout & Includes
- `_layouts/default.html` — base page layout
- `_includes/` — partial components (head, masthead, sidebar, scripts, analytics, SEO)
- `_sass/` — Sass stylesheets (vendor subdirs for breakpoint, font-awesome, magnific-popup, susy)

### Google Scholar Integration
- `google_scholar_crawler/` — Python crawler for fetching citation stats
- `.github/workflows/google_scholar_crawler.yaml` — GitHub Action that runs daily and on push
- `_includes/fetch_google_scholar_stats.html` — include for displaying scholar stats
- `GOOGLE_SCHOLAR_ID` must be set in repository secrets for the crawler to work

### Displaying Paper Citations
To show citation count for a specific paper, use:
```html
<span class='show_paper_citations' data='PAPER_ID'></span>
```
Get the paper ID from Google Scholar URL: `citation_for_view=XXXXX`

## Configuration Notes

- Site title and description in `_config.yml` are bilingual (Chinese primary)
- Author profile fields include: name, avatar, bio, location, employer, email, Google Scholar, GitHub, etc.
- Bilingual toggle is configured via `languages` array in `_config.yml`
- Google Analytics ID is optional and configured in `_config.yml`
- SEO verification codes for Google, Bing, and Baidu can be added to `_config.yml`
