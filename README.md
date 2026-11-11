# ChRIS: An Overview for HARBOR

Slides introducing ChRIS to the HARBOR consortium. The deck says what ChRIS is, why it is built around one small contract, and where it sits inside a HARBOR Trusted Domain.

The argument in one line: a ChRIS app is a container that reads a directory, writes a directory and exits, and a chain of those apps leaves behind a directory tree that is the provenance record. OpenShift governs the cluster. ChRIS makes the science that runs on it auditable.

## Presenting

The deck is a hub-and-spoke "nexus", the same shape as the [NSDF2026](https://github.com/rudolphpienaar/NSDF2026) talk: an outline (slide 3) from which sections are chosen live, so the same deck serves a ten-minute slot or an hour.

| Key | Action |
|---|---|
| `1`-`9`, or Up/Down + Enter, or click | open a section from the outline |
| Right / Left | next / previous (reveals bullets one at a time) |
| Backspace (or Esc) | back to the outline from anywhere in a section |
| `f` | toggle the deck's own fullscreen |

Running off the end of a section also returns to the outline, and visited sections are dimmed. In browser fullscreen use Backspace, since browsers keep Esc for leaving fullscreen.

## Building locally

The deck is written in [slidedown](https://github.com/FNNDSC/slidedown) (`talk.sd`, `command-line` theme) and compiles to static HTML in `talk/`.

```bash
# with a slidedown checkout at ~/src/slidedown, at or after commit 0711397
uv run --project ~/src/slidedown slidedown . talk --inputFile talk.sd --theme command-line
cd talk && python3 -m http.server 8000      # then open http://localhost:8000
```

The `command-line` theme, slide labels and the `.term{}`, `.takeaway{}` and `.source{}` blocks arrived with FNNDSC/slidedown#3 through #7. An older checkout will fail with an unknown theme.

## Deployment

`.github/workflows/pages.yml` builds the deck on every push to `master` and deploys `talk/` to GitHub Pages. slidedown is pinned to commit `0711397` so an upstream change can't break the deck unannounced. Bump the pin on purpose.

## Layout

| Path | What |
|---|---|
| `talk.sd` | the deck source |
| `docs/refs.bib` | every source behind a slide (BibTeX, with provenance notes) |
| `.github/workflows/pages.yml` | build and deploy |

## Sources

Slides that make a factual claim carry a source line, and the full references are in [`docs/refs.bib`](docs/refs.bib). The three published papers were checked against Crossref and PubMed. Statements about HARBOR come from the consortium's Task Description Document, which is an internal deliverable still under negotiation.

## License

[MIT](LICENSE) © 2026 Rudolph Pienaar
