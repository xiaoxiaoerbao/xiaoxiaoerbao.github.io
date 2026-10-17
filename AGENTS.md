# AGENTS.md

## Project overview

This is the personal academic website of Daxing Xu / 许达兴 (university teacher and
researcher in bioinformatics, genomics, and programming education at Henan Institute of
Science and Technology), published as a GitHub Pages **user site** from the repository
`xiaoxiaoerbao/xiaoxiaoerbao.github.io` at <https://xiaoxiaoerbao.github.io>.

The site is a single static page: there is no framework, no JavaScript, no build step,
and no dependencies.

## Repository structure

```
.
├── _config.yml   # GitHub Pages / Jekyll config (single line: theme: jekyll-theme-cayman)
├── index.html    # The entire site: one self-contained Chinese (zh-CN) page
├── style.css     # All styling, hand-written CSS with custom properties
└── README.md     # Repo name only
```

- `index.html` (`lang="zh-CN"`) is a complete standalone HTML document with inline
  section anchors (`#about`, `#research`, `#teaching`, `#publications`, `#projects`,
  `#blog`, `#contact`) used by the sticky top navigation.
- `style.css` defines the design system via CSS custom properties in `:root`
  (`--accent`, `--accent-dark`, `--max-width`, `--radius`, `--shadow`, etc.) and
  responsive breakpoints at `860px` and `560px`.
- `_config.yml` sets `theme: jekyll-theme-cayman`. Because `index.html` has no Jekyll
  front matter it is served as-is; the theme would only matter if Markdown pages were
  added later.

## Technology stack

- Static HTML5 + hand-written CSS3 only. No JavaScript, no templating, no bundler.
- Hosted on GitHub Pages with implicit Jekyll processing (files without front matter
  pass through unchanged).
- No `package.json`, `Gemfile`, `pyproject.toml`, or any other manifest — do not add
  one unless the project scope changes.

## Build, test, and deployment

There is no build and no test suite.

- **Preview locally:** open `index.html` directly in a browser, or run a static server
  (e.g. `python3 -m http.server`) from the repo root. `jekyll serve` also works but is
  not required.
- **Deploy:** push to the `main` branch of the GitHub remote; GitHub Pages rebuilds and
  publishes automatically within a minute or two. There is no CI pipeline.
- **Verification after changes:** load the page, check the nav anchor links, and check
  layout at desktop width plus the `860px` and `560px` breakpoints (browser dev tools).

## Code style guidelines

- **Content language:** page copy is in Simplified Chinese; keep pinyin/English only for
  names and technical terms where helpful (e.g. `许达兴（Daxing Xu）`, `Java`, `R 语言`,
  `Linux`, `Shell`). Keep this convention when adding content.
- **HTML:** semantic elements (`header`, `nav`, `main`, `section`, `article`,
  `footer`); section `id`s must match the nav links; include `aria-label` on landmark
  regions as the existing markup does.
- **CSS:** add new colors/spacing as custom properties in `:root` rather than magic
  values; reuse existing classes (`.section`, `.card`, `.section-label`,
  `.muted-section`, etc.) before inventing new ones; keep layout responsive — any new
  grid section needs rules in both `@media` blocks.
- **Formatting:** 2-space indentation in both files, matching the existing code.
- Keep the site dependency-free; introduce tooling only if the maintainer asks.

## Security considerations

- The page contains no forms, scripts, or third-party assets; keep it that way unless
  explicitly requested.
- The contact section uses a placeholder email (`your.email@example.com`) — do not
  invent a real address; only fill it in if the maintainer provides one.
- Do not commit any private data, credentials, or unpublished personal information.
