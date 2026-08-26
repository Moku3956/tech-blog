# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

This repository is a [Zenn](https://zenn.dev) content repository, linked to a Zenn account via GitHub integration. Zenn watches this repo and publishes/updates articles and books automatically when changes are pushed to `main` — there is no build or deploy step to run manually.

## Commands

- `npx zenn preview` — start a local preview server for articles/books.
- `npx zenn new:article` — scaffold a new article under `articles/` with a generated slug and frontmatter.
- `npx zenn new:book` — scaffold a new book under `books/`.

There is no lint, build, or test suite in this repo (the `npm test` script is npm's default placeholder and does nothing meaningful).

## Structure

- `articles/*.md` — one Markdown file per article. Filename (minus `.md`) is the article's slug and must be unique; it's referenced in the article's URL on Zenn.
- `books/<book-slug>/` — one directory per book, containing a `config.yaml` and chapter Markdown files.

## Article frontmatter

Each file in `articles/` starts with YAML frontmatter, e.g.:

```yaml
---
title: "記事タイトル"
emoji: "😀"
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["javascript", "react"]
published: true
---
```

- `published: false` keeps an article as a draft (not visible on Zenn, but still previewable locally and safe to push).
- `type` must be exactly `tech` or `idea`.
- `topics` accepts up to 5 tags; lowercase alphanumeric is safest for matching Zenn's tag pages.

When creating or editing articles, preserve/validate this frontmatter shape — Zenn's publish pipeline depends on it parsing correctly.
