# Mostly Harmless Econometrics — reading group website

Live site: <https://kevin123883.github.io/mostly-harmless-seminar/>

Built with [Quarto](https://quarto.org) and deployed to GitHub Pages by
[`.github/workflows/publish.yml`](.github/workflows/publish.yml).

## How it fits together

```
Overleaf ──(Menu → GitHub → Push)──▶ Kevin123883/Mostly-Harmless   (slides, LaTeX)
                                              │
                                              ▼  hourly check, or on push here
                              this repo: compile session*/session*.tex → render site → Pages
```

- **Slides** live in Overleaf and are pushed to
  [Kevin123883/Mostly-Harmless](https://github.com/Kevin123883/Mostly-Harmless).
  Each session has its own folder there (`session1/`, `session2/`, ...). Every
  `session*/session*.tex` is compiled to `slides/session*.pdf` on the site, so a
  recitation deck `session1/session1-1.tex` becomes `slides/session1-1.pdf`.
  Other `.tex` files (e.g. in `drafts/`) are ignored.
- **Site content** (group info, session pages) lives in this repo.

## Common tasks

**Update slides.** Edit in Overleaf, then Menu → GitHub → *Push Overleaf changes to GitHub*.
The site picks up the change within the hour. To publish immediately, open the
[Actions tab](../../actions/workflows/publish.yml) and click *Run workflow*, or run

```bash
gh workflow run publish.yml -R Kevin123883/mostly-harmless-seminar
```

**Add a session.** Copy `session-template.md` to `sessions/02.qmd` (keep the
two-digit number so sessions sort correctly), fill it in, and push. Put the slides at
`session2/session2.tex` in Overleaf so the link `../slides/session2.pdf` resolves.

**Post a recording.** Do not commit video files. Upload the recording to YouTube
(unlisted), Zoom cloud, Box, or Panopto, then either link it in the session page:

```markdown
- [Recording](https://...)
```

or embed a YouTube/Vimeo video with Quarto's video shortcode:

```markdown
{{< video https://www.youtube.com/watch?v=VIDEO_ID >}}
```

## Local preview

```bash
quarto preview
```

The slide PDFs are built only in CI; locally, drop a PDF into `slides/` to test links.

## Note

GitHub pauses scheduled workflows after 60 days without repository activity.
If slides stop updating automatically, push any commit here or run the workflow manually.
