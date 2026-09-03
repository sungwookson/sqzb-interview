# sglang-rbln 설계 리뷰 — SqueezeBits 2nd assessment

Beamer talk answering the 10 questions. Source is plain LaTeX so it round-trips
cleanly through git ⇄ Overleaf.

## Compile

- **Compiler: XeLaTeX** (needed for `kotex` + `fontspec`/`metropolis`).
- `latexmkrc` already forces it: `latexmk main.tex` locally.
- Overleaf: Menu → Compiler → **XeLaTeX**. (It usually auto-detects `fontspec`.)

## Use with Overleaf

**Option A — GitHub import (recommended, real co-working loop):**
1. Push this repo to GitHub.
2. Overleaf → New Project → *Import from GitHub* → pick this repo.
3. When Claude pushes a change, in Overleaf: *Menu → GitHub → Pull*.

**Option B — zip upload (zero setup):**
`zip -r talk.zip . -x '.git/*'` → Overleaf → New Project → *Upload Project*.

## Structure

```
main.tex            documentclass + \input each section
preamble.tex        theme, palette (brick red #C03221), \hd{} section-header macro
sections/
  00-intro.tex      title, agenda, "RBLN stack inferred from vllm-rbln"
  q01.tex … q10.tex  one topic per file — edit these
  99-close.tex      milestones / risks, thank-you
figures/
  q03-residual.tex  S = cached prefix + residual R  → bucket chosen from R
  q05-spectrum.tex  eager → JIT → capture → strict AOT
  q08-boundary.tex  host / device split for RadixAttention
```

## To fill in (personal experience)

- **Q7** — a concrete host-bottleneck measurement.
- **Q9** — static-graph decoding experience, or a graceful "haven't done it".
- **Q10** — a real latency-triage story.
- **Q4** — confirm the Qwen-VL details against your memory.

Full prose + anticipated follow-ups live in the Linear issues (SUN-31…40,
"Interview-ready (Qxx)" comments).
